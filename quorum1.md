# Quorum, la revancha

Bueno, me decepcionó un poco que c9 me fallará con respecto a virtualBox, pero bueno.

Quien no arriesga no gana. Compré una máquina virtual en Digital ocean, 3GB y 20GB SSD, con Ubuntu 16.04.3 x64

## [Instalando VirtualBox](https://www.virtualbox.org/wiki/Linux_Downloads)

```bash
$ uname -a
Linux quorum1 4.4.0-103-generic #126-Ubuntu SMP Mon Dec 4 16:23:28 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial
```

Ergo...

```bash
$ sudo apt-get update
$ sudo apt-get install gdebi-core
$ wget http://download.virtualbox.org/virtualbox/5.2.4/virtualbox-5.2_5.2.4-119785~Ubuntu~xenial_amd64.deb
$ sudo gdebi virtualbox-5.2_5.2.4-119785~Ubuntu~trusty_amd64.deb 
```

## [DKMS](https://github.com/Mange/rtl8192eu-linux-driver/issues/44)

El mismo error salió... pero no hay problema

```
$ sudo apt-get install linux-headers-$(uname -r) build-essential dkms
```

Pal recuerdo

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-4.4.0-103-generic is already the newest version (4.4.0-103.126).
linux-headers-4.4.0-103-generic set to manually installed.
The following package was automatically installed and is no longer required:
  grub-pc-bin
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  binutils cpp cpp-5 dpkg-dev fakeroot g++ g++-5 gcc gcc-5 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libasan2 libatomic1 libc-dev-bin libc6-dev libcc1-0 libcilkrts5 libdpkg-perl libfakeroot libfile-fcntllock-perl libgcc-5-dev libgomp1
  libisl15 libitm1 liblsan0 libmpc3 libmpx0 libquadmath0 libstdc++-5-dev libtsan0 libubsan0 linux-libc-dev make manpages-dev
Suggested packages:
  binutils-doc cpp-doc gcc-5-locales debian-keyring g++-multilib g++-5-multilib gcc-5-doc libstdc++6-5-dbg gcc-multilib autoconf automake
  libtool flex bison gdb gcc-doc gcc-5-multilib libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan2-dbg liblsan0-dbg libtsan0-dbg
  libubsan0-dbg libcilkrts5-dbg libmpx0-dbg libquadmath0-dbg glibc-doc libstdc++-5-doc make-doc
The following NEW packages will be installed:
  binutils build-essential cpp cpp-5 dkms dpkg-dev fakeroot g++ g++-5 gcc gcc-5 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libasan2 libatomic1 libc-dev-bin libc6-dev libcc1-0 libcilkrts5 libdpkg-perl libfakeroot libfile-fcntllock-perl
  libgcc-5-dev libgomp1 libisl15 libitm1 liblsan0 libmpc3 libmpx0 libquadmath0 libstdc++-5-dev libtsan0 libubsan0 linux-libc-dev make
  manpages-dev
0 upgraded, 37 newly installed, 0 to remove and 15 not upgraded.
Need to get 38.7 MB of archives.
After this operation, 144 MB of additional disk space will be used.
Do you want to continue? [Y/n]
```

Yes.

## Reintentando

```bash
$ sudo gdebi virtualbox-5.2_5.2.4-119785~Ubuntu~trusty_amd64.deb 
```

Esta vez se demora por algo del user group... quiero creer que es una buena señal.

```
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reading state information... Done

Oracle VM VirtualBox
 VirtualBox is a powerful PC virtualization solution allowing you to run a
 wide range of PC operating systems on your Linux system. This includes
 Windows, Linux, FreeBSD, DOS, OpenBSD and others. VirtualBox comes with a broad
 feature set and excellent performance, making it the premier virtualization
 software solution on the market.
