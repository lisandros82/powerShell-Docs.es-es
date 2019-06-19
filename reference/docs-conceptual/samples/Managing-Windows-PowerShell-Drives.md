---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Administrar unidades de Windows PowerShell
ms.openlocfilehash: 32efa282fb787753942e43acab53c7b6eaeb88e3
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030150"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="f290d-103">Administrar unidades de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f290d-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="f290d-104">Una *unidad de Windows PowerShell* es una ubicación de almacén de datos a la que se puede acceder como una unidad del sistema de archivos en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f290d-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="f290d-105">Los proveedores de Windows PowerShell crean algunas unidades automáticamente, como las unidades de sistema de archivos (C: y D:), las unidades de Registro (HKCU: y HKLM:) y la unidad de certificado (Cert:). También puede crear sus propias unidades de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f290d-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="f290d-106">Estas unidades son muy útiles, pero estarán disponibles solo en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f290d-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="f290d-107">No se puede tener acceso a ellas con otras herramientas de Windows, como el Explorador de archivos o Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="f290d-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="f290d-108">Windows PowerShell usa el término **PSDrive** en los comandos que funcionan con las unidades de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f290d-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="f290d-109">Use el cmdlet **Get-PSDrive** para ver una lista de las unidades de WindowsPowerShell en su sesión de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f290d-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

