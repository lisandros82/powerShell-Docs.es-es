---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Trabajar con entradas del Registro
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952382"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="5e34c-103">Trabajar con entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="5e34c-103">Working with Registry Entries</span></span>

<span data-ttu-id="5e34c-104">Las entradas del Registro son propiedades de claves y, como tales, no se pueden examinar de forma directa, de modo que es preciso adoptar un enfoque ligeramente diferente al trabajar con ellas.</span><span class="sxs-lookup"><span data-stu-id="5e34c-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="5e34c-105">Enumerar entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="5e34c-105">Listing Registry Entries</span></span>

<span data-ttu-id="5e34c-106">Existen muchas formas de examinar entradas del Registro.</span><span class="sxs-lookup"><span data-stu-id="5e34c-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="5e34c-107">La más sencilla consiste en obtener los nombres de propiedad asociados a una clave.</span><span class="sxs-lookup"><span data-stu-id="5e34c-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="5e34c-108">Por ejemplo, para ver los nombres de las entradas de la clave del Registro **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span><span class="sxs-lookup"><span data-stu-id="5e34c-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="5e34c-109">Las claves del Registro tienen una propiedad con el nombre genérico "Property" que es una lista de entradas del Registro en la clave.</span><span class="sxs-lookup"><span data-stu-id="5e34c-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="5e34c-110">Con el siguiente comando se selecciona la propiedad Property y se expanden los elementos de forma que se muestran en una lista:</span><span class="sxs-lookup"><span data-stu-id="5e34c-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="5e34c-111">Para ver las entradas del Registro en un formato más legible, use **Get-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="5e34c-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="5e34c-112">Las propiedades relativas a Windows PowerShell de la clave tienen antepuesto el prefijo "PS", como **PSPath**, **PSParentPath**, **PSChildName** y **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="5e34c-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="5e34c-113">Puede usar la notación "**.**" para hacer referencia a la ubicación actual.</span><span class="sxs-lookup"><span data-stu-id="5e34c-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="5e34c-114">Puede usar **Set-Location** para cambiar al contenedor del Registro **CurrentVersion** en primer lugar:</span><span class="sxs-lookup"><span data-stu-id="5e34c-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="5e34c-115">Otra opción consiste en usar el elemento integrado HKLM PSDrive con **Set-Location**:</span><span class="sxs-lookup"><span data-stu-id="5e34c-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="5e34c-116">Luego, puede usar la notación "**.**" de la ubicación actual para enumerar las propiedades sin especificar una ruta de acceso completa:</span><span class="sxs-lookup"><span data-stu-id="5e34c-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="5e34c-117">La expansión de la ruta de acceso funciona tal como lo hace en el sistema de archivos, así que desde esta ubicación se puede obtener la lista de **ItemProperty** de **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** mediante **Get-ItemProperty -Path ..\\Help**.</span><span class="sxs-lookup"><span data-stu-id="5e34c-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="5e34c-118">Obtener una sola entrada del Registro</span><span class="sxs-lookup"><span data-stu-id="5e34c-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="5e34c-119">Si quiere recuperar una entrada específica de una clave del Registro, puede usar uno de los diversos métodos posibles existentes.</span><span class="sxs-lookup"><span data-stu-id="5e34c-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="5e34c-120">En este ejemplo se encuentra el valor de **DevicePath** en **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="5e34c-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="5e34c-121">Con **Get-ItemProperty**, use el parámetro **Path** para especificar el nombre de la clave y el parámetro **Name** para especificar el nombre de la entrada **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="5e34c-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="5e34c-122">Este comando devuelve las propiedades estándar de Windows PowerShell, así como la propiedad **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="5e34c-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="5e34c-123">Aunque **Get-ItemProperty** tiene los parámetros **Filter**, **Include** y **Exclude**, no se pueden usar para filtrar por nombre de propiedad.</span><span class="sxs-lookup"><span data-stu-id="5e34c-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="5e34c-124">Estos parámetros hacen referencia a claves del Registro (que son rutas de acceso de los elementos) y no a entradas del Registro (que son propiedades de los elementos).</span><span class="sxs-lookup"><span data-stu-id="5e34c-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="5e34c-125">Otra opción sería usar la herramienta de línea de comandos Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="5e34c-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="5e34c-126">Para obtener ayuda con reg.exe, escriba **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="5e34c-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="5e34c-127">en un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="5e34c-127">at a command prompt.</span></span> <span data-ttu-id="5e34c-128">Para buscar la entrada DevicePath, use reg.exe tal y como se muestra en el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="5e34c-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="5e34c-129">También puede usar el objeto **WshShell COM** para encontrar algunas entradas del Registro, aunque este método no funciona con datos binarios de gran tamaño o con nombres de entradas del Registro que contengan caracteres como "\\").</span><span class="sxs-lookup"><span data-stu-id="5e34c-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="5e34c-130">Anexe el nombre de la propiedad a la ruta de acceso de elemento con un separador \\:</span><span class="sxs-lookup"><span data-stu-id="5e34c-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="5e34c-131">Crear entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="5e34c-131">Creating New Registry Entries</span></span>

<span data-ttu-id="5e34c-132">Para agregar una nueva entrada denominada "PowerShellPath" a la clave **CurrentVersion**, use **New-ItemProperty** con la ruta de acceso a la clave, el nombre de la entrada y el valor de la entrada.</span><span class="sxs-lookup"><span data-stu-id="5e34c-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="5e34c-133">En este ejemplo, tomaremos el valor de la variable de Windows PowerShell **$PSHome**, que almacena la ruta de acceso al directorio de instalación de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e34c-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="5e34c-134">Puede agregar la nueva entrada a la clave usando el siguiente comando; este comando también devolverá información sobre la nueva entrada:</span><span class="sxs-lookup"><span data-stu-id="5e34c-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="5e34c-135">**PropertyType** debe ser el nombre de un miembro de la enumeración **Microsoft.Win32.RegistryValueKind** de la siguiente tabla:</span><span class="sxs-lookup"><span data-stu-id="5e34c-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="5e34c-136">Valor de PropertyType</span><span class="sxs-lookup"><span data-stu-id="5e34c-136">PropertyType Value</span></span>|<span data-ttu-id="5e34c-137">Significado</span><span class="sxs-lookup"><span data-stu-id="5e34c-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="5e34c-138">Binary</span><span class="sxs-lookup"><span data-stu-id="5e34c-138">Binary</span></span>|<span data-ttu-id="5e34c-139">Datos binarios</span><span class="sxs-lookup"><span data-stu-id="5e34c-139">Binary data</span></span>|
|<span data-ttu-id="5e34c-140">DWord</span><span class="sxs-lookup"><span data-stu-id="5e34c-140">DWord</span></span>|<span data-ttu-id="5e34c-141">Un número que es un UInt32 válido</span><span class="sxs-lookup"><span data-stu-id="5e34c-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="5e34c-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="5e34c-142">ExpandString</span></span>|<span data-ttu-id="5e34c-143">Una cadena que puede contener variables de entorno que se expanden dinámicamente</span><span class="sxs-lookup"><span data-stu-id="5e34c-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="5e34c-144">MultiString</span><span class="sxs-lookup"><span data-stu-id="5e34c-144">MultiString</span></span>|<span data-ttu-id="5e34c-145">Una cadena de varias líneas</span><span class="sxs-lookup"><span data-stu-id="5e34c-145">A multiline string</span></span>|
|<span data-ttu-id="5e34c-146">Cadena</span><span class="sxs-lookup"><span data-stu-id="5e34c-146">String</span></span>|<span data-ttu-id="5e34c-147">Cualquier valor de cadena</span><span class="sxs-lookup"><span data-stu-id="5e34c-147">Any string value</span></span>|
|<span data-ttu-id="5e34c-148">QWord</span><span class="sxs-lookup"><span data-stu-id="5e34c-148">QWord</span></span>|<span data-ttu-id="5e34c-149">8 bytes de datos binarios</span><span class="sxs-lookup"><span data-stu-id="5e34c-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="5e34c-150">Una entrada del Registro se puede agregar a varias ubicaciones si se especifica una matriz de valores para el parámetro **Path**:</span><span class="sxs-lookup"><span data-stu-id="5e34c-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="5e34c-151">Un valor de entrada del Registro preexistente también se puede sobrescribir si se agrega el parámetro **Force** a cualquier comando **New-ItemProperty**.</span><span class="sxs-lookup"><span data-stu-id="5e34c-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="5e34c-152">Cambiar el nombre de entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="5e34c-152">Renaming Registry Entries</span></span>

<span data-ttu-id="5e34c-153">Para cambiar el nombre de la entrada **PowerShellPath** a "PSHome," use **Rename-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="5e34c-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="5e34c-154">Para mostrar el valor cuyo nombre ha cambiado, agregue el parámetro **PassThru** al comando.</span><span class="sxs-lookup"><span data-stu-id="5e34c-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="5e34c-155">Eliminar entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="5e34c-155">Deleting Registry Entries</span></span>

<span data-ttu-id="5e34c-156">Para eliminar las entradas del Registro PSHome y PowerShellPath, use **Remove-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="5e34c-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```