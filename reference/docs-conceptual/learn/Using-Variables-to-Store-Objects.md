---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Usar variables para almacenar objetos
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030376"
---
# <a name="using-variables-to-store-objects"></a>Usar variables para almacenar objetos

PowerShell funciona con objetos. PowerShell le permite crear objetos con nombre conocidos como variables.
Los nombres de variables pueden incluir el carácter de subrayado y cualquier carácter alfanumérico. Cuando se utiliza en PowerShell, siempre se especifica una variable utilizando el carácter \$ seguido del nombre de la variable.

## <a name="creating-a-variable"></a>Creación de una variable

Para crear una variable, puede escribir un nombre de variable válido:

```
PS> $loc
PS>
```

Este ejemplo no devuelve ningún resultado porque `$loc` no tiene un valor. Puede crear una variable y asignarle un valor en el mismo paso. PowerShell solo crea la variable si no existe.
De lo contrario, asigna el valor especificado a la variable existente. En el ejemplo siguiente se almacena la ubicación actual en la variable `$loc`:

```powershell
$loc = Get-Location
```

PowerShell no muestra ninguna salida cuando se escribe este comando. PowerShell envía la salida de "Get-Location" a `$loc`. En PowerShell, los datos que no están asignados o redirigidos se envían a la pantalla. Si se escribe `$loc`, se muestra la ubicación actual:

```
PS> $loc

Path
----
C:\temp
```

Puede usar `Get-Member` para mostrar información sobre el contenido de las variables. `Get-Member` muestra que `$loc` es un objeto **PathInfo**, al igual que la salida de `Get-Location`:

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>Manipulación de variables

PowerShell proporciona varios comandos para manipular variables. Para ver una lista completa en un formato legible, escriba:

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

PowerShell también crea varias variables definidas por el sistema. Puede usar el cmdlet `Remove-Variable` para quitar variables, que no se controlan mediante PowerShell, de la sesión actual. Escriba el siguiente comando para borrar todas las variables:

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Después de ejecutar el comando anterior, el cmdlet `Get-Variable` muestra las variables del sistema de PowerShell.

PowerShell también crea una unidad variable. Use el siguiente ejemplo para mostrar todas las variables de PowerShell mediante la unidad variable:

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>Uso de variables de Cmd.exe

PowerShell puede usar las mismas variables de entorno disponibles para cualquier proceso de Windows, incluido **cmd.exe**. Estas variables se exponen a través de una unidad denominada `env:`. Para ver estas variables, escriba el comando siguiente:

```powershell
Get-ChildItem env:
```

Los cmdlet `*-Variable` estándar no están diseñados para trabajar con variables de entorno. Las variables de entorno son accesibles mediante el prefijo de unidad `env:`. Por ejemplo, la variable **%SystemRoot%** de **cmd.exe** contiene el nombre del directorio raíz del sistema operativo. En PowerShell, se utiliza `$env:SystemRoot` para acceder al mismo valor.

```
PS> $env:SystemRoot
C:\WINDOWS
```

También puede crear y modificar variables de entorno desde PowerShell. Las variables de entorno de PowerShell siguen las mismas reglas para las variables de entorno que se utilizan en cualquier otra parte del sistema operativo. En el ejemplo siguiente se crea una nueva variable de entorno:

```powershell
$env:LIB_PATH='/usr/local/lib'
```

Aunque no es obligatorio, es común que los nombres de variables de entorno utilicen todas las letras mayúsculas.
