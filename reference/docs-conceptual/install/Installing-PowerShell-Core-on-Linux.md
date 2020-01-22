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
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="cfad8-103">Instalación de PowerShell Core en Linux</span><span class="sxs-lookup"><span data-stu-id="cfad8-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="cfad8-104">Admite [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] y [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="cfad8-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="cfad8-105">Para las distribuciones de Linux que no se admiten de forma oficial, puede probar a instalar PowerShell con el [Paquete Snap de PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="cfad8-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="cfad8-106">También puede intentar implementar los archivos binarios de PowerShell directamente mediante el [archivo `tar.gz`][tar] de Linux, pero tendrá que configurar las dependencias necesarias según el sistema operativo en pasos independientes.</span><span class="sxs-lookup"><span data-stu-id="cfad8-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="cfad8-107">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="cfad8-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="cfad8-108">Una vez instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="cfad8-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="cfad8-109">Ejecute `pwsh-preview` si instaló una [versión preliminar](#installing-preview-releases).</span><span class="sxs-lookup"><span data-stu-id="cfad8-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

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
> <span data-ttu-id="cfad8-110">Si ya tiene instalado el [SDK de .NET Core](/dotnet/core/sdk), es fácil instalar PowerShell como una [herramienta global de .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="cfad8-110">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="installing-preview-releases"></a><span data-ttu-id="cfad8-111">Instalación de versiones preliminares</span><span class="sxs-lookup"><span data-stu-id="cfad8-111">Installing Preview Releases</span></span>

<span data-ttu-id="cfad8-112">Al instalar una versión preliminar de PowerShell Core para Linux mediante un repositorio de paquetes, el nombre del paquete cambia de `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-112">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="cfad8-113">La instalación mediante la descarga directa solo cambia el nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="cfad8-113">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="cfad8-114">La tabla siguiente contiene los comandos para instalar los paquetes estables y de versión preliminar mediante los diversos administradores de paquetes:</span><span class="sxs-lookup"><span data-stu-id="cfad8-114">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="cfad8-115">Distribuciones</span><span class="sxs-lookup"><span data-stu-id="cfad8-115">Distribution(s)</span></span>|<span data-ttu-id="cfad8-116">Comando estable</span><span class="sxs-lookup"><span data-stu-id="cfad8-116">Stable Command</span></span> | <span data-ttu-id="cfad8-117">Comando de versión preliminar</span><span class="sxs-lookup"><span data-stu-id="cfad8-117">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="cfad8-118">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="cfad8-118">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="cfad8-119">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="cfad8-119">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="cfad8-120">Fedora</span><span class="sxs-lookup"><span data-stu-id="cfad8-120">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="cfad8-121">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cfad8-121">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="cfad8-122">Instalación mediante un repositorio de paquetes, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cfad8-122">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="cfad8-123">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="cfad8-123">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="cfad8-124">El método preferido es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="cfad8-124">The preferred method is as follows:</span></span>

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

<span data-ttu-id="cfad8-125">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="cfad8-125">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfad8-126">Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-126">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="cfad8-127">Instalación mediante descarga directa, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cfad8-127">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="cfad8-128">Descargue el paquete de Debian `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cfad8-128">Download the Debian package `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cfad8-129">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="cfad8-129">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cfad8-130">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="cfad8-130">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="cfad8-131">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cfad8-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="cfad8-132">Desinstalación, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cfad8-132">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="cfad8-133">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cfad8-133">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="cfad8-134">Instalación mediante un repositorio de paquetes, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cfad8-134">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="cfad8-135">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="cfad8-135">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="cfad8-136">El método preferido es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="cfad8-136">The preferred method is as follows:</span></span>

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

<span data-ttu-id="cfad8-137">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="cfad8-137">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfad8-138">Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-138">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="cfad8-139">Instalación mediante descarga directa, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cfad8-139">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="cfad8-140">Descargue el paquete de Debian `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cfad8-140">Download the Debian package `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cfad8-141">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="cfad8-141">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cfad8-142">El comando `dpkg -i` produce un error con las dependencias unmet.</span><span class="sxs-lookup"><span data-stu-id="cfad8-142">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="cfad8-143">El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cfad8-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="cfad8-144">Desinstalación, Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cfad8-144">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="cfad8-145">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="cfad8-145">Ubuntu 18.10</span></span>

<span data-ttu-id="cfad8-146">La instalación se admite a través de `snapd`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-146">Installation is supported via `snapd`.</span></span> <span data-ttu-id="cfad8-147">Para ver instrucciones, consulte [Paquete Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="cfad8-147">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="cfad8-148">Ubuntu 18.10 es una [versión provisional](https://www.ubuntu.com/about/release-cycle) que [la comunidad admite](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="cfad8-148">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="cfad8-149">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="cfad8-149">Ubuntu 19.04</span></span>

<span data-ttu-id="cfad8-150">La instalación se admite a través de `snapd`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-150">Installation is supported via `snapd`.</span></span> <span data-ttu-id="cfad8-151">Para ver instrucciones, consulte [Paquete Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="cfad8-151">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="cfad8-152">Ubuntu 19.04 es una [versión provisional](https://www.ubuntu.com/about/release-cycle) que [la comunidad admite](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="cfad8-152">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="cfad8-153">Debian 8</span><span class="sxs-lookup"><span data-stu-id="cfad8-153">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="cfad8-154">Instalación mediante un repositorio de paquetes, Debian 8</span><span class="sxs-lookup"><span data-stu-id="cfad8-154">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="cfad8-155">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="cfad8-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="cfad8-156">El método preferido es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="cfad8-156">The preferred method is as follows:</span></span>

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

<span data-ttu-id="cfad8-157">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="cfad8-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfad8-158">Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="cfad8-159">Debian 9</span><span class="sxs-lookup"><span data-stu-id="cfad8-159">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="cfad8-160">Instalación mediante un repositorio de paquetes, Debian 9</span><span class="sxs-lookup"><span data-stu-id="cfad8-160">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="cfad8-161">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="cfad8-161">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="cfad8-162">El método preferido es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="cfad8-162">The preferred method is as follows:</span></span>

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

<span data-ttu-id="cfad8-163">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="cfad8-163">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfad8-164">Después del registro, puede actualizar PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-164">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="cfad8-165">Instalación mediante descarga directa, Debian 9</span><span class="sxs-lookup"><span data-stu-id="cfad8-165">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="cfad8-166">Descargue el paquete de Debian `powershell_7.0.0-1.debian.9_amd64.deb` desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="cfad8-166">Download the Debian package `powershell_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="cfad8-167">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="cfad8-167">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="cfad8-168">Desinstalación, Debian 9</span><span class="sxs-lookup"><span data-stu-id="cfad8-168">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="cfad8-169">Debian 10</span><span class="sxs-lookup"><span data-stu-id="cfad8-169">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="cfad8-170">Debian 10 solo es compatible con PowerShell 7.0 y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="cfad8-170">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="cfad8-171">Instalación mediante descarga directa, Debian 10</span><span class="sxs-lookup"><span data-stu-id="cfad8-171">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="cfad8-172">Descargue el paquete tar.gz `powershell_7.0.0-preview-7-linux-x64.tar.gz` desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="cfad8-172">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="cfad8-173">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="cfad8-173">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="cfad8-174">Alpine 3.9 y 3.10</span><span class="sxs-lookup"><span data-stu-id="cfad8-174">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="cfad8-175">Alpine 3.9 y 3.10 solo son compatibles con PowerShell 7.0. y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="cfad8-175">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="cfad8-176">Instalación mediante descarga directa, Alpine 3.9 y 3.10</span><span class="sxs-lookup"><span data-stu-id="cfad8-176">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="cfad8-177">Descargue el paquete tar.gz `powershell_7.0.0-preview-7-linux-x64.tar.gz` desde la página de [versiones][] en la máquina Alpine.</span><span class="sxs-lookup"><span data-stu-id="cfad8-177">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="cfad8-178">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="cfad8-178">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="centos-7"></a><span data-ttu-id="cfad8-179">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cfad8-179">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="cfad8-180">Este paquete funciona en Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="cfad8-180">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="cfad8-181">Instalación mediante un repositorio de paquetes (opción preferida), CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cfad8-181">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="cfad8-182">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="cfad8-182">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cfad8-183">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="cfad8-183">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfad8-184">Después del registro, puede actualizar PowerShell con `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-184">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="cfad8-185">Instalación mediante descarga directa, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cfad8-185">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="cfad8-186">Cuando use [CentOS 7][], descargue el paquete RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina CentOS.</span><span class="sxs-lookup"><span data-stu-id="cfad8-186">Using [CentOS 7][], download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="cfad8-187">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="cfad8-187">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cfad8-188">Puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="cfad8-188">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="cfad8-189">Desinstalación, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cfad8-189">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cfad8-191">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cfad8-191">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cfad8-192">Instalación a través de un repositorio de paquetes (opción preferida), Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cfad8-192">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="cfad8-193">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="cfad8-193">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cfad8-194">Como superusuario, registre el repositorio de Microsoft una vez.</span><span class="sxs-lookup"><span data-stu-id="cfad8-194">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfad8-195">Después del registro, puede actualizar PowerShell con `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-195">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cfad8-196">Instalación mediante descarga directa, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cfad8-196">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="cfad8-197">Descargue el paquete RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="cfad8-197">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="cfad8-198">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="cfad8-198">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cfad8-199">Puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="cfad8-199">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cfad8-200">Desinstalación, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cfad8-200">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="cfad8-201">openSUSE</span><span class="sxs-lookup"><span data-stu-id="cfad8-201">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="cfad8-202">Instalación, OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="cfad8-202">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="cfad8-203">Instalación, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="cfad8-203">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="cfad8-204">Desinstalación, openSUSE 42.3 y openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="cfad8-204">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="cfad8-205">Fedora</span><span class="sxs-lookup"><span data-stu-id="cfad8-205">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="cfad8-206">Fedora 28 solo se admite en PowerShell Core 6.1 y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="cfad8-206">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="cfad8-207">Fedora 29 y 30 solo son compatibles con PowerShell 7.0 y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="cfad8-207">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="cfad8-208">Instalación mediante un repositorio de paquetes (opción preferida), Fedora 28, 29 y 30</span><span class="sxs-lookup"><span data-stu-id="cfad8-208">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="cfad8-209">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="cfad8-209">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="cfad8-210">Instalación mediante descarga directa, Fedora 28, 29 y 30</span><span class="sxs-lookup"><span data-stu-id="cfad8-210">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="cfad8-211">Descargue el paquete RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="cfad8-211">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="cfad8-212">Luego, ejecute los comandos siguientes en el terminal:</span><span class="sxs-lookup"><span data-stu-id="cfad8-212">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cfad8-213">Puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="cfad8-213">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="cfad8-214">Desinstalación, Fedora 28, 29 y 30</span><span class="sxs-lookup"><span data-stu-id="cfad8-214">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="cfad8-215">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="cfad8-215">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="cfad8-216">Microsoft no admite de forma oficial la compatibilidad con Arch, cuyo mantenimiento lo realiza la comunidad.</span><span class="sxs-lookup"><span data-stu-id="cfad8-216">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="cfad8-217">PowerShell está disponible en el repositorio de usuario [Arch Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="cfad8-217">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="cfad8-218">Se puede compilar con la [versión etiquetada más reciente][arch-release].</span><span class="sxs-lookup"><span data-stu-id="cfad8-218">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="cfad8-219">Se puede compilar desde la [última confirmación en maestro][arch-git].</span><span class="sxs-lookup"><span data-stu-id="cfad8-219">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="cfad8-220">Se puede instalar mediante el [binario de la versión más reciente][arch-bin].</span><span class="sxs-lookup"><span data-stu-id="cfad8-220">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="cfad8-221">Los paquetes del AUR se mantienen gracias a la comunidad, ya que no hay asistencia oficial.</span><span class="sxs-lookup"><span data-stu-id="cfad8-221">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="cfad8-222">Para más información sobre cómo instalar paquetes desde el AUR, vea la [wiki de Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="cfad8-222">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="cfad8-224">Paquete Snap</span><span class="sxs-lookup"><span data-stu-id="cfad8-224">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="cfad8-225">Obtención de snapd</span><span class="sxs-lookup"><span data-stu-id="cfad8-225">Getting snapd</span></span>

<span data-ttu-id="cfad8-226">`snapd` es necesario para ejecutar paquetes Snap.</span><span class="sxs-lookup"><span data-stu-id="cfad8-226">`snapd` is required to run snaps.</span></span> <span data-ttu-id="cfad8-227">Use [estas instrucciones](https://docs.snapcraft.io/core/install) para asegurarse de que tiene `snapd` instalado.</span><span class="sxs-lookup"><span data-stu-id="cfad8-227">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="cfad8-228">Instalación mediante Snap</span><span class="sxs-lookup"><span data-stu-id="cfad8-228">Installation via Snap</span></span>

<span data-ttu-id="cfad8-229">PowerShell Core para Linux se publica en la [Snap store](https://snapcraft.io/store) para facilitar la instalación y las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="cfad8-229">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="cfad8-230">El método preferido es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="cfad8-230">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="cfad8-231">Para instalar una versión preliminar, use el método siguiente:</span><span class="sxs-lookup"><span data-stu-id="cfad8-231">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="cfad8-232">Después de la instalación, Snap se actualizará automáticamente.</span><span class="sxs-lookup"><span data-stu-id="cfad8-232">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="cfad8-233">Puede desencadenar una actualización mediante `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-233">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="cfad8-234">Desinstalación</span><span class="sxs-lookup"><span data-stu-id="cfad8-234">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="cfad8-235">or</span><span class="sxs-lookup"><span data-stu-id="cfad8-235">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="cfad8-236">Kali</span><span class="sxs-lookup"><span data-stu-id="cfad8-236">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="cfad8-237">Microsoft no admite de forma oficial la compatibilidad con Kali, cuyo mantenimiento lo realiza la comunidad.</span><span class="sxs-lookup"><span data-stu-id="cfad8-237">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="cfad8-238">Instalación, Kali</span><span class="sxs-lookup"><span data-stu-id="cfad8-238">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="cfad8-239">Desinstalación, Kali</span><span class="sxs-lookup"><span data-stu-id="cfad8-239">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="cfad8-240">Raspbian</span><span class="sxs-lookup"><span data-stu-id="cfad8-240">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="cfad8-241">La compatibilidad con Raspbian es experimental.</span><span class="sxs-lookup"><span data-stu-id="cfad8-241">Raspbian support is experimental.</span></span>

<span data-ttu-id="cfad8-242">Actualmente, PowerShell solo se admite en Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="cfad8-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="cfad8-243">CoreCLR y PowerShell Core solo funcionarán en dispositivos Pi 2 y Pi 3 dado que otros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tienen un procesador no admitido.</span><span class="sxs-lookup"><span data-stu-id="cfad8-243">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="cfad8-244">Descargue [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) y siga las [instrucciones de instalación](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para tenerlo en su Pi.</span><span class="sxs-lookup"><span data-stu-id="cfad8-244">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="cfad8-245">Instalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="cfad8-245">Installation - Raspbian</span></span>

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

<span data-ttu-id="cfad8-246">Opcionalmente, puede crear un vínculo simbólico para iniciar PowerShell sin especificar la ruta de acceso al archivo binario `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-246">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="cfad8-247">Desinstalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="cfad8-247">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="cfad8-248">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="cfad8-248">Binary Archives</span></span>

<span data-ttu-id="cfad8-249">Se proporcionan archivos binarios `tar.gz` de PowerShell para plataformas Linux, a fin de permitir escenarios de implementación avanzados.</span><span class="sxs-lookup"><span data-stu-id="cfad8-249">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="cfad8-250">Dependencias</span><span class="sxs-lookup"><span data-stu-id="cfad8-250">Dependencies</span></span>

<span data-ttu-id="cfad8-251">PowerShell compila archivos binarios portátiles para todas las distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="cfad8-251">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="cfad8-252">Aun así, el entorno de ejecución de .NET Core requiere dependencias diferentes en otras distribuciones, y PowerShell también.</span><span class="sxs-lookup"><span data-stu-id="cfad8-252">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="cfad8-253">En la tabla siguiente se muestran las dependencias de .NET Core 2.0 que se admiten oficialmente en diferentes distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="cfad8-253">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="cfad8-254">SO</span><span class="sxs-lookup"><span data-stu-id="cfad8-254">OS</span></span>                 | <span data-ttu-id="cfad8-255">Dependencias</span><span class="sxs-lookup"><span data-stu-id="cfad8-255">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="cfad8-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cfad8-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="cfad8-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cfad8-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cfad8-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="cfad8-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="cfad8-259">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="cfad8-259">Ubuntu 17.10</span></span>       | <span data-ttu-id="cfad8-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cfad8-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cfad8-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="cfad8-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="cfad8-262">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cfad8-262">Ubuntu 18.04</span></span>       | <span data-ttu-id="cfad8-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cfad8-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cfad8-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="cfad8-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="cfad8-265">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="cfad8-265">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="cfad8-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cfad8-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cfad8-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="cfad8-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="cfad8-268">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="cfad8-268">Debian 9 (Stretch)</span></span> | <span data-ttu-id="cfad8-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="cfad8-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cfad8-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="cfad8-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="cfad8-271">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cfad8-271">CentOS 7</span></span> <br> <span data-ttu-id="cfad8-272">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="cfad8-272">Oracle Linux 7</span></span> <br> <span data-ttu-id="cfad8-273">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="cfad8-273">RHEL 7</span></span> | <span data-ttu-id="cfad8-274">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="cfad8-274">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="cfad8-275">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="cfad8-275">openSUSE 42.3</span></span> | <span data-ttu-id="cfad8-276">libcurl4, libopenssl1_0_0 y libicu52_1</span><span class="sxs-lookup"><span data-stu-id="cfad8-276">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="cfad8-277">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="cfad8-277">openSUSE Leap 15</span></span> | <span data-ttu-id="cfad8-278">libcurl4, libopenssl1_0_0 y libicu60_2</span><span class="sxs-lookup"><span data-stu-id="cfad8-278">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="cfad8-279">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="cfad8-279">Fedora 27</span></span> <br> <span data-ttu-id="cfad8-280">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="cfad8-280">Fedora 28</span></span> | <span data-ttu-id="cfad8-281">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="cfad8-281">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="cfad8-282">Para implementar archivos binarios de PowerShell en distribuciones de Linux que no se admiten oficialmente, debe instalar las dependencias necesarias para el sistema operativo de destino en varios pasos.</span><span class="sxs-lookup"><span data-stu-id="cfad8-282">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="cfad8-283">Por ejemplo, nuestro [dockerfile de Amazon Linux][amazon-dockerfile] instala primero las dependencias y, después, extrae el archivo `tar.gz` de Linux.</span><span class="sxs-lookup"><span data-stu-id="cfad8-283">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="cfad8-284">Instalación, archivos binarios</span><span class="sxs-lookup"><span data-stu-id="cfad8-284">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="cfad8-285">Linux</span><span class="sxs-lookup"><span data-stu-id="cfad8-285">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="cfad8-286">Desinstalación de archivos binarios</span><span class="sxs-lookup"><span data-stu-id="cfad8-286">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="cfad8-287">Rutas de acceso</span><span class="sxs-lookup"><span data-stu-id="cfad8-287">Paths</span></span>

* <span data-ttu-id="cfad8-288">`$PSHOME` es `/opt/microsoft/powershell/7/`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-288">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
* <span data-ttu-id="cfad8-289">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-289">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="cfad8-290">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-290">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="cfad8-291">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-291">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cfad8-292">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-292">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cfad8-293">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-293">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="cfad8-294">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="cfad8-294">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="cfad8-295">Los perfiles respetan la configuración de cada host de PowerShell, por lo que hay perfiles predeterminados específicos del host en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="cfad8-295">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="cfad8-296">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en Linux.</span><span class="sxs-lookup"><span data-stu-id="cfad8-296">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
