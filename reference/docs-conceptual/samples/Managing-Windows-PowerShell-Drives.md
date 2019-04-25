---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Administrar unidades de Windows PowerShell
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: 9ac5136fb28b450ea6397cab2f36082c50f22e1f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057832"
---
# <a name="managing-windows-powershell-drives"></a>Administrar unidades de Windows PowerShell

Una *unidad de Windows PowerShell* es una ubicación de almacén de datos a la que se puede acceder como una unidad del sistema de archivos en Windows PowerShell. Los proveedores de Windows PowerShell crean algunas unidades automáticamente, como las unidades de sistema de archivos (C: y D:), las unidades de Registro (HKCU: y HKLM:) y la unidad de certificado (Cert:). También puede crear sus propias unidades de Windows PowerShell. Estas unidades son muy útiles, pero estarán disponibles solo en Windows PowerShell. No se puede tener acceso a ellas con otras herramientas de Windows, como el Explorador de archivos o Cmd.exe.

Windows PowerShell usa el término **PSDrive** en los comandos que funcionan con las unidades de Windows PowerShell. Use el cmdlet **Get-PSDrive** para ver una lista de las unidades de WindowsPowerShell en su sesión de Windows PowerShell.

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

Aunque las unidades que aparecen en la presentación difieren de las unidades del sistema, la lista tendrá un aspecto similar a la salida del comando **Get-PSDrive** mostrado anteriormente.

Las unidades del sistema de archivos son un subconjunto de las unidades de Windows PowerShell. Puede identificar las unidades del sistema de archivos por la entrada FileSystem en la columna Provider. (Las unidades del sistema de archivos en Windows PowerShell son compatibles con el proveedor FileSystem de Windows PowerShell).

Para ver la sintaxis del cmdlet **Get-PSDrive**, escriba un comando **Get-Command** con el parámetro **Syntax**:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

El parámetro **PSProvider** permite mostrar únicamente las unidades de Windows PowerShell compatibles con un proveedor determinado. Por ejemplo, para mostrar solo las unidades de Windows PowerShell compatibles con el proveedor FileSystem de Windows PowerShell, escriba un comando **Get-PSDrive** con el parámetro **PSProvider** y el valor **FileSystem**:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Para ver las unidades de Windows PowerShell que representan los subárboles del Registro, use el parámetro **PSProvider** para mostrar solo las unidades de Windows PowerShell compatibles con el proveedor de Registro de Windows PowerShell:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

También puede usar los cmdlets Location estándar con las unidades de disco de Windows PowerShell:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Agregar nuevas unidades de Windows PowerShell (New-PSDrive)

Puede usar el comando **New-PSDrive** para agregar sus propias unidades de Windows PowerShell. Para obtener la sintaxis del comando **New-PSDrive**, escriba el comando **Get-Command** con el parámetro **Syntax**:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Para crear una unidad de Windows PowerShell, debe proporcionar tres parámetros:

- Un nombre de unidad (puede usar cualquier nombre válido de Windows PowerShell)

- El PSProvider (use "FileSystem" para las ubicaciones del sistema de archivos y "Registry" para las ubicaciones del Registro)

- La raíz; es decir, la ruta de acceso a la raíz de la nueva unidad

Por ejemplo, puede crear una unidad llamada "Office" que esté asignada a la carpeta que contiene las aplicaciones de Microsoft Office del equipo, como **C:\\Archivos de programa\\Microsoft Office\\OFFICE11**. Para crear la unidad, escriba el siguiente comando:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> Por lo general, las rutas de acceso no distinguen mayúsculas de minúsculas.

La referencia a la nueva unidad de Windows PowerShell se hace como con cualquier otra unidad de Windows PowerShell; es decir, por su nombre seguido de dos puntos (**:**).

Una unidad de Windows PowerShell puede hacer que muchas tareas sean mucho más sencillas de realizar. Por ejemplo, algunas de las claves más importantes en el Registro de Windows tienen rutas de acceso muy largas, lo que las hace complicadas de acceder y difíciles de recordar. La información de configuración crítica reside en **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**. Si quiere ver y cambiar elementos en la clave del Registro CurrentVersion, puede escribir lo siguiente para crear una unidad de Windows PowerShell que se base en esa clave:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

Luego, puede cambiar la ubicación a la unidad **cvkey:**, como lo haría con cualquier otra unidad:``

`PS> cd cvkey:`

o:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

El cmdlet New-PsDrive agrega la nueva unidad solo en la sesión actual de Windows PowerShell. Si cierra la ventana de Windows PowerShell, la nueva unidad se perderá. Para guardar una unidad de Windows PowerShell, use el cmdlet Export-Console para exportar la sesión actual de Windows PowerShell y luego use el parámetro **PSConsoleFile** de PowerShell.exe para importarla. También puede agregar la nueva unidad al perfil de Windows PowerShell.

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Eliminar unidades de Windows PowerShell (Remove-PSDrive)

Puede usar el cmdlet **Remove-PSDrive** para eliminar unidades de Windows PowerShell. El cmdlet **Remove-PSDrive** es fácil de usar. Para eliminar una unidad específica de Windows PowerShell, basta con proporcionar el nombre de dicha unidad.

Por ejemplo, si ha agregado la unidad de Windows PowerShell **Office**, como se indica en el tema sobre **New-PSDrive**, puede eliminarla escribiendo lo siguiente:

```powershell
Remove-PSDrive -Name Office
```

Para eliminar la unidad **cvkey:** de Windows PowerShell, que también se muestra en el tema **New-PSDrive**, use el siguiente comando:

```powershell
Remove-PSDrive -Name cvkey
```

Una unidad de Windows PowerShell es fácil de eliminar, pero esto no podrá llevarlo a cabo mientras se encuentre en la unidad. Por ejemplo:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a>Agregar y quitar unidades fuera de Windows PowerShell

Windows PowerShell detecta las unidades del sistema de archivos que se han agregado o quitado en Windows, incluidas las unidades de red asignadas, las unidades USB conectadas y las unidades que se han eliminado mediante el comando **net use** o los métodos **WScript.NetworkMapNetworkDrive** y **RemoveNetworkDrive** de un script de Windows Script Host (WSH).