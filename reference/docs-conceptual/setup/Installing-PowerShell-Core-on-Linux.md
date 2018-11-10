---
title: Instalación de PowerShell Core en Linux
description: Información sobre cómo instalar PowerShell Core en varias distribuciones Linux
ms.date: 08/06/2018
ms.openlocfilehash: a20384c768113ed2313591cfa8c29eeadd94f80f
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226005"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="e1ce6-103">Instalación de PowerShell Core en Linux</span><span class="sxs-lookup"><span data-stu-id="e1ce6-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="e1ce6-104">Es compatible con [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] y [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="e1ce6-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="e1ce6-105">Para distribuciones de Linux que no sean compatibles oficialmente, puede usar el archivo [Paquete Snap de PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="e1ce6-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="e1ce6-106">También puede intentar implementar los archivos binarios de PowerShell directamente mediante el [archivo `tar.gz`][tar] de Linux, pero deberá configurar las dependencias necesarias según el sistema operativo en pasos independientes.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e1ce6-107">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="e1ce6-108">Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="e1ce6-109">Instalación de versiones preliminares</span><span class="sxs-lookup"><span data-stu-id="e1ce6-109">Installing Preview Releases</span></span>

<span data-ttu-id="e1ce6-110">Al instalar una versión preliminar de PowerShell Core para Linux mediante un repositorio de paquetes, el nombre del paquete cambia de `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="e1ce6-111">La instalación mediante la descarga directa solo cambia el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="e1ce6-112">A continuación se muestra una tabla con los comandos para instalar los paquetes estables y de versión preliminar mediante los diversos administradores de paquetes:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="e1ce6-113">Distribuciones</span><span class="sxs-lookup"><span data-stu-id="e1ce6-113">Distribution(s)</span></span>|<span data-ttu-id="e1ce6-114">Comando estable</span><span class="sxs-lookup"><span data-stu-id="e1ce6-114">Stable Command</span></span> | <span data-ttu-id="e1ce6-115">Comando de versión preliminar</span><span class="sxs-lookup"><span data-stu-id="e1ce6-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="e1ce6-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="e1ce6-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="e1ce6-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="e1ce6-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="e1ce6-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="e1ce6-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="e1ce6-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="e1ce6-120">Instalación mediante un repositorio de paquetes, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="e1ce6-121">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="e1ce6-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e1ce6-122">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-122">This is the preferred method.</span></span>

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

<span data-ttu-id="e1ce6-123">Como superusuario, registre el repositorio de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="e1ce6-124">Desde ese momento, solo debe usar `sudo apt-get upgrade powershell` para actualizar la instalación.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="e1ce6-125">Instalación mediante descarga directa, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="e1ce6-126">Descargue el paquete de Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e1ce6-126">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="e1ce6-127">desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e1ce6-128">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e1ce6-129">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e1ce6-130">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="e1ce6-131">Desinstalación, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="e1ce6-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e1ce6-133">Instalación mediante un repositorio de paquetes, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e1ce6-134">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="e1ce6-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e1ce6-135">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-135">This is the preferred method.</span></span>

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

<span data-ttu-id="e1ce6-136">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e1ce6-137">Instalación mediante descarga directa, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e1ce6-138">Descargue el paquete de Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e1ce6-138">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="e1ce6-139">desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e1ce6-140">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e1ce6-141">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e1ce6-142">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e1ce6-143">Desinstalación, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="e1ce6-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-144">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="e1ce6-145">Se ha agregado compatibilidad con Ubuntu 18.04 después de `6.1.0-preview.2`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-145">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="e1ce6-146">Instalación mediante un repositorio de paquetes, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-146">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="e1ce6-147">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="e1ce6-147">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e1ce6-148">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-148">This is the preferred method.</span></span>

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

<span data-ttu-id="e1ce6-149">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-149">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="e1ce6-150">Instalación mediante descarga directa, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-150">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="e1ce6-151">Descargue el paquete de Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e1ce6-151">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="e1ce6-152">desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-152">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e1ce6-153">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-153">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e1ce6-154">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-154">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e1ce6-155">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-155">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="e1ce6-156">Desinstalación, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-156">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="e1ce6-157">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="e1ce6-157">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="e1ce6-158">Se ha agregado compatibilidad con Ubuntu 18.10 después de `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-158">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="e1ce6-159">Como 18.10 es una compilación diaria, solo tiene soporte técnico comunitario.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-159">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="e1ce6-160">La instalación en 18.10 se admite mediante `snapd`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-160">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="e1ce6-161">Consulte [Paquete Snap][snap] para ver instrucciones completas;</span><span class="sxs-lookup"><span data-stu-id="e1ce6-161">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="e1ce6-162">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e1ce6-162">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e1ce6-163">Instalación mediante un repositorio de paquetes, Debian 8</span><span class="sxs-lookup"><span data-stu-id="e1ce6-163">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e1ce6-164">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="e1ce6-164">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e1ce6-165">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-165">This is the preferred method.</span></span>

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

<span data-ttu-id="e1ce6-166">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-166">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="e1ce6-167">Instalación mediante descarga directa, Debian 8</span><span class="sxs-lookup"><span data-stu-id="e1ce6-167">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="e1ce6-168">Descargue el paquete de Debian `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e1ce6-168">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="e1ce6-169">desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-169">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e1ce6-170">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-170">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e1ce6-171">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-171">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e1ce6-172">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-172">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="e1ce6-173">Desinstalación, Debian 8</span><span class="sxs-lookup"><span data-stu-id="e1ce6-173">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="e1ce6-174">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e1ce6-174">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e1ce6-175">Instalación mediante un repositorio de paquetes, Debian 9</span><span class="sxs-lookup"><span data-stu-id="e1ce6-175">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e1ce6-176">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="e1ce6-176">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e1ce6-177">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-177">This is the preferred method.</span></span>

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

<span data-ttu-id="e1ce6-178">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-178">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e1ce6-179">Instalación mediante descarga directa, Debian 9</span><span class="sxs-lookup"><span data-stu-id="e1ce6-179">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e1ce6-180">Descargue el paquete de Debian `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e1ce6-180">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="e1ce6-181">desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-181">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e1ce6-182">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-182">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e1ce6-183">Desinstalación, Debian 9</span><span class="sxs-lookup"><span data-stu-id="e1ce6-183">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e1ce6-184">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e1ce6-184">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="e1ce6-185">Este paquete también funciona en Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-185">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e1ce6-186">Instalación mediante un repositorio de paquetes (opción preferida), CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e1ce6-186">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e1ce6-187">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="e1ce6-187">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e1ce6-188">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-188">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e1ce6-189">Instalación mediante descarga directa, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e1ce6-189">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e1ce6-190">Con [CentOS 7][], descargue el paquete RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="e1ce6-190">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="e1ce6-191">desde la página de [versiones][] en la máquina CentOS.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-191">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e1ce6-192">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e1ce6-193">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e1ce6-194">Desinstalación, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e1ce6-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e1ce6-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e1ce6-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e1ce6-197">Instalación a través de un repositorio de paquetes (opción preferida), Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e1ce6-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e1ce6-198">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="e1ce6-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e1ce6-199">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e1ce6-200">Instalación mediante descarga directa, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e1ce6-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e1ce6-201">Descargue el paquete RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="e1ce6-201">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="e1ce6-202">desde la página de [versiones][] en la máquina Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-202">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e1ce6-203">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-203">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e1ce6-204">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-204">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e1ce6-205">Desinstalación, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e1ce6-205">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="e1ce6-206">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e1ce6-206">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="e1ce6-207">Instalación, OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e1ce6-207">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="e1ce6-208">Instalación, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e1ce6-208">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="e1ce6-209">Desinstalación, openSUSE 42.3 y openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e1ce6-209">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="e1ce6-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="e1ce6-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="e1ce6-211">Fedora 28 solo se admite en PowerShell Core 6.1 y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="e1ce6-212">Instalación mediante un repositorio de paquetes (opción preferida), Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e1ce6-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e1ce6-213">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="e1ce6-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="e1ce6-214">Instalación mediante descarga directa, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e1ce6-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e1ce6-215">Descargue el paquete RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="e1ce6-215">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="e1ce6-216">desde la página de [versiones][] en la máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-216">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e1ce6-217">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-217">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e1ce6-218">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="e1ce6-218">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="e1ce6-219">Desinstalación, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e1ce6-219">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e1ce6-220">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e1ce6-220">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="e1ce6-221">La compatibilidad con Arch es experimental.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-221">Arch support is experimental.</span></span>

<span data-ttu-id="e1ce6-222">PowerShell está disponible en el repositorio de usuario [Arch Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="e1ce6-222">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e1ce6-223">Se puede compilar con la [versión etiquetada más reciente][arch-release].</span><span class="sxs-lookup"><span data-stu-id="e1ce6-223">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e1ce6-224">Se puede compilar desde la [última confirmación en maestro][arch-git].</span><span class="sxs-lookup"><span data-stu-id="e1ce6-224">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e1ce6-225">Se puede instalar mediante el [binario de la versión más reciente][arch-bin].</span><span class="sxs-lookup"><span data-stu-id="e1ce6-225">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e1ce6-226">Los paquetes del AUR se mantienen gracias a la comunidad, ya que no hay asistencia oficial.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-226">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="e1ce6-227">Para más información sobre cómo instalar paquetes desde el AUR, vea la [wiki de Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-227">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="e1ce6-229">Paquete Snap</span><span class="sxs-lookup"><span data-stu-id="e1ce6-229">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="e1ce6-230">Obtención de snapd</span><span class="sxs-lookup"><span data-stu-id="e1ce6-230">Getting snapd</span></span>

<span data-ttu-id="e1ce6-231">`snapd` es necesario para ejecutar paquetes Snap.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-231">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="e1ce6-232">Use [estas instrucciones](https://docs.snapcraft.io/core/install) para asegurarse de que tiene `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-232">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="e1ce6-233">Instalación mediante Snap</span><span class="sxs-lookup"><span data-stu-id="e1ce6-233">Installation via Snap</span></span>

<span data-ttu-id="e1ce6-234">PowerShell Core para Linux se publica en la [Snap store](https://snapcraft.io/store) para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="e1ce6-234">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="e1ce6-235">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-235">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="e1ce6-236">Si desea instalar la versión preliminar, use el siguiente método.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-236">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="e1ce6-237">Después de instalar Snap, se actualizará automáticamente, pero puede desencadenar una actualización con `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-237">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="e1ce6-238">Desinstalación</span><span class="sxs-lookup"><span data-stu-id="e1ce6-238">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="e1ce6-239">o</span><span class="sxs-lookup"><span data-stu-id="e1ce6-239">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="e1ce6-240">Kali</span><span class="sxs-lookup"><span data-stu-id="e1ce6-240">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="e1ce6-241">Instalación, Kali</span><span class="sxs-lookup"><span data-stu-id="e1ce6-241">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
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

### <a name="uninstallation---kali"></a><span data-ttu-id="e1ce6-242">Desinstalación, Kali</span><span class="sxs-lookup"><span data-stu-id="e1ce6-242">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="e1ce6-243">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e1ce6-243">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="e1ce6-244">La compatibilidad con Raspbian es experimental.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-244">Raspbian support is experimental.</span></span>

<span data-ttu-id="e1ce6-245">Actualmente, PowerShell solo se admite en Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-245">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="e1ce6-246">Asimismo, CoreCLR (y, por tanto, PowerShell Core) solo funcionará en dispositivos Pi 2 y Pi 3 dado que otros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tienen un procesador no admitido.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-246">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="e1ce6-247">Descargue [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) y siga las [instrucciones de instalación](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para tenerlo en su Pi.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-247">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="e1ce6-248">Instalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="e1ce6-248">Installation - Raspbian</span></span>

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

<span data-ttu-id="e1ce6-249">Opcionalmente, puede crear un vínculo simbólico para poder iniciar PowerShell sin especificar la ruta de acceso al archivo binario "pwsh".</span><span class="sxs-lookup"><span data-stu-id="e1ce6-249">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e1ce6-250">Desinstalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="e1ce6-250">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e1ce6-251">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="e1ce6-251">Binary Archives</span></span>

<span data-ttu-id="e1ce6-252">Se proporcionan archivos binarios `tar.gz` de PowerShell para plataformas Linux, a fin de permitir escenarios de implementación avanzados.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-252">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e1ce6-253">Dependencias</span><span class="sxs-lookup"><span data-stu-id="e1ce6-253">Dependencies</span></span>

<span data-ttu-id="e1ce6-254">PowerShell compila archivos binarios portátiles para todas las distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-254">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="e1ce6-255">Aun así, el entorno de ejecución de .NET Core requiere dependencias diferentes en otras distribuciones, y por eso PowerShell hace lo mismo.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-255">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="e1ce6-256">En la tabla siguiente se muestran las dependencias de .NET Core 2.0 que se admiten oficialmente en diferentes distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-256">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="e1ce6-257">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="e1ce6-257">OS</span></span>                 | <span data-ttu-id="e1ce6-258">Dependencias</span><span class="sxs-lookup"><span data-stu-id="e1ce6-258">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e1ce6-259">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-259">Ubuntu 14.04</span></span>       | <span data-ttu-id="e1ce6-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e1ce6-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e1ce6-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e1ce6-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e1ce6-262">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-262">Ubuntu 16.04</span></span>       | <span data-ttu-id="e1ce6-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e1ce6-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e1ce6-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e1ce6-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e1ce6-265">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e1ce6-265">Ubuntu 17.10</span></span>       | <span data-ttu-id="e1ce6-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e1ce6-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e1ce6-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e1ce6-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e1ce6-268">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e1ce6-268">Ubuntu 18.04</span></span>       | <span data-ttu-id="e1ce6-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e1ce6-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e1ce6-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="e1ce6-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="e1ce6-271">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e1ce6-271">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e1ce6-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e1ce6-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e1ce6-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e1ce6-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e1ce6-274">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="e1ce6-274">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e1ce6-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e1ce6-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e1ce6-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e1ce6-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e1ce6-277">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e1ce6-277">CentOS 7</span></span> <br> <span data-ttu-id="e1ce6-278">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e1ce6-278">Oracle Linux 7</span></span> <br> <span data-ttu-id="e1ce6-279">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e1ce6-279">RHEL 7</span></span> | <span data-ttu-id="e1ce6-280">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="e1ce6-280">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e1ce6-281">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e1ce6-281">openSUSE 42.3</span></span> | <span data-ttu-id="e1ce6-282">libcurl4, libopenssl1_0_0 y libicu52_1</span><span class="sxs-lookup"><span data-stu-id="e1ce6-282">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="e1ce6-283">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e1ce6-283">openSUSE Leap 15</span></span> | <span data-ttu-id="e1ce6-284">libcurl4, libopenssl1_0_0 y libicu60_2</span><span class="sxs-lookup"><span data-stu-id="e1ce6-284">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="e1ce6-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="e1ce6-285">Fedora 27</span></span> <br> <span data-ttu-id="e1ce6-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e1ce6-286">Fedora 28</span></span> | <span data-ttu-id="e1ce6-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="e1ce6-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e1ce6-288">Para implementar archivos binarios de PowerShell en distribuciones de Linux que no se admiten oficialmente, debe instalar las dependencias necesarias para el sistema operativo de destino en varios pasos.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="e1ce6-289">Por ejemplo, nuestro [dockerfile de Amazon Linux][amazon-dockerfile] instala primero las dependencias y, después, extrae el archivo `tar.gz` de Linux.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e1ce6-290">Instalación, archivos binarios</span><span class="sxs-lookup"><span data-stu-id="e1ce6-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e1ce6-291">Linux</span><span class="sxs-lookup"><span data-stu-id="e1ce6-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="e1ce6-292">Desinstalación de archivos binarios</span><span class="sxs-lookup"><span data-stu-id="e1ce6-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e1ce6-293">Rutas de acceso</span><span class="sxs-lookup"><span data-stu-id="e1ce6-293">Paths</span></span>

* <span data-ttu-id="e1ce6-294">`$PSHOME` es `/opt/microsoft/powershell/6.1.0/`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-294">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="e1ce6-295">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e1ce6-296">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e1ce6-297">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e1ce6-298">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e1ce6-299">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e1ce6-300">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e1ce6-301">Los perfiles respetan la configuración de cada host de PowerShell, por lo que hay perfiles predeterminados específicos del host en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e1ce6-302">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en Linux.</span><span class="sxs-lookup"><span data-stu-id="e1ce6-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
