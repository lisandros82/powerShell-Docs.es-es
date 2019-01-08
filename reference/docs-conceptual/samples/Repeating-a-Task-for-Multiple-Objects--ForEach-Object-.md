---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Repetir una tarea para varios objetos ForEach Object
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 64d85edad4a6931b2376b95b6d1f5b4d5194399f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403337"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="b1aa5-103">Repetir una tarea para varios objetos (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="b1aa5-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="b1aa5-104">El cmdlet **ForEach-Object** usa bloques de script y el descriptor `$_` del objeto de canalización actual para permitir ejecutar un comando en cada objeto de la canalización.</span><span class="sxs-lookup"><span data-stu-id="b1aa5-104">The **ForEach-Object** cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="b1aa5-105">Se puede usar para realizar algunas tareas complejas.</span><span class="sxs-lookup"><span data-stu-id="b1aa5-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="b1aa5-106">Una situación en la que puede resultar útil es la manipulación de datos para mejorar su utilidad.</span><span class="sxs-lookup"><span data-stu-id="b1aa5-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="b1aa5-107">Por ejemplo, la clase Win32_LogicalDisk de WMI puede usarse para devolver información del espacio libre de cada disco local.</span><span class="sxs-lookup"><span data-stu-id="b1aa5-107">For example, the Win32_LogicalDisk class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="b1aa5-108">Los datos se devuelven en bytes, lo que dificulta su lectura:</span><span class="sxs-lookup"><span data-stu-id="b1aa5-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

<span data-ttu-id="b1aa5-109">Podemos convertir el valor FreeSpace a megabytes dividiendo cada valor por 1024 dos veces; después de la primera división, los datos están en kilobytes y tras la segunda, en megabytes.</span><span class="sxs-lookup"><span data-stu-id="b1aa5-109">We can convert the FreeSpace value to megabytes by dividing each value by 1024 twice; after the first division, the data is in kilobytes, and after the second division it is megabytes.</span></span> <span data-ttu-id="b1aa5-110">Para realizar este paso en un bloque de script ForEach-Object, escriba lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="b1aa5-110">You can do that in a ForEach-Object script block by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

<span data-ttu-id="b1aa5-111">Desafortunadamente, la salida actual consta de datos sin una etiqueta asociada.</span><span class="sxs-lookup"><span data-stu-id="b1aa5-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="b1aa5-112">Dado que las propiedades de WMI como esta son de solo lectura, no se puede convertir directamente el valor de FreeSpace.</span><span class="sxs-lookup"><span data-stu-id="b1aa5-112">Because WMI properties such as this are read-only, you cannot directly convert FreeSpace.</span></span> <span data-ttu-id="b1aa5-113">Si escribe esto:</span><span class="sxs-lookup"><span data-stu-id="b1aa5-113">If you type this:</span></span>

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="b1aa5-114">Obtiene un mensaje de error:</span><span class="sxs-lookup"><span data-stu-id="b1aa5-114">You get an error message:</span></span>

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

<span data-ttu-id="b1aa5-115">Puede reorganizar los datos mediante algunas técnicas avanzadas, pero un enfoque más sencillo es crear un nuevo objeto con **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="b1aa5-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using **Select-Object**.</span></span>