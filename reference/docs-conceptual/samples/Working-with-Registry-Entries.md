---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Trabajar con entradas del Registro
ms.openlocfilehash: c1fd6f57f13240eb2039f2d5756796678800aee0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030717"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="77930-103">Trabajar con entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="77930-103">Working with Registry Entries</span></span>

<span data-ttu-id="77930-104">Las entradas del Registro son propiedades de claves y, como tales, no se pueden examinar de forma directa, de modo que es preciso adoptar un enfoque ligeramente diferente al trabajar con ellas.</span><span class="sxs-lookup"><span data-stu-id="77930-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="77930-105">Enumerar entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="77930-105">Listing Registry Entries</span></span>

<span data-ttu-id="77930-106">Existen muchas formas de examinar entradas del Registro.</span><span class="sxs-lookup"><span data-stu-id="77930-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="77930-107">La más sencilla consiste en obtener los nombres de propiedad asociados a una clave.</span><span class="sxs-lookup"><span data-stu-id="77930-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="77930-108">Por ejemplo, para ver los nombres de las entradas en la clave de Registro `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, utilice `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="77930-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="77930-109">Las claves del Registro tienen una propiedad con el nombre genérico "Property" que es una lista de entradas del Registro en la clave.</span><span class="sxs-lookup"><span data-stu-id="77930-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="77930-110">Con el siguiente comando se selecciona la propiedad Property y se expanden los elementos de forma que se muestran en una lista:</span><span class="sxs-lookup"><span data-stu-id="77930-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

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

<span data-ttu-id="77930-111">Para ver las entradas del Registro en un formato más legible, use `Get-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="77930-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

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

<span data-ttu-id="77930-112">Las propiedades relativas a Windows PowerShell de la clave tienen antepuesto el prefijo "PS", como **PSPath**, **PSParentPath**, **PSChildName** y **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="77930-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="77930-113">Puede usar la notación `*.*` para hacer referencia a la ubicación actual.</span><span class="sxs-lookup"><span data-stu-id="77930-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="77930-114">Puede usar `Set-Location` para cambiar al contenedor del Registro **CurrentVersion** en primer lugar:</span><span class="sxs-lookup"><span data-stu-id="77930-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="77930-115">Otra opción consiste en usar el elemento integrado HKLM PSDrive con `Set-Location`:</span><span class="sxs-lookup"><span data-stu-id="77930-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="77930-116">Luego, puede usar la notación `*.*` de la ubicación actual para enumerar las propiedades sin especificar una ruta de acceso completa:</span><span class="sxs-lookup"><span data-stu-id="77930-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

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

<span data-ttu-id="77930-117">Expansión de la ruta de acceso funciona igual que lo hace en el sistema de archivos, así que desde esta ubicación se puede obtener la lista **ItemProperty** para `HKLM:\SOFTWARE\Microsoft\Windows\Help` mediante `Get-ItemProperty -Path ..\Help`.</span><span class="sxs-lookup"><span data-stu-id="77930-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="77930-118">Obtener una sola entrada del Registro</span><span class="sxs-lookup"><span data-stu-id="77930-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="77930-119">Si quiere recuperar una entrada específica de una clave del Registro, puede usar uno de los diversos métodos posibles existentes.</span><span class="sxs-lookup"><span data-stu-id="77930-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="77930-120">Este ejemplo busca el valor de **DevicePath** en `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="77930-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="77930-121">Con `Get-ItemProperty`, use el parámetro **Path** para especificar el nombre de la clave y el parámetro **Name** para especificar el nombre de la entrada **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="77930-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

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

<span data-ttu-id="77930-122">Este comando devuelve las propiedades estándar de Windows PowerShell, así como la propiedad **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="77930-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="77930-123">Aunque `Get-ItemProperty` tiene los parámetros **Filter**, **Include** y **Exclude**, no se pueden usar para filtrar por nombre de propiedad.</span><span class="sxs-lookup"><span data-stu-id="77930-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="77930-124">Estos parámetros hacen referencia a claves del Registro (que son rutas de acceso de los elementos) y no a entradas del Registro.</span><span class="sxs-lookup"><span data-stu-id="77930-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="77930-125">Las entradas del Registro que son propiedades de los elementos.</span><span class="sxs-lookup"><span data-stu-id="77930-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="77930-126">Otra opción sería usar la herramienta de línea de comandos Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="77930-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="77930-127">Para obtener ayuda con reg.exe, escriba `reg.exe /?` en un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="77930-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="77930-128">Para buscar la entrada DevicePath, use reg.exe tal y como se muestra en el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="77930-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="77930-129">También puede usar el objeto **WshShell** COM para encontrar algunas entradas del Registro, aunque este método no funciona con datos binarios de gran tamaño o con nombres de entradas del Registro que contengan caracteres como "\\").</span><span class="sxs-lookup"><span data-stu-id="77930-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="77930-130">Anexe el nombre de la propiedad a la ruta de acceso de elemento con un separador \\:</span><span class="sxs-lookup"><span data-stu-id="77930-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="77930-131">Obtención de una sola entrada del Registro</span><span class="sxs-lookup"><span data-stu-id="77930-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="77930-132">Si quiere cambiar una entrada específica de una clave del Registro, puede usar uno de los diversos métodos posibles existentes.</span><span class="sxs-lookup"><span data-stu-id="77930-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="77930-133">En este ejemplo, se modifica la entrada **Path** bajo `HKEY_CURRENT_USER\Environment`.</span><span class="sxs-lookup"><span data-stu-id="77930-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="77930-134">La entrada **Path** especifica dónde encontrar los archivos ejecutables.</span><span class="sxs-lookup"><span data-stu-id="77930-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="77930-135">Recupere el valor actual de la entrada **Path** mediante `Get-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="77930-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="77930-136">Agregue el nuevo valor y sepárelo con un `;`.</span><span class="sxs-lookup"><span data-stu-id="77930-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="77930-137">Use `Set-ItemProperty` con la clave especificada, el nombre de la entrada y el valor para modificar la entrada del Registro.</span><span class="sxs-lookup"><span data-stu-id="77930-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="77930-138">Aunque `Set-ItemProperty` tiene los parámetros **Filter**, **Include** y **Exclude**, no se pueden usar para filtrar por nombre de propiedad.</span><span class="sxs-lookup"><span data-stu-id="77930-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="77930-139">Estos parámetros hacen referencia a claves del Registro (que son rutas de acceso de los elementos) y no a entradas del Registro (que son propiedades de los elementos).</span><span class="sxs-lookup"><span data-stu-id="77930-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="77930-140">Otra opción sería usar la herramienta de línea de comandos Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="77930-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="77930-141">Para obtener ayuda con reg.exe, escriba **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="77930-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="77930-142">en un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="77930-142">at a command prompt.</span></span>

