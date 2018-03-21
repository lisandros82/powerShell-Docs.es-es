# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="b88fb-101">Instalación de PowerShell Core en macOS y Linux</span><span class="sxs-lookup"><span data-stu-id="b88fb-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="b88fb-102">Admite [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch] y [macOS 10.12][mac].</span><span class="sxs-lookup"><span data-stu-id="b88fb-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="b88fb-103">Para distribuciones de Linux que no sean compatibles oficialmente, puede usar el archivo [AppImage de PowerShell][lai].</span><span class="sxs-lookup"><span data-stu-id="b88fb-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span> <span data-ttu-id="b88fb-104">También puede intentar implementar los archivos binarios de PowerShell directamente mediante el [archivo `tar.gz`][tar] de Linux, pero deberá configurar las dependencias necesarias según el sistema operativo en pasos independientes.</span><span class="sxs-lookup"><span data-stu-id="b88fb-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="b88fb-105">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="b88fb-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="b88fb-106">Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="b88fb-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="b88fb-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="b88fb-108">Instalación mediante un repositorio de paquetes, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="b88fb-109">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b88fb-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span> <span data-ttu-id="b88fb-110">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="b88fb-110">This is the preferred method.</span></span>

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

<span data-ttu-id="b88fb-111">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="b88fb-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="b88fb-112">Instalación mediante descarga directa, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="b88fb-113">Descargue el paquete de Debian `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="b88fb-113">Download the Debian package `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

<span data-ttu-id="b88fb-114">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b88fb-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b88fb-115">Tenga en cuenta que se producirá un error en `dpkg -i` con dependencias sin cumplir. El comando siguiente, `apt-get install -f`, las resuelve y termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b88fb-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="b88fb-116">Desinstalación, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="b88fb-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="b88fb-118">Instalación mediante un repositorio de paquetes, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="b88fb-119">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b88fb-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b88fb-120">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="b88fb-120">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b88fb-121">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="b88fb-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="b88fb-122">Instalación mediante descarga directa, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="b88fb-123">Descargue el paquete de Debian `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu:</span><span class="sxs-lookup"><span data-stu-id="b88fb-123">Download the Debian package `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

<span data-ttu-id="b88fb-124">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b88fb-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b88fb-125">Tenga en cuenta que se producirá un error en `dpkg -i` con dependencias sin cumplir. El comando siguiente, `apt-get install -f`, las resuelve y termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b88fb-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="b88fb-126">Desinstalación, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="b88fb-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="b88fb-128">Instalación mediante un repositorio de paquetes, Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="b88fb-129">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b88fb-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b88fb-130">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="b88fb-130">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b88fb-131">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="b88fb-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="b88fb-132">Instalación mediante descarga directa, Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="b88fb-133">Descargue el paquete de Debian `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu:</span><span class="sxs-lookup"><span data-stu-id="b88fb-133">Download the Debian package `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

<span data-ttu-id="b88fb-134">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b88fb-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b88fb-135">Tenga en cuenta que se producirá un error en `dpkg -i` con dependencias sin cumplir. El comando siguiente, `apt-get install -f`, las resuelve y termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b88fb-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="b88fb-136">Desinstalación, Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="b88fb-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="b88fb-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="b88fb-138">Instalación mediante un repositorio de paquetes, Debian 8</span><span class="sxs-lookup"><span data-stu-id="b88fb-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="b88fb-139">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b88fb-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b88fb-140">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="b88fb-140">This is the preferred method.</span></span>

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

