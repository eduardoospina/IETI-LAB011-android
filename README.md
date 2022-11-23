# IETI-LAB011-android

## AUTOR.

Eduardo Ospina Mejia


## Inyeccion



En este parte tienes que implementar la configuración para poder utilizar inyección de dependencias con Hilt en tu Task Planner App. El laboratorio muestra el código ejemplo para implementar el modelo de inyección de dependencias utilizando un ejemplo ( GoogleAnalyticsService ). La idea es que apliques el mismo concepto para tu configuración de Retrofit y en base al anterior laboratorio

    1) Agrega la dependencia y plugin necesarios para hacer funcionar Hilt:

![](https://i.postimg.cc/bNM1n88g/hilt-1.png)

![](https://i.postimg.cc/DwXLdDwT/hilt-2.png)

![](https://i.postimg.cc/hGRxCrX7/hilt-3.png)

![](https://i.postimg.cc/vm7nCVn2/hilt-4.png)

![](https://i.postimg.cc/xCtz1VtK/hilt-5.png)

![](https://i.postimg.cc/4yyhK2Sj/hilt-6.png)

    2) Añade en el build.gradle a nivel de proyecto el siguiente plugin:

    buildscript {
    	...
    	ext.hilt_version = '2.40'
    	dependencies {
    	    ...
    	    classpath "com.google.dagger:hilt-android-gradle-plugin:$hilt_version"    
        }
    }

![](https://i.postimg.cc/4yyhK2Sj/hilt-6.png)

![](https://i.postimg.cc/2j9WpmqY/hilt-7.png)

    3) agrega en el build.gradle del app el plugin que acabaste de instalar

    plugins { 
       ...
       id 'dagger.hilt.android.plugin'
    }
    android {
       ...
    }

![](https://i.postimg.cc/FH3kJLTF/hilt-8.png)

    4) Añade la dependencia de hilt a tu app build.gradle de la siguiente manera:

     implementation "com.google.dagger:hilt-android:$hilt_version"
     annotationProcessor 'com.google.dagger:hilt-compiler:$hilt_version'

![](https://i.postimg.cc/SK42LxP6/hilt-9.png)



    5) Crea una clase que extienda a Application ( de android.app.Application ), agrega la anotación de Hilt:

    @HiltAndroidApp
    class ExampleApplication extends Application() { ... }

![](https://i.postimg.cc/pVSmGZ7X/hilt-10.png)

    6) Define la clase módulo de inyección:

    @Module
    @InstallIn(SingletonComponent.class)
    class AnalyticsModule {
        @Provides 
        public AnalyticsService provideAnalyticsService() { 
    	    return GoogleAnalyticsService() 
    	}
    }

![](https://i.postimg.cc/LXXsvY31/hilt-11.png)

    7) Anota alguna de tus actividades con @AndroidEntryPoint e inyecta tu modulo para verificar que funciona:

    @Inject
    AnalyticsService analyticsService;

![](https://i.postimg.cc/3Rcxq8tb/hilt-12.png)

Envía el link de tu repositorio público con tu solución:
