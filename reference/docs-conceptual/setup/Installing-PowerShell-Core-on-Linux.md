---
ms.date: 08/09/2017
keywords: powershell,cmdlet,descargar,instalar,configurar,linux
title: Instalación de PowerShell Core en Linux
ms.openlocfilehash: 
ms.sourcegitcommit: 
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: ""
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="b8048-101">Instalación de PowerShell Core en Linux</span><span class="sxs-lookup"><span data-stu-id="b8048-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="b8048-102">Admite [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] y [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="b8048-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="b8048-103">Para distribuciones de Linux que no sean compatibles oficialmente, puede usar el archivo [AppImage de PowerShell][lai].</span><span class="sxs-lookup"><span data-stu-id="b8048-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="b8048-104">También puede intentar implementar los archivos binarios de PowerShell directamente mediante el [archivo `tar.gz`][tar] de Linux, pero deberá configurar las dependencias necesarias según el sistema operativo en pasos independientes.</span><span class="sxs-lookup"><span data-stu-id="b8048-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="b8048-105">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="b8048-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="b8048-106">Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="b8048-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="b8048-107">Instalación de versiones preliminares</span><span class="sxs-lookup"><span data-stu-id="b8048-107">Installing Preview Releases</span></span>

<span data-ttu-id="b8048-108">Al instalar una versión preliminar de PowerShell Core para Linux mediante un repositorio de paquetes, el nombre del paquete cambia de `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="b8048-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="b8048-109">La instalación mediante la descarga directa solo cambia el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="b8048-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="b8048-110">A continuación se muestra una tabla con los comandos para instalar los paquetes estables y de versión preliminar mediante los diversos administradores de paquetes:</span><span class="sxs-lookup"><span data-stu-id="b8048-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="b8048-111">Distribuciones</span><span class="sxs-lookup"><span data-stu-id="b8048-111">Distribution(s)</span></span>|<span data-ttu-id="b8048-112">Comando estable</span><span class="sxs-lookup"><span data-stu-id="b8048-112">Stable Command</span></span> | <span data-ttu-id="b8048-113">Comando de versión preliminar</span><span class="sxs-lookup"><span data-stu-id="b8048-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="b8048-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="b8048-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="b8048-115">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="b8048-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="b8048-116">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="b8048-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="b8048-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="b8048-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="b8048-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b8048-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="b8048-119">Instalación mediante un repositorio de paquetes, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b8048-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="b8048-120">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b8048-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b8048-121">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="b8048-121">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b8048-122">Como superusuario, registre el repositorio de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b8048-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="b8048-123">Desde ese momento, solo debe usar `sudo apt-get upgrade powershell` para actualizar la instalación.</span><span class="sxs-lookup"><span data-stu-id="b8048-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="b8048-124">Instalación mediante descarga directa, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b8048-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="b8048-125">Descargue el paquete de Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b8048-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b8048-126">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b8048-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b8048-127">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="b8048-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="b8048-128">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8048-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="b8048-129">Desinstalación, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b8048-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="b8048-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b8048-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="b8048-131">Instalación mediante un repositorio de paquetes, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b8048-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="b8048-132">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b8048-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b8048-133">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="b8048-133">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b8048-134">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="b8048-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="b8048-135">Instalación mediante descarga directa, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b8048-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="b8048-136">Descargue el paquete de Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b8048-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b8048-137">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b8048-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b8048-138">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="b8048-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="b8048-139">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8048-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="b8048-140">Desinstalación, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b8048-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="b8048-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="b8048-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="b8048-142">Se ha agregado compatibilidad con Ubuntu 17.04 después de `6.1.0-preview.2`.</span><span class="sxs-lookup"><span data-stu-id="b8048-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="b8048-143">Instalación mediante un repositorio de paquetes, Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="b8048-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="b8048-144">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b8048-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b8048-145">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="b8048-145">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b8048-146">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="b8048-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="b8048-147">Instalación mediante descarga directa, Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="b8048-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="b8048-148">Descargue el paquete de Debian `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b8048-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b8048-149">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b8048-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b8048-150">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="b8048-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="b8048-151">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8048-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="b8048-152">Desinstalación, Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="b8048-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="b8048-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b8048-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="b8048-154">Se ha agregado compatibilidad con Ubuntu 18.04 después de `6.1.0-preview.2`.</span><span class="sxs-lookup"><span data-stu-id="b8048-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="b8048-155">Instalación mediante un repositorio de paquetes, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b8048-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="b8048-156">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b8048-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b8048-157">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="b8048-157">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="b8048-158">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="b8048-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="b8048-159">Instalación mediante descarga directa, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b8048-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="b8048-160">Descargue el paquete de Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b8048-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b8048-161">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b8048-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b8048-162">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="b8048-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="b8048-163">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8048-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="b8048-164">Desinstalación, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b8048-164">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="b8048-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="b8048-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="b8048-166">Instalación mediante un repositorio de paquetes, Debian 8</span><span class="sxs-lookup"><span data-stu-id="b8048-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="b8048-167">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b8048-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b8048-168">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="b8048-168">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

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

