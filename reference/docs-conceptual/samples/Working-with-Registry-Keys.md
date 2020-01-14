---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Trabajar con claves del Registro
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736852"
---
# <a name="working-with-registry-keys"></a>Trabajar con claves del Registro

Dado que las claves del Registro son elementos en unidades de PowerShell, trabajar con ellas es muy similar a trabajar con archivos y carpetas. Una diferencia fundamental es que todos los elementos en una unidad de PowerShell basada en el Registro es un contenedor, como una carpeta en una unidad del sistema de archivos. Sin embargo, las entradas del Registro y sus valores asociados son propiedades de los elementos, no elementos distintos.

## <a name="listing-all-subkeys-of-a-registry-key"></a>Enumerar a todas las subclaves de una clave del Registro

Puede mostrar todos los elementos directamente dentro de una clave del Registro, para lo que debe usar `Get-ChildItem`. Agregue el parámetro **Force** opcional para mostrar elementos ocultos o del sistema. Por ejemplo, este comando muestra los elementos directamente en la unidad `HKCU:` de PowerShell que se corresponde con el subárbol `HKEY_CURRENT_USER` del Registro:

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

Estas son las claves de nivel superior visibles en `HKEY_CURRENT_USER` en el Editor del Registro (Regedit.exe).

Para especificar esta ruta de acceso del Registro también puede especificar el nombre del proveedor del Registro, seguido de `::`. El nombre completo del proveedor del registro es `Microsoft.PowerShell.Core\Registry`, pero se puede acortar a simplemente `Registry`. Cualquiera de los siguientes comandos enumerará el contenido directamente en `HKCU:`.

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Estos comandos muestran solo los elementos contenidos directamente, lo que se parece a usar `DIR` en **Cmd.exe** o `ls` en un shell de UNIX. Para mostrar los elementos contenidos, debe especificar el parámetro **Recurse**. Para enumerar todas las claves del Registro en `HKCU:`, use el comando siguiente.

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

`Get-ChildItem` puede realizar funcionalidades de filtrado complejas a través de sus parámetros **Path**, **Filter**, **Include** y **Exclude**, pero dichos parámetros suelen basarse solo en el nombre. Con el cmdlet `Where-Object` puede realizar un filtrado complejo basado en otras propiedades de los elementos. El siguiente comando busca en `HKCU:\Software` todas las claves que no tengan más de una subclave y que tengan exactamente cuatro valores:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a>Copiar claves

La copia se realiza con `Copy-Item`. En el ejemplo siguiente se copia la subclave `CurrentVersion` de `HKLM:\SOFTWARE\Microsoft\Windows\` y todas sus propiedades en `HKCU:\`.

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

Si examina esta nueva clave en el Editor del Registro o mediante `Get-ChildItem`, observará que no tiene copias de las subclaves contenidas en la nueva ubicación. Para copiar todo el contenido de un contenedor, debe especificar el parámetro **Recurse**. Para hacer que el comando de copia anterior sea recursivo, debe usar este comando:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

Puede seguir usando otras herramientas que tiene a su disposición para realizar copias del sistema de archivos. Todas las herramientas de edición del Registro, incluidas **reg.exe**, **regini.exe**, **regedit.exe** y los objetos COM que admiten la edición del Registro, como **WScript.Shell** y la clase **StdRegProv** de WMI, puede usarse desde Windows PowerShell.

## <a name="creating-keys"></a>Crear claves

Crear nuevas claves en el Registro es más sencillo que crear un nuevo elemento en un sistema de archivos. Dado que todas las claves del Registro son contenedores, no es necesario especificar el tipo de elemento; solo tiene que proporcionar una ruta de acceso explícita, como:

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

También puede usar una ruta de acceso basada en el proveedor para especificar una clave:

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a>Eliminar claves

El proceso de eliminación de elementos es básicamente igual para todos los proveedores. Los siguientes comandos quitarán elementos de forma automática:

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a>Quitar todas las claves bajo una clave específica

Los elementos contenidos se pueden quitar mediante `Remove-Item`, pero se pedirá que se confirme la eliminación si el elemento contiene algo más. Por ejemplo, si se intenta eliminar la subclave `HKCU:\CurrentVersion` creada, se muestra lo siguiente:

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Para eliminar los elementos contenidos sin preguntar, especifique el parámetro **Recurse**:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Si quiere quitar todos los elementos de `HKCU:\CurrentVersion`, pero no del `HKCU:\CurrentVersion` mismo, podría usar en su lugar:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
