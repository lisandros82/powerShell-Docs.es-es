---
title: Instalación de PowerShell Core en Linux
description: Información sobre cómo instalar PowerShell Core en varias distribuciones Linux
ms.date: 07/19/2019
ms.openlocfilehash: 3b0b9b1520247fa49760e631c837196fb7107b5f
ms.sourcegitcommit: cab4e4e67dbed024864887c7f8984abb4db3a78b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2020
ms.locfileid: "76022270"
---
# <a name="installing-powershell-core-on-linux"></a>Instalación de PowerShell Core en Linux

Admite [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] y [Arch Linux][arch].

Para las distribuciones de Linux que no se admiten de forma oficial, puede probar a instalar PowerShell con el [Paquete Snap de PowerShell][snap]. También puede intentar implementar los archivos binarios de PowerShell directamente mediante el [archivo `tar.gz`][tar] de Linux, pero tendrá que configurar las dependencias necesarias según el sistema operativo en pasos independientes.

Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub. Una vez instalado el paquete, ejecute `pwsh` desde un terminal. Ejecute `pwsh-preview` si instaló una [versión preliminar](#installing-preview-releases).

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb8]: #debian-8
[deb9]: #debian-9
[deb10]: #debian-10
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

> [!TIP]
> Si ya tiene instalado el [SDK de .NET Core](/dotnet/core/sdk), es fácil instalar PowerShell como una [herramienta global de .NET](/dotnet/core/tools/global-tools).
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="installing-preview-releases"></a>Instalación de versiones preliminares

Al instalar una versión preliminar de PowerShell Core para Linux mediante un repositorio de paquetes, el nombre del paquete cambia de `powershell` a `powershell-preview`.

La instalación mediante la descarga directa solo cambia el nombre de archivo.

La tabla siguiente contiene los comandos para instalar los paquetes estables y de versión preliminar mediante los diversos administradores de paquetes:

|Distribuciones|Comando estable | Comando de versión preliminar |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Instalación mediante un repositorio de paquetes, Ubuntu 16.04

PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.

El método preferido es el siguiente:

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Como superusuario, registre el repositorio de Microsoft una vez. Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Instalación mediante descarga directa, Ubuntu 16.04

Descargue el paquete de Debian `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.

Luego, ejecute los comandos siguientes en el terminal:

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> El comando `dpkg -i` produce un error con las dependencias unmet. El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Desinstalación, Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

### <a name="installation-via-package-repository---ubuntu-1804"></a>Instalación mediante un repositorio de paquetes, Ubuntu 18.04

PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.

El método preferido es el siguiente:

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Como superusuario, registre el repositorio de Microsoft una vez. Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Instalación mediante descarga directa, Ubuntu 18.04

Descargue el paquete de Debian `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.

Luego, ejecute los comandos siguientes en el terminal:

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> El comando `dpkg -i` produce un error con las dependencias unmet. El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.

### <a name="uninstallation---ubuntu-1804"></a>Desinstalación, Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

La instalación se admite a través de `snapd`. Para ver instrucciones, consulte [Paquete Snap][snap].

> [!NOTE]
> Ubuntu 18.10 es una [versión provisional](https://www.ubuntu.com/about/release-cycle) que [la comunidad admite](../powershell-support-lifecycle.md).

## <a name="ubuntu-1904"></a>Ubuntu 19.04

La instalación se admite a través de `snapd`. Para ver instrucciones, consulte [Paquete Snap][snap].

> [!NOTE]
> Ubuntu 19.04 es una [versión provisional](https://www.ubuntu.com/about/release-cycle) que [la comunidad admite](../powershell-support-lifecycle.md).

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Instalación mediante un repositorio de paquetes, Debian 8

PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.

El método preferido es el siguiente:

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Como superusuario, registre el repositorio de Microsoft una vez. Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Instalación mediante un repositorio de paquetes, Debian 9

PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.

El método preferido es el siguiente:

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Como superusuario, registre el repositorio de Microsoft una vez. Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---debian-9"></a>Instalación mediante descarga directa, Debian 9

Descargue el paquete de Debian `powershell_7.0.0-1.debian.9_amd64.deb` desde la página de [versiones][] en la máquina Debian.

Luego, ejecute los comandos siguientes en el terminal:

```sh
sudo dpkg -i powershell_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Desinstalación, Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a>Debian 10

> [!NOTE]
> Debian 10 solo es compatible con PowerShell 7.0 y versiones más recientes.

### <a name="installation-via-direct-download---debian-10"></a>Instalación mediante descarga directa, Debian 10

Descargue el paquete tar.gz `powershell_7.0.0-preview-7-linux-x64.tar.gz` desde la página de [versiones][] en la máquina Debian.

Luego, ejecute los comandos siguientes en el terminal:

```sh
sudo apt-get update
# install the requirements
sudo apt-get install -y \
        less \
        locales \
        ca-certificates \
        libicu63 \
        libssl1.1 \
        libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        liblttng-ust0 \
        libstdc++6 \
        zlib1g \
        curl

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0-preview.4/powershell-7.0.0-preview.4-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7-preview

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7-preview

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7-preview/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7-preview/pwsh /usr/bin/pwsh-preview

# Start PowerShell
pwsh-preview
```

## <a name="alpine-39-and-310"></a>Alpine 3.9 y 3.10

> [!NOTE]
> Alpine 3.9 y 3.10 solo son compatibles con PowerShell 7.0. y versiones más recientes.

### <a name="installation-via-direct-download---alpine-39-and-310"></a>Instalación mediante descarga directa, Alpine 3.9 y 3.10

Descargue el paquete tar.gz `powershell_7.0.0-preview-7-linux-x64.tar.gz` desde la página de [versiones][] en la máquina Alpine.

Luego, ejecute los comandos siguientes en el terminal:

```sh
# install the requirements
sudo apk add --no-cache \
    ca-certificates \
    less \
    ncurses-terminfo-base \
    krb5-libs \
    libgcc \
    libintl \
    libssl1.1 \
    libstdc++ \
    tzdata \
    userspace-rcu \
    zlib \
    icu-libs \
    curl

sudo apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
    lttng-ust

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0-preview.4/powershell-7.0.0-preview.4-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7-preview

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7-preview

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7-preview/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7-preview/pwsh /usr/bin/pwsh-preview

# Start PowerShell
pwsh-preview
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Este paquete funciona en Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Instalación mediante un repositorio de paquetes (opción preferida), CentOS 7

PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación y las actualizaciones.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Como superusuario, registre el repositorio de Microsoft una vez. Después del registro, puede actualizar PowerShell con `sudo yum update powershell`.

### <a name="installation-via-direct-download---centos-7"></a>Instalación mediante descarga directa, CentOS 7

Cuando use [CentOS 7][], descargue el paquete RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina CentOS.

Luego, ejecute los comandos siguientes en el terminal:

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

Puede instalar el paquete RPM sin el paso intermedio de descargarlo:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Desinstalación, CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Instalación a través de un repositorio de paquetes (opción preferida), Red Hat Enterprise Linux (RHEL) 7

PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación y las actualizaciones.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Como superusuario, registre el repositorio de Microsoft una vez. Después del registro, puede actualizar PowerShell con `sudo yum update powershell`.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Instalación mediante descarga directa, Red Hat Enterprise Linux (RHEL) 7

Descargue el paquete RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Red Hat Enterprise Linux.

Luego, ejecute los comandos siguientes en el terminal:

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

Puede instalar el paquete RPM sin el paso intermedio de descargarlo:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Desinstalación, Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>openSUSE

### <a name="installation---opensuse-423"></a>Instalación, OpenSUSE 42.3

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a>Instalación, openSUSE Leap 15

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Desinstalación, openSUSE 42.3 y openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 solo se admite en PowerShell Core 6.1 y versiones más recientes.

> [!NOTE]
> Fedora 29 y 30 solo son compatibles con PowerShell 7.0 y versiones más recientes.

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a>Instalación mediante un repositorio de paquetes (opción preferida), Fedora 28, 29 y 30

PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación y las actualizaciones.

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a>Instalación mediante descarga directa, Fedora 28, 29 y 30

Descargue el paquete RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Fedora.

Luego, ejecute los comandos siguientes en el terminal:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

Puede instalar el paquete RPM sin el paso intermedio de descargarlo:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a>Desinstalación, Fedora 28, 29 y 30

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> Microsoft no admite de forma oficial la compatibilidad con Arch, cuyo mantenimiento lo realiza la comunidad.

PowerShell está disponible en el repositorio de usuario [Arch Linux][] (AUR).

* Se puede compilar con la [versión etiquetada más reciente][arch-release].
* Se puede compilar desde la [última confirmación en maestro][arch-git].
* Se puede instalar mediante el [binario de la versión más reciente][arch-bin].

Los paquetes del AUR se mantienen gracias a la comunidad, ya que no hay asistencia oficial.

Para más información sobre cómo instalar paquetes desde el AUR, vea la [wiki de Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la comunidad.

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Paquete Snap

### <a name="getting-snapd"></a>Obtención de snapd

`snapd` es necesario para ejecutar paquetes Snap. Use [estas instrucciones](https://docs.snapcraft.io/core/install) para asegurarse de que tiene `snapd` instalado.

### <a name="installation-via-snap"></a>Instalación mediante Snap

PowerShell Core para Linux se publica en la [Snap store](https://snapcraft.io/store) para facilitar la instalación y las actualizaciones.

El método preferido es el siguiente:

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Para instalar una versión preliminar, use el método siguiente:

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Después de la instalación, Snap se actualizará automáticamente. Puede desencadenar una actualización mediante `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Desinstalación

```sh
sudo snap remove powershell
```

or

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

> [!NOTE]
> Microsoft no admite de forma oficial la compatibilidad con Kali, cuyo mantenimiento lo realiza la comunidad.

### <a name="installation---kali"></a>Instalación, Kali

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>Desinstalación, Kali

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> La compatibilidad con Raspbian es experimental.

Actualmente, PowerShell solo se admite en Raspbian Stretch.

CoreCLR y PowerShell Core solo funcionarán en dispositivos Pi 2 y Pi 3 dado que otros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tienen un procesador no admitido.

Descargue [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) y siga las [instrucciones de instalación](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para tenerlo en su Pi.

### <a name="installation---raspbian"></a>Instalación, Raspbian

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

Opcionalmente, puede crear un vínculo simbólico para iniciar PowerShell sin especificar la ruta de acceso al archivo binario `pwsh`.

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Desinstalación, Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Archivos binarios

Se proporcionan archivos binarios `tar.gz` de PowerShell para plataformas Linux, a fin de permitir escenarios de implementación avanzados.

### <a name="dependencies"></a>Dependencias

PowerShell compila archivos binarios portátiles para todas las distribuciones de Linux. Aun así, el entorno de ejecución de .NET Core requiere dependencias diferentes en otras distribuciones, y PowerShell también.

En la tabla siguiente se muestran las dependencias de .NET Core 2.0 que se admiten oficialmente en diferentes distribuciones de Linux.

| SO                 | Dependencias |
| ------------------ | ------------ |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libcurl, openssl-libs, libicu |
| openSUSE 42.3 | libcurl4, libopenssl1_0_0 y libicu52_1 |
| openSUSE Leap 15 | libcurl4, libopenssl1_0_0 y libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Para implementar archivos binarios de PowerShell en distribuciones de Linux que no se admiten oficialmente, debe instalar las dependencias necesarias para el sistema operativo de destino en varios pasos. Por ejemplo, nuestro [dockerfile de Amazon Linux][amazon-dockerfile] instala primero las dependencias y, después, extrae el archivo `tar.gz` de Linux.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a>Instalación, archivos binarios

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Desinstalación de archivos binarios

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Rutas de acceso

* `$PSHOME` es `/opt/microsoft/powershell/7/`.
* Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.
* Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.
* Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.
* Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.
* Los módulos predeterminados se leerán de `$PSHOME/Modules`.
* El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.

Los perfiles respetan la configuración de cada host de PowerShell, por lo que hay perfiles predeterminados específicos del host en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.

PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en Linux.

[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