<span data-ttu-id="b88fb-141">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="b88fb-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="b88fb-142">Instalación mediante descarga directa, Debian 8</span><span class="sxs-lookup"><span data-stu-id="b88fb-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="b88fb-143">Descargue el paquete de Debian `powershell_6.0.0-1.debian.8_amd64.deb` desde la página de [versiones][] en la máquina Debian:</span><span class="sxs-lookup"><span data-stu-id="b88fb-143">Download the Debian package `powershell_6.0.0-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

<span data-ttu-id="b88fb-144">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b88fb-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b88fb-145">Tenga en cuenta que se producirá un error en `dpkg -i` con dependencias sin cumplir. El comando siguiente, `apt-get install -f`, las resuelve y termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b88fb-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="b88fb-146">Desinstalación, Debian 8</span><span class="sxs-lookup"><span data-stu-id="b88fb-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="b88fb-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="b88fb-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="b88fb-148">Instalación mediante un repositorio de paquetes, Debian 9</span><span class="sxs-lookup"><span data-stu-id="b88fb-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="b88fb-149">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b88fb-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="b88fb-150">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="b88fb-150">This is the preferred method.</span></span>

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

<span data-ttu-id="b88fb-151">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="b88fb-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="b88fb-152">Instalación mediante descarga directa, Debian 9</span><span class="sxs-lookup"><span data-stu-id="b88fb-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="b88fb-153">Descargue el paquete de Debian `powershell_6.0.0-1.debian.9_amd64.deb` desde la página de [versiones][] en la máquina Debian:</span><span class="sxs-lookup"><span data-stu-id="b88fb-153">Download the Debian package `powershell_6.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="b88fb-154">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b88fb-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="b88fb-155">Tenga en cuenta que se producirá un error en `dpkg -i` con dependencias sin cumplir. El comando siguiente, `apt-get install -f`, las resuelve y termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b88fb-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="b88fb-156">Desinstalación, Debian 9</span><span class="sxs-lookup"><span data-stu-id="b88fb-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="b88fb-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b88fb-157">CentOS 7</span></span>

