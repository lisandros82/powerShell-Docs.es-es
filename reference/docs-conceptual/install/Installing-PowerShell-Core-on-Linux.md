---
title: Instalación de PowerShell Core en Linux
description: Información sobre cómo instalar PowerShell Core en varias distribuciones Linux
ms.date: 08/06/2018
ms.openlocfilehash: 32d6c0e718ca798af2f6a5d796c3ca362e7befd9
ms.sourcegitcommit: 13e170e8bff29d3d5f854c874de88f53c5e5ef20
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67829435"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="3388e-103">Instalación de PowerShell Core en Linux</span><span class="sxs-lookup"><span data-stu-id="3388e-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="3388e-104">Admite [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9],
[CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse],
[Fedora 27][fedora], [Fedora 28][fedora] y [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="3388e-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9],
[CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse],
[Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="3388e-105">Para las distribuciones de Linux que no se admiten de forma oficial, puede probar el [Paquete Snap de PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="3388e-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="3388e-106">También puede intentar implementar los archivos binarios de PowerShell directamente mediante el [archivo `tar.gz`][tar] de Linux, pero tendrá que configurar las dependencias necesarias según el sistema operativo en pasos independientes.</span><span class="sxs-lookup"><span data-stu-id="3388e-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="3388e-107">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="3388e-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="3388e-108">Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="3388e-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
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

## <a name="installing-preview-releases"></a><span data-ttu-id="3388e-109">Instalación de versiones preliminares</span><span class="sxs-lookup"><span data-stu-id="3388e-109">Installing Preview Releases</span></span>

<span data-ttu-id="3388e-110">Al instalar una versión preliminar de PowerShell Core para Linux mediante un repositorio de paquetes, el nombre del paquete cambia de `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="3388e-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="3388e-111">La instalación mediante la descarga directa solo cambia el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="3388e-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="3388e-112">A continuación se muestra una tabla con los comandos para instalar los paquetes estables y de versión preliminar mediante los diversos administradores de paquetes:</span><span class="sxs-lookup"><span data-stu-id="3388e-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="3388e-113">Distribuciones</span><span class="sxs-lookup"><span data-stu-id="3388e-113">Distribution(s)</span></span>|<span data-ttu-id="3388e-114">Comando estable</span><span class="sxs-lookup"><span data-stu-id="3388e-114">Stable Command</span></span> | <span data-ttu-id="3388e-115">Comando de versión preliminar</span><span class="sxs-lookup"><span data-stu-id="3388e-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="3388e-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="3388e-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="3388e-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="3388e-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="3388e-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="3388e-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="3388e-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3388e-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="3388e-120">Instalación mediante un repositorio de paquetes, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3388e-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="3388e-121">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3388e-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3388e-122">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="3388e-122">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3388e-123">Como superusuario, registre el repositorio de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3388e-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="3388e-124">Desde ese momento, solo debe usar `sudo apt-get upgrade powershell` para actualizar la instalación.</span><span class="sxs-lookup"><span data-stu-id="3388e-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="3388e-125">Instalación mediante descarga directa, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3388e-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="3388e-126">Descargue el paquete de Debian `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="3388e-126">Download the Debian package `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="3388e-127">desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="3388e-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3388e-128">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3388e-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3388e-129">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="3388e-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3388e-130">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3388e-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="3388e-131">Desinstalación, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3388e-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="3388e-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3388e-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="3388e-133">Instalación mediante un repositorio de paquetes, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3388e-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="3388e-134">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3388e-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3388e-135">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="3388e-135">This is the preferred method.</span></span>

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

<span data-ttu-id="3388e-136">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="3388e-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="3388e-137">Instalación mediante descarga directa, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3388e-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="3388e-138">Descargue el paquete de Debian `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="3388e-138">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="3388e-139">desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="3388e-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3388e-140">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3388e-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3388e-141">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="3388e-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3388e-142">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3388e-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="3388e-143">Desinstalación, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3388e-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="3388e-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3388e-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="3388e-145">Instalación mediante un repositorio de paquetes, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3388e-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="3388e-146">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3388e-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3388e-147">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="3388e-147">This is the preferred method.</span></span>

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

<span data-ttu-id="3388e-148">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="3388e-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="3388e-149">Instalación mediante descarga directa, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3388e-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="3388e-150">Descargue el paquete de Debian `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="3388e-150">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="3388e-151">desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="3388e-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3388e-152">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3388e-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3388e-153">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="3388e-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="3388e-154">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3388e-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="3388e-155">Desinstalación, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3388e-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="3388e-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="3388e-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="3388e-157">Dado que la versión 18.10 es una [versión provisional](https://www.ubuntu.com/about/release-cycle), solo la [admite la comunidad](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="3388e-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="3388e-158">La instalación en 18.10 se admite mediante `snapd`.</span><span class="sxs-lookup"><span data-stu-id="3388e-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="3388e-159">Vea [Paquete Snap][snap] para obtener instrucciones completas;</span><span class="sxs-lookup"><span data-stu-id="3388e-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="3388e-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="3388e-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="3388e-161">Instalación mediante un repositorio de paquetes, Debian 8</span><span class="sxs-lookup"><span data-stu-id="3388e-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="3388e-162">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3388e-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3388e-163">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="3388e-163">This is the preferred method.</span></span>

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

<span data-ttu-id="3388e-164">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="3388e-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="3388e-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="3388e-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="3388e-166">Instalación mediante un repositorio de paquetes, Debian 9</span><span class="sxs-lookup"><span data-stu-id="3388e-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="3388e-167">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3388e-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3388e-168">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="3388e-168">This is the preferred method.</span></span>

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

<span data-ttu-id="3388e-169">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="3388e-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="3388e-170">Instalación mediante descarga directa, Debian 9</span><span class="sxs-lookup"><span data-stu-id="3388e-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="3388e-171">Descargue el paquete de Debian `powershell_6.2.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="3388e-171">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="3388e-172">desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="3388e-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3388e-173">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3388e-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="3388e-174">Desinstalación, Debian 9</span><span class="sxs-lookup"><span data-stu-id="3388e-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="3388e-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3388e-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="3388e-176">Este paquete también funciona en Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="3388e-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="3388e-177">Instalación mediante un repositorio de paquetes (opción preferida), CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3388e-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="3388e-178">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3388e-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3388e-179">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3388e-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="3388e-180">Instalación mediante descarga directa, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3388e-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="3388e-181">Con [CentOS 7][], descargue el paquete RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="3388e-181">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="3388e-182">desde la página de [versiones][] en la máquina CentOS.</span><span class="sxs-lookup"><span data-stu-id="3388e-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="3388e-183">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3388e-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3388e-184">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="3388e-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="3388e-185">Desinstalación, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3388e-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3388e-187">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3388e-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3388e-188">Instalación a través de un repositorio de paquetes (opción preferida), Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3388e-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3388e-189">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3388e-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3388e-190">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3388e-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3388e-191">Instalación mediante descarga directa, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3388e-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3388e-192">Descargue el paquete RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="3388e-192">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="3388e-193">desde la página de [versiones][] en la máquina Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="3388e-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="3388e-194">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3388e-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3388e-195">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="3388e-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3388e-196">Desinstalación, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3388e-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="3388e-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3388e-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="3388e-198">Instalación, OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3388e-198">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="3388e-199">Instalación, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="3388e-199">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="3388e-200">Desinstalación, openSUSE 42.3 y openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="3388e-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="3388e-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="3388e-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="3388e-202">Fedora 28 solo se admite en PowerShell Core 6.1 y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="3388e-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="3388e-203">Instalación mediante un repositorio de paquetes (opción preferida), Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3388e-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="3388e-204">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3388e-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="3388e-205">Instalación mediante descarga directa, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3388e-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="3388e-206">Descargue el paquete RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="3388e-206">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="3388e-207">desde la página de [versiones][] en la máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="3388e-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="3388e-208">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3388e-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3388e-209">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="3388e-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="3388e-210">Desinstalación, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3388e-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="3388e-211">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="3388e-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="3388e-212">La compatibilidad con Arch es experimental.</span><span class="sxs-lookup"><span data-stu-id="3388e-212">Arch support is experimental.</span></span>

<span data-ttu-id="3388e-213">PowerShell está disponible en el repositorio de usuario [Arch Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="3388e-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="3388e-214">Se puede compilar con la [versión etiquetada más reciente][arch-release].</span><span class="sxs-lookup"><span data-stu-id="3388e-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="3388e-215">Se puede compilar desde la [última confirmación en maestro][arch-git].</span><span class="sxs-lookup"><span data-stu-id="3388e-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="3388e-216">Se puede instalar mediante el [binario de la versión más reciente][arch-bin].</span><span class="sxs-lookup"><span data-stu-id="3388e-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="3388e-217">Los paquetes del AUR se mantienen gracias a la comunidad, ya que no hay asistencia oficial.</span><span class="sxs-lookup"><span data-stu-id="3388e-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="3388e-218">Para más información sobre cómo instalar paquetes desde el AUR, vea la [wiki de Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="3388e-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="3388e-220">Paquete Snap</span><span class="sxs-lookup"><span data-stu-id="3388e-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="3388e-221">Obtención de snapd</span><span class="sxs-lookup"><span data-stu-id="3388e-221">Getting snapd</span></span>

<span data-ttu-id="3388e-222">`snapd` es necesario para ejecutar paquetes Snap.</span><span class="sxs-lookup"><span data-stu-id="3388e-222">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="3388e-223">Use [estas instrucciones](https://docs.snapcraft.io/core/install) para asegurarse de que tiene `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="3388e-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="3388e-224">Instalación mediante Snap</span><span class="sxs-lookup"><span data-stu-id="3388e-224">Installation via Snap</span></span>

<span data-ttu-id="3388e-225">PowerShell Core para Linux se publica en la [Snap store](https://snapcraft.io/store) para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3388e-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="3388e-226">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="3388e-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="3388e-227">Si desea instalar la versión preliminar, use el siguiente método.</span><span class="sxs-lookup"><span data-stu-id="3388e-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="3388e-228">Después de instalar Snap, se actualizará automáticamente, pero puede desencadenar una actualización con `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="3388e-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="3388e-229">Desinstalación</span><span class="sxs-lookup"><span data-stu-id="3388e-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="3388e-230">o</span><span class="sxs-lookup"><span data-stu-id="3388e-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="3388e-231">Kali</span><span class="sxs-lookup"><span data-stu-id="3388e-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="3388e-232">Instalación, Kali</span><span class="sxs-lookup"><span data-stu-id="3388e-232">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="3388e-233">Desinstalación, Kali</span><span class="sxs-lookup"><span data-stu-id="3388e-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="3388e-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="3388e-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="3388e-235">La compatibilidad con Raspbian es experimental.</span><span class="sxs-lookup"><span data-stu-id="3388e-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="3388e-236">Actualmente, PowerShell solo se admite en Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="3388e-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="3388e-237">Asimismo, CoreCLR (y, por tanto, PowerShell Core) solo funcionará en dispositivos Pi 2 y Pi 3 dado que otros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tienen un procesador no admitido.</span><span class="sxs-lookup"><span data-stu-id="3388e-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="3388e-238">Descargue [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) y siga las [instrucciones de instalación](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para tenerlo en su Pi.</span><span class="sxs-lookup"><span data-stu-id="3388e-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="3388e-239">Instalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="3388e-239">Installation - Raspbian</span></span>

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

<span data-ttu-id="3388e-240">Opcionalmente, puede crear un vínculo simbólico para poder iniciar PowerShell sin especificar la ruta de acceso al archivo binario "pwsh".</span><span class="sxs-lookup"><span data-stu-id="3388e-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="3388e-241">Desinstalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="3388e-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="3388e-242">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="3388e-242">Binary Archives</span></span>

<span data-ttu-id="3388e-243">Se proporcionan archivos binarios `tar.gz` de PowerShell para plataformas Linux, a fin de permitir escenarios de implementación avanzados.</span><span class="sxs-lookup"><span data-stu-id="3388e-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="3388e-244">Dependencias</span><span class="sxs-lookup"><span data-stu-id="3388e-244">Dependencies</span></span>

<span data-ttu-id="3388e-245">PowerShell compila archivos binarios portátiles para todas las distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="3388e-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="3388e-246">Aun así, el entorno de ejecución de .NET Core requiere dependencias diferentes en otras distribuciones, y por eso PowerShell hace lo mismo.</span><span class="sxs-lookup"><span data-stu-id="3388e-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="3388e-247">En la tabla siguiente se muestran las dependencias de .NET Core 2.0 que se admiten oficialmente en diferentes distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="3388e-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="3388e-248">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="3388e-248">OS</span></span>                 | <span data-ttu-id="3388e-249">Dependencias</span><span class="sxs-lookup"><span data-stu-id="3388e-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="3388e-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3388e-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="3388e-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3388e-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3388e-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="3388e-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="3388e-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3388e-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="3388e-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3388e-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3388e-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="3388e-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="3388e-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="3388e-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="3388e-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3388e-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3388e-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="3388e-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="3388e-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="3388e-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="3388e-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3388e-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3388e-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="3388e-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="3388e-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="3388e-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="3388e-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3388e-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3388e-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="3388e-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="3388e-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="3388e-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="3388e-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3388e-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3388e-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="3388e-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="3388e-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3388e-268">CentOS 7</span></span> <br> <span data-ttu-id="3388e-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="3388e-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="3388e-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="3388e-270">RHEL 7</span></span> | <span data-ttu-id="3388e-271">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="3388e-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="3388e-272">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="3388e-272">openSUSE 42.3</span></span> | <span data-ttu-id="3388e-273">libcurl4, libopenssl1_0_0 y libicu52_1</span><span class="sxs-lookup"><span data-stu-id="3388e-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="3388e-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="3388e-274">openSUSE Leap 15</span></span> | <span data-ttu-id="3388e-275">libcurl4, libopenssl1_0_0 y libicu60_2</span><span class="sxs-lookup"><span data-stu-id="3388e-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="3388e-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="3388e-276">Fedora 27</span></span> <br> <span data-ttu-id="3388e-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3388e-277">Fedora 28</span></span> | <span data-ttu-id="3388e-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="3388e-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="3388e-279">Para implementar archivos binarios de PowerShell en distribuciones de Linux que no se admiten oficialmente, debe instalar las dependencias necesarias para el sistema operativo de destino en varios pasos.</span><span class="sxs-lookup"><span data-stu-id="3388e-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="3388e-280">Por ejemplo, nuestro [dockerfile de Amazon Linux][amazon-dockerfile] instala primero las dependencias y, después, extrae el archivo `tar.gz` de Linux.</span><span class="sxs-lookup"><span data-stu-id="3388e-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="3388e-281">Instalación, archivos binarios</span><span class="sxs-lookup"><span data-stu-id="3388e-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="3388e-282">Linux</span><span class="sxs-lookup"><span data-stu-id="3388e-282">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="3388e-283">Desinstalación de archivos binarios</span><span class="sxs-lookup"><span data-stu-id="3388e-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="3388e-284">Paths</span><span class="sxs-lookup"><span data-stu-id="3388e-284">Paths</span></span>

* <span data-ttu-id="3388e-285">`$PSHOME` es `/opt/microsoft/powershell/6.2.0/`.</span><span class="sxs-lookup"><span data-stu-id="3388e-285">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="3388e-286">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="3388e-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="3388e-287">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="3388e-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="3388e-288">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="3388e-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3388e-289">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="3388e-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3388e-290">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="3388e-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="3388e-291">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="3388e-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="3388e-292">Los perfiles respetan la configuración de cada host de PowerShell, por lo que hay perfiles predeterminados específicos del host en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="3388e-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="3388e-293">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en Linux.</span><span class="sxs-lookup"><span data-stu-id="3388e-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
