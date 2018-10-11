---
title: Instalación de PowerShell Core en Linux
description: Información sobre cómo instalar PowerShell Core en varias distribuciones Linux
ms.date: 08/06/2018
ms.openlocfilehash: acd88f686ce6a657c9ccda9d2615d4ab355ddcbe
ms.sourcegitcommit: 601609575a3214ea7086a3bcb586ae0d1df3d418
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532959"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="6ac0a-103">Instalación de PowerShell Core en Linux</span><span class="sxs-lookup"><span data-stu-id="6ac0a-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="6ac0a-104">Es compatible con [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] y [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="6ac0a-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="6ac0a-105">Para distribuciones de Linux que no sean compatibles oficialmente, puede usar el archivo [Paquete Snap de PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="6ac0a-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="6ac0a-106">También puede intentar implementar los archivos binarios de PowerShell directamente mediante el [archivo `tar.gz`][tar] de Linux, pero deberá configurar las dependencias necesarias según el sistema operativo en pasos independientes.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="6ac0a-107">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="6ac0a-108">Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="6ac0a-109">Instalación de versiones preliminares</span><span class="sxs-lookup"><span data-stu-id="6ac0a-109">Installing Preview Releases</span></span>

<span data-ttu-id="6ac0a-110">Al instalar una versión preliminar de PowerShell Core para Linux mediante un repositorio de paquetes, el nombre del paquete cambia de `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="6ac0a-111">La instalación mediante la descarga directa solo cambia el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="6ac0a-112">A continuación se muestra una tabla con los comandos para instalar los paquetes estables y de versión preliminar mediante los diversos administradores de paquetes:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="6ac0a-113">Distribuciones</span><span class="sxs-lookup"><span data-stu-id="6ac0a-113">Distribution(s)</span></span>|<span data-ttu-id="6ac0a-114">Comando estable</span><span class="sxs-lookup"><span data-stu-id="6ac0a-114">Stable Command</span></span> | <span data-ttu-id="6ac0a-115">Comando de versión preliminar</span><span class="sxs-lookup"><span data-stu-id="6ac0a-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="6ac0a-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="6ac0a-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="6ac0a-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="6ac0a-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="6ac0a-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="6ac0a-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="6ac0a-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="6ac0a-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="6ac0a-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="6ac0a-121">Instalación mediante un repositorio de paquetes, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="6ac0a-122">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="6ac0a-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="6ac0a-123">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-123">This is the preferred method.</span></span>

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

<span data-ttu-id="6ac0a-124">Como superusuario, registre el repositorio de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="6ac0a-125">Desde ese momento, solo debe usar `sudo apt-get upgrade powershell` para actualizar la instalación.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="6ac0a-126">Instalación mediante descarga directa, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="6ac0a-127">Descargue el paquete de Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="6ac0a-127">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="6ac0a-128">desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="6ac0a-129">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="6ac0a-130">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="6ac0a-131">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="6ac0a-132">Desinstalación, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="6ac0a-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="6ac0a-134">Instalación mediante un repositorio de paquetes, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="6ac0a-135">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="6ac0a-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="6ac0a-136">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-136">This is the preferred method.</span></span>

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

<span data-ttu-id="6ac0a-137">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="6ac0a-138">Instalación mediante descarga directa, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="6ac0a-139">Descargue el paquete de Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="6ac0a-139">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="6ac0a-140">desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="6ac0a-141">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="6ac0a-142">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="6ac0a-143">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="6ac0a-144">Desinstalación, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="6ac0a-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="6ac0a-146">Se ha agregado compatibilidad con Ubuntu 18.04 después de `6.1.0-preview.2`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="6ac0a-147">Instalación mediante un repositorio de paquetes, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="6ac0a-148">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="6ac0a-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="6ac0a-149">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-149">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="6ac0a-150">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="6ac0a-151">Instalación mediante descarga directa, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="6ac0a-152">Descargue el paquete de Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="6ac0a-152">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="6ac0a-153">desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="6ac0a-154">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="6ac0a-155">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="6ac0a-156">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="6ac0a-157">Desinstalación, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="6ac0a-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="6ac0a-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="6ac0a-159">Se ha agregado compatibilidad con Ubuntu 18.10 después de `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="6ac0a-160">Como 18.10 es una compilación diaria, solo tiene soporte técnico comunitario.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="6ac0a-161">La instalación en 18.10 se admite mediante `snapd`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="6ac0a-162">Consulte [Paquete Snap][snap] para ver instrucciones completas;</span><span class="sxs-lookup"><span data-stu-id="6ac0a-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="6ac0a-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="6ac0a-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="6ac0a-164">Instalación mediante un repositorio de paquetes, Debian 8</span><span class="sxs-lookup"><span data-stu-id="6ac0a-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="6ac0a-165">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="6ac0a-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="6ac0a-166">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-166">This is the preferred method.</span></span>

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

<span data-ttu-id="6ac0a-167">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="6ac0a-168">Instalación mediante descarga directa, Debian 8</span><span class="sxs-lookup"><span data-stu-id="6ac0a-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="6ac0a-169">Descargue el paquete de Debian `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="6ac0a-169">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="6ac0a-170">desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="6ac0a-171">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="6ac0a-172">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="6ac0a-173">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="6ac0a-174">Desinstalación, Debian 8</span><span class="sxs-lookup"><span data-stu-id="6ac0a-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="6ac0a-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="6ac0a-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="6ac0a-176">Instalación mediante un repositorio de paquetes, Debian 9</span><span class="sxs-lookup"><span data-stu-id="6ac0a-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="6ac0a-177">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="6ac0a-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="6ac0a-178">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-178">This is the preferred method.</span></span>

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

<span data-ttu-id="6ac0a-179">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="6ac0a-180">Instalación mediante descarga directa, Debian 9</span><span class="sxs-lookup"><span data-stu-id="6ac0a-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="6ac0a-181">Descargue el paquete de Debian `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="6ac0a-181">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="6ac0a-182">desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="6ac0a-183">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="6ac0a-184">Desinstalación, Debian 9</span><span class="sxs-lookup"><span data-stu-id="6ac0a-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="6ac0a-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6ac0a-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="6ac0a-186">Este paquete también funciona en Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="6ac0a-187">Instalación mediante un repositorio de paquetes (opción preferida), CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6ac0a-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="6ac0a-188">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="6ac0a-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="6ac0a-189">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="6ac0a-190">Instalación mediante descarga directa, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6ac0a-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="6ac0a-191">Con [CentOS 7][], descargue el paquete RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="6ac0a-191">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="6ac0a-192">desde la página de [versiones][] en la máquina CentOS.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="6ac0a-193">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="6ac0a-194">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="6ac0a-195">Desinstalación, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6ac0a-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6ac0a-197">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6ac0a-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6ac0a-198">Instalación a través de un repositorio de paquetes (opción preferida), Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6ac0a-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="6ac0a-199">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="6ac0a-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="6ac0a-200">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6ac0a-201">Instalación mediante descarga directa, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6ac0a-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="6ac0a-202">Descargue el paquete RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="6ac0a-202">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="6ac0a-203">desde la página de [versiones][] en la máquina Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="6ac0a-204">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="6ac0a-205">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6ac0a-206">Desinstalación, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6ac0a-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="6ac0a-207">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="6ac0a-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="6ac0a-208">Al instalar PowerShell Core, `zypper` puede notificar el siguiente error:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.1.0-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.1.0-1.rhel.7.x86_64
 Solution 2: break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="6ac0a-209">En este caso, verifique que haya una biblioteca `libcurl` compatible. Para ello, compruebe que mediante el siguiente comando se muestre que el paquete `libcurl4` está instalado:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="6ac0a-210">A continuación, elija la solución `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` al instalar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-210">Then choose the `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="6ac0a-211">Instalación mediante un repositorio de paquetes (opción preferida), OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="6ac0a-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="6ac0a-212">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="6ac0a-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="6ac0a-213">Instalación mediante descarga directa, OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="6ac0a-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="6ac0a-214">Descargue el paquete RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-214">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="6ac0a-215">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="6ac0a-216">Desinstalación, OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="6ac0a-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="6ac0a-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="6ac0a-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="6ac0a-218">Fedora 28 solo se admite en PowerShell Core 6.1 y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="6ac0a-219">Instalación mediante un repositorio de paquetes (opción preferida), Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="6ac0a-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="6ac0a-220">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="6ac0a-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="6ac0a-221">Instalación mediante descarga directa, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="6ac0a-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="6ac0a-222">Descargue el paquete RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="6ac0a-222">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="6ac0a-223">desde la página de [versiones][] en la máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="6ac0a-224">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="6ac0a-225">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="6ac0a-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="6ac0a-226">Desinstalación, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="6ac0a-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="6ac0a-227">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="6ac0a-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="6ac0a-228">La compatibilidad con Arch es experimental.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-228">Arch support is experimental.</span></span>

<span data-ttu-id="6ac0a-229">PowerShell está disponible en el repositorio de usuario [Arch Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="6ac0a-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="6ac0a-230">Se puede compilar con la [versión etiquetada más reciente][arch-release].</span><span class="sxs-lookup"><span data-stu-id="6ac0a-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="6ac0a-231">Se puede compilar desde la [última confirmación en maestro][arch-git].</span><span class="sxs-lookup"><span data-stu-id="6ac0a-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="6ac0a-232">Se puede instalar mediante el [binario de la versión más reciente][arch-bin].</span><span class="sxs-lookup"><span data-stu-id="6ac0a-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="6ac0a-233">Los paquetes del AUR se mantienen gracias a la comunidad, ya que no hay asistencia oficial.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="6ac0a-234">Para más información sobre cómo instalar paquetes desde el AUR, vea la [wiki de Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="6ac0a-236">Paquete Snap</span><span class="sxs-lookup"><span data-stu-id="6ac0a-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="6ac0a-237">Obtención de snapd</span><span class="sxs-lookup"><span data-stu-id="6ac0a-237">Getting snapd</span></span>

<span data-ttu-id="6ac0a-238">`snapd` es necesario para ejecutar paquetes Snap.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-238">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="6ac0a-239">Use [estas instrucciones](https://docs.snapcraft.io/core/install) para asegurarse de que tiene `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="6ac0a-240">Instalación mediante Snap</span><span class="sxs-lookup"><span data-stu-id="6ac0a-240">Installation via Snap</span></span>

<span data-ttu-id="6ac0a-241">PowerShell Core para Linux se publica en la [Snap store](https://snapcraft.io/store) para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="6ac0a-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="6ac0a-242">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="6ac0a-243">Después de instalar Snap, se actualizará automáticamente, pero puede desencadenar una actualización con `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="6ac0a-244">Desinstalación</span><span class="sxs-lookup"><span data-stu-id="6ac0a-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="6ac0a-245">Kali</span><span class="sxs-lookup"><span data-stu-id="6ac0a-245">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="6ac0a-246">El soporte técnico de Kali no funciona actualmente.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-246">Kali support is not currently working.</span></span> <span data-ttu-id="6ac0a-247">Use el [paquete de Snap][snap] en su lugar.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-247">Please use the [Snap package][snap] instead.</span></span>

### <a name="installation"></a><span data-ttu-id="6ac0a-248">Instalación</span><span class="sxs-lookup"><span data-stu-id="6ac0a-248">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="6ac0a-249">Desinstalación, Kali</span><span class="sxs-lookup"><span data-stu-id="6ac0a-249">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="6ac0a-250">Raspbian</span><span class="sxs-lookup"><span data-stu-id="6ac0a-250">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="6ac0a-251">La compatibilidad con Raspbian es experimental.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-251">Raspbian support is experimental.</span></span>

<span data-ttu-id="6ac0a-252">Actualmente, PowerShell solo se admite en Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-252">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="6ac0a-253">Asimismo, CoreCLR (y, por tanto, PowerShell Core) solo funcionará en dispositivos Pi 2 y Pi 3 dado que otros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tienen un procesador no admitido.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-253">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="6ac0a-254">Descargue [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) y siga las [instrucciones de instalación](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para tenerlo en su Pi.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="6ac0a-255">Instalación</span><span class="sxs-lookup"><span data-stu-id="6ac0a-255">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="6ac0a-256">Opcionalmente, puede crear un vínculo simbólico para poder iniciar PowerShell sin especificar la ruta de acceso al archivo binario "pwsh".</span><span class="sxs-lookup"><span data-stu-id="6ac0a-256">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="6ac0a-257">Desinstalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="6ac0a-257">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="6ac0a-258">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="6ac0a-258">Binary Archives</span></span>

<span data-ttu-id="6ac0a-259">Se proporcionan archivos binarios `tar.gz` de PowerShell para plataformas Linux, a fin de permitir escenarios de implementación avanzados.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="6ac0a-260">Dependencias</span><span class="sxs-lookup"><span data-stu-id="6ac0a-260">Dependencies</span></span>

<span data-ttu-id="6ac0a-261">PowerShell compila archivos binarios portátiles para todas las distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-261">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="6ac0a-262">Aun así, el entorno de ejecución de .NET Core requiere dependencias diferentes en otras distribuciones, y por eso PowerShell hace lo mismo.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-262">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="6ac0a-263">En la tabla siguiente se muestran las dependencias de .NET Core 2.0 que se admiten oficialmente en diferentes distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="6ac0a-264">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="6ac0a-264">OS</span></span>                 | <span data-ttu-id="6ac0a-265">Dependencias</span><span class="sxs-lookup"><span data-stu-id="6ac0a-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="6ac0a-266">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-266">Ubuntu 14.04</span></span>       | <span data-ttu-id="6ac0a-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="6ac0a-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6ac0a-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="6ac0a-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="6ac0a-269">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-269">Ubuntu 16.04</span></span>       | <span data-ttu-id="6ac0a-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="6ac0a-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6ac0a-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="6ac0a-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="6ac0a-272">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="6ac0a-272">Ubuntu 17.10</span></span>       | <span data-ttu-id="6ac0a-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="6ac0a-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6ac0a-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="6ac0a-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="6ac0a-275">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6ac0a-275">Ubuntu 18.04</span></span>       | <span data-ttu-id="6ac0a-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="6ac0a-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6ac0a-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="6ac0a-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="6ac0a-278">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="6ac0a-278">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="6ac0a-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="6ac0a-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6ac0a-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="6ac0a-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="6ac0a-281">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="6ac0a-281">Debian 9 (Stretch)</span></span> | <span data-ttu-id="6ac0a-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="6ac0a-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6ac0a-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="6ac0a-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="6ac0a-284">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6ac0a-284">CentOS 7</span></span> <br> <span data-ttu-id="6ac0a-285">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="6ac0a-285">Oracle Linux 7</span></span> <br> <span data-ttu-id="6ac0a-286">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="6ac0a-286">RHEL 7</span></span> <br> <span data-ttu-id="6ac0a-287">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="6ac0a-287">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="6ac0a-288">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="6ac0a-288">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="6ac0a-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="6ac0a-289">Fedora 27</span></span> <br> <span data-ttu-id="6ac0a-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="6ac0a-290">Fedora 28</span></span> | <span data-ttu-id="6ac0a-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="6ac0a-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="6ac0a-292">Para implementar archivos binarios de PowerShell en distribuciones de Linux que no se admiten oficialmente, debe instalar las dependencias necesarias para el sistema operativo de destino en varios pasos.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-292">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="6ac0a-293">Por ejemplo, nuestro [dockerfile de Amazon Linux][amazon-dockerfile] instala primero las dependencias y, después, extrae el archivo `tar.gz` de Linux.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="6ac0a-294">Instalación, archivos binarios</span><span class="sxs-lookup"><span data-stu-id="6ac0a-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="6ac0a-295">Linux</span><span class="sxs-lookup"><span data-stu-id="6ac0a-295">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="6ac0a-296">Desinstalación de archivos binarios</span><span class="sxs-lookup"><span data-stu-id="6ac0a-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="6ac0a-297">Rutas de acceso</span><span class="sxs-lookup"><span data-stu-id="6ac0a-297">Paths</span></span>

* <span data-ttu-id="6ac0a-298">`$PSHOME` es `/opt/microsoft/powershell/6.1.0/`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-298">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="6ac0a-299">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="6ac0a-300">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="6ac0a-301">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="6ac0a-302">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="6ac0a-303">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-303">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="6ac0a-304">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="6ac0a-305">Los perfiles respetan la configuración de cada host de PowerShell, por lo que hay perfiles predeterminados específicos del host en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="6ac0a-306">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en Linux.</span><span class="sxs-lookup"><span data-stu-id="6ac0a-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
