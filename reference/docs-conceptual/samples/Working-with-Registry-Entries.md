---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Trabajar con entradas del Registro
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681545"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="412c8-103">Trabajar con entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="412c8-103">Working with Registry Entries</span></span>

<span data-ttu-id="412c8-104">Las entradas del Registro son propiedades de claves y, como tales, no se pueden examinar de forma directa, de modo que es preciso adoptar un enfoque ligeramente diferente al trabajar con ellas.</span><span class="sxs-lookup"><span data-stu-id="412c8-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="412c8-105">Enumerar entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="412c8-105">Listing Registry Entries</span></span>

<span data-ttu-id="412c8-106">Existen muchas formas de examinar entradas del Registro.</span><span class="sxs-lookup"><span data-stu-id="412c8-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="412c8-107">La más sencilla consiste en obtener los nombres de propiedad asociados a una clave.</span><span class="sxs-lookup"><span data-stu-id="412c8-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="412c8-108">Por ejemplo, para ver los nombres de las entradas de la clave del registro `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, utilice `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="412c8-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="412c8-109">Las claves del Registro tienen una propiedad con el nombre genérico "Property" que es una lista de entradas del Registro en la clave.</span><span class="sxs-lookup"><span data-stu-id="412c8-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="412c8-110">Con el siguiente comando se selecciona la propiedad Property y se expanden los elementos de forma que se muestran en una lista:</span><span class="sxs-lookup"><span data-stu-id="412c8-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="412c8-111">Para ver las entradas del registro en un formato más legible, use `Get-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="412c8-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
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

