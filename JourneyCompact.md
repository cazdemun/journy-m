# Creando aplicaciones Android en c9 / CloudNine

## Instalar Java 8

```
$ java -version
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get -y install oracle-java8-installer
$ java -version
```
## Instalar Android SDK

```
$ mkdir android_sdk
$ cd android_sdk
$ wget https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip
$ unzip sdk-tools-linux-3859397.zip 
$ rm sdk-tools-linux-3859397.zip 
```

## Actualizar Android SDK

```
$ cd ~/workspace/android_sdk/tools/bin
$ ./sdkmanager --list
$ touch ~/.android/repositories.cfg
$ ./sdkmanager --update

$ cd ~/workspace/android_sdk/tools/bin
$ ./sdkmanager --list
$ cd ~/workspace/android_sdk/
$ rm -rf emulator
```