<span data-ttu-id="f290d-110">Aunque las unidades que aparecen en la presentación difieren de las unidades del sistema, la lista tendrá un aspecto similar a la salida del comando **Get-PSDrive** mostrado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f290d-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="f290d-111">Las unidades del sistema de archivos son un subconjunto de las unidades de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f290d-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="f290d-112">Puede identificar las unidades del sistema de archivos por la entrada FileSystem en la columna Provider.</span><span class="sxs-lookup"><span data-stu-id="f290d-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="f290d-113">(Las unidades del sistema de archivos en Windows PowerShell son compatibles con el proveedor FileSystem de Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="f290d-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="f290d-114">Para ver la sintaxis del cmdlet **Get-PSDrive**, escriba un comando **Get-Command** con el parámetro **Syntax**:</span><span class="sxs-lookup"><span data-stu-id="f290d-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="f290d-115">El parámetro **PSProvider** permite mostrar únicamente las unidades de Windows PowerShell compatibles con un proveedor determinado.</span><span class="sxs-lookup"><span data-stu-id="f290d-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="f290d-116">Por ejemplo, para mostrar solo las unidades de Windows PowerShell compatibles con el proveedor FileSystem de Windows PowerShell, escriba un comando **Get-PSDrive** con el parámetro **PSProvider** y el valor **FileSystem**:</span><span class="sxs-lookup"><span data-stu-id="f290d-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="f290d-117">Para ver las unidades de Windows PowerShell que representan los subárboles del Registro, use el parámetro **PSProvider** para mostrar solo las unidades de Windows PowerShell compatibles con el proveedor de Registro de Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f290d-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="f290d-118">También puede usar los cmdlets Location estándar con las unidades de disco de Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f290d-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="f290d-119">Agregar nuevas unidades de Windows PowerShell (New-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="f290d-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="f290d-120">Puede usar el comando **New-PSDrive** para agregar sus propias unidades de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f290d-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="f290d-121">Para obtener la sintaxis del comando **New-PSDrive**, escriba el comando **Get-Command** con el parámetro **Syntax**:</span><span class="sxs-lookup"><span data-stu-id="f290d-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="f290d-122">Para crear una unidad de Windows PowerShell, debe proporcionar tres parámetros:</span><span class="sxs-lookup"><span data-stu-id="f290d-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="f290d-123">Un nombre de unidad (puede usar cualquier nombre válido de Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="f290d-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="f290d-124">El PSProvider (use "FileSystem" para las ubicaciones del sistema de archivos y "Registry" para las ubicaciones del Registro)</span><span class="sxs-lookup"><span data-stu-id="f290d-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="f290d-125">La raíz; es decir, la ruta de acceso a la raíz de la nueva unidad</span><span class="sxs-lookup"><span data-stu-id="f290d-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="f290d-126">Por ejemplo, puede crear una unidad llamada "Office" que esté asignada a la carpeta que contiene las aplicaciones de Microsoft Office del equipo, como **C:\\Archivos de programa\\Microsoft Office\\OFFICE11**.</span><span class="sxs-lookup"><span data-stu-id="f290d-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="f290d-127">Para crear la unidad, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="f290d-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="f290d-128">Por lo general, las rutas de acceso no distinguen mayúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="f290d-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="f290d-129">La referencia a la nueva unidad de Windows PowerShell se hace como con cualquier otra unidad de Windows PowerShell; es decir, por su nombre seguido de dos puntos ( **:** ).</span><span class="sxs-lookup"><span data-stu-id="f290d-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="f290d-130">Una unidad de Windows PowerShell puede hacer que muchas tareas sean mucho más sencillas de realizar.</span><span class="sxs-lookup"><span data-stu-id="f290d-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="f290d-131">Por ejemplo, algunas de las claves más importantes en el Registro de Windows tienen rutas de acceso muy largas, lo que las hace complicadas de acceder y difíciles de recordar.</span><span class="sxs-lookup"><span data-stu-id="f290d-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="f290d-132">La información de configuración crítica reside en **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="f290d-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="f290d-133">Si quiere ver y cambiar elementos en la clave del Registro CurrentVersion, puede escribir lo siguiente para crear una unidad de Windows PowerShell que se base en esa clave:</span><span class="sxs-lookup"><span data-stu-id="f290d-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="f290d-134">Luego, puede cambiar la ubicación a la unidad **cvkey:** , como lo haría con cualquier otra unidad:\`\`</span><span class="sxs-lookup"><span data-stu-id="f290d-134">You can then change location to the **cvkey:** drive as you would any other drive:\`\`</span></span>

`PS> cd cvkey:`

<span data-ttu-id="f290d-135">o:</span><span class="sxs-lookup"><span data-stu-id="f290d-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="f290d-136">El cmdlet New-PsDrive agrega la nueva unidad solo en la sesión actual de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f290d-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="f290d-137">Si cierra la ventana de Windows PowerShell, la nueva unidad se perderá.</span><span class="sxs-lookup"><span data-stu-id="f290d-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="f290d-138">Para guardar una unidad de Windows PowerShell, use el cmdlet Export-Console para exportar la sesión actual de Windows PowerShell y luego use el parámetro **PSConsoleFile** de PowerShell.exe para importarla.</span><span class="sxs-lookup"><span data-stu-id="f290d-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="f290d-139">También puede agregar la nueva unidad al perfil de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f290d-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="f290d-140">Eliminar unidades de Windows PowerShell (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="f290d-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="f290d-141">Puede usar el cmdlet **Remove-PSDrive** para eliminar unidades de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f290d-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="f290d-142">El cmdlet **Remove-PSDrive** es fácil de usar. Para eliminar una unidad específica de Windows PowerShell, basta con proporcionar el nombre de dicha unidad.</span><span class="sxs-lookup"><span data-stu-id="f290d-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="f290d-143">Por ejemplo, si ha agregado la unidad de Windows PowerShell **Office**, como se indica en el tema sobre **New-PSDrive**, puede eliminarla escribiendo lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="f290d-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="f290d-144">Para eliminar la unidad **cvkey:** de Windows PowerShell, que también se muestra en el tema **New-PSDrive**, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="f290d-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="f290d-145">Una unidad de Windows PowerShell es fácil de eliminar, pero esto no podrá llevarlo a cabo mientras se encuentre en la unidad.</span><span class="sxs-lookup"><span data-stu-id="f290d-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="f290d-146">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f290d-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="f290d-147">Agregar y quitar unidades fuera de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f290d-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="f290d-148">Windows PowerShell detecta las unidades del sistema de archivos que se han agregado o quitado en Windows, incluidas las unidades de red asignadas, las unidades USB conectadas y las unidades que se han eliminado mediante el comando **net use** o los métodos **WScript.NetworkMapNetworkDrive** y **RemoveNetworkDrive** de un script de Windows Script Host (WSH).</span><span class="sxs-lookup"><span data-stu-id="f290d-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>
