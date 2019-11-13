---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Introducción a la configuración de estado deseado (DSC) para Linux
ms.openlocfilehash: b1bc9b9fafd89a1af0f967de38a817bff1f3ffe3
ms.sourcegitcommit: 14b50e5446f69729f72231f5dc6f536cdd1084c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73933846"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="38f97-103">Introducción a la configuración de estado deseado (DSC) para Linux</span><span class="sxs-lookup"><span data-stu-id="38f97-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="38f97-104">En este tema se ofrece una introducción al uso de la configuración de estado deseado (DSC) de PowerShell para Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="38f97-105">Para obtener información general sobre DSC, consulte [Introducción a la configuración de estado deseado de Windows PowerShell](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="38f97-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="38f97-106">Versiones de sistemas operativos Linux compatibles</span><span class="sxs-lookup"><span data-stu-id="38f97-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="38f97-107">Se admiten las siguientes versiones de sistemas operativos Linux para DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-107">The following Linux operating system versions are supported for DSC for Linux.</span></span>

- <span data-ttu-id="38f97-108">CentOS 5, 6 y 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="38f97-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="38f97-109">Debian GNU/Linux 6, 7 y 8 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="38f97-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="38f97-110">Oracle Linux 5, 6 y 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="38f97-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="38f97-111">Red Hat Enterprise Linux Server 5, 6 y 7 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="38f97-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="38f97-112">SUSE Linux Enterprise Server 10, 11 y 12 (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="38f97-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="38f97-113">Ubuntu Server 12.04 LTS, 14.04 LTS y 16.04 LTS (x86/x64)</span><span class="sxs-lookup"><span data-stu-id="38f97-113">Ubuntu Server 12.04 LTS, 14.04 LTS and 16.04 LTS (x86/x64)</span></span>

<span data-ttu-id="38f97-114">En la tabla siguiente se describen las dependencias de paquetes necesarios para DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-114">The following table describes the required package dependencies for DSC for Linux.</span></span>

|  <span data-ttu-id="38f97-115">Paquete necesario</span><span class="sxs-lookup"><span data-stu-id="38f97-115">Required package</span></span> |  <span data-ttu-id="38f97-116">Descripción</span><span class="sxs-lookup"><span data-stu-id="38f97-116">Description</span></span> |  <span data-ttu-id="38f97-117">Versión mínima</span><span class="sxs-lookup"><span data-stu-id="38f97-117">Minimum version</span></span> |
|---|---|---|
| <span data-ttu-id="38f97-118">glibc</span><span class="sxs-lookup"><span data-stu-id="38f97-118">glibc</span></span>| <span data-ttu-id="38f97-119">Biblioteca de GNU</span><span class="sxs-lookup"><span data-stu-id="38f97-119">GNU Library</span></span>| <span data-ttu-id="38f97-120">2…4 – 31.30</span><span class="sxs-lookup"><span data-stu-id="38f97-120">2…4 – 31.30</span></span>|
| <span data-ttu-id="38f97-121">python</span><span class="sxs-lookup"><span data-stu-id="38f97-121">python</span></span>| <span data-ttu-id="38f97-122">Python</span><span class="sxs-lookup"><span data-stu-id="38f97-122">Python</span></span>| <span data-ttu-id="38f97-123">2.4 – 3.4</span><span class="sxs-lookup"><span data-stu-id="38f97-123">2.4 – 3.4</span></span>|
| <span data-ttu-id="38f97-124">omiserver</span><span class="sxs-lookup"><span data-stu-id="38f97-124">omiserver</span></span>| <span data-ttu-id="38f97-125">Infraestructura de administración abierta</span><span class="sxs-lookup"><span data-stu-id="38f97-125">Open Management Infrastructure</span></span>| <span data-ttu-id="38f97-126">1.0.8.1</span><span class="sxs-lookup"><span data-stu-id="38f97-126">1.0.8.1</span></span>|
| <span data-ttu-id="38f97-127">openssl</span><span class="sxs-lookup"><span data-stu-id="38f97-127">openssl</span></span>| <span data-ttu-id="38f97-128">Bibliotecas de OpenSSL</span><span class="sxs-lookup"><span data-stu-id="38f97-128">OpenSSL Libraries</span></span>| <span data-ttu-id="38f97-129">0.9.8 o 1.0</span><span class="sxs-lookup"><span data-stu-id="38f97-129">0.9.8 or 1.0</span></span>|
| <span data-ttu-id="38f97-130">ctypes</span><span class="sxs-lookup"><span data-stu-id="38f97-130">ctypes</span></span>| <span data-ttu-id="38f97-131">Biblioteca de Python CTypes</span><span class="sxs-lookup"><span data-stu-id="38f97-131">Python CTypes library</span></span>| <span data-ttu-id="38f97-132">Debe coincidir con la versión de Python</span><span class="sxs-lookup"><span data-stu-id="38f97-132">Must match Python version</span></span>|
| <span data-ttu-id="38f97-133">libcurl</span><span class="sxs-lookup"><span data-stu-id="38f97-133">libcurl</span></span>| <span data-ttu-id="38f97-134">Biblioteca de cliente http cURL</span><span class="sxs-lookup"><span data-stu-id="38f97-134">cURL http client library</span></span>| <span data-ttu-id="38f97-135">7.15.1</span><span class="sxs-lookup"><span data-stu-id="38f97-135">7.15.1</span></span>|

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="38f97-136">Instalación de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="38f97-136">Installing DSC for Linux</span></span>

<span data-ttu-id="38f97-137">Debe instalar la [infraestructura de administración abierta (OMI)](https://github.com/Microsoft/omi) antes de instalar DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-137">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="38f97-138">Instalación de la OMI</span><span class="sxs-lookup"><span data-stu-id="38f97-138">Installing OMI</span></span>

<span data-ttu-id="38f97-139">La configuración de estado deseado para Linux requiere el servidor CIM de infraestructura de administración abierta (OMI), versión 1.0.8.1 o posterior.</span><span class="sxs-lookup"><span data-stu-id="38f97-139">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="38f97-140">OMI se puede descargar en The Open Group: [Infraestructura de administración abierta (OMI)](https://github.com/Microsoft/omi)</span><span class="sxs-lookup"><span data-stu-id="38f97-140">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="38f97-141">Para instalar OMI, instale el paquete que sea adecuado para su sistema Linux (.rpm o .deb) y versión de OpenSSL (ssl_098 o ssl_100), y la arquitectura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="38f97-141">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="38f97-142">Los paquetes RPM son adecuados para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server y Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-142">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="38f97-143">Los paquetes DEB son adecuados para Debian GNU/Linux y Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="38f97-143">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="38f97-144">Los paquetes ssl_098 son adecuados para equipos con OpenSSL 0.9.8 instalado, mientras que los paquetes ssl_100 son adecuados para equipos con OpenSSL 1.0 instalado.</span><span class="sxs-lookup"><span data-stu-id="38f97-144">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="38f97-145">Para determinar la versión de OpenSSL instalada, ejecute el comando `openssl version`.</span><span class="sxs-lookup"><span data-stu-id="38f97-145">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="38f97-146">Ejecute el siguiente comando para instalar OMI en un sistema con CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="38f97-146">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="38f97-147">Instalación de DSC</span><span class="sxs-lookup"><span data-stu-id="38f97-147">Installing DSC</span></span>

<span data-ttu-id="38f97-148">DSC para Linux está disponible para su descarga [aquí](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span><span class="sxs-lookup"><span data-stu-id="38f97-148">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="38f97-149">Para instalar DSC, instale el paquete que sea adecuado para su sistema Linux (.rpm o .deb) y versión de OpenSSL (ssl_098 o ssl_100), y la arquitectura (x64/x86).</span><span class="sxs-lookup"><span data-stu-id="38f97-149">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="38f97-150">Los paquetes RPM son adecuados para CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server y Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-150">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="38f97-151">Los paquetes DEB son adecuados para Debian GNU/Linux y Ubuntu Server.</span><span class="sxs-lookup"><span data-stu-id="38f97-151">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="38f97-152">Los paquetes ssl_098 son adecuados para equipos con OpenSSL 0.9.8 instalado, mientras que los paquetes ssl_100 son adecuados para equipos con OpenSSL 1.0 instalado.</span><span class="sxs-lookup"><span data-stu-id="38f97-152">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="38f97-153">Para determinar la versión instalada de OpenSSL, ejecute el comando openssl version.</span><span class="sxs-lookup"><span data-stu-id="38f97-153">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="38f97-154">Ejecute el siguiente comando para instalar DSC en un sistema con CentOS 7 x64.</span><span class="sxs-lookup"><span data-stu-id="38f97-154">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="38f97-155">Uso de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="38f97-155">Using DSC for Linux</span></span>

<span data-ttu-id="38f97-156">En las siguientes secciones se explica cómo crear y ejecutar configuraciones DSC en equipos Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-156">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="38f97-157">Creación de un documento MOF de configuración</span><span class="sxs-lookup"><span data-stu-id="38f97-157">Creating a configuration MOF document</span></span>

<span data-ttu-id="38f97-158">Se utiliza la palabra clave de Windows PowerShell Configuration a fin de crear una configuración para los equipos Linux, de la misma forma que para los equipos Windows.</span><span class="sxs-lookup"><span data-stu-id="38f97-158">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="38f97-159">En los pasos siguientes se describe la creación de un documento de configuración para un equipo Linux con Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38f97-159">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="38f97-160">Importe el módulo nx.</span><span class="sxs-lookup"><span data-stu-id="38f97-160">Import the nx module.</span></span> <span data-ttu-id="38f97-161">El módulo de Windows PowerShell nx contiene el esquema para los recursos integrados de DSC para Linux y debe instalarse en el equipo local e importarse en la configuración.</span><span class="sxs-lookup"><span data-stu-id="38f97-161">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="38f97-162">Para instalar el módulo nx, copie el directorio del módulo nx en `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` o `$PSHOME\Modules`.</span><span class="sxs-lookup"><span data-stu-id="38f97-162">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="38f97-163">El módulo nx se incluye en la DSC para paquetes de instalación de Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-163">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="38f97-164">Para importar el módulo nx en la configuración, utilice el comando `Import-DSCResource`:</span><span class="sxs-lookup"><span data-stu-id="38f97-164">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="38f97-165">Defina una configuración y genere el documento de configuración:</span><span class="sxs-lookup"><span data-stu-id="38f97-165">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="38f97-166">Insertar la configuración en el equipo Linux</span><span class="sxs-lookup"><span data-stu-id="38f97-166">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="38f97-167">Los documentos de configuración (archivos MOF) se pueden insertar en el equipo Linux mediante el cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="38f97-167">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="38f97-168">Para usar este cmdlet, junto con los cmdlets [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) o [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), de forma remota en un equipo Linux, debe usar un elemento CIMSession.</span><span class="sxs-lookup"><span data-stu-id="38f97-168">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="38f97-169">El cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) se usa para crear un elemento CIMSession para el equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-169">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="38f97-170">En el código siguiente se muestra cómo crear un elemento CIMSession de DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-170">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> <span data-ttu-id="38f97-171">En el modo "Push", la credencial de usuario debe ser un usuario raíz del equipo Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-171">For "Push" mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="38f97-172">Solo se admiten conexiones SSL/TLS de DSC para Linux, el cmdlet `New-CimSession` debe utilizarse con el parámetro -UseSSL establecido en $true.</span><span class="sxs-lookup"><span data-stu-id="38f97-172">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="38f97-173">El certificado SSL que utiliza OMI (para DSC) se especifica en el archivo `/etc/opt/omi/conf/omiserver.conf` con las propiedades pemfile y keyfile.</span><span class="sxs-lookup"><span data-stu-id="38f97-173">The SSL certificate used by OMI (for DSC) is specified in the file: `/etc/opt/omi/conf/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="38f97-174">Si este certificado no es de confianza para el equipo de Windows en el que se está ejecutando el cmdlet [New-CimSession](/powershell/module/CimCmdlets/New-CimSession), puede elegir omitir la validación de certificados con las opciones de CIMSession `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span><span class="sxs-lookup"><span data-stu-id="38f97-174">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="38f97-175">Ejecute el comando siguiente para insertar la configuración DSC en el nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-175">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="38f97-176">Distribuir la configuración con un servidor de extracción</span><span class="sxs-lookup"><span data-stu-id="38f97-176">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="38f97-177">Las configuraciones se pueden distribuir a un equipo Linux con un servidor de extracción, igual que con equipos Windows.</span><span class="sxs-lookup"><span data-stu-id="38f97-177">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="38f97-178">Para obtener instrucciones sobre el uso de un servidor de extracción, consulte [Servidores de extracción de la configuración de estado deseado de Windows PowerShell](../pull-server/pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="38f97-178">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="38f97-179">Para obtener información adicional y conocer las limitaciones relativas al uso de equipos Linux con un servidor de extracción, consulte las notas de la versión de la configuración de estado deseado para Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-179">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="38f97-180">Trabajar con configuraciones de forma local</span><span class="sxs-lookup"><span data-stu-id="38f97-180">Working with configurations locally</span></span>

<span data-ttu-id="38f97-181">DSC para Linux incluye scripts para trabajar con la configuración del equipo Linux local.</span><span class="sxs-lookup"><span data-stu-id="38f97-181">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="38f97-182">Estos scripts se encuentran en `/opt/microsoft/dsc/Scripts` e incluyen lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="38f97-182">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="38f97-183">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="38f97-183">GetDscConfiguration.py</span></span>

<span data-ttu-id="38f97-184">Devuelve la configuración actual que se aplica al equipo.</span><span class="sxs-lookup"><span data-stu-id="38f97-184">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="38f97-185">Es similar al cmdlet de Windows PowerShell `Get-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="38f97-185">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="38f97-186">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="38f97-186">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="38f97-187">Devuelve la metaconfiguración actual que se aplica al equipo.</span><span class="sxs-lookup"><span data-stu-id="38f97-187">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="38f97-188">Es similar al cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="38f97-188">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="38f97-189">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="38f97-189">InstallModule.py</span></span>

<span data-ttu-id="38f97-190">Instala un módulo de recursos de DSC personalizado.</span><span class="sxs-lookup"><span data-stu-id="38f97-190">Installs a custom DSC resource module.</span></span> <span data-ttu-id="38f97-191">Requiere la ruta de acceso a un archivo .zip que contenga la biblioteca de objetos compartidos del módulo y los archivos MOF del esquema.</span><span class="sxs-lookup"><span data-stu-id="38f97-191">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="38f97-192">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="38f97-192">RemoveModule.py</span></span>

<span data-ttu-id="38f97-193">Quita un módulo de recursos de DSC personalizado.</span><span class="sxs-lookup"><span data-stu-id="38f97-193">Removes a custom DSC resource module.</span></span> <span data-ttu-id="38f97-194">Requiere el nombre del módulo que se va a quitar.</span><span class="sxs-lookup"><span data-stu-id="38f97-194">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="38f97-195">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="38f97-195">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="38f97-196">Aplica un archivo MOF de configuración en el equipo.</span><span class="sxs-lookup"><span data-stu-id="38f97-196">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="38f97-197">Es similar al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="38f97-197">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="38f97-198">Requiere la ruta de acceso al MOF de configuración que se va a aplicar.</span><span class="sxs-lookup"><span data-stu-id="38f97-198">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="38f97-199">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="38f97-199">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="38f97-200">Aplica a un archivo MOF de metaconfiguración en el equipo.</span><span class="sxs-lookup"><span data-stu-id="38f97-200">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="38f97-201">Es similar al cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="38f97-201">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="38f97-202">Requiere la ruta de acceso al MOF de metaconfiguración que se va a aplicar.</span><span class="sxs-lookup"><span data-stu-id="38f97-202">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="38f97-203">Archivos de registro de la configuración de estado deseado para Linux de PowerShell</span><span class="sxs-lookup"><span data-stu-id="38f97-203">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="38f97-204">Los siguientes archivos de registro son mensajes generados para DSC para Linux.</span><span class="sxs-lookup"><span data-stu-id="38f97-204">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="38f97-205">Archivo de registro</span><span class="sxs-lookup"><span data-stu-id="38f97-205">Log file</span></span>|<span data-ttu-id="38f97-206">Directory</span><span class="sxs-lookup"><span data-stu-id="38f97-206">Directory</span></span>|<span data-ttu-id="38f97-207">Descripción</span><span class="sxs-lookup"><span data-stu-id="38f97-207">Description</span></span>|
|---|---|---|
|<span data-ttu-id="38f97-208">**omiserver.log**</span><span class="sxs-lookup"><span data-stu-id="38f97-208">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="38f97-209">Mensajes relacionados con la operación del servidor CIM OMI.</span><span class="sxs-lookup"><span data-stu-id="38f97-209">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="38f97-210">**dsc.log**</span><span class="sxs-lookup"><span data-stu-id="38f97-210">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="38f97-211">Mensajes relacionados con el funcionamiento del administrador de configuración local (LCM) y las operaciones de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="38f97-211">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|
