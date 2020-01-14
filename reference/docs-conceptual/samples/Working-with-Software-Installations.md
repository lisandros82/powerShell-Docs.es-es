---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Trabajar con instalaciones de software
ms.openlocfilehash: d164064418ad7a0209166c81a7c3cc32a9db300a
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737158"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="eaaee-103">Trabajar con instalaciones de software</span><span class="sxs-lookup"><span data-stu-id="eaaee-103">Working with Software Installations</span></span>

<span data-ttu-id="eaaee-104">Puede usar la clase **Win32_Product** de WMI para acceder a las aplicaciones diseñadas para usar Windows Installer, si bien no todas las aplicaciones de hoy en día usan Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="eaaee-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="eaaee-105">Por lo general, las aplicaciones que usan otras rutinas de instalación no se administran con Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="eaaee-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="eaaee-106">Las técnicas concretas para trabajar con esas aplicaciones dependen del instalador de software y de las decisiones tomadas por el desarrollador de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="eaaee-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="eaaee-107">Por ejemplo, las aplicaciones que se instalan copiando los archivos a una carpeta del equipo no se suelen poder administrar con las técnicas aquí descritas.</span><span class="sxs-lookup"><span data-stu-id="eaaee-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="eaaee-108">Puede administrar estas aplicaciones como archivos y carpetas recurriendo a las técnicas descritas en [Trabajar con archivos y carpetas](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="eaaee-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="eaaee-109">La clase **Win32_Product** no está optimizada para consultas.</span><span class="sxs-lookup"><span data-stu-id="eaaee-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="eaaee-110">Las consultas que utilizan filtros con caracteres comodín provocan que WMI utilice el proveedor MSI para enumerar todos los productos instalados y, a continuación, analice la lista completa de forma secuencial para controlar el filtro.</span><span class="sxs-lookup"><span data-stu-id="eaaee-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="eaaee-111">Esto también inicia una comprobación de coherencia de los paquetes instalados, verificando y reparando la instalación.</span><span class="sxs-lookup"><span data-stu-id="eaaee-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="eaaee-112">La validación es un proceso lento y puede provocar errores en los registros de eventos.</span><span class="sxs-lookup"><span data-stu-id="eaaee-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="eaaee-113">Para obtener más información, consulte el [artículo de KB 974524](https://support.microsoft.com/help/974524).</span><span class="sxs-lookup"><span data-stu-id="eaaee-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="eaaee-114">Lista de aplicaciones de Windows Installer</span><span class="sxs-lookup"><span data-stu-id="eaaee-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="eaaee-115">Para confeccionar una lista de las aplicaciones instaladas con Windows Installer en un sistema local o remoto, use esta sencilla consulta WMI:</span><span class="sxs-lookup"><span data-stu-id="eaaee-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

<span data-ttu-id="eaaee-116">Para mostrar todas las propiedades del objeto **Win32_Product**, use el parámetro **Properties** de los cmdlets de formato, como el cmdlet `Format-List`, con un valor de `*` (todos).</span><span class="sxs-lookup"><span data-stu-id="eaaee-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.5 (x64)
Version               : 16.84.26919
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.5 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.5 (x64)
IdentifyingNumber     : {BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20181105
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}v16.84.26919\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\4f97a771.msi
PackageCache          : C:\WINDOWS\Installer\4f97a771.msi
PackageCode           : {9A271A10-039D-49EA-8D24-043D91B9F915}
PackageName           : dotnet-runtime-2.1.5-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

<span data-ttu-id="eaaee-117">Otra posibilidad es usar el parámetro `Get-CimInstance` **Filter** para seleccionar solo Microsoft .NET Framework 2.0 Runtime.</span><span class="sxs-lookup"><span data-stu-id="eaaee-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET 2.0 Runtime.</span></span> <span data-ttu-id="eaaee-118">El valor del parámetro **Filter** usa la sintaxis del lenguaje de consulta de WMI (WQL), no la sintaxis de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eaaee-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="eaaee-119">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="eaaee-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="eaaee-120">Para mostrar solo las propiedades que le interesen, use el parámetro **Property** de los cmdlets de formato.</span><span class="sxs-lookup"><span data-stu-id="eaaee-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.5 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\4f97a771.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="eaaee-121">Enumerar todas las aplicaciones no instalables</span><span class="sxs-lookup"><span data-stu-id="eaaee-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="eaaee-122">La mayoría de las aplicaciones estándar registran un desinstalador con Windows, por lo que podemos trabajar con ellas localmente buscándolas en el Registro de Windows.</span><span class="sxs-lookup"><span data-stu-id="eaaee-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="eaaee-123">No hay ninguna manera garantizada de encontrar todas las aplicaciones en un sistema.</span><span class="sxs-lookup"><span data-stu-id="eaaee-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="eaaee-124">Sin embargo, es posible buscar todos los programas en las listas que se muestran en **Agregar o quitar programas** en la clave del Registro siguiente:</span><span class="sxs-lookup"><span data-stu-id="eaaee-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs** in the following registry key:</span></span>

<span data-ttu-id="eaaee-125">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="eaaee-125">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="eaaee-126">Podemos examinar esta clave para buscar aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="eaaee-126">We can examine this key to find applications.</span></span> <span data-ttu-id="eaaee-127">Podemos hacer que la clave Uninstall sea más fácil de ver si asignamos una unidad de PowerShell a esta ubicación del Registro:</span><span class="sxs-lookup"><span data-stu-id="eaaee-127">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

<span data-ttu-id="eaaee-128">Ya tenemos una unidad denominada "Uninstall:" que se puede usar para buscar instalaciones de aplicaciones de forma cómoda y rápida.</span><span class="sxs-lookup"><span data-stu-id="eaaee-128">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="eaaee-129">Podemos hallar el número de aplicaciones instaladas contando el número de claves del Registro en la desinstalación: Unidad de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="eaaee-129">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

<span data-ttu-id="eaaee-130">Podemos realizar más búsquedas en esta lista de aplicaciones mediante diversas técnicas, comenzando por `Get-ChildItem`.</span><span class="sxs-lookup"><span data-stu-id="eaaee-130">We can search this list of applications further by using a variety of techniques, beginning with `Get-ChildItem`.</span></span> <span data-ttu-id="eaaee-131">Use el siguiente comando para obtener una lista de aplicaciones y guardarlas en la variable `$UninstallableApplications`:</span><span class="sxs-lookup"><span data-stu-id="eaaee-131">To get a list of applications and save them in the `$UninstallableApplications` variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="eaaee-132">Para ver los valores de las entradas del Registro en las claves del Registro bajo Uninstall, use el método GetValue en las claves del Registro.</span><span class="sxs-lookup"><span data-stu-id="eaaee-132">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="eaaee-133">El valor del método es el nombre de la entrada del Registro.</span><span class="sxs-lookup"><span data-stu-id="eaaee-133">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="eaaee-134">Por ejemplo, use el siguiente comando para buscar los nombres para mostrar de las aplicaciones en la clave Uninstall:</span><span class="sxs-lookup"><span data-stu-id="eaaee-134">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="eaaee-135">No hay ninguna garantía de que estos valores sean únicos.</span><span class="sxs-lookup"><span data-stu-id="eaaee-135">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="eaaee-136">En el siguiente ejemplo, aparecen dos elementos instalados como "Windows Media Encoder 9 Series":</span><span class="sxs-lookup"><span data-stu-id="eaaee-136">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```powershell
$UninstallableApplications | Where-Object -FilterScript {
  $_.GetValue("DisplayName") -eq "Microsoft Silverlight"
}
```

```Output
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name                           Property
----                           --------
{89F4137D-6C26-4A84-BDB8-2E5A4 AuthorizedCDFPrefix :
BB71E00}                       Comments            :
                               Contact             :
                               DisplayVersion      : 5.1.50918.0
                               HelpLink            : http://go.microsoft.com/fwlink/?LinkID=91955
                               HelpTelephone       :
                               InstallDate         : 20190115
                               InstallLocation     : C:\Program Files\Microsoft Silverlight\
                               InstallSource       : c:\ef64c54526db9c34cd477c103e68a254\
                               ModifyPath          : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               NoModify            : 1
                               NoRepair            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 236432
                               UninstallString     : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 5
                               VersionMinor        : 1
                               WindowsInstaller    : 1
                               Version             : 84002534
                               Language            : 1033
                               DisplayName         : Microsoft Silverlight
                               sEstimatedSize2     : 79214
```

## <a name="installing-applications"></a><span data-ttu-id="eaaee-137">Instalación de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="eaaee-137">Installing Applications</span></span>

<span data-ttu-id="eaaee-138">Puede usar la clase **Win32_Product** para instalar paquetes de Windows Installer, tanto de forma local como remota.</span><span class="sxs-lookup"><span data-stu-id="eaaee-138">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="eaaee-139">Para instalar una aplicación, debe iniciar PowerShell con la opción "Ejecutar como administrador".</span><span class="sxs-lookup"><span data-stu-id="eaaee-139">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="eaaee-140">En las instalaciones remotas, use una ruta de red de convención de nomenclatura Universal (UNC) para especificar la ruta de acceso al paquete .msi, ya que el subsistema WMI no entiende las rutas de acceso de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eaaee-140">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="eaaee-141">Por ejemplo, para instalar el paquete NewPackage.msi ubicado en el recurso compartido de red `\\AppServ\dsp` en el equipo remoto PC01, escriba el siguiente comando en el símbolo del sistema de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="eaaee-141">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="eaaee-142">Las aplicaciones que no usan la tecnología de Windows Installer pueden tener métodos específicos de aplicación para la implementación automática.</span><span class="sxs-lookup"><span data-stu-id="eaaee-142">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="eaaee-143">Consulte la documentación de la aplicación o el sistema de soporte técnico del proveedor de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="eaaee-143">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="eaaee-144">Desinstalación de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="eaaee-144">Removing Applications</span></span>

<span data-ttu-id="eaaee-145">El proceso de desinstalación de un paquete de Windows Installer mediante PowerShell funciona aproximadamente del mismo modo que la instalación de un paquete.</span><span class="sxs-lookup"><span data-stu-id="eaaee-145">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="eaaee-146">En este ejemplo, el paquete que se va a desinstalar se selecciona por su nombre; en algunos casos, probablemente sea más fácil filtrar con **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="eaaee-146">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="eaaee-147">Desinstalar otras aplicaciones no es tan sencillo, aun cuando se haga localmente.</span><span class="sxs-lookup"><span data-stu-id="eaaee-147">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="eaaee-148">Encontraremos las cadenas de desinstalación de línea de comandos de estas aplicaciones extrayendo la propiedad **UninstallString**.</span><span class="sxs-lookup"><span data-stu-id="eaaee-148">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="eaaee-149">Este método funciona con aplicaciones de Windows Installer y con los programas antiguos que aparecen bajo la clave Uninstall:</span><span class="sxs-lookup"><span data-stu-id="eaaee-149">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="eaaee-150">Si lo desea, puede filtrar el resultado por el nombre para mostrar:</span><span class="sxs-lookup"><span data-stu-id="eaaee-150">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="eaaee-151">Sin embargo, puede que estas cadenas no se puedan usar directamente desde el símbolo del sistema de PowerShell sin realizar alguna modificación.</span><span class="sxs-lookup"><span data-stu-id="eaaee-151">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="eaaee-152">Actualización de aplicaciones de Windows Installer</span><span class="sxs-lookup"><span data-stu-id="eaaee-152">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="eaaee-153">Para actualizar una aplicación, es necesario conocer su nombre y la ruta de acceso al paquete de actualización de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="eaaee-153">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="eaaee-154">Con esa información, podrá actualizar una aplicación con un solo comando de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="eaaee-154">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