<span data-ttu-id="b8048-169">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="b8048-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="b8048-170">Instalación mediante descarga directa, Debian 8</span><span class="sxs-lookup"><span data-stu-id="b8048-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="b8048-171">Descargue el paquete de Debian `powershell_6.0.2-1.debian.8_amd64.deb` desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="b8048-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="b8048-172">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b8048-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b8048-173">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="b8048-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="b8048-174">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8048-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="b8048-175">Desinstalación, Debian 8</span><span class="sxs-lookup"><span data-stu-id="b8048-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="b8048-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="b8048-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="b8048-177">Instalación mediante un repositorio de paquetes, Debian 9</span><span class="sxs-lookup"><span data-stu-id="b8048-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="b8048-178">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b8048-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b8048-179">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="b8048-179">This is the preferred method.</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

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

<span data-ttu-id="b8048-180">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="b8048-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="b8048-181">Instalación mediante descarga directa, Debian 9</span><span class="sxs-lookup"><span data-stu-id="b8048-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="b8048-182">Descargue el paquete de Debian `powershell_6.0.2-1.debian.9_amd64.deb` desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="b8048-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="b8048-183">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b8048-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="b8048-184">Desinstalación, Debian 9</span><span class="sxs-lookup"><span data-stu-id="b8048-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="b8048-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b8048-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="b8048-186">Este paquete también funciona en Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="b8048-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="b8048-187">Instalación mediante un repositorio de paquetes (opción preferida), CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b8048-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="b8048-188">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b8048-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b8048-189">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8048-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="b8048-190">Instalación mediante descarga directa, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b8048-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="b8048-191">Cuando use [CentOS 7][], descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina CentOS.</span><span class="sxs-lookup"><span data-stu-id="b8048-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="b8048-192">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b8048-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b8048-193">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b8048-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="b8048-194">Desinstalación, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b8048-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b8048-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b8048-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b8048-197">Instalación a través de un repositorio de paquetes (opción preferida), Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b8048-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b8048-198">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b8048-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b8048-199">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8048-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b8048-200">Instalación mediante descarga directa, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b8048-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b8048-201">Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="b8048-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="b8048-202">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b8048-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b8048-203">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b8048-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b8048-204">Desinstalación, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b8048-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="b8048-205">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="b8048-205">OpenSUSE 42.3</span></span>

<span data-ttu-id="b8048-206">Al instalar PowerShell Core, `zypper` puede notificar el siguiente error:</span><span class="sxs-lookup"><span data-stu-id="b8048-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="b8048-207">En este caso, verifique que haya una biblioteca `libcurl` compatible. Para ello, compruebe que mediante el siguiente comando se muestre que el paquete `libcurl4` está instalado:</span><span class="sxs-lookup"><span data-stu-id="b8048-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="b8048-208">A continuación, elija la solución `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` al instalar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8048-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="b8048-209">Instalación mediante un repositorio de paquetes (opción preferida), OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="b8048-209">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="b8048-210">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b8048-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="b8048-211">Instalación mediante descarga directa, OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="b8048-211">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="b8048-212">Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="b8048-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b8048-213">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b8048-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="b8048-214">Desinstalación, OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="b8048-214">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="b8048-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="b8048-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="b8048-216">Fedora 28 solo se admite en PowerShell Core 6.1 y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="b8048-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="b8048-217">Instalación mediante un repositorio de paquetes (opción preferida), Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="b8048-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="b8048-218">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b8048-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="b8048-219">Instalación mediante descarga directa, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="b8048-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="b8048-220">Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="b8048-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="b8048-221">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b8048-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b8048-222">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b8048-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="b8048-223">Desinstalación, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="b8048-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="b8048-224">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="b8048-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="b8048-225">La compatibilidad con Arch es experimental.</span><span class="sxs-lookup"><span data-stu-id="b8048-225">Arch support is experimental.</span></span>

