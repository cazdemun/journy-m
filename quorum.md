# Desarrollando para Quorum

## ¿Será posible desarrollar para Quorum en c9?

Esa es la pregunta del millón.

Por lo pronto, según [este tutorial][1]oficial de Truffle necesito instalar VirtualBox y Vagrant.

Me pregunto como funcionará VirtualBox sin una GUI... tal vez sea mucho más manejable.

O tal vez no.

No quiero sonar negativo, pero la verdad no creo que sea posible. Sobretodo con el tema del espacio.

## Instalando VirtualBox

Primero, voy a la página oficial y descargo el link con wget.

Veo que el archivo tiene una extension .deb

Flash-backs del curso de Administración de la Información, creo que ya sé lo que debo hacer.

En [[2]] están los enlaces de descarga. Para saber cual es cual, necesito saber la versión de la máquina de c9.

```bash
$ uname -a
Linux cazdemun-quorum-5783640 4.9.17-c9 #1 SMP Thu Mar 23 01:38:54 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:        14.04
Codename:       trusty
```

Con un click derecho->guardar ruta del enlace basta. Gracias a las intrucciones en [[3]], sé como lidiar con una extensión .deb, 

```bash
$ sudo apt-get update
$ sudo apt-get install gdebi-core
$ wget http://download.virtualbox.org/virtualbox/5.2.4/virtualbox-5.2_5.2.4-119785~Ubuntu~trusty_amd64.deb
$ sudo gdebi virtualbox-5.2_5.2.4-119785~Ubuntu~trusty_amd64.deb 
```

Y aquí debería acabar la historia...

## Empezando de nuevo...

Luego de la última línea, esto es lo que ocurre.

```bash
.
.
.
Adding group 'vboxusers' (GID 118) ...
Done.
This system is currently not set up to build kernel modules.
Please install the Linux kernel "header" files matching the current kernel
for adding new hardware support to the system.
This system is currently not set up to build kernel modules.
Please install the Linux kernel "header" files matching the current kernel
for adding new hardware support to the system.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.11) ...
```

En [este link de StackOverflow][4] dicen que es necesario agregar esta línea antes de la instalación:

```bash
$ sudo apt-get install xserver-xorg xserver-xorg-core
```

No funcionó... a probar [instalando el dkms][5], que es para habilitar kernels dinámicos o algo así.

```
$ sudo apt-get install git linux-headers-generic build-essential dkms
```

No funciona... pero en el mismo [[5]] dice algo sobre el paquete específico en vez de la parte linux-headers-generics. Creo que el paquete específico es el que sale cuando escribes uname -r.

```
$ uname -r
$ sudo apt-get install git linux-headers-4.9.17-c9 build-essential dkms

E: Unable to locate package linux-headers-4.9.17-c9
E: Couldn't find any package by regex 'linux-headers-4.9.17-c9'
```

Ummm, qué extraño, no encuentra los paquetes. En [[6]] y [[7]] hablan sobre sitios para encontrar paquetes... pero la verdad es que creo que el problema está en otro lado.

## I can´t see

Obviamente no puedo iniciar una GUI, por lo que en [[5]] me entré que hay una opción para iniciar la VM sin la interfaz gráfica:

```
$ VBoxManage startvm "VM name" --type headless
```

VBoxManage version --type headless

## [I surrender][8]

```
Software that is not supported in Cloud9 workspaces:

    Virtualbox, KVM, VMWare and other virtualization software
    Docker, RKT, Rocket, LXD and other similar containerization software and other virtualization software
    OpenVPN
```

## Conclusiones

Fue entretenido gastar toda la tarde, aprendí ciertas cosas... pero la verdad un curso sobre arquitectura de computadoras y sistemas operativos no me vendría mal.

Al parecer el problema en realidad es no tener priviliegios en el contenedor de docker. Además, la versión del kernel de c9 es una versión propia, si no me equivoco, por el nombre.

Parecer ser que ha llegado el momento de sacar la caballería pesada.

Sí, esto es, una cuenta premium en c9 para poder usar una máquina virtual de DigitalOcean con esa IDE.

Sé que puedo trabajar sin necesidad de la cuenta premium, pero la verdad me cansa el estar usando nano y pasar cosas a través del ssh a cada rato.

No olvidar, sin embargo, que todo esto es solo para ejecutar quorum. La verdad no creo que sean necesarias las máquinas virtuales (siempre puedo tratar cada contenedor de c9 como una máquina virutal), pero el tutorial las pide, y sin el tutorial estoy perdido.

Un link adicional: <https://github.com/boot2docker/boot2docker/issues/897>

Creo que en un futuro podré sacarle la vuelta a c9 e instalarlo... tal vez.

# Links

[1]: http://truffleframework.com/tutorials/building-dapps-for-quorum-private-enterprise-blockchains
[2]: https://www.virtualbox.org/wiki/Linux_Downloads
[3]: https://www.rstudio.com/products/rstudio/download-server/
[4]: https://askubuntu.com/questions/98416/error-kernel-headers-not-found-but-they-are-in-place
[5]: https://github.com/Mange/rtl8192eu-linux-driver/issues/44
[6]: https://askubuntu.com/questions/378558/unable-to-locate-package-while-trying-to-install-packages-with-apt
[7]: https://packages.ubuntu.com/
[8]: https://docs.c9.io/docs/software-we-do-not-support

```
[1]: http://truffleframework.com/tutorials/building-dapps-for-quorum-private-enterprise-blockchains
[2]: https://www.virtualbox.org/wiki/Linux_Downloads
[3]: https://www.rstudio.com/products/rstudio/download-server/
[4]: https://askubuntu.com/questions/98416/error-kernel-headers-not-found-but-they-are-in-place
[5]: https://github.com/Mange/rtl8192eu-linux-driver/issues/44
[6]: https://askubuntu.com/questions/378558/unable-to-locate-package-while-trying-to-install-packages-with-apt
[7]: https://packages.ubuntu.com/
[8]: https://docs.c9.io/docs/software-we-do-not-support
```