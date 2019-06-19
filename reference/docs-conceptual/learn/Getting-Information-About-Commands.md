---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Obtener información sobre los comandos
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030945"
---
# <a name="getting-information-about-commands"></a>Obtener información sobre los comandos

El `Get-Command` de PowerShell muestra los comandos que están disponibles en la sesión actual.
Cuando ejecute el cmdlet `Get-Command`, verá algo similar a la siguiente salida:

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

Esta salida se parece mucho a la salida de la Ayuda de **cmd.exe**: es un resumen tabular de comandos internos. En el extracto de la salida del comando `Get-Command` mostrado anteriormente, cada comando muestra una sección CommandType de Cmdlet. Un cmdlet es el tipo de comando intrínseco de PowerShell. Este tipo corresponde aproximadamente a comandos como `dir` y `cd` en **cmd.exe** o a los comandos integrados de shells Unix como bash.

El cmdlet `Get-Command` tiene un parámetro **Syntax** que devuelve la sintaxis de cada cmdlet. El siguiente ejemplo muestra cómo obtener la sintaxis del cmdlet `Get-Help`:

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>Visualización de los comandos disponibles por tipo

El comando `Get-Command` enumera únicamente los cmdlets de la sesión actual. En realidad, PowerShell admite otros muchos tipos de comandos:

- Alias
- Funciones
- Scripts

Los archivos externos ejecutables o los que tienen un controlador de tipo de archivo registrado también se clasifican como comandos.

Para obtener todos los comandos de la sesión, escriba:

```powershell
Get-Command *
```

Esta lista incluye los comandos externos de su ruta de búsqueda, para que pueda contener miles de elementos.
Es más útil buscar en un conjunto reducido de comandos.

> [!NOTE]
> El asterisco (\*) sirve de comodín para hallar coincidencias en los argumentos de comando de PowerShell. El carácter \* quiere decir "coincide con uno o varios caracteres". Así, puede escribir `Get-Command a*` para encontrar todos los comandos que comienzan por la letra "a". A diferencia de las búsquedas con comodín en **cmd.exe**, los comodines de PowerShell también encontrarán coincidencias de período.

Use el parámetro **CommandType** de `Get-Command` para obtener los comandos nativos de otros tipos.
cmdlet.

Para obtener los alias de comandos (que son los sobrenombres asignados de los comandos), escriba:

```powershell
Get-Command -CommandType Alias
```

Para obtener las funciones en la sesión actual, escriba:

```powershell
Get-Command -CommandType Function
```

Para mostrar los scripts en la ruta de búsqueda de PowerShell, escriba:

```powershell
Get-Command -CommandType Script
```
