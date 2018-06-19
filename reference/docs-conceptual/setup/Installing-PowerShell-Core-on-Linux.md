# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="3df95-101">Instalación de PowerShell Core en Linux</span><span class="sxs-lookup"><span data-stu-id="3df95-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="3df95-102">Admite [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] y [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="3df95-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="3df95-103">Para distribuciones de Linux que no sean compatibles oficialmente, puede usar el archivo [AppImage de PowerShell][lai].</span><span class="sxs-lookup"><span data-stu-id="3df95-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="3df95-104">También puede intentar implementar los archivos binarios de PowerShell directamente mediante el [archivo `tar.gz`][tar] de Linux, pero deberá configurar las dependencias necesarias según el sistema operativo en pasos independientes.</span><span class="sxs-lookup"><span data-stu-id="3df95-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="3df95-105">Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.</span><span class="sxs-lookup"><span data-stu-id="3df95-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="3df95-106">Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.</span><span class="sxs-lookup"><span data-stu-id="3df95-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="3df95-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3df95-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="3df95-108">Instalación mediante un repositorio de paquetes, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3df95-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="3df95-109">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3df95-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3df95-110">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="3df95-110">This is the preferred method.</span></span>

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

<span data-ttu-id="3df95-111">Como superusuario, registre el repositorio de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3df95-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="3df95-112">Desde ese momento, solo debe usar `sudo apt-get upgrade powershell` para actualizar la instalación.</span><span class="sxs-lookup"><span data-stu-id="3df95-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="3df95-113">Instalación mediante descarga directa, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3df95-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="3df95-114">Descargue el paquete de Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="3df95-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3df95-115">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3df95-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="3df95-116">Tenga en cuenta que se producirá un error en `dpkg -i` con dependencias sin cumplir. El comando siguiente, `apt-get install -f`, las resuelve y termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3df95-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="3df95-117">Desinstalación, Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3df95-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="3df95-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3df95-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="3df95-119">Instalación mediante un repositorio de paquetes, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3df95-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="3df95-120">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3df95-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3df95-121">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="3df95-121">This is the preferred method.</span></span>

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

<span data-ttu-id="3df95-122">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="3df95-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="3df95-123">Instalación mediante descarga directa, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3df95-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="3df95-124">Descargue el paquete de Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="3df95-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3df95-125">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3df95-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="3df95-126">Tenga en cuenta que se producirá un error en `dpkg -i` con dependencias sin cumplir. El comando siguiente, `apt-get install -f`, las resuelve y termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3df95-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="3df95-127">Desinstalación, Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3df95-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="3df95-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="3df95-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="3df95-129">Instalación mediante un repositorio de paquetes, Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="3df95-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="3df95-130">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3df95-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3df95-131">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="3df95-131">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3df95-132">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="3df95-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="3df95-133">Instalación mediante descarga directa, Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="3df95-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="3df95-134">Descargue el paquete de Debian `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="3df95-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="3df95-135">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3df95-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="3df95-136">Tenga en cuenta que se producirá un error en `dpkg -i` con dependencias sin cumplir. El comando siguiente, `apt-get install -f`, las resuelve y termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3df95-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="3df95-137">Desinstalación, Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="3df95-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="3df95-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="3df95-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="3df95-139">Instalación mediante un repositorio de paquetes, Debian 8</span><span class="sxs-lookup"><span data-stu-id="3df95-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="3df95-140">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3df95-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3df95-141">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="3df95-141">This is the preferred method.</span></span>

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

<span data-ttu-id="3df95-142">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="3df95-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="3df95-143">Instalación mediante descarga directa, Debian 8</span><span class="sxs-lookup"><span data-stu-id="3df95-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="3df95-144">Descargue el paquete de Debian `powershell_6.0.2-1.debian.8_amd64.deb` desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="3df95-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3df95-145">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3df95-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3df95-146">Tenga en cuenta que `dpkg -i` producirá un error con dependencias inadecuadas.</span><span class="sxs-lookup"><span data-stu-id="3df95-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="3df95-147">El comando siguiente, `apt-get install -f` lo resuelve y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3df95-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="3df95-148">Desinstalación, Debian 8</span><span class="sxs-lookup"><span data-stu-id="3df95-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="3df95-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="3df95-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="3df95-150">Instalación mediante un repositorio de paquetes, Debian 9</span><span class="sxs-lookup"><span data-stu-id="3df95-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="3df95-151">PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3df95-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="3df95-152">Este es el método preferido.</span><span class="sxs-lookup"><span data-stu-id="3df95-152">This is the preferred method.</span></span>

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

<span data-ttu-id="3df95-153">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.</span><span class="sxs-lookup"><span data-stu-id="3df95-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="3df95-154">Instalación mediante descarga directa, Debian 9</span><span class="sxs-lookup"><span data-stu-id="3df95-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="3df95-155">Descargue el paquete de Debian `powershell_6.0.2-1.debian.9_amd64.deb` desde la página de [versiones][] en la máquina Debian.</span><span class="sxs-lookup"><span data-stu-id="3df95-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="3df95-156">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3df95-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="3df95-157">Tenga en cuenta que `dpkg -i` producirá un error con dependencias inadecuadas.</span><span class="sxs-lookup"><span data-stu-id="3df95-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="3df95-158">El comando siguiente, `apt-get install -f` lo resuelve y, luego, termina de configurar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3df95-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="3df95-159">Desinstalación, Debian 9</span><span class="sxs-lookup"><span data-stu-id="3df95-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="3df95-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3df95-160">CentOS 7</span></span>

> <span data-ttu-id="3df95-161">Este paquete también funciona en Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="3df95-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="3df95-162">Instalación mediante un repositorio de paquetes (opción preferida), CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3df95-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="3df95-163">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3df95-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3df95-164">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3df95-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="3df95-165">Instalación mediante descarga directa, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3df95-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="3df95-166">Cuando use [CentOS 7][], descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina CentOS.</span><span class="sxs-lookup"><span data-stu-id="3df95-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="3df95-167">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3df95-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3df95-168">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="3df95-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="3df95-169">Desinstalación, CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3df95-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3df95-171">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3df95-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3df95-172">Instalación a través de un repositorio de paquetes (opción preferida), Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3df95-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3df95-173">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3df95-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="3df95-174">Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3df95-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3df95-175">Instalación mediante descarga directa, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3df95-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="3df95-176">Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="3df95-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="3df95-177">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3df95-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3df95-178">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="3df95-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="3df95-179">Desinstalación, Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="3df95-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="3df95-180">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="3df95-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="3df95-181">Al instalar PowerShell Core, `zypper` puede notificar el siguiente error:</span><span class="sxs-lookup"><span data-stu-id="3df95-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="3df95-182">En este caso, verifique que haya una biblioteca `libcurl` compatible. Para ello, compruebe que mediante el siguiente comando se muestre que el paquete `libcurl4` está instalado:</span><span class="sxs-lookup"><span data-stu-id="3df95-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="3df95-183">A continuación, elija la solución `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` al instalar el paquete de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3df95-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="3df95-184">Instalación mediante un repositorio de paquetes (opción preferida), OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="3df95-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="3df95-185">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3df95-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="3df95-186">Instalación mediante descarga directa, OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="3df95-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="3df95-187">Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="3df95-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3df95-188">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="3df95-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="3df95-189">Desinstalación, OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="3df95-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="3df95-190">Fedora</span><span class="sxs-lookup"><span data-stu-id="3df95-190">Fedora</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="3df95-191">Instalación mediante un repositorio de paquetes (opción preferida), Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3df95-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="3df95-192">PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).</span><span class="sxs-lookup"><span data-stu-id="3df95-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="3df95-193">Instalación mediante descarga directa, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3df95-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="3df95-194">Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Fedora.</span><span class="sxs-lookup"><span data-stu-id="3df95-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="3df95-195">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3df95-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="3df95-196">También puede instalar el paquete RPM sin el paso intermedio de descargarlo:</span><span class="sxs-lookup"><span data-stu-id="3df95-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="3df95-197">Desinstalación, Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3df95-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="3df95-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="3df95-198">Arch Linux</span></span>

<span data-ttu-id="3df95-199">PowerShell está disponible en el repositorio de usuario [Arch Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="3df95-199">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="3df95-200">Se puede compilar con la [versión etiquetada más reciente][arch-release].</span><span class="sxs-lookup"><span data-stu-id="3df95-200">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="3df95-201">Se puede compilar desde la [última confirmación en maestro][arch-git].</span><span class="sxs-lookup"><span data-stu-id="3df95-201">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="3df95-202">Se puede instalar mediante el [binario de la versión más reciente][arch-bin].</span><span class="sxs-lookup"><span data-stu-id="3df95-202">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="3df95-203">Los paquetes del AUR se mantienen gracias a la comunidad, ya que no hay asistencia oficial.</span><span class="sxs-lookup"><span data-stu-id="3df95-203">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="3df95-204">Para más información sobre cómo instalar paquetes desde el AUR, vea la [wiki de Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="3df95-204">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="3df95-206">AppImage de Linux</span><span class="sxs-lookup"><span data-stu-id="3df95-206">Linux AppImage</span></span>

<span data-ttu-id="3df95-207">Si usa una distribución de Linux reciente, descargue el archivo AppImage `powershell-6.0.1-x86_64.AppImage` desde la página de [versiones][] en el equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="3df95-207">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="3df95-208">Después, ejecute lo siguiente en el terminal:</span><span class="sxs-lookup"><span data-stu-id="3df95-208">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="3df95-209">El archivo [AppImage][] permite ejecutar PowerShell sin instalarlo.</span><span class="sxs-lookup"><span data-stu-id="3df95-209">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="3df95-210">Se trata de una aplicación portátil que empaqueta PowerShell y sus dependencias (incluidas las dependencias del sistema de .NET Core) en un paquete coherente.</span><span class="sxs-lookup"><span data-stu-id="3df95-210">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="3df95-211">Este paquete es un archivo binario único que funciona con independencia de la distribución de Linux del usuario.</span><span class="sxs-lookup"><span data-stu-id="3df95-211">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="3df95-213">Kali</span><span class="sxs-lookup"><span data-stu-id="3df95-213">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="3df95-214">Instalación</span><span class="sxs-lookup"><span data-stu-id="3df95-214">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="3df95-215">Ejecución de PowerShell en la versión más reciente de Kali (Kali GNU/Linux Rolling) sin instalarlo</span><span class="sxs-lookup"><span data-stu-id="3df95-215">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="3df95-216">Desinstalación, Kali</span><span class="sxs-lookup"><span data-stu-id="3df95-216">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="3df95-217">Raspbian</span><span class="sxs-lookup"><span data-stu-id="3df95-217">Raspbian</span></span>

<span data-ttu-id="3df95-218">Actualmente, PowerShell solo se admite en Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="3df95-218">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="3df95-219">Asimismo, CoreCLR (y, por tanto, PowerShell Core) solo funcionará en dispositivos Pi 2 y Pi 3 dado que otros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tienen un procesador no admitido.</span><span class="sxs-lookup"><span data-stu-id="3df95-219">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="3df95-220">Descargue [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) y siga las [instrucciones de instalación](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para tenerlo en su Pi.</span><span class="sxs-lookup"><span data-stu-id="3df95-220">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="3df95-221">Instalación</span><span class="sxs-lookup"><span data-stu-id="3df95-221">Installation</span></span>

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

<span data-ttu-id="3df95-222">Opcionalmente, puede crear un vínculo simbólico para poder iniciar PowerShell sin especificar la ruta de acceso al archivo binario "pwsh".</span><span class="sxs-lookup"><span data-stu-id="3df95-222">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="3df95-223">Desinstalación, Raspbian</span><span class="sxs-lookup"><span data-stu-id="3df95-223">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="3df95-224">Archivos binarios</span><span class="sxs-lookup"><span data-stu-id="3df95-224">Binary Archives</span></span>

<span data-ttu-id="3df95-225">Se proporcionan archivos binarios `tar.gz` de PowerShell para plataformas Linux, a fin de permitir escenarios de implementación avanzados.</span><span class="sxs-lookup"><span data-stu-id="3df95-225">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="3df95-226">Dependencias</span><span class="sxs-lookup"><span data-stu-id="3df95-226">Dependencies</span></span>

<span data-ttu-id="3df95-227">PowerShell compila archivos binarios portátiles para todas las distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="3df95-227">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="3df95-228">Aun así, el entorno de ejecución de .NET Core requiere dependencias diferentes en otras distribuciones, y por eso PowerShell hace lo mismo.</span><span class="sxs-lookup"><span data-stu-id="3df95-228">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="3df95-229">En la tabla siguiente se muestran las dependencias de .NET Core 2.0 que se admiten oficialmente en diferentes distribuciones de Linux.</span><span class="sxs-lookup"><span data-stu-id="3df95-229">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="3df95-230">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="3df95-230">OS</span></span>                 | <span data-ttu-id="3df95-231">Dependencias</span><span class="sxs-lookup"><span data-stu-id="3df95-231">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="3df95-232">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="3df95-232">Ubuntu 14.04</span></span>       | <span data-ttu-id="3df95-233">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3df95-233">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3df95-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="3df95-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="3df95-235">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="3df95-235">Ubuntu 16.04</span></span>       | <span data-ttu-id="3df95-236">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3df95-236">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3df95-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="3df95-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="3df95-238">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="3df95-238">Ubuntu 17.04</span></span>       | <span data-ttu-id="3df95-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3df95-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3df95-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="3df95-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="3df95-241">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="3df95-241">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="3df95-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3df95-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3df95-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="3df95-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="3df95-244">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="3df95-244">Debian 9 (Stretch)</span></span> | <span data-ttu-id="3df95-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="3df95-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="3df95-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="3df95-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="3df95-247">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="3df95-247">CentOS 7</span></span> <br> <span data-ttu-id="3df95-248">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="3df95-248">Oracle Linux 7</span></span> <br> <span data-ttu-id="3df95-249">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="3df95-249">RHEL 7</span></span> <br> <span data-ttu-id="3df95-250">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="3df95-250">OpenSUSE 42.2</span></span> | <span data-ttu-id="3df95-251">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="3df95-251">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="3df95-252">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="3df95-252">Fedora 27</span></span> <br> <span data-ttu-id="3df95-253">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="3df95-253">Fedora 28</span></span> | <span data-ttu-id="3df95-254">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="3df95-254">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="3df95-255">Para implementar archivos binarios de PowerShell en distribuciones de Linux que no se admiten oficialmente, debe instalar las dependencias necesarias para el sistema operativo de destino en varios pasos.</span><span class="sxs-lookup"><span data-stu-id="3df95-255">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="3df95-256">Por ejemplo, nuestro [dockerfile de Amazon Linux][amazon-dockerfile] instala primero las dependencias y, después, extrae el archivo `tar.gz` de Linux.</span><span class="sxs-lookup"><span data-stu-id="3df95-256">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="3df95-257">Instalación, archivos binarios</span><span class="sxs-lookup"><span data-stu-id="3df95-257">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="3df95-258">Linux</span><span class="sxs-lookup"><span data-stu-id="3df95-258">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="3df95-259">Desinstalación de archivos binarios</span><span class="sxs-lookup"><span data-stu-id="3df95-259">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="3df95-260">Rutas de acceso</span><span class="sxs-lookup"><span data-stu-id="3df95-260">Paths</span></span>

* <span data-ttu-id="3df95-261">`$PSHOME` es `/opt/microsoft/powershell/6.0.2/`.</span><span class="sxs-lookup"><span data-stu-id="3df95-261">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="3df95-262">Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="3df95-262">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="3df95-263">Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.</span><span class="sxs-lookup"><span data-stu-id="3df95-263">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="3df95-264">Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="3df95-264">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3df95-265">Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.</span><span class="sxs-lookup"><span data-stu-id="3df95-265">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="3df95-266">Los módulos predeterminados se leerán de `$PSHOME/Modules`.</span><span class="sxs-lookup"><span data-stu-id="3df95-266">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="3df95-267">El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.</span><span class="sxs-lookup"><span data-stu-id="3df95-267">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="3df95-268">Los perfiles respetan la configuración de cada host de PowerShell, por lo que hay perfiles predeterminados específicos del host en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="3df95-268">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="3df95-269">PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en Linux.</span><span class="sxs-lookup"><span data-stu-id="3df95-269">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