<span data-ttu-id="77930-143">En el ejemplo siguiente se cambia la entrada **Path** mediante la eliminación de la ruta de acceso que se agregó en el ejemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="77930-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="77930-144">`Get-ItemProperty` aún se utiliza para recuperar el valor actual para evitar tener que analizar la cadena devuelta desde `reg query`.</span><span class="sxs-lookup"><span data-stu-id="77930-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="77930-145">Los métodos **SubString** y **LastIndexOf** se usan para recuperar la última ruta de acceso que se agrega a la entrada **Path**.</span><span class="sxs-lookup"><span data-stu-id="77930-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="77930-146">Crear entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="77930-146">Creating New Registry Entries</span></span>

<span data-ttu-id="77930-147">Para agregar una nueva entrada denominada "PowerShellPath" a la clave **CurrentVersion**, use `New-ItemProperty` con la ruta de acceso a la clave, el nombre de la entrada y el valor de la entrada.</span><span class="sxs-lookup"><span data-stu-id="77930-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="77930-148">En este ejemplo, tomaremos el valor de la variable de Windows PowerShell `$PSHome`, que almacena la ruta de acceso al directorio de instalación de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77930-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="77930-149">Puede agregar la nueva entrada a la clave usando el siguiente comando; este comando también devolverá información sobre la nueva entrada:</span><span class="sxs-lookup"><span data-stu-id="77930-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

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

<span data-ttu-id="77930-150">**PropertyType** debe ser el nombre de un miembro de la enumeración **Microsoft.Win32.RegistryValueKind** de la siguiente tabla:</span><span class="sxs-lookup"><span data-stu-id="77930-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="77930-151">Valor de PropertyType</span><span class="sxs-lookup"><span data-stu-id="77930-151">PropertyType Value</span></span>|<span data-ttu-id="77930-152">Significado</span><span class="sxs-lookup"><span data-stu-id="77930-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="77930-153">Binary</span><span class="sxs-lookup"><span data-stu-id="77930-153">Binary</span></span>|<span data-ttu-id="77930-154">Datos binarios</span><span class="sxs-lookup"><span data-stu-id="77930-154">Binary data</span></span>|
|<span data-ttu-id="77930-155">DWord</span><span class="sxs-lookup"><span data-stu-id="77930-155">DWord</span></span>|<span data-ttu-id="77930-156">Un número que es un UInt32 válido</span><span class="sxs-lookup"><span data-stu-id="77930-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="77930-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="77930-157">ExpandString</span></span>|<span data-ttu-id="77930-158">Una cadena que puede contener variables de entorno que se expanden dinámicamente</span><span class="sxs-lookup"><span data-stu-id="77930-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="77930-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="77930-159">MultiString</span></span>|<span data-ttu-id="77930-160">Una cadena de varias líneas</span><span class="sxs-lookup"><span data-stu-id="77930-160">A multiline string</span></span>|
|<span data-ttu-id="77930-161">Cadena</span><span class="sxs-lookup"><span data-stu-id="77930-161">String</span></span>|<span data-ttu-id="77930-162">Cualquier valor de cadena</span><span class="sxs-lookup"><span data-stu-id="77930-162">Any string value</span></span>|
|<span data-ttu-id="77930-163">QWord</span><span class="sxs-lookup"><span data-stu-id="77930-163">QWord</span></span>|<span data-ttu-id="77930-164">8 bytes de datos binarios</span><span class="sxs-lookup"><span data-stu-id="77930-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="77930-165">Una entrada del Registro se puede agregar a varias ubicaciones si se especifica una matriz de valores para el parámetro **Path**:</span><span class="sxs-lookup"><span data-stu-id="77930-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="77930-166">Un valor de entrada del Registro preexistente también se puede sobrescribir si se agrega el parámetro **Force** a cualquier comando `New-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="77930-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="77930-167">Cambiar el nombre de entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="77930-167">Renaming Registry Entries</span></span>

<span data-ttu-id="77930-168">Para cambiar el nombre de la entrada **PowerShellPath** a "PSHome," use `Rename-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="77930-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="77930-169">Para mostrar el valor cuyo nombre ha cambiado, agregue el parámetro **PassThru** al comando.</span><span class="sxs-lookup"><span data-stu-id="77930-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="77930-170">Eliminar entradas del Registro</span><span class="sxs-lookup"><span data-stu-id="77930-170">Deleting Registry Entries</span></span>

<span data-ttu-id="77930-171">Para eliminar las entradas del Registro PSHome y PowerShellPath, use `Remove-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="77930-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
