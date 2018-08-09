---
title: Instalación de PowerShell Core en Linux
description: Información sobre cómo instalar PowerShell Core en varias distribuciones Linux
ms.date: 08/06/2018
ms.openlocfilehash: a6b0e3003f84ea6dc99cffcc7edf1b5b6963aa21
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587455"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="9b6bf-103">Instalación de PowerShell Core en Linux</span><span class="sxs-lookup"><span data-stu-id="9b6bf-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="9b6bf-104">Es compatible con [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] y [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="9b6bf-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="9b6bf-105">Para distribuciones de Linux que no sean compatibles oficialmente, puede usar el archivo [Paquete Snap de PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="9b6bf-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="9b6bf-106">También puede intentar implementar los archivos binarios de PowerShell directamente mediante el [archivo `tar.gz`][tar] de Linux, pero deberá configurar las dependencias necesarias según el sistema operativo en pasos independientes.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="9b6bf-107">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="9b6bf-108">Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="9b6bf-109">Instalación de versiones preliminares</span><span class="sxs-lookup"><span data-stu-id="9b6bf-109">Installing Preview Releases</span></span>

<span data-ttu-id="9b6bf-110">Al instalar una versión preliminar de PowerShell Core para Linux mediante un repositorio de paquetes, el nombre del paquete cambia de `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="9b6bf-111">La instalación mediante la descarga directa solo cambia el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="9b6bf-112">A continuación se muestra una tabla con los comandos para instalar los paquetes estables y de versión preliminar mediante los diversos administradores de paquetes:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="9b6bf-113">Distribuciones</span><span class="sxs-lookup"><span data-stu-id="9b6bf-113">Distribution(s)</span></span>|<span data-ttu-id="9b6bf-114">Comando estable</span><span class="sxs-lookup"><span data-stu-id="9b6bf-114">Stable Command</span></span> | <span data-ttu-id="9b6bf-115">Comando de versión preliminar</span><span class="sxs-lookup"><span data-stu-id="9b6bf-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="9b6bf-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="9b6bf-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="9b6bf-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="9b6bf-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="9b6bf-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="9b6bf-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="9b6bf-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="9b6bf-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="9b6bf-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="9b6bf-121">Instalación mediante un repositorio de paquetes, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="9b6bf-122">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="9b6bf-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="9b6bf-123">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-123">This is the preferred method.</span></span>

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

<span data-ttu-id="9b6bf-124">Como superusuario, registre el repositorio de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="9b6bf-125">Desde ese momento, solo debe usar `sudo apt-get upgrade powershell` para actualizar la instalación.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="9b6bf-126">Instalación mediante descarga directa, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="9b6bf-127">Descargue el paquete de Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-127">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="9b6bf-128">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="9b6bf-129">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="9b6bf-130">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="9b6bf-131">Desinstalación, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="9b6bf-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="9b6bf-133">Instalación mediante un repositorio de paquetes, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="9b6bf-134">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="9b6bf-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="9b6bf-135">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-135">This is the preferred method.</span></span>

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

<span data-ttu-id="9b6bf-136">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="9b6bf-137">Instalación mediante descarga directa, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="9b6bf-138">Descargue el paquete de Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-138">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="9b6bf-139">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-139">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="9b6bf-140">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-140">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="9b6bf-141">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="9b6bf-142">Desinstalación, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-142">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="9b6bf-143">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-143">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="9b6bf-144">Se ha agregado compatibilidad con Ubuntu 18.04 después de `6.1.0-preview.2`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-144">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="9b6bf-145">Instalación mediante un repositorio de paquetes, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="9b6bf-146">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="9b6bf-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="9b6bf-147">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-147">This is the preferred method.</span></span>

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

<span data-ttu-id="9b6bf-148">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="9b6bf-149">Instalación mediante descarga directa, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="9b6bf-150">Descargue el paquete de Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-150">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="9b6bf-151">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-151">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="9b6bf-152">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-152">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="9b6bf-153">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="9b6bf-154">Desinstalación, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-154">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="9b6bf-155">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="9b6bf-155">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="9b6bf-156">Se ha agregado compatibilidad con Ubuntu 18.10 después de `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-156">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="9b6bf-157">Como 18.10 es una compilación diaria, solo tiene soporte técnico comunitario.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-157">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="9b6bf-158">La instalación en 18.10 se admite mediante `snapd`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="9b6bf-159">Consulte [Paquete Snap][snap] para ver instrucciones completas;</span><span class="sxs-lookup"><span data-stu-id="9b6bf-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="9b6bf-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="9b6bf-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="9b6bf-161">Instalación mediante un repositorio de paquetes, Debian 8</span><span class="sxs-lookup"><span data-stu-id="9b6bf-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="9b6bf-162">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="9b6bf-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="9b6bf-163">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-163">This is the preferred method.</span></span>

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

<span data-ttu-id="9b6bf-164">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="9b6bf-165">Instalación mediante descarga directa, Debian 8</span><span class="sxs-lookup"><span data-stu-id="9b6bf-165">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="9b6bf-166">Descargue el paquete de Debian `powershell_6.0.2-1.debian.8_amd64.deb` desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-166">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="9b6bf-167">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-167">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="9b6bf-168">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-168">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="9b6bf-169">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-169">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="9b6bf-170">Desinstalación, Debian 8</span><span class="sxs-lookup"><span data-stu-id="9b6bf-170">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="9b6bf-171">Debian 9</span><span class="sxs-lookup"><span data-stu-id="9b6bf-171">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="9b6bf-172">Instalación mediante un repositorio de paquetes, Debian 9</span><span class="sxs-lookup"><span data-stu-id="9b6bf-172">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="9b6bf-173">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="9b6bf-173">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="9b6bf-174">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-174">This is the preferred method.</span></span>

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

<span data-ttu-id="9b6bf-175">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-175">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="9b6bf-176">Instalación mediante descarga directa, Debian 9</span><span class="sxs-lookup"><span data-stu-id="9b6bf-176">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="9b6bf-177">Descargue el paquete de Debian `powershell_6.0.2-1.debian.9_amd64.deb` desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-177">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="9b6bf-178">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-178">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="9b6bf-179">Desinstalación, Debian 9</span><span class="sxs-lookup"><span data-stu-id="9b6bf-179">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="9b6bf-180">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9b6bf-180">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="9b6bf-181">Este paquete también funciona en Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-181">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="9b6bf-182">Instalación mediante un repositorio de paquetes (opción preferida), CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9b6bf-182">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="9b6bf-183">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="9b6bf-183">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="9b6bf-184">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-184">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="9b6bf-185">Instalación mediante descarga directa, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9b6bf-185">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="9b6bf-186">Cuando use [CentOS 7][], descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina CentOS.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-186">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="9b6bf-187">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-187">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="9b6bf-188">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="9b6bf-189">Desinstalación, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9b6bf-189">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9b6bf-191">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9b6bf-191">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9b6bf-192">Instalación a través de un repositorio de paquetes (opción preferida), Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9b6bf-192">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="9b6bf-193">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="9b6bf-193">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="9b6bf-194">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-194">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9b6bf-195">Instalación mediante descarga directa, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9b6bf-195">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="9b6bf-196">Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-196">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="9b6bf-197">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-197">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="9b6bf-198">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-198">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9b6bf-199">Desinstalación, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9b6bf-199">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="9b6bf-200">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="9b6bf-200">OpenSUSE 42.3</span></span>

<span data-ttu-id="9b6bf-201">Al instalar PowerShell Core, `zypper` puede notificar el siguiente error:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-201">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="9b6bf-202">En este caso, verifique que haya una biblioteca `libcurl` compatible. Para ello, compruebe que mediante el siguiente comando se muestre que el paquete `libcurl4` está instalado:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-202">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="9b6bf-203">A continuación, elija la solución `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` al instalar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-203">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="9b6bf-204">Instalación mediante un repositorio de paquetes (opción preferida), OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="9b6bf-204">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="9b6bf-205">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="9b6bf-205">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="9b6bf-206">Instalación mediante descarga directa, OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="9b6bf-206">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="9b6bf-207">Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-207">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="9b6bf-208">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-208">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="9b6bf-209">Desinstalación, OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="9b6bf-209">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="9b6bf-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="9b6bf-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="9b6bf-211">Fedora 28 solo se admite en PowerShell Core 6.1 y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="9b6bf-212">Instalación mediante un repositorio de paquetes (opción preferida), Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9b6bf-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="9b6bf-213">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="9b6bf-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="9b6bf-214">Instalación mediante descarga directa, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9b6bf-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="9b6bf-215">Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-215">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="9b6bf-216">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-216">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="9b6bf-217">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-217">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="9b6bf-218">Desinstalación, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9b6bf-218">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="9b6bf-219">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="9b6bf-219">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="9b6bf-220">La compatibilidad con Arch es experimental.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-220">Arch support is experimental.</span></span>

<span data-ttu-id="9b6bf-221">PowerShell está disponible en el repositorio de usuario [Arch Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="9b6bf-221">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="9b6bf-222">Se puede compilar con la [versión etiquetada más reciente][arch-release].</span><span class="sxs-lookup"><span data-stu-id="9b6bf-222">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="9b6bf-223">Se puede compilar desde la [última confirmación en maestro][arch-git].</span><span class="sxs-lookup"><span data-stu-id="9b6bf-223">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="9b6bf-224">Se puede instalar mediante el [binario de la versión más reciente][arch-bin].</span><span class="sxs-lookup"><span data-stu-id="9b6bf-224">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="9b6bf-225">Los paquetes del AUR se mantienen gracias a la comunidad, ya que no hay asistencia oficial.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-225">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="9b6bf-226">Para más información sobre cómo instalar paquetes desde el AUR, vea la [wiki de Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-226">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="9b6bf-228">Paquete Snap</span><span class="sxs-lookup"><span data-stu-id="9b6bf-228">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="9b6bf-229">Obtención de snapd</span><span class="sxs-lookup"><span data-stu-id="9b6bf-229">Getting snapd</span></span>

<span data-ttu-id="9b6bf-230">`snapd` es necesario para ejecutar paquetes Snap.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-230">`snapd` is required to run snaps.</span></span>  <span data-ttu-id="9b6bf-231">Use [estas instrucciones](https://docs.snapcraft.io/core/install) para asegurarse de que tiene `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-231">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="9b6bf-232">Instalación mediante Snap</span><span class="sxs-lookup"><span data-stu-id="9b6bf-232">Installation via Snap</span></span>

<span data-ttu-id="9b6bf-233">PowerShell Core para Linux se publica en la [Snap store](https://snapcraft.io/store) para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="9b6bf-233">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="9b6bf-234">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-234">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="9b6bf-235">Después de instalar Snap, se actualizará automáticamente, pero puede desencadenar una actualización con `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-235">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="9b6bf-236">Desinstalación</span><span class="sxs-lookup"><span data-stu-id="9b6bf-236">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a><span data-ttu-id="9b6bf-237">AppImage de Linux</span><span class="sxs-lookup"><span data-stu-id="9b6bf-237">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="9b6bf-238">La compatibilidad con AppImage es experimental.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-238">AppImage support is experimental</span></span>

<span data-ttu-id="9b6bf-239">Si usa una distribución de Linux reciente, descargue el archivo AppImage `powershell-6.0.1-x86_64.AppImage` desde la página de [versiones][] en el equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-239">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="9b6bf-240">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="9b6bf-240">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="9b6bf-241">El archivo [AppImage][] permite ejecutar PowerShell sin instalarlo.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-241">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="9b6bf-242">Se trata de una aplicación portátil que empaqueta PowerShell y sus dependencias (incluidas las dependencias del sistema de .NET Core) en un paquete coherente.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-242">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="9b6bf-243">Este paquete es un archivo binario único que funciona con independencia de la distribución de Linux del usuario.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-243">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="9b6bf-245">Kali</span><span class="sxs-lookup"><span data-stu-id="9b6bf-245">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="9b6bf-246">La compatibilidad con Kali es experimental.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-246">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="9b6bf-247">Instalación</span><span class="sxs-lookup"><span data-stu-id="9b6bf-247">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="9b6bf-248">Ejecución de PowerShell en la versión más reciente de Kali (Kali GNU/Linux Rolling) sin instalarlo</span><span class="sxs-lookup"><span data-stu-id="9b6bf-248">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="9b6bf-249">Desinstalación, Kali</span><span class="sxs-lookup"><span data-stu-id="9b6bf-249">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="9b6bf-250">Raspbian</span><span class="sxs-lookup"><span data-stu-id="9b6bf-250">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="9b6bf-251">La compatibilidad con Raspbian es experimental.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-251">Raspbian support is experimental.</span></span>

<span data-ttu-id="9b6bf-252">Actualmente, PowerShell solo se admite en Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-252">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="9b6bf-253">Asimismo, CoreCLR (y, por tanto, PowerShell Core) solo funcionará en dispositivos Pi 2 y Pi 3 dado que otros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tienen un procesador no admitido.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-253">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="9b6bf-254">Descargue [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) y siga las [instrucciones de instalación](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para tenerlo en su Pi.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="9b6bf-255">Instalación</span><span class="sxs-lookup"><span data-stu-id="9b6bf-255">Installation</span></span>

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

<span data-ttu-id="9b6bf-256">Opcionalmente, puede crear un vínculo simbólico para poder iniciar PowerShell sin especificar la ruta de acceso al archivo binario "pwsh".</span><span class="sxs-lookup"><span data-stu-id="9b6bf-256">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="9b6bf-257">Desinstalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="9b6bf-257">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="9b6bf-258">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="9b6bf-258">Binary Archives</span></span>

<span data-ttu-id="9b6bf-259">Se proporcionan archivos binarios `tar.gz` de PowerShell para plataformas Linux, a fin de permitir escenarios de implementación avanzados.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="9b6bf-260">Dependencias</span><span class="sxs-lookup"><span data-stu-id="9b6bf-260">Dependencies</span></span>

<span data-ttu-id="9b6bf-261">PowerShell compila archivos binarios portátiles para todas las distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-261">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="9b6bf-262">Aun así, el entorno de ejecución de .NET Core requiere dependencias diferentes en otras distribuciones, y por eso PowerShell hace lo mismo.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-262">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="9b6bf-263">En la tabla siguiente se muestran las dependencias de .NET Core 2.0 que se admiten oficialmente en diferentes distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="9b6bf-264">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="9b6bf-264">OS</span></span>                 | <span data-ttu-id="9b6bf-265">Dependencias</span><span class="sxs-lookup"><span data-stu-id="9b6bf-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="9b6bf-266">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-266">Ubuntu 14.04</span></span>       | <span data-ttu-id="9b6bf-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="9b6bf-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9b6bf-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="9b6bf-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="9b6bf-269">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-269">Ubuntu 16.04</span></span>       | <span data-ttu-id="9b6bf-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="9b6bf-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9b6bf-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="9b6bf-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="9b6bf-272">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="9b6bf-272">Ubuntu 17.10</span></span>       | <span data-ttu-id="9b6bf-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="9b6bf-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9b6bf-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="9b6bf-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="9b6bf-275">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9b6bf-275">Ubuntu 18.04</span></span>       | <span data-ttu-id="9b6bf-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="9b6bf-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9b6bf-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="9b6bf-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="9b6bf-278">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="9b6bf-278">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="9b6bf-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="9b6bf-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9b6bf-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="9b6bf-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="9b6bf-281">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="9b6bf-281">Debian 9 (Stretch)</span></span> | <span data-ttu-id="9b6bf-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="9b6bf-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9b6bf-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="9b6bf-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="9b6bf-284">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9b6bf-284">CentOS 7</span></span> <br> <span data-ttu-id="9b6bf-285">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="9b6bf-285">Oracle Linux 7</span></span> <br> <span data-ttu-id="9b6bf-286">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="9b6bf-286">RHEL 7</span></span> <br> <span data-ttu-id="9b6bf-287">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="9b6bf-287">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="9b6bf-288">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="9b6bf-288">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="9b6bf-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="9b6bf-289">Fedora 27</span></span> <br> <span data-ttu-id="9b6bf-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9b6bf-290">Fedora 28</span></span> | <span data-ttu-id="9b6bf-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="9b6bf-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="9b6bf-292">Para implementar archivos binarios de PowerShell en distribuciones de Linux que no se admiten oficialmente, debe instalar las dependencias necesarias para el sistema operativo de destino en varios pasos.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-292">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="9b6bf-293">Por ejemplo, nuestro [dockerfile de Amazon Linux][amazon-dockerfile] instala primero las dependencias y, después, extrae el archivo `tar.gz` de Linux.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="9b6bf-294">Instalación, archivos binarios</span><span class="sxs-lookup"><span data-stu-id="9b6bf-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="9b6bf-295">Linux</span><span class="sxs-lookup"><span data-stu-id="9b6bf-295">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="9b6bf-296">Desinstalación de archivos binarios</span><span class="sxs-lookup"><span data-stu-id="9b6bf-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="9b6bf-297">Rutas de acceso</span><span class="sxs-lookup"><span data-stu-id="9b6bf-297">Paths</span></span>

* <span data-ttu-id="9b6bf-298">`$PSHOME` es `/opt/microsoft/powershell/6.0.2/`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-298">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="9b6bf-299">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="9b6bf-300">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="9b6bf-301">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9b6bf-302">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9b6bf-303">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-303">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="9b6bf-304">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="9b6bf-305">Los perfiles respetan la configuración de cada host de PowerShell, por lo que hay perfiles predeterminados específicos del host en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="9b6bf-306">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en Linux.</span><span class="sxs-lookup"><span data-stu-id="9b6bf-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