<span data-ttu-id="412c8-112">Las propiedades relativas a Windows PowerShell de la clave tienen antepuesto el prefijo "PS", como **PSPath**, **PSParentPath**, **PSChildName** y **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="412c8-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="412c8-113">Puede usar la notación "`*.*`." para hacer referencia a la ubicación actual.</span><span class="sxs-lookup"><span data-stu-id="412c8-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="412c8-114">Puede usar `Set-Location` para cambiar a la **CurrentVersion** contenedor del registro primera:</span><span class="sxs-lookup"><span data-stu-id="412c8-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="412c8-115">Como alternativa, puede usar el elemento integrado HKLM PSDrive con `Set-Location`:</span><span class="sxs-lookup"><span data-stu-id="412c8-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="412c8-116">Luego, puede usar la notación "`*.*`." de la ubicación actual para enumerar las propiedades sin especificar una ruta de acceso completa:</span><span class="sxs-lookup"><span data-stu-id="412c8-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="412c8-117">Expansión de la ruta de acceso funciona igual que lo hace en el sistema de archivos, así que desde esta ubicación se puede obtener el **ItemProperty** lista para `HKLM:\SOFTWARE\Microsoft\Windows\Help` utilizando `Get-ItemProperty -Path ..\Help`.</span><span class="sxs-lookup"><span data-stu-id="412c8-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="412c8-118">Obtener una sola entrada del Registro</span><span class="sxs-lookup"><span data-stu-id="412c8-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="412c8-119">Si quiere recuperar una entrada específica de una clave del Registro, puede usar uno de los diversos métodos posibles existentes.</span><span class="sxs-lookup"><span data-stu-id="412c8-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="412c8-120">Este ejemplo busca el valor de **DevicePath** en `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="412c8-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="412c8-121">Mediante `Get-ItemProperty`, utilice el **ruta de acceso** parámetro para especificar el nombre de la clave y el **nombre** parámetro para especificar el nombre de la **DevicePath** entrada.</span><span class="sxs-lookup"><span data-stu-id="412c8-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="412c8-122">Este comando devuelve las propiedades estándar de Windows PowerShell, así como la propiedad **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="412c8-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="412c8-123">Aunque `Get-ItemProperty` tiene **filtro**, **Include**, y **excluir** parámetros, no se puede usar para filtrar por nombre de propiedad.</span><span class="sxs-lookup"><span data-stu-id="412c8-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="412c8-124">Estos parámetros hacen referencia a las claves del registro, que son las rutas de acceso de elemento y no las entradas de registro.</span><span class="sxs-lookup"><span data-stu-id="412c8-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="412c8-125">Entradas del registro que son propiedades del elemento.</span><span class="sxs-lookup"><span data-stu-id="412c8-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="412c8-126">Otra opción sería usar la herramienta de línea de comandos Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="412c8-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="412c8-127">Para obtener ayuda con reg.exe, escriba `reg.exe /?` en un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="412c8-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="412c8-128">Para buscar la entrada DevicePath, use reg.exe tal y como se muestra en el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="412c8-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="412c8-129">También puede usar el objeto **WshShell COM** para encontrar algunas entradas del Registro, aunque este método no funciona con datos binarios de gran tamaño o con nombres de entradas del Registro que contengan caracteres como "\\").</span><span class="sxs-lookup"><span data-stu-id="412c8-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="412c8-130">Anexe el nombre de la propiedad a la ruta de acceso de elemento con un separador \\:</span><span class="sxs-lookup"><span data-stu-id="412c8-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a><span data-ttu-id="412c8-131">Configuración de una sola entrada del registro</span><span class="sxs-lookup"><span data-stu-id="412c8-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="412c8-132">Si desea cambiar una entrada específica de una clave del registro, puede usar uno de los varios enfoques posibles.</span><span class="sxs-lookup"><span data-stu-id="412c8-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="412c8-133">En este ejemplo se modifica el **ruta** entrada bajo `HKEY_CURRENT_USER\Environment`.</span><span class="sxs-lookup"><span data-stu-id="412c8-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="412c8-134">El **ruta** entrada especifica dónde encontrar los archivos ejecutables.</span><span class="sxs-lookup"><span data-stu-id="412c8-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="412c8-135">Recuperar el valor actual de la **ruta** entrada mediante `Get-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="412c8-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="412c8-136">Agregar el nuevo valor sepárelo con una `;`.</span><span class="sxs-lookup"><span data-stu-id="412c8-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="412c8-137">Use `Set-ItemProperty` con la clave especificada, el nombre de la entrada y el valor para modificar la entrada del registro.</span><span class="sxs-lookup"><span data-stu-id="412c8-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="412c8-138">Aunque `Set-ItemProperty` tiene **filtro**, **Include**, y **excluir** parámetros, no se puede usar para filtrar por nombre de propiedad.</span><span class="sxs-lookup"><span data-stu-id="412c8-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="412c8-139">Estos parámetros hacen referencia a claves del Registro (que son rutas de acceso de los elementos) y no a entradas del Registro (que son propiedades de los elementos).</span><span class="sxs-lookup"><span data-stu-id="412c8-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="412c8-140">Otra opción sería usar la herramienta de línea de comandos Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="412c8-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="412c8-141">Para obtener ayuda con reg.exe, escriba **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="412c8-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="412c8-142">en un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="412c8-142">at a command prompt.</span></span>

<span data-ttu-id="412c8-143">El ejemplo siguiente se cambia el **ruta** entrada mediante la eliminación de la ruta de acceso que se agregó en el ejemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="412c8-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="412c8-144">`Get-ItemProperty` aún se utiliza para recuperar el valor actual para evitar tener que analizar la cadena devuelta desde `reg query`.</span><span class="sxs-lookup"><span data-stu-id="412c8-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="412c8-145">El **subcadena** y **LastIndexOf** métodos se usan para recuperar la última ruta de acceso que se agrega a la **ruta** entrada.</span><span class="sxs-lookup"><span data-stu-id="412c8-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="412c8-146">Crear entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="412c8-146">Creating New Registry Entries</span></span>

