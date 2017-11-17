---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Ordenar objetos
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 2df45c64656e74dc8b72957ce59f2a5e5ee663b6
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2017
---
# <a name="sorting-objects"></a><span data-ttu-id="3b2f0-103">Ordenar objetos</span><span class="sxs-lookup"><span data-stu-id="3b2f0-103">Sorting Objects</span></span>
<span data-ttu-id="3b2f0-104">Podemos organizar los datos mostrados para examinarlos más fácilmente mediante el cmdlet **Sort-Object**.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-104">We can organize displayed data to make it easier to scan by using the **Sort-Object** cmdlet.</span></span> <span data-ttu-id="3b2f0-105">**Sort-Object** toma el nombre de una o varias propiedades para la ordenación, y devuelve los datos ordenados por los valores de esas propiedades.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-105">**Sort-Object** takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

<span data-ttu-id="3b2f0-106">Considere el problema de enumerar instancias de Win32_SystemDriver.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-106">Consider the problem of listing Win32_SystemDriver instances.</span></span> <span data-ttu-id="3b2f0-107">Si queremos ordenar por **State** y luego por **Name**, podemos escribir lo siguiente para hacerlo:</span><span class="sxs-lookup"><span data-stu-id="3b2f0-107">If we want to sort by **State** and then by **Name**, we can do it by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

<span data-ttu-id="3b2f0-108">Aunque se trata de una presentación larga, puede ver los elementos con el mismo estado agrupados:</span><span class="sxs-lookup"><span data-stu-id="3b2f0-108">Although this is a lengthy display, you can see items with the same state grouped together:</span></span>

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

<span data-ttu-id="3b2f0-109">También puede ordenar los objetos en orden inverso especificando el parámetro **Descending**.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-109">You can also sort the objects in reverse order by specifying the **Descending** parameter.</span></span> <span data-ttu-id="3b2f0-110">Se invierte el criterio de ordenación para que los nombres se ordenen en orden alfabético inverso y los números se ordenen en orden descendente por su tamaño.</span><span class="sxs-lookup"><span data-stu-id="3b2f0-110">This reverses the sort order so that names are sorted in reverse alphabetical order and numbers are sorted by descending size.</span></span>

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

