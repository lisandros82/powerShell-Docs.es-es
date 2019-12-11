---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Flujo de información
ms.openlocfilehash: c54603cf0dd4f0b69f8147620130f9f29bc3e5ec
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147615"
---
# <a name="information-stream"></a>Flujo de información

PowerShell 5.0 agrega un nuevo flujo de **información** estructurado para transmitir datos estructurados entre un script y su host. `Write-Host` también se actualizó para emitir su salida en el flujo de **información**, donde ahora se puede capturar o silenciar. El nuevo cmdlet `Write-Information` usado con los parámetros comunes **InformationVariable** y **InformationAction** permiten más flexibilidad y funcionalidad.

La función siguiente usa cmdlets que aprovechan el nuevo flujo de **información**.

```powershell
function OutputGusher {
  [CmdletBinding()]
  param()
  Write-Host -ForegroundColor Green 'Preparing to give you output!'
  Write-Host '============================='
  Write-Host 'I ' -ForegroundColor White -NoNewline
  Write-Host '<3 ' -ForegroundColor Red -NoNewline
  Write-Host 'Output' -ForegroundColor White
  Write-Host '============================='

  $p = Get-Process -id $pid
  $p

  Write-Information $p -Tag Process
  Write-Information 'Some spammy logging information' -Tag LogLow
  Write-Information 'Some important logging information' -Tag LogHigh

  Write-Host
  Write-Host -ForegroundColor Green 'SCRIPT COMPLETE!!'
}
```

En los ejemplos se muestran los resultados de la ejecución de esta función.

```powershell
$r = c:\temp\OutputGusher
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================

SCRIPT COMPLETE!!
```

La variable `$r` ha capturado la información del proceso en la variable de script `$p`.

```powershell
$r.Id
4008
```

A diferencia del cmdlet `Write-Host`, usar el parámetro **InformationVariable** de `Write-Information` le permite capturar la salida en una variable. Con la **etiqueta**, puede crear canales independientes para el mensaje enviado al flujo de **información**.

```powershell
$r = OutputGusher -InformationVariable iv
$ivOutput = $iv | Group-Object -AsHash { $_.Tags[0] } -AsString
$ivOutput
```

```Output
Preparing to give you output!
=============================
I <3 Output
=============================
SCRIPT COMPLETE!!

Name                 Value
----                 -----
LogLow               {Some spammy logging information}
LogHigh              {Some important logging information}
Process              {System.Diagnostics.Process (powershell)}
PSHOST               {Preparing to give you output!, =============================, I , <3 ...}
```

Cuando envía un mensaje al flujo de **información** con una etiqueta, ese mensaje no se muestra en la aplicación host, pero se puede recuperar con el nombre de la etiqueta. Por ejemplo:

```powershell
$iv | where Tags -eq 'LogHigh'
```

```Output
Some important logging information
```