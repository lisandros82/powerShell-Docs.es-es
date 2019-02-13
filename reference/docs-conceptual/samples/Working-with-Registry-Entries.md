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
# <a name="working-with-registry-entries"></a>Trabajar con entradas del Registro

Las entradas del Registro son propiedades de claves y, como tales, no se pueden examinar de forma directa, de modo que es preciso adoptar un enfoque ligeramente diferente al trabajar con ellas.

### <a name="listing-registry-entries"></a>Enumerar entradas del Registro

Existen muchas formas de examinar entradas del Registro. La más sencilla consiste en obtener los nombres de propiedad asociados a una clave. Por ejemplo, para ver los nombres de las entradas de la clave del registro `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, utilice `Get-Item`. Las claves del Registro tienen una propiedad con el nombre genérico "Property" que es una lista de entradas del Registro en la clave.
Con el siguiente comando se selecciona la propiedad Property y se expanden los elementos de forma que se muestran en una lista:

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

Para ver las entradas del registro en un formato más legible, use `Get-ItemProperty`:

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

Las propiedades relativas a Windows PowerShell de la clave tienen antepuesto el prefijo "PS", como **PSPath**, **PSParentPath**, **PSChildName** y **PSProvider**.

Puede usar la notación "`*.*`." para hacer referencia a la ubicación actual. Puede usar `Set-Location` para cambiar a la **CurrentVersion** contenedor del registro primera:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Como alternativa, puede usar el elemento integrado HKLM PSDrive con `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

Luego, puede usar la notación "`*.*`." de la ubicación actual para enumerar las propiedades sin especificar una ruta de acceso completa:

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

Expansión de la ruta de acceso funciona igual que lo hace en el sistema de archivos, así que desde esta ubicación se puede obtener el **ItemProperty** lista para `HKLM:\SOFTWARE\Microsoft\Windows\Help` utilizando `Get-ItemProperty -Path ..\Help`.

### <a name="getting-a-single-registry-entry"></a>Obtener una sola entrada del Registro

Si quiere recuperar una entrada específica de una clave del Registro, puede usar uno de los diversos métodos posibles existentes. Este ejemplo busca el valor de **DevicePath** en `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

Mediante `Get-ItemProperty`, utilice el **ruta de acceso** parámetro para especificar el nombre de la clave y el **nombre** parámetro para especificar el nombre de la **DevicePath** entrada.

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

Este comando devuelve las propiedades estándar de Windows PowerShell, así como la propiedad **DevicePath**.

> [!NOTE]
> Aunque `Get-ItemProperty` tiene **filtro**, **Include**, y **excluir** parámetros, no se puede usar para filtrar por nombre de propiedad. Estos parámetros hacen referencia a las claves del registro, que son las rutas de acceso de elemento y no las entradas de registro. Entradas del registro que son propiedades del elemento.

Otra opción sería usar la herramienta de línea de comandos Reg.exe. Para obtener ayuda con reg.exe, escriba `reg.exe /?` en un símbolo del sistema. Para buscar la entrada DevicePath, use reg.exe tal y como se muestra en el siguiente comando:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

También puede usar el objeto **WshShell COM** para encontrar algunas entradas del Registro, aunque este método no funciona con datos binarios de gran tamaño o con nombres de entradas del Registro que contengan caracteres como "\\"). Anexe el nombre de la propiedad a la ruta de acceso de elemento con un separador \\:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a>Configuración de una sola entrada del registro

Si desea cambiar una entrada específica de una clave del registro, puede usar uno de los varios enfoques posibles. En este ejemplo se modifica el **ruta** entrada bajo `HKEY_CURRENT_USER\Environment`. El **ruta** entrada especifica dónde encontrar los archivos ejecutables.

1. Recuperar el valor actual de la **ruta** entrada mediante `Get-ItemProperty`.
2. Agregar el nuevo valor sepárelo con una `;`.
3. Use `Set-ItemProperty` con la clave especificada, el nombre de la entrada y el valor para modificar la entrada del registro.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Aunque `Set-ItemProperty` tiene **filtro**, **Include**, y **excluir** parámetros, no se puede usar para filtrar por nombre de propiedad. Estos parámetros hacen referencia a claves del Registro (que son rutas de acceso de los elementos) y no a entradas del Registro (que son propiedades de los elementos).

Otra opción sería usar la herramienta de línea de comandos Reg.exe. Para obtener ayuda con reg.exe, escriba **reg.exe /?**
en un símbolo del sistema.

El ejemplo siguiente se cambia el **ruta** entrada mediante la eliminación de la ruta de acceso que se agregó en el ejemplo anterior.
`Get-ItemProperty` aún se utiliza para recuperar el valor actual para evitar tener que analizar la cadena devuelta desde `reg query`. El **subcadena** y **LastIndexOf** métodos se usan para recuperar la última ruta de acceso que se agrega a la **ruta** entrada.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a>Crear entradas del Registro

Para agregar una nueva entrada denominada "PowerShellPath" a la **CurrentVersion** el uso de claves, `New-ItemProperty` con la ruta de acceso a la clave, el nombre de la entrada y el valor de la entrada. En este ejemplo, tomaremos el valor de la variable de Windows PowerShell `$PSHome`, que almacena la ruta de acceso al directorio de instalación de Windows PowerShell.

Puede agregar la nueva entrada a la clave usando el siguiente comando; este comando también devolverá información sobre la nueva entrada:

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

**PropertyType** debe ser el nombre de un miembro de la enumeración **Microsoft.Win32.RegistryValueKind** de la siguiente tabla:

|Valor de PropertyType|Significado|
|----------------------|-----------|
|Binary|Datos binarios|
|DWord|Un número que es un UInt32 válido|
|ExpandString|Una cadena que puede contener variables de entorno que se expanden dinámicamente|
|MultiString|Una cadena de varias líneas|
|Cadena|Cualquier valor de cadena|
|QWord|8 bytes de datos binarios|

> [!NOTE]
> Una entrada del Registro se puede agregar a varias ubicaciones si se especifica una matriz de valores para el parámetro **Path**:

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

También se puede sobrescribir un valor de entrada del registro preexistente agregando el **Force** cualquier parámetro `New-ItemProperty` comando.

### <a name="renaming-registry-entries"></a>Cambiar el nombre de entradas del Registro

Para cambiar el nombre de la **PowerShellPath** entrada a "PSHome," use `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Para mostrar el valor cuyo nombre ha cambiado, agregue el parámetro **PassThru** al comando.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Eliminar entradas del Registro

Para eliminar las entradas del registro de la PSHome y PowerShellPath, use `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