> <span data-ttu-id="b88fb-158">Este paquete también funciona en Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="b88fb-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="b88fb-159">Instalación mediante un repositorio de paquetes (opción preferida), CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b88fb-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="b88fb-160">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b88fb-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b88fb-161">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b88fb-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="b88fb-162">Instalación mediante descarga directa, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b88fb-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="b88fb-163">Cuando use [CentOS 7][], descargue el paquete RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina CentOS:</span><span class="sxs-lookup"><span data-stu-id="b88fb-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b88fb-164">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b88fb-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b88fb-165">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b88fb-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="b88fb-166">Desinstalación, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b88fb-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b88fb-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b88fb-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b88fb-169">Instalación a través de un repositorio de paquetes (opción preferida), Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b88fb-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b88fb-170">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b88fb-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="b88fb-171">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b88fb-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b88fb-172">Instalación mediante descarga directa, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b88fb-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="b88fb-173">Descargue el paquete RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Red Hat Enterprise Linux:</span><span class="sxs-lookup"><span data-stu-id="b88fb-173">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="b88fb-174">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b88fb-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b88fb-175">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b88fb-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="b88fb-176">Desinstalación, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="b88fb-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="b88fb-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="b88fb-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="b88fb-178">**Nota**: Al instalar PowerShell Core, `zypper` puede informar del siguiente error:</span><span class="sxs-lookup"><span data-stu-id="b88fb-178">**Note:** When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```text
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="b88fb-179">En este caso, verifique que haya una biblioteca `libcurl` compatible. Para ello, compruebe que mediante el siguiente comando se muestre que el paquete `libcurl4` está instalado:</span><span class="sxs-lookup"><span data-stu-id="b88fb-179">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="b88fb-180">A continuación, elija la solución `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` al instalar el paquete `powershell`.</span><span class="sxs-lookup"><span data-stu-id="b88fb-180">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the `powershell` package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="b88fb-181">Instalación mediante un repositorio de paquetes (opción preferida), OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="b88fb-181">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="b88fb-182">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b88fb-182">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="b88fb-183">Instalación mediante descarga directa, OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="b88fb-183">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="b88fb-184">Descargue el paquete RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina OpenSUSE:</span><span class="sxs-lookup"><span data-stu-id="b88fb-184">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b88fb-185">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b88fb-185">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="b88fb-186">Desinstalación, OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="b88fb-186">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="b88fb-187">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b88fb-187">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="b88fb-188">Instalación mediante un repositorio de paquetes (opción preferida), Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b88fb-188">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="b88fb-189">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b88fb-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="b88fb-190">Instalación mediante descarga directa, Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b88fb-190">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="b88fb-191">Descargue el paquete RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Fedora:</span><span class="sxs-lookup"><span data-stu-id="b88fb-191">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b88fb-192">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b88fb-192">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b88fb-193">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b88fb-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="b88fb-194">Desinstalación, Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b88fb-194">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="b88fb-195">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b88fb-195">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="b88fb-196">Instalación mediante un repositorio de paquetes (opción preferida), Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b88fb-196">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="b88fb-197">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="b88fb-197">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="b88fb-198">Instalación mediante descarga directa, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b88fb-198">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="b88fb-199">Descargue el paquete RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Fedora:</span><span class="sxs-lookup"><span data-stu-id="b88fb-199">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b88fb-200">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b88fb-200">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="b88fb-201">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="b88fb-201">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="b88fb-202">Desinstalación, Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b88fb-202">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="b88fb-203">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="b88fb-203">Arch Linux</span></span>

<span data-ttu-id="b88fb-204">PowerShell está disponible en el repositorio de usuario [Arch Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="b88fb-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="b88fb-205">Se puede compilar con la [versión etiquetada más reciente][arch-release].</span><span class="sxs-lookup"><span data-stu-id="b88fb-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="b88fb-206">Se puede compilar desde la [última confirmación en maestro][arch-git].</span><span class="sxs-lookup"><span data-stu-id="b88fb-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="b88fb-207">Se puede instalar mediante el [binario de la versión más reciente][arch-bin].</span><span class="sxs-lookup"><span data-stu-id="b88fb-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="b88fb-208">Los paquetes del AUR se mantienen gracias a la comunidad, ya que no hay asistencia oficial.</span><span class="sxs-lookup"><span data-stu-id="b88fb-208">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="b88fb-209">Para más información sobre cómo instalar paquetes desde el AUR, vea la [wiki de Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="b88fb-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="b88fb-211">AppImage de Linux</span><span class="sxs-lookup"><span data-stu-id="b88fb-211">Linux AppImage</span></span>

<span data-ttu-id="b88fb-212">Si usa una distribución de Linux reciente, descargue el archivo AppImage `powershell-6.0.0-x86_64.AppImage` desde la página de [versiones][] en el equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="b88fb-212">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="b88fb-213">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="b88fb-213">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

<span data-ttu-id="b88fb-214">El archivo [AppImage][] permite ejecutar PowerShell sin instalarlo.</span><span class="sxs-lookup"><span data-stu-id="b88fb-214">The [AppImage][] lets you run PowerShell without installing it.</span></span> <span data-ttu-id="b88fb-215">Se trata de una aplicación portátil que empaqueta PowerShell y sus dependencias (incluidas las dependencias del sistema de .NET Core) en un paquete coherente.</span><span class="sxs-lookup"><span data-stu-id="b88fb-215">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span> <span data-ttu-id="b88fb-216">Este paquete funciona con independencia de la distribución de Linux del usuario y es un solo archivo binario.</span><span class="sxs-lookup"><span data-stu-id="b88fb-216">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="b88fb-218">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="b88fb-218">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="b88fb-219">Instalación mediante Homebrew (opción preferida), macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="b88fb-219">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="b88fb-220">[Homebrew][brew] es el administrador de paquetes que faltan de macOS.</span><span class="sxs-lookup"><span data-stu-id="b88fb-220">[Homebrew][brew] is the missing package manager for macOS.</span></span> <span data-ttu-id="b88fb-221">Si no se encuentra el comando `brew`, debe instalar Homebrew según [sus instrucciones][brew].</span><span class="sxs-lookup"><span data-stu-id="b88fb-221">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="b88fb-222">Una vez que haya instalado Homebrew, le resultará muy fácil instalar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b88fb-222">Once you've installed Homebrew, installing PowerShell is easy.</span></span> <span data-ttu-id="b88fb-223">En primer lugar, instale [Homebrew-Cask][cask] para poder instalar más paquetes:</span><span class="sxs-lookup"><span data-stu-id="b88fb-223">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="b88fb-224">Ahora puede instalar PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b88fb-224">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="b88fb-225">Cuando se publiquen nuevas versiones de PowerShell, bastará con actualizar las fórmulas de Homebrew y PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b88fb-225">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="b88fb-226">Nota: Debido a [este problema de Cask](https://github.com/caskroom/homebrew-cask/issues/29301), actualmente es necesario efectuar una reinstalación para actualizar.</span><span class="sxs-lookup"><span data-stu-id="b88fb-226">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="b88fb-227">Instalación mediante descarga directa, macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="b88fb-227">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="b88fb-228">Cuando use macOS 10.12, descargue el paquete PKG `powershell-6.0.0-osx.10.12-x64.pkg` desde la página de [versiones][] en la máquina macOS.</span><span class="sxs-lookup"><span data-stu-id="b88fb-228">Using macOS 10.12, download the PKG package `powershell-6.0.0-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="b88fb-229">Haga doble clic en el archivo y siga las indicaciones, o bien instálelo desde el terminal:</span><span class="sxs-lookup"><span data-stu-id="b88fb-229">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="b88fb-230">Desinstalación, macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="b88fb-230">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="b88fb-231">Si ha instalado PowerShell con Homebrew, la desinstalación es fácil:</span><span class="sxs-lookup"><span data-stu-id="b88fb-231">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="b88fb-232">Si ha instalado PowerShell mediante descarga directa, deberá quitar PowerShell manualmente:</span><span class="sxs-lookup"><span data-stu-id="b88fb-232">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="b88fb-233">Para desinstalar las rutas de acceso de PowerShell adicionales (por ejemplo, la ruta de acceso al perfil de usuario), vea más adelante en este documento la sección [Rutas de acceso][paths] y elimine las rutas de acceso deseadas con `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="b88fb-233">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span> <span data-ttu-id="b88fb-234">(Nota: Esto no es necesario si ha realizado la instalación con Homebrew).</span><span class="sxs-lookup"><span data-stu-id="b88fb-234">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="b88fb-235">Kali</span><span class="sxs-lookup"><span data-stu-id="b88fb-235">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="b88fb-236">Instalación</span><span class="sxs-lookup"><span data-stu-id="b88fb-236">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="b88fb-237">Ejecución de PowerShell en la versión más reciente de Kali (Kali GNU/Linux Rolling) sin instalarlo</span><span class="sxs-lookup"><span data-stu-id="b88fb-237">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="b88fb-238">Desinstalación, Kali</span><span class="sxs-lookup"><span data-stu-id="b88fb-238">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a><span data-ttu-id="b88fb-239">Raspbian</span><span class="sxs-lookup"><span data-stu-id="b88fb-239">Raspbian</span></span>

<span data-ttu-id="b88fb-240">Actualmente, PowerShell solo se admite en Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="b88fb-240">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="b88fb-241">Instalación</span><span class="sxs-lookup"><span data-stu-id="b88fb-241">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="b88fb-242">Desinstalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="b88fb-242">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="b88fb-243">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="b88fb-243">Binary Archives</span></span>

<span data-ttu-id="b88fb-244">Se proporcionan archivos binarios `tar.gz` de PowerShell para que las plataformas macOS y Linux permitan escenarios de implementación avanzada.</span><span class="sxs-lookup"><span data-stu-id="b88fb-244">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="b88fb-245">Dependencias</span><span class="sxs-lookup"><span data-stu-id="b88fb-245">Dependencies</span></span>

<span data-ttu-id="b88fb-246">En el caso de Linux, PowerShell compila binarios portátiles para todas las distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="b88fb-246">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="b88fb-247">Aun así, el entorno de ejecución de .NET Core requiere dependencias diferentes en otras distribuciones, y por eso PowerShell hace lo mismo.</span><span class="sxs-lookup"><span data-stu-id="b88fb-247">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="b88fb-248">En la tabla siguiente se muestran las dependencias de .NET Core 2.0 en diferentes distribuciones de Linux admitidas oficialmente.</span><span class="sxs-lookup"><span data-stu-id="b88fb-248">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="b88fb-249">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="b88fb-249">OS</span></span>                 | <span data-ttu-id="b88fb-250">Dependencias</span><span class="sxs-lookup"><span data-stu-id="b88fb-250">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="b88fb-251">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-251">Ubuntu 14.04</span></span>       | <span data-ttu-id="b88fb-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b88fb-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b88fb-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="b88fb-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="b88fb-254">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-254">Ubuntu 16.04</span></span>       | <span data-ttu-id="b88fb-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b88fb-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b88fb-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="b88fb-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="b88fb-257">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="b88fb-257">Ubuntu 17.04</span></span>       | <span data-ttu-id="b88fb-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b88fb-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b88fb-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="b88fb-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="b88fb-260">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="b88fb-260">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="b88fb-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b88fb-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b88fb-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="b88fb-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="b88fb-263">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="b88fb-263">Debian 9 (Stretch)</span></span> | <span data-ttu-id="b88fb-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="b88fb-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="b88fb-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="b88fb-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="b88fb-266">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="b88fb-266">CentOS 7</span></span> <br> <span data-ttu-id="b88fb-267">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="b88fb-267">Oracle Linux 7</span></span> <br> <span data-ttu-id="b88fb-268">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="b88fb-268">RHEL 7</span></span> <br> <span data-ttu-id="b88fb-269">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="b88fb-269">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="b88fb-270">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="b88fb-270">Fedora 25</span></span> | <span data-ttu-id="b88fb-271">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="b88fb-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="b88fb-272">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="b88fb-272">Fedora 26</span></span>          | <span data-ttu-id="b88fb-273">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="b88fb-273">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="b88fb-274">Para implementar los archivos binarios de PowerShell en las distribuciones de Linux que no se admiten oficialmente, deberá instalar las dependencias necesarias para el sistema operativo de destino en pasos independientes.</span><span class="sxs-lookup"><span data-stu-id="b88fb-274">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="b88fb-275">Por ejemplo, nuestro [dockerfile de Amazon Linux][amazon-dockerfile] instala primero las dependencias y, después, extrae el archivo `tar.gz` de Linux.</span><span class="sxs-lookup"><span data-stu-id="b88fb-275">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="b88fb-276">Instalación, archivos binarios</span><span class="sxs-lookup"><span data-stu-id="b88fb-276">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="b88fb-277">Linux</span><span class="sxs-lookup"><span data-stu-id="b88fb-277">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="b88fb-278">macOS</span><span class="sxs-lookup"><span data-stu-id="b88fb-278">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="b88fb-279">Desinstalación, archivos binarios</span><span class="sxs-lookup"><span data-stu-id="b88fb-279">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="b88fb-280">Linux</span><span class="sxs-lookup"><span data-stu-id="b88fb-280">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="b88fb-281">macOS</span><span class="sxs-lookup"><span data-stu-id="b88fb-281">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="b88fb-282">Rutas de acceso</span><span class="sxs-lookup"><span data-stu-id="b88fb-282">Paths</span></span>

* <span data-ttu-id="b88fb-283">`$PSHOME` es `/opt/microsoft/powershell/6.0.0/`.</span><span class="sxs-lookup"><span data-stu-id="b88fb-283">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="b88fb-284">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="b88fb-284">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="b88fb-285">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="b88fb-285">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="b88fb-286">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="b88fb-286">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b88fb-287">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="b88fb-287">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b88fb-288">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="b88fb-288">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="b88fb-289">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="b88fb-289">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="b88fb-290">Los perfiles respetan la configuración de cada host de PowerShell, por lo que hay perfiles predeterminados específicos del host en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="b88fb-290">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="b88fb-291">En Linux y macOS, se respeta la [especificación de directorio base de XDG][xdg-bds].</span><span class="sxs-lookup"><span data-stu-id="b88fb-291">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="b88fb-292">Tenga en cuenta que, dado que macOS es una derivación de BSD, el prefijo que se usa es `/usr/local` en lugar de `/opt`.</span><span class="sxs-lookup"><span data-stu-id="b88fb-292">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span> <span data-ttu-id="b88fb-293">Por lo tanto, `$PSHOME` es `/usr/local/microsoft/powershell/6.0.0/`, y el vínculo simbólico se coloca en `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="b88fb-293">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
