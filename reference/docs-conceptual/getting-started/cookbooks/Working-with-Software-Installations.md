---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Trabajar con instalaciones de software
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: bb97ad37c4295351c0fc2e3c6e1209c8dd673f06
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-software-installations"></a><span data-ttu-id="47d76-103">Trabajar con instalaciones de software</span><span class="sxs-lookup"><span data-stu-id="47d76-103">Working with Software Installations</span></span>

<span data-ttu-id="47d76-104">Puede usar la clase **Win32_Product** de WMI para acceder a las aplicaciones diseñadas para usar Windows Installer, si bien no todas las aplicaciones de hoy en día usan Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="47d76-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="47d76-105">Dado que Windows Installer proporciona la gama más amplia de técnicas estándar para trabajar con aplicaciones instalables, nos centraremos principalmente en esas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="47d76-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="47d76-106">Por lo general, las aplicaciones que usan otras rutinas de instalación no se administrarán con Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="47d76-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="47d76-107">Las técnicas concretas para trabajar con esas aplicaciones dependerán del instalador de software y de las decisiones tomadas por el desarrollador de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="47d76-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="47d76-108">Las aplicaciones que se instalan copiando los archivos de la aplicación en el equipo normalmente no se suelen poder administrar con las técnicas aquí descritas.</span><span class="sxs-lookup"><span data-stu-id="47d76-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="47d76-109">Puede administrar estas aplicaciones como archivos y carpetas recurriendo a las técnicas descritas en la sección "Trabajar con archivos y carpetas".</span><span class="sxs-lookup"><span data-stu-id="47d76-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

### <a name="listing-windows-installer-applications"></a><span data-ttu-id="47d76-110">Lista de aplicaciones de Windows Installer</span><span class="sxs-lookup"><span data-stu-id="47d76-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="47d76-111">Para confeccionar una lista de las aplicaciones instaladas con Windows Installer en un sistema local o remoto, use esta sencilla consulta WMI:</span><span class="sxs-lookup"><span data-stu-id="47d76-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="47d76-112">Para mostrar todas las propiedades del objeto Win32_Product, use el parámetro Properties de los cmdlets de formato, como el cmdlet Format-List, con un valor de \* (todos).</span><span class="sxs-lookup"><span data-stu-id="47d76-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