<span data-ttu-id="b8048-226">PowerShell está disponible en el repositorio de usuario [Arch Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="b8048-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="b8048-227">Se puede compilar con la [versión etiquetada más reciente][arch-release].</span><span class="sxs-lookup"><span data-stu-id="b8048-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="b8048-228">Se puede compilar desde la [última confirmación en maestro][arch-git].</span><span class="sxs-lookup"><span data-stu-id="b8048-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="b8048-229">Se puede instalar mediante el [binario de la versión más reciente][arch-bin].</span><span class="sxs-lookup"><span data-stu-id="b8048-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="b8048-230">Los paquetes del AUR se mantienen gracias a la comunidad, ya que no hay asistencia oficial.</span><span class="sxs-lookup"><span data-stu-id="b8048-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="b8048-231">Para más información sobre cómo instalar paquetes desde el AUR, vea la [wiki de Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="b8048-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="b8048-233">AppImage de Linux</span><span class="sxs-lookup"><span data-stu-id="b8048-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="b8048-234">La compatibilidad con AppImage es experimental.</span><span class="sxs-lookup"><span data-stu-id="b8048-234">AppImage support is experimental</span></span>

<span data-ttu-id="b8048-235">Si usa una distribución de Linux reciente, descargue el archivo AppImage `powershell-6.0.1-x86_64.AppImage` desde la página de [versiones][] en el equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="b8048-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="b8048-236">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b8048-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="b8048-237">El archivo [AppImage][] permite ejecutar PowerShell sin instalarlo.</span><span class="sxs-lookup"><span data-stu-id="b8048-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="b8048-238">Se trata de una aplicación portátil que empaqueta PowerShell y sus dependencias (incluidas las dependencias del sistema de .NET Core) en un paquete coherente.</span><span class="sxs-lookup"><span data-stu-id="b8048-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="b8048-239">Este paquete es un archivo binario único que funciona con independencia de la distribución de Linux del usuario.</span><span class="sxs-lookup"><span data-stu-id="b8048-239">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="b8048-241">Kali</span><span class="sxs-lookup"><span data-stu-id="b8048-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="b8048-242">La compatibilidad con Kali es experimental.</span><span class="sxs-lookup"><span data-stu-id="b8048-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="b8048-243">Instalación</span><span class="sxs-lookup"><span data-stu-id="b8048-243">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="b8048-244">Ejecución de PowerShell en la versión más reciente de Kali (Kali GNU/Linux Rolling) sin instalarlo</span><span class="sxs-lookup"><span data-stu-id="b8048-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="b8048-245">Desinstalación, Kali</span><span class="sxs-lookup"><span data-stu-id="b8048-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="b8048-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="b8048-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="b8048-247">La compatibilidad con Raspbian es experimental.</span><span class="sxs-lookup"><span data-stu-id="b8048-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="b8048-248">Actualmente, PowerShell solo se admite en Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="b8048-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="b8048-249">Asimismo, CoreCLR (y, por tanto, PowerShell Core) solo funcionará en dispositivos Pi 2 y Pi 3 dado que otros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tienen un procesador no admitido.</span><span class="sxs-lookup"><span data-stu-id="b8048-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="b8048-250">Descargue [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) y siga las [instrucciones de instalación](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para tenerlo en su Pi.</span><span class="sxs-lookup"><span data-stu-id="b8048-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="b8048-251">Instalación</span><span class="sxs-lookup"><span data-stu-id="b8048-251">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="b8048-252">Opcionalmente, puede crear un vínculo simbólico para poder iniciar PowerShell sin especificar la ruta de acceso al archivo binario "pwsh".</span><span class="sxs-lookup"><span data-stu-id="b8048-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="b8048-253">Desinstalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="b8048-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="b8048-254">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="b8048-254">Binary Archives</span></span>

<span data-ttu-id="b8048-255">Se proporcionan archivos binarios `tar.gz` de PowerShell para plataformas Linux, a fin de permitir escenarios de implementación avanzados.</span><span class="sxs-lookup"><span data-stu-id="b8048-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="b8048-256">Dependencias</span><span class="sxs-lookup"><span data-stu-id="b8048-256">Dependencies</span></span>

<span data-ttu-id="b8048-257">PowerShell compila archivos binarios portátiles para todas las distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="b8048-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="b8048-258">Aun así, el entorno de ejecución de .NET Core requiere dependencias diferentes en otras distribuciones, y por eso PowerShell hace lo mismo.</span><span class="sxs-lookup"><span data-stu-id="b8048-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="b8048-259">En la tabla siguiente se muestran las dependencias de .NET Core 2.0 que se admiten oficialmente en diferentes distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="b8048-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="b8048-260">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="b8048-260">OS</span></span>                 | <span data-ttu-id="b8048-261">Dependencias</span><span class="sxs-lookup"><span data-stu-id="b8048-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="b8048-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b8048-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="b8048-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b8048-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b8048-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="b8048-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="b8048-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b8048-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="b8048-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b8048-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b8048-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="b8048-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="b8048-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="b8048-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="b8048-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b8048-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b8048-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="b8048-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="b8048-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b8048-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="b8048-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b8048-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b8048-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="b8048-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="b8048-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="b8048-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="b8048-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b8048-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b8048-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="b8048-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="b8048-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="b8048-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="b8048-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b8048-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b8048-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="b8048-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="b8048-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b8048-280">CentOS 7</span></span> <br> <span data-ttu-id="b8048-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="b8048-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="b8048-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="b8048-282">RHEL 7</span></span> <br> <span data-ttu-id="b8048-283">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="b8048-283">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="b8048-284">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="b8048-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="b8048-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="b8048-285">Fedora 27</span></span> <br> <span data-ttu-id="b8048-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="b8048-286">Fedora 28</span></span> | <span data-ttu-id="b8048-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="b8048-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="b8048-288">Para implementar archivos binarios de PowerShell en distribuciones de Linux que no se admiten oficialmente, debe instalar las dependencias necesarias para el sistema operativo de destino en varios pasos.</span><span class="sxs-lookup"><span data-stu-id="b8048-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="b8048-289">Por ejemplo, nuestro [dockerfile de Amazon Linux][amazon-dockerfile] instala primero las dependencias y, después, extrae el archivo `tar.gz` de Linux.</span><span class="sxs-lookup"><span data-stu-id="b8048-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="b8048-290">Instalación, archivos binarios</span><span class="sxs-lookup"><span data-stu-id="b8048-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="b8048-291">Linux</span><span class="sxs-lookup"><span data-stu-id="b8048-291">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="b8048-292">Desinstalación de archivos binarios</span><span class="sxs-lookup"><span data-stu-id="b8048-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="b8048-293">Rutas de acceso</span><span class="sxs-lookup"><span data-stu-id="b8048-293">Paths</span></span>

* <span data-ttu-id="b8048-294">`$PSHOME` es `/opt/microsoft/powershell/6.0.2/`.</span><span class="sxs-lookup"><span data-stu-id="b8048-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="b8048-295">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="b8048-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="b8048-296">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="b8048-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="b8048-297">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="b8048-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b8048-298">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="b8048-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b8048-299">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="b8048-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="b8048-300">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="b8048-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="b8048-301">Los perfiles respetan la configuración de cada host de PowerShell, por lo que hay perfiles predeterminados específicos del host en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="b8048-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="b8048-302">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en Linux.</span><span class="sxs-lookup"><span data-stu-id="b8048-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
