---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Usar nombres de comando conocidos
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c5665f64fd832eb9c807f413a8e879f63db7f8c6
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403510"
---
# <a name="using-familiar-command-names"></a>Usar nombres de comando conocidos

PowerShell admite alias para referirse a comandos con nombres alternativos. La creación de alias permite a los usuarios con experiencia en otros shells utilizar los nombres de comandos comunes que ya conocen en operaciones similares en PowerShell.

La creación de alias asocia un nombre nuevo con otro comando. Por ejemplo, PowerShell tiene una función interna denominada `Clear-Host` que borra la ventana de salida. Puede escribir el alias `cls` o `clear` en un símbolo del sistema. PowerShell interpreta estos alias y ejecuta la función `Clear-Host`.

Esta característica ayuda a los usuarios a aprender PowerShell. Primero, la mayoría de los usuarios de **cmd.exe** y Unix tienen un amplio repertorio de comandos que los usuarios ya conocen por su nombre. Los equivalentes de PowerShell pueden no producir resultados idénticos. Sin embargo, los resultados son lo suficientemente cercanos como para que los usuarios puedan trabajar sin conocer el nombre del comando PowerShell. El automatismo es otra fuente importante de frustración cuando se aprende un nuevo shell de comandos. Si ha usado **cmd.exe** durante años, puede escribir de forma refleja el comando `cls` para borrar la pantalla. Sin el alias de `Clear-Host`, recibirá un mensaje de error y no sabrá qué hacer para borrar la salida.

La siguiente lista muestra algunos de los comandos de **cmd.exe** y Unix comunes que puede usar en PowerShell:

|||||
|-|-|-|-|
|cat|dir|montar|rm|
|cd|echo|move|rmdir|
|chdir|erase|popd|sleep|
|clear|h|ps|sort|
|cls|history|pushd|tee|
|copy|kill|pwd|tipo|
|del|lp|r|write|
|diff|ls|ren||

El cmdlet `Get-Alias` muestra el nombre real del comando PowerShell nativo asociado a un alias.

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a>Interpretación de los alias estándar

Los alias que describimos anteriormente fueron diseñados para ser compatibles con los nombres de otros shells de comandos.
La mayoría de los alias integrados en PowerShell están diseñados para ser breves. Los nombres más cortos son más fáciles de escribir, pero son difíciles de leer si no sabe a qué se refieren.

Los alias de PowerShell intentan comprometer la claridad y la brevedad. PowerShell utiliza un conjunto estándar de alias para sustantivos y verbos comunes.

Abreviaturas de ejemplo:

| Sustantivo o verbo | Abreviatura |
|--------------|--------------|
| Get          | g            |
| Establecer          | s            |
| Elemento         | i            |
| Ubicación     | l            |
| Comando      | cm           |
| Alias        | al           |

Estos alias son comprensibles cuando se conocen los nombres abreviados.

| Nombre del cmdlet    | Alias |
|----------------|-------|
| `Get-Item `    | gi    |
| `Set-Item`     | si    |
| `Get-Location` | gl    |
| `Set-Location` | sl    |
| `Get-Command`  | gcm   |
| `Get-Alias`    | gal   |

Cuando ya esté familiarizado con la creación de alias de PowerShell, es fácil adivinar que el alias **sal** se refiere a `Set-Alias`.

## <a name="creating-new-aliases"></a>Creación de nuevos alias

Con el cmdlet `Set-Alias` puede crear sus propios alias. Por ejemplo, las siguientes instrucciones crean los alias de cmdlet estándar que se describen anteriormente:

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

Internamente, PowerShell usa comandos similares durante el inicio, pero estos alias no se pueden cambiar.
Si intenta ejecutar realmente uno de estos comandos, obtiene un error que indica que no se puede modificar el alias. Por ejemplo:

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```