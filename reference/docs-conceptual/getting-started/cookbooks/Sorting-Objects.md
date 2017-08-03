---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Ordenar objetos
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 2df45c64656e74dc8b72957ce59f2a5e5ee663b6
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="sorting-objects"></a>Ordenar objetos
Podemos organizar los datos mostrados para examinarlos más fácilmente mediante el cmdlet **Sort-Object**. **Sort-Object** toma el nombre de una o varias propiedades para la ordenación, y devuelve los datos ordenados por los valores de esas propiedades.

Considere el problema de enumerar instancias de Win32_SystemDriver. Si queremos ordenar por **State** y luego por **Name**, podemos escribir lo siguiente para hacerlo:

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Aunque se trata de una presentación larga, puede ver los elementos con el mismo estado agrupados:

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

También puede ordenar los objetos en orden inverso especificando el parámetro **Descending**. Se invierte el criterio de ordenación para que los nombres se ordenen en orden alfabético inverso y los números se ordenen en orden descendente por su tamaño.

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```