Do you want to install the software package? [y/N]:y
(Reading database ... 60876 files and directories currently installed.)
Preparing to unpack virtualbox-5.2_5.2.4-119785~Ubuntu~xenial_amd64.deb ...
Unpacking virtualbox-5.2 (5.2.4-119785~Ubuntu~xenial) over (5.2.4-119785~Ubuntu~xenial) ...
Setting up virtualbox-5.2 (5.2.4-119785~Ubuntu~xenial) ...
addgroup: The group 'vboxusers' already exists as a system group. Exiting.
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
```

Wuju!

Ahora, en teoría debería aprender como manipular VirtualBox y tal... pero no, ya es mucho por hoy.

Aunque el crear máquinas virtuales suena tentador.

Tal vez mañana, solo por diversión, cree una máquina virtual dentro y realizar el tutorial ahí (instalándole de nuevo VirtualBox y todo).

Por cierto, ahora que tengo que instalar npm desde cero, me encontré con esto [[3]].

## Instalando VirtualBox (resumen)

```bash
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial
```

```bash
$ sudo apt-get update
$ sudo apt-get install linux-headers-$(uname -r) build-essential dkms
$ sudo apt-get install gdebi-core
$ wget http://download.virtualbox.org/virtualbox/5.2.4/virtualbox-5.2_5.2.4-119785~Ubuntu~xenial_amd64.deb
$ sudo gdebi virtualbox-5.2_5.2.4-119785~Ubuntu~xenial_amd64.deb
```

Yup, todo un día para eso.

## Instalando Vagrant

Esta vez intentaré algo distinto...

Ugh, había un comando para buscar los paquetes por nombre y reg, y encima me decía los que tenía instalado.

En fin, creo que he estado instalando mal todo este tiempo los paquetes...

```bash
$ apt install vagrant
$ vagrant -v 
Vagrant 1.8.1
```

Ojalá esto nos sirva.

Vagrant es un manejador o administrados de programas de virtualización. Esto es, puedes crear un archivo que maneje todos los aspectos de configuración al momento de crear máquinas virtuales. Puedes crear varias, cada una con una programación determinada, en vez de estar haciéndolo uno por uno, manualmente, abriendo VirtualBox o VMWare. Uno pensaría que estos programas tendrías su propia forma de hace esto, pero bueno.

Por defecto Vagrant funciona con VirtualBox, yay.

Edit: No, no sirve, maldito apt

```
$ wget https://releases.hashicorp.com/vagrant/2.0.1/vagrant_2.0.1_x86_64.deb?_ga=2.132644814.1590067383.1513891582-1167772899.1513891582
```

## Instalando npm

```
$ apt install npm
$ npm -v 
3.5.2
```

## Instalando node

```bash
$ apt install nodejs-legacy
$ node -v
v4.2.6
```

¡No usar apt-get!

Seguir esta guía para installar node (la parte de NMV): https://www.godaddy.com/help/install-nodejs-ubuntu-17395

```bash
$ nvm install 8.9.3
$ node -v
v8.9.3
$ npm -v
5.5.1
```

## Instalando Truffle

```
$ npm install -g truffle
$ truffle version
Truffle v4.0.4 (core: 4.0.4)
Solidity v0.4.18 (solc-js)
```

## Installation Bash Script

En caso de que tenga que volver a hacer todo esto de nuevo, escribiré un script bash donde estén todos estos comandos:

```bash
# Instalando

# Revisando Versiones

echo 'Version de nodejs'
node -v

echo 'Version de npm'
npm -v

echo 'Version de truffle y solidity'
truffle version
```

## Ahora sí, quorum

No, esto no tiene un final feliz, la razón es esto:

https://www.digitalocean.com/community/questions/vagrant-and-virtualbox-gurumeditation-problem

Sin embargo, al parecer no es necesario intalar vagrant, solo ejecutar el sh que viene en el ejemplo...

## Unit Testing

# Links

[3]: https://itsfoss.com/apt-vs-apt-get-difference/