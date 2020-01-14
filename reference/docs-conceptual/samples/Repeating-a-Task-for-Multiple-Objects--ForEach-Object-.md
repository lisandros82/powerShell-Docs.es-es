---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Repetir una tarea para varios objetos ForEach Object
ms.openlocfilehash: bf89070fd9b006fa9b0b262ab63ffadd81072ecc
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736886"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a><span data-ttu-id="7953e-103">Repetir una tarea para varios objetos (ForEach-Object)</span><span class="sxs-lookup"><span data-stu-id="7953e-103">Repeating a Task for Multiple Objects (ForEach-Object)</span></span>

<span data-ttu-id="7953e-104">El cmdlet `ForEach-Object` usa bloques de script y el descriptor `$_` del objeto de canalización actual para permitir ejecutar un comando en cada objeto de la canalización.</span><span class="sxs-lookup"><span data-stu-id="7953e-104">The `ForEach-Object` cmdlet uses script blocks and the `$_` descriptor for the current pipeline object to let you run a command on each object in the pipeline.</span></span> <span data-ttu-id="7953e-105">Se puede usar para realizar algunas tareas complejas.</span><span class="sxs-lookup"><span data-stu-id="7953e-105">This can be used to perform some complicated tasks.</span></span>

<span data-ttu-id="7953e-106">Una situación en la que puede resultar útil es la manipulación de datos para mejorar su utilidad.</span><span class="sxs-lookup"><span data-stu-id="7953e-106">One situation where this can be useful is manipulating data to make it more useful.</span></span> <span data-ttu-id="7953e-107">Por ejemplo, la clase **Win32_LogicalDisk** de WMI puede usarse para devolver información del espacio libre de cada disco local.</span><span class="sxs-lookup"><span data-stu-id="7953e-107">For example, the **Win32_LogicalDisk** class from WMI can be used to return free space information for each local disk.</span></span> <span data-ttu-id="7953e-108">Los datos se devuelven en bytes, lo que dificulta su lectura:</span><span class="sxs-lookup"><span data-stu-id="7953e-108">The data is returned in terms of bytes, however, which makes it difficult to read:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

<span data-ttu-id="7953e-109">Podemos convertir el valor de **FreeSpace** en megabytes dividiendo cada valor por 1 MB.</span><span class="sxs-lookup"><span data-stu-id="7953e-109">We can convert the **FreeSpace** value to megabytes by dividing each value by 1MB.</span></span> <span data-ttu-id="7953e-110">Puede hacerlo en un bloque de script de `ForEach-Object` escribiendo:</span><span class="sxs-lookup"><span data-stu-id="7953e-110">You can do that in a `ForEach-Object` script block by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

<span data-ttu-id="7953e-111">Desafortunadamente, la salida actual consta de datos sin una etiqueta asociada.</span><span class="sxs-lookup"><span data-stu-id="7953e-111">Unfortunately, the output is now data with no associated label.</span></span> <span data-ttu-id="7953e-112">Dado que las propiedades de WMI como esta son de solo lectura, no se puede convertir directamente el valor de **FreeSpace**.</span><span class="sxs-lookup"><span data-stu-id="7953e-112">Because WMI properties such as this are read-only, you cannot directly convert **FreeSpace**.</span></span> <span data-ttu-id="7953e-113">Si escribe esto:</span><span class="sxs-lookup"><span data-stu-id="7953e-113">If you type this:</span></span>

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

<span data-ttu-id="7953e-114">Obtiene un mensaje de error:</span><span class="sxs-lookup"><span data-stu-id="7953e-114">You get an error message:</span></span>

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

<span data-ttu-id="7953e-115">Puede reorganizar los datos mediante algunas técnicas avanzadas, pero un enfoque más simple es crear un objeto con `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="7953e-115">You could reorganize the data by using some advanced techniques, but a simpler approach is to create a new object, by using `Select-Object`.</span></span>
