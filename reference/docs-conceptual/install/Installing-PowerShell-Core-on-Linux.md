---
title: Instalación de PowerShell Core en Linux
description: Información sobre cómo instalar PowerShell Core en varias distribuciones Linux
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372199"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="b4704-103">Instalación de PowerShell Core en Linux</span><span class="sxs-lookup"><span data-stu-id="b4704-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="b4704-104">Admite [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9],
 [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] y [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="b4704-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9],
 [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="b4704-105">Para las distribuciones de Linux que no se admiten de forma oficial, puede probar a instalar PowerShell con el [Paquete Snap de PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="b4704-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="b4704-106">También puede intentar implementar los archivos binarios de PowerShell directamente mediante el [archivo `tar.gz`][tar] de Linux, pero tendrá que configurar las dependencias necesarias según el sistema operativo en pasos independientes.</span><span class="sxs-lookup"><span data-stu-id="b4704-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="b4704-107">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="b4704-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="b4704-108">Una vez instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="b4704-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="b4704-109">Instalación de versiones preliminares</span><span class="sxs-lookup"><span data-stu-id="b4704-109">Installing Preview Releases</span></span>

<span data-ttu-id="b4704-110">Al instalar una versión preliminar de PowerShell Core para Linux mediante un repositorio de paquetes, el nombre del paquete cambia de `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="b4704-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="b4704-111">La instalación mediante la descarga directa solo cambia el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="b4704-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="b4704-112">La tabla siguiente contiene los comandos para instalar los paquetes estables y de versión preliminar mediante los diversos administradores de paquetes:</span><span class="sxs-lookup"><span data-stu-id="b4704-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="b4704-113">Distribuciones</span><span class="sxs-lookup"><span data-stu-id="b4704-113">Distribution(s)</span></span>|<span data-ttu-id="b4704-114">Comando estable</span><span class="sxs-lookup"><span data-stu-id="b4704-114">Stable Command</span></span> | <span data-ttu-id="b4704-115">Comando de versión preliminar</span><span class="sxs-lookup"><span data-stu-id="b4704-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="b4704-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="b4704-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="b4704-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="b4704-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="b4704-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="b4704-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="b4704-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b4704-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="b4704-120">Instalación mediante un repositorio de paquetes, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b4704-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="b4704-121">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="b4704-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="b4704-122">El método preferido es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="b4704-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="b4704-123">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="b4704-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="b4704-124">Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="b4704-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="b4704-125">Instalación mediante descarga directa, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b4704-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="b4704-126">Descargue el paquete de Debian `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b4704-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b4704-127">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b4704-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b4704-128">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="b4704-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="b4704-129">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4704-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="b4704-130">Desinstalación, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b4704-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="b4704-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b4704-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="b4704-132">Instalación mediante un repositorio de paquetes, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b4704-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="b4704-133">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="b4704-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="b4704-134">El método preferido es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="b4704-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="b4704-135">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="b4704-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="b4704-136">Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="b4704-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="b4704-137">Instalación mediante descarga directa, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b4704-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="b4704-138">Descargue el paquete de Debian `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b4704-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="b4704-139">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b4704-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="b4704-140">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="b4704-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="b4704-141">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b4704-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="b4704-142">Desinstalación, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b4704-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="b4704-143">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="b4704-143">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="b4704-144">Dado que la versión 18.10 es una [versión provisional](https://www.ubuntu.com/about/release-cycle), solo la [admite la comunidad](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="b4704-144">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="b4704-145">La instalación en 18.10 se admite mediante `snapd`.</span><span class="sxs-lookup"><span data-stu-id="b4704-145">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="b4704-146">Vea [Paquete Snap][snap] para obtener instrucciones completas;</span><span class="sxs-lookup"><span data-stu-id="b4704-146">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="b4704-147">Debian 8</span><span class="sxs-lookup"><span data-stu-id="b4704-147">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="b4704-148">Instalación mediante un repositorio de paquetes, Debian 8</span><span class="sxs-lookup"><span data-stu-id="b4704-148">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="b4704-149">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="b4704-149">PowerShell Core, for Linux, is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="b4704-150">El método preferido es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="b4704-150">The preferred method is as follows:</span></span>

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

<span data-ttu-id="b4704-151">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="b4704-151">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="b4704-152">Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="b4704-152">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="b4704-153">Debian 9</span><span class="sxs-lookup"><span data-stu-id="b4704-153">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="b4704-154">Instalación mediante un repositorio de paquetes, Debian 9</span><span class="sxs-lookup"><span data-stu-id="b4704-154">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="b4704-155">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="b4704-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="b4704-156">El método preferido es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="b4704-156">The preferred method is as follows:</span></span>

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

<span data-ttu-id="b4704-157">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="b4704-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="b4704-158">Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="b4704-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="b4704-159">Instalación mediante descarga directa, Debian 9</span><span class="sxs-lookup"><span data-stu-id="b4704-159">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="b4704-160">Descargue el paquete de Debian `powershell_6.2.0-1.debian.9_amd64.deb` desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="b4704-160">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="b4704-161">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b4704-161">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="b4704-162">Desinstalación, Debian 9</span><span class="sxs-lookup"><span data-stu-id="b4704-162">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="b4704-163">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b4704-163">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="b4704-164">Este paquete funciona en Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="b4704-164">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="b4704-165">Instalación mediante un repositorio de paquetes (opción preferida), CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b4704-165">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="b4704-166">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="b4704-166">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b4704-167">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="b4704-167">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="b4704-168">Después del registro, puede actualizar PowerShell con `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="b4704-168">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="b4704-169">Instalación mediante descarga directa, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b4704-169">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="b4704-170">Cuando use [CentOS 7][], descargue el paquete RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina CentOS.</span><span class="sxs-lookup"><span data-stu-id="b4704-170">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="b4704-171">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b4704-171">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b4704-172">Puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b4704-172">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="b4704-173">Desinstalación, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b4704-173">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b4704-175">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b4704-175">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b4704-176">Instalación a través de un repositorio de paquetes (opción preferida), Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b4704-176">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b4704-177">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="b4704-177">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b4704-178">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="b4704-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="b4704-179">Después del registro, puede actualizar PowerShell con `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="b4704-179">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b4704-180">Instalación mediante descarga directa, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b4704-180">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b4704-181">Descargue el paquete RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="b4704-181">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="b4704-182">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b4704-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b4704-183">Puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b4704-183">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b4704-184">Desinstalación, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b4704-184">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="b4704-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="b4704-185">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="b4704-186">Instalación, OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="b4704-186">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="b4704-187">Instalación, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="b4704-187">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="b4704-188">Desinstalación, openSUSE 42.3 y openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="b4704-188">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="b4704-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="b4704-189">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="b4704-190">Fedora 28 solo se admite en PowerShell Core 6.1 y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="b4704-190">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="b4704-191">Instalación mediante un repositorio de paquetes (opción preferida), Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="b4704-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="b4704-192">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="b4704-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="b4704-193">Instalación mediante descarga directa, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="b4704-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="b4704-194">Descargue el paquete RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="b4704-194">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="b4704-195">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b4704-195">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b4704-196">Puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b4704-196">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="b4704-197">Desinstalación, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="b4704-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="b4704-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="b4704-198">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="b4704-199">La compatibilidad con Arch es experimental.</span><span class="sxs-lookup"><span data-stu-id="b4704-199">Arch support is experimental.</span></span>

<span data-ttu-id="b4704-200">PowerShell está disponible en el repositorio de usuario [Arch Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="b4704-200">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="b4704-201">Se puede compilar con la [versión etiquetada más reciente][arch-release].</span><span class="sxs-lookup"><span data-stu-id="b4704-201">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="b4704-202">Se puede compilar desde la [última confirmación en maestro][arch-git].</span><span class="sxs-lookup"><span data-stu-id="b4704-202">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="b4704-203">Se puede instalar mediante el [binario de la versión más reciente][arch-bin].</span><span class="sxs-lookup"><span data-stu-id="b4704-203">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="b4704-204">Los paquetes del AUR se mantienen gracias a la comunidad, ya que no hay asistencia oficial.</span><span class="sxs-lookup"><span data-stu-id="b4704-204">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="b4704-205">Para más información sobre cómo instalar paquetes desde el AUR, vea la [wiki de Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="b4704-205">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="b4704-207">Paquete Snap</span><span class="sxs-lookup"><span data-stu-id="b4704-207">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="b4704-208">Obtención de snapd</span><span class="sxs-lookup"><span data-stu-id="b4704-208">Getting snapd</span></span>

<span data-ttu-id="b4704-209">`snapd` es necesario para ejecutar paquetes Snap.</span><span class="sxs-lookup"><span data-stu-id="b4704-209">`snapd` is required to run snaps.</span></span> <span data-ttu-id="b4704-210">Use [estas instrucciones](https://docs.snapcraft.io/core/install) para asegurarse de que tiene `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="b4704-210">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="b4704-211">Instalación mediante Snap</span><span class="sxs-lookup"><span data-stu-id="b4704-211">Installation via Snap</span></span>

<span data-ttu-id="b4704-212">PowerShell Core para Linux se publica en la [Snap store](https://snapcraft.io/store) para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="b4704-212">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="b4704-213">El método preferido es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="b4704-213">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="b4704-214">Para instalar una versión preliminar, use el método siguiente:</span><span class="sxs-lookup"><span data-stu-id="b4704-214">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="b4704-215">Después de la instalación, Snap se actualizará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="b4704-215">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="b4704-216">Puede desencadenar una actualización mediante `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="b4704-216">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="b4704-217">Desinstalación</span><span class="sxs-lookup"><span data-stu-id="b4704-217">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="b4704-218">o</span><span class="sxs-lookup"><span data-stu-id="b4704-218">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="b4704-219">Kali</span><span class="sxs-lookup"><span data-stu-id="b4704-219">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="b4704-220">Instalación, Kali</span><span class="sxs-lookup"><span data-stu-id="b4704-220">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="b4704-221">Desinstalación, Kali</span><span class="sxs-lookup"><span data-stu-id="b4704-221">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="b4704-222">Raspbian</span><span class="sxs-lookup"><span data-stu-id="b4704-222">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="b4704-223">La compatibilidad con Raspbian es experimental.</span><span class="sxs-lookup"><span data-stu-id="b4704-223">Raspbian support is experimental.</span></span>

<span data-ttu-id="b4704-224">Actualmente, PowerShell solo se admite en Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="b4704-224">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="b4704-225">CoreCLR y PowerShell Core solo funcionarán en dispositivos Pi 2 y Pi 3 dado que otros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tienen un procesador no admitido.</span><span class="sxs-lookup"><span data-stu-id="b4704-225">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="b4704-226">Descargue [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) y siga las [instrucciones de instalación](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para tenerlo en su Pi.</span><span class="sxs-lookup"><span data-stu-id="b4704-226">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="b4704-227">Instalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="b4704-227">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="b4704-228">Opcionalmente, puede crear un vínculo simbólico para iniciar PowerShell sin especificar la ruta de acceso al archivo binario `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="b4704-228">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="b4704-229">Desinstalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="b4704-229">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="b4704-230">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="b4704-230">Binary Archives</span></span>

<span data-ttu-id="b4704-231">Se proporcionan archivos binarios `tar.gz` de PowerShell para plataformas Linux, a fin de permitir escenarios de implementación avanzados.</span><span class="sxs-lookup"><span data-stu-id="b4704-231">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="b4704-232">Dependencias</span><span class="sxs-lookup"><span data-stu-id="b4704-232">Dependencies</span></span>

<span data-ttu-id="b4704-233">PowerShell compila archivos binarios portátiles para todas las distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="b4704-233">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="b4704-234">Aun así, el entorno de ejecución de .NET Core requiere dependencias diferentes en otras distribuciones, y PowerShell también.</span><span class="sxs-lookup"><span data-stu-id="b4704-234">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="b4704-235">En la tabla siguiente se muestran las dependencias de .NET Core 2.0 que se admiten oficialmente en diferentes distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="b4704-235">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="b4704-236">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="b4704-236">OS</span></span>                 | <span data-ttu-id="b4704-237">Dependencias</span><span class="sxs-lookup"><span data-stu-id="b4704-237">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="b4704-238">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b4704-238">Ubuntu 16.04</span></span>       | <span data-ttu-id="b4704-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b4704-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b4704-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="b4704-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="b4704-241">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="b4704-241">Ubuntu 17.10</span></span>       | <span data-ttu-id="b4704-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b4704-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b4704-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="b4704-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="b4704-244">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="b4704-244">Ubuntu 18.04</span></span>       | <span data-ttu-id="b4704-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b4704-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b4704-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="b4704-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="b4704-247">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="b4704-247">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="b4704-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b4704-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b4704-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="b4704-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="b4704-250">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="b4704-250">Debian 9 (Stretch)</span></span> | <span data-ttu-id="b4704-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b4704-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b4704-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="b4704-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="b4704-253">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b4704-253">CentOS 7</span></span> <br> <span data-ttu-id="b4704-254">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="b4704-254">Oracle Linux 7</span></span> <br> <span data-ttu-id="b4704-255">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="b4704-255">RHEL 7</span></span> | <span data-ttu-id="b4704-256">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="b4704-256">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="b4704-257">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="b4704-257">openSUSE 42.3</span></span> | <span data-ttu-id="b4704-258">libcurl4, libopenssl1_0_0 y libicu52_1</span><span class="sxs-lookup"><span data-stu-id="b4704-258">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="b4704-259">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="b4704-259">openSUSE Leap 15</span></span> | <span data-ttu-id="b4704-260">libcurl4, libopenssl1_0_0 y libicu60_2</span><span class="sxs-lookup"><span data-stu-id="b4704-260">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="b4704-261">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="b4704-261">Fedora 27</span></span> <br> <span data-ttu-id="b4704-262">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="b4704-262">Fedora 28</span></span> | <span data-ttu-id="b4704-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="b4704-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="b4704-264">Para implementar archivos binarios de PowerShell en distribuciones de Linux que no se admiten oficialmente, debe instalar las dependencias necesarias para el sistema operativo de destino en varios pasos.</span><span class="sxs-lookup"><span data-stu-id="b4704-264">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="b4704-265">Por ejemplo, nuestro [dockerfile de Amazon Linux][amazon-dockerfile] instala primero las dependencias y, después, extrae el archivo `tar.gz` de Linux.</span><span class="sxs-lookup"><span data-stu-id="b4704-265">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="b4704-266">Instalación, archivos binarios</span><span class="sxs-lookup"><span data-stu-id="b4704-266">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="b4704-267">Linux</span><span class="sxs-lookup"><span data-stu-id="b4704-267">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="b4704-268">Desinstalación de archivos binarios</span><span class="sxs-lookup"><span data-stu-id="b4704-268">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="b4704-269">Paths</span><span class="sxs-lookup"><span data-stu-id="b4704-269">Paths</span></span>

* <span data-ttu-id="b4704-270">`$PSHOME` es `/opt/microsoft/powershell/6.2.0/`.</span><span class="sxs-lookup"><span data-stu-id="b4704-270">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="b4704-271">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="b4704-271">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="b4704-272">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="b4704-272">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="b4704-273">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="b4704-273">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b4704-274">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="b4704-274">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b4704-275">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="b4704-275">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="b4704-276">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="b4704-276">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="b4704-277">Los perfiles respetan la configuración de cada host de PowerShell, por lo que hay perfiles predeterminados específicos del host en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="b4704-277">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="b4704-278">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en Linux.</span><span class="sxs-lookup"><span data-stu-id="b4704-278">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