<span data-ttu-id="412c8-147">Para agregar una nueva entrada denominada "PowerShellPath" a la **CurrentVersion** el uso de claves, `New-ItemProperty` con la ruta de acceso a la clave, el nombre de la entrada y el valor de la entrada.</span><span class="sxs-lookup"><span data-stu-id="412c8-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="412c8-148">En este ejemplo, tomaremos el valor de la variable de Windows PowerShell `$PSHome`, que almacena la ruta de acceso al directorio de instalación de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="412c8-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="412c8-149">Puede agregar la nueva entrada a la clave usando el siguiente comando; este comando también devolverá información sobre la nueva entrada:</span><span class="sxs-lookup"><span data-stu-id="412c8-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="412c8-150">**PropertyType** debe ser el nombre de un miembro de la enumeración **Microsoft.Win32.RegistryValueKind** de la siguiente tabla:</span><span class="sxs-lookup"><span data-stu-id="412c8-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="412c8-151">Valor de PropertyType</span><span class="sxs-lookup"><span data-stu-id="412c8-151">PropertyType Value</span></span>|<span data-ttu-id="412c8-152">Significado</span><span class="sxs-lookup"><span data-stu-id="412c8-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="412c8-153">Binary</span><span class="sxs-lookup"><span data-stu-id="412c8-153">Binary</span></span>|<span data-ttu-id="412c8-154">Datos binarios</span><span class="sxs-lookup"><span data-stu-id="412c8-154">Binary data</span></span>|
|<span data-ttu-id="412c8-155">DWord</span><span class="sxs-lookup"><span data-stu-id="412c8-155">DWord</span></span>|<span data-ttu-id="412c8-156">Un número que es un UInt32 válido</span><span class="sxs-lookup"><span data-stu-id="412c8-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="412c8-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="412c8-157">ExpandString</span></span>|<span data-ttu-id="412c8-158">Una cadena que puede contener variables de entorno que se expanden dinámicamente</span><span class="sxs-lookup"><span data-stu-id="412c8-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="412c8-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="412c8-159">MultiString</span></span>|<span data-ttu-id="412c8-160">Una cadena de varias líneas</span><span class="sxs-lookup"><span data-stu-id="412c8-160">A multiline string</span></span>|
|<span data-ttu-id="412c8-161">Cadena</span><span class="sxs-lookup"><span data-stu-id="412c8-161">String</span></span>|<span data-ttu-id="412c8-162">Cualquier valor de cadena</span><span class="sxs-lookup"><span data-stu-id="412c8-162">Any string value</span></span>|
|<span data-ttu-id="412c8-163">QWord</span><span class="sxs-lookup"><span data-stu-id="412c8-163">QWord</span></span>|<span data-ttu-id="412c8-164">8 bytes de datos binarios</span><span class="sxs-lookup"><span data-stu-id="412c8-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="412c8-165">Una entrada del Registro se puede agregar a varias ubicaciones si se especifica una matriz de valores para el parámetro **Path**:</span><span class="sxs-lookup"><span data-stu-id="412c8-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="412c8-166">También se puede sobrescribir un valor de entrada del registro preexistente agregando el **Force** cualquier parámetro `New-ItemProperty` comando.</span><span class="sxs-lookup"><span data-stu-id="412c8-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="412c8-167">Cambiar el nombre de entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="412c8-167">Renaming Registry Entries</span></span>

<span data-ttu-id="412c8-168">Para cambiar el nombre de la **PowerShellPath** entrada a "PSHome," use `Rename-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="412c8-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="412c8-169">Para mostrar el valor cuyo nombre ha cambiado, agregue el parámetro **PassThru** al comando.</span><span class="sxs-lookup"><span data-stu-id="412c8-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="412c8-170">Eliminar entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="412c8-170">Deleting Registry Entries</span></span>

<span data-ttu-id="412c8-171">Para eliminar las entradas del registro de la PSHome y PowerShellPath, use `Remove-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="412c8-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
