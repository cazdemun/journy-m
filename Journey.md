# Creando aplicaciones Android en c9 / CloudNine

Esta es, tal vez, mi tutorial más ambicioso hasta la fecha. Manos a la obra.

# Pequeña intro

Hasta donde he visto, para construir una aplicación solo son necesarias tres cosas:

* La carpeta del proyecto

* JDK 

* Android SDK

Le rezaré a los cielos para que el JDK ya esté instalado:

```
$ java -version

java version "1.7.0_151"
OpenJDK Runtime Environment (IcedTea 2.6.11) (7u151-2.6.11-0ubuntu1.14.04.1)
OpenJDK 64-Bit Server VM (build 24.151-b01, mixed mode)
```

En cuanto a la carpeta del proyecto siempre puedo descargarme un hola mundo de GitHub, aunque por ahí leí que habían problemas duplicando proyectos, ¿tal vez por algo en el Gradle? 

El Android SDK es el problema. 

## Android SDK

No entiendo si es un programa que se ejecuta al inicio, o tan solo un conjunto de subprogramas o archivos bash, que es lo que parece ser cuando descomprimo la carpeta.
En fin, en [[4]], en la parte de abajo, está el link de descarga para Linux, 130 mb.
Copiar el link y escribir lo siguiente (basado en [[1]]):

```
$ mkdir android_sdk
$ cd android_sdk
$ wget https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip
$ unzip sdk-tools-linux-3859397.zip 
```

En teoría el SDK ya está instalado. Según [[6]], en tools/bin/sdkmanager se pueden instalar y actualizar los paquetes.
Ahora... ¿a qué le llama paquetes? 
¿A cada uno de los archivos sh como screenshot2 o lint?
¿Solo los ejecuto cuando necesito algo o tengo que hacer un make o build o instalarlos o algo?
¿No existe alguna forma de inicializar todo con el SDK?
¿Un script que genere un proyecto en blanco o algo?

### Problemas en el purgatorio

Intenté ejecutar lo siguiente

```
$ cd android_sdk/tools/bin
$ ./sdkmanager --list
Exception in thread "main" java.lang.UnsupportedClassVersionError: com/android/sdklib/tool/SdkManagerCli : Unsupported major.minor version 52.0
        at java.lang.ClassLoader.defineClass1(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:803)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:442)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:64)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:354)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:348)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:347)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:425)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:312)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:358)
        at sun.launcher.LauncherHelper.checkAndLoadMain(LauncherHelper.java:482)
```

En [[7]] dicen que es por la versión de Java...

Felizmente encontré justo lo que necesitaba en [[8]] y en [[9]]

```
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get install oracle-java8-installer
```

Darle enter a todo lo que pida.

### Update Android SDK

Al parecer, la versión del SDK está aaalgo desactualizada.
Si ejecutas el comando update es probable que te tire error por un archivo en especial (repositories.cfg).
Según [[10]], solamente hay que crear dicho archivo con touch.

```
$ cd android_sdk/tools/bin
$ ./sdkmanager --list
$ touch ~/.android/repositories.cfg
$ ./sdkmanager --update
```

Deberían instalarse las carpetas emulator, patcher y platform-tools. 
Eliminaré la de emulator por el espacio.
Por cierto, hay que hacer de nuevo esto:

```
$ cd android_sdk/tools/bin
$ ./sdkmanager --list
```

Porque luego del update, por algún motivo, el path te queda inutilizable hasta que vuelves a entrar.

## Android App File System

Intuyo que el que Android sea bastante dependiente de su sistema de archivos es culpa de Java.
En fin, las aplicaciones en Android tienen sus archivos cada uno en un sitio fijo, 
y he aquí un pequeño gráfico porque los árboles de directorios siempre me han mareado más de la cuenta.


Fuentes [[2]][[3]]

# Links

[[1]] https://stackoverflow.com/questions/34556884/how-to-install-android-sdk-on-ubuntu

[1]: https://stackoverflow.com/questions/34556884/how-to-install-android-sdk-on-ubuntu

[[2]]: https://developer.android.com/studio/projects/index.html

[2]: https://developer.android.com/studio/projects/index.html

[[3]]: https://www.youtube.com/watch?v=kT6JFvLxoxs

[3]: https://www.youtube.com/watch?v=kT6JFvLxoxs

[[4]]: https://developer.android.com/studio/index.html

[4]: https://developer.android.com/studio/index.html

[[5]]: https://community.c9.io/t/android-app-emulation/6382

[5]: https://community.c9.io/t/android-app-emulation/6382

[[6]] https://developer.android.com/studio/command-line/index.html

[6]: https://developer.android.com/studio/command-line/index.html

[[7]] https://stackoverflow.com/questions/22489398/unsupported-major-minor-version-52-0

[7]: https://stackoverflow.com/questions/22489398/unsupported-major-minor-version-52-0

[[8]] http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html

[8]: http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html

[[9]] https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04

[9]: https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-ubuntu-16-04

[[10]] https://askubuntu.com/questions/885658/android-sdk-repositories-cfg-could-not-be-loaded

[10]: https://askubuntu.com/questions/885658/android-sdk-repositories-cfg-could-not-be-loaded