<span data-ttu-id="47d76-113">También podría usar el parámetro **Get-WmiObject Filter** para seleccionar únicamente Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="47d76-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="47d76-114">Dado que el filtro empleado en este comando es un filtro WMI, se usa la sintaxis de lenguaje de consulta de WMI (WQL), no la sintaxis de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47d76-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="47d76-115">En su lugar:</span><span class="sxs-lookup"><span data-stu-id="47d76-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="47d76-116">Tenga en cuenta que, a menudo, las consultas WQL usan caracteres (como espacios o signos igual) que en Windows PowerShell tienen un significado especial.</span><span class="sxs-lookup"><span data-stu-id="47d76-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="47d76-117">Por esta razón, es recomendable incluir siempre el valor del parámetro Filter entre comillas.</span><span class="sxs-lookup"><span data-stu-id="47d76-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="47d76-118">También puede usar el carácter de escape de Windows PowerShell, un acento grave (\`), aunque puede que la legibilidad no mejore.</span><span class="sxs-lookup"><span data-stu-id="47d76-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="47d76-119">El siguiente comando equivale al comando anterior y devuelve los mismos resultados, pero usa un acento grave para aplicar escape en los caracteres especiales, en lugar de entrecomillar la cadena de filtro completa.</span><span class="sxs-lookup"><span data-stu-id="47d76-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="47d76-120">Para mostrar solo las propiedades que le interesen, use el parámetro Property de los cmdlets.</span><span class="sxs-lookup"><span data-stu-id="47d76-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

<span data-ttu-id="47d76-121">Por último, para buscar solo los nombres de las aplicaciones instaladas, una sencilla instrucción **Format-Wide** simplifica la salida:</span><span class="sxs-lookup"><span data-stu-id="47d76-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="47d76-122">Ya tenemos varias formas de ver las aplicaciones que usan Windows Installer para instalarse, pero no hemos tenido en cuenta otras aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="47d76-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="47d76-123">La mayoría de las aplicaciones estándar registran su desinstalador con Windows, por lo que podemos trabajar con ellas localmente buscándolas en el Registro de Windows.</span><span class="sxs-lookup"><span data-stu-id="47d76-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

### <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="47d76-124">Enumerar todas las aplicaciones no instalables</span><span class="sxs-lookup"><span data-stu-id="47d76-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="47d76-125">Aunque no hay ninguna manera en firme de encontrar todas las aplicaciones en un sistema, sí se pueden encontrar todos los programas en las listas que se muestran en el cuadro de diálogo Agregar o quitar programas.</span><span class="sxs-lookup"><span data-stu-id="47d76-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="47d76-126">Agregar o quitar programas detecta estas aplicaciones en la siguiente clave del Registro:</span><span class="sxs-lookup"><span data-stu-id="47d76-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="47d76-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span><span class="sxs-lookup"><span data-stu-id="47d76-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="47d76-128">También podemos examinar esta clave para buscar aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="47d76-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="47d76-129">Podemos hacer que la clave Uninstall sea más fácil de ver si asignamos una unidad de Windows PowerShell a esta ubicación del Registro:</span><span class="sxs-lookup"><span data-stu-id="47d76-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="47d76-130">La unidad **HKLM:** se asigna a la raíz de **HKEY_LOCAL_MACHINE**, por lo que usamos esa unidad en la ruta de acceso a la clave Uninstall.</span><span class="sxs-lookup"><span data-stu-id="47d76-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="47d76-131">En vez de **HKLM:**, podríamos haber especificado la ruta del Registro mediante **HKLM** o **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="47d76-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="47d76-132">La ventaja de usar una unidad de Registro existente es que podemos usar la finalización con tabulación para rellenar los nombres de claves, con lo cual no es necesario escribirlas.</span><span class="sxs-lookup"><span data-stu-id="47d76-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="47d76-133">Ya tenemos una unidad denominada "Uninstall" que se puede usar para buscar instalaciones de aplicaciones de forma cómoda y rápida.</span><span class="sxs-lookup"><span data-stu-id="47d76-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="47d76-134">Podemos hallar el número de aplicaciones instaladas contando el número de claves del Registro en la unidad de Windows PowerShell Uninstall:</span><span class="sxs-lookup"><span data-stu-id="47d76-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="47d76-135">Podemos realizar más búsquedas en esta lista de aplicaciones mediante diversas técnicas, comenzando por **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="47d76-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="47d76-136">Use el siguiente comando para obtener una lista de aplicaciones y guardarlas en la variable **$UninstallableApplications**:</span><span class="sxs-lookup"><span data-stu-id="47d76-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="47d76-137">Aquí usamos un nombre de variable largo para mayor claridad.</span><span class="sxs-lookup"><span data-stu-id="47d76-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="47d76-138">En la realidad, no es necesario usar nombres largos.</span><span class="sxs-lookup"><span data-stu-id="47d76-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="47d76-139">Aunque se puede recurrir a la finalización con tabulación en los nombres de variables, también se pueden usar nombres de 1-2 caracteres para acelerar el proceso.</span><span class="sxs-lookup"><span data-stu-id="47d76-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="47d76-140">Los nombres más largos y descriptivos son muy útiles cuando se está desarrollando código para reutilizarlo.</span><span class="sxs-lookup"><span data-stu-id="47d76-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="47d76-141">Para ver los valores de las entradas del Registro en las claves del Registro bajo Uninstall, use el método GetValue en las claves del Registro.</span><span class="sxs-lookup"><span data-stu-id="47d76-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="47d76-142">El valor del método es el nombre de la entrada del Registro.</span><span class="sxs-lookup"><span data-stu-id="47d76-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="47d76-143">Por ejemplo, use el siguiente comando para buscar los nombres para mostrar de las aplicaciones en la clave Uninstall:</span><span class="sxs-lookup"><span data-stu-id="47d76-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="47d76-144">No hay ninguna garantía de que estos valores sean únicos.</span><span class="sxs-lookup"><span data-stu-id="47d76-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="47d76-145">En el siguiente ejemplo, aparecen dos elementos instalados como "Windows Media Encoder 9 Series":</span><span class="sxs-lookup"><span data-stu-id="47d76-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

### <a name="installing-applications"></a><span data-ttu-id="47d76-146">Instalación de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="47d76-146">Installing Applications</span></span>

<span data-ttu-id="47d76-147">Puede usar la clase **Win32_Product** para instalar paquetes de Windows Installer, tanto de forma local como remota.</span><span class="sxs-lookup"><span data-stu-id="47d76-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="47d76-148">En Windows Vista, Windows Server 2008 y versiones posteriores de Windows, hay que iniciar Windows PowerShell con la opción "Ejecutar como administrador" para instalar una aplicación.</span><span class="sxs-lookup"><span data-stu-id="47d76-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="47d76-149">En las instalaciones remotas, use una ruta de red de convención de nomenclatura Universal (UNC) para especificar la ruta de acceso al paquete .msi, ya que el subsistema WMI no entiende las rutas de acceso de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="47d76-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="47d76-150">Por ejemplo, para instalar el paquete NewPackage.msi ubicado en el recurso compartido de red \\\\AppServ\\dsp en el equipo remoto PC01, escriba el siguiente comando en el símbolo del sistema de Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="47d76-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="47d76-151">Las aplicaciones que no usan la tecnología de Windows Installer pueden tener métodos específicos de aplicación disponibles para la implementación automática.</span><span class="sxs-lookup"><span data-stu-id="47d76-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="47d76-152">Para saber si hay un método de automatización de la implementación, consulte la documentación de la aplicación pertinente o el sistema de Ayuda del proveedor de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="47d76-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="47d76-153">En algunos casos, incluso en aquellos en los que el proveedor de la aplicación no la haya diseñado específicamente para la automatización de la instalación, es posible que el fabricante del software de instalador posea algunas técnicas para la automatización.</span><span class="sxs-lookup"><span data-stu-id="47d76-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

### <a name="removing-applications"></a><span data-ttu-id="47d76-154">Desinstalación de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="47d76-154">Removing Applications</span></span>

<span data-ttu-id="47d76-155">El proceso de desinstalación de un paquete de Windows Installer mediante Windows PowerShell funciona aproximadamente del mismo modo que la instalación de un paquete.</span><span class="sxs-lookup"><span data-stu-id="47d76-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="47d76-156">En este ejemplo, el paquete que se va a desinstalar se selecciona por su nombre; en algunos casos, probablemente sea más fácil filtrar con **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="47d76-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="47d76-157">Desinstalar otras aplicaciones no es tan sencillo, aun cuando se haga localmente.</span><span class="sxs-lookup"><span data-stu-id="47d76-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="47d76-158">Encontraremos las cadenas de desinstalación de línea de comandos de estas aplicaciones extrayendo la propiedad **UninstallString**.</span><span class="sxs-lookup"><span data-stu-id="47d76-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="47d76-159">Este método funciona con aplicaciones de Windows Installer y con los programas antiguos que aparecen bajo la clave Uninstall:</span><span class="sxs-lookup"><span data-stu-id="47d76-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="47d76-160">Si lo desea, puede filtrar el resultado por el nombre para mostrar:</span><span class="sxs-lookup"><span data-stu-id="47d76-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="47d76-161">Sin embargo, puede que estas cadenas no se puedan usar directamente desde el símbolo del sistema de Windows PowerShell sin realizar alguna modificación.</span><span class="sxs-lookup"><span data-stu-id="47d76-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

### <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="47d76-162">Actualización de aplicaciones de Windows Installer</span><span class="sxs-lookup"><span data-stu-id="47d76-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="47d76-163">Para actualizar una aplicación, es necesario conocer su nombre y la ruta de acceso al paquete de actualización de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="47d76-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="47d76-164">Con esa información, podrá actualizar una aplicación con un solo comando de Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="47d76-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```