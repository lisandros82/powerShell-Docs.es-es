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
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Repetir una tarea para varios objetos (ForEach-Object)

El cmdlet `ForEach-Object` usa bloques de script y el descriptor `$_` del objeto de canalización actual para permitir ejecutar un comando en cada objeto de la canalización. Se puede usar para realizar algunas tareas complejas.

Una situación en la que puede resultar útil es la manipulación de datos para mejorar su utilidad. Por ejemplo, la clase **Win32_LogicalDisk** de WMI puede usarse para devolver información del espacio libre de cada disco local. Los datos se devuelven en bytes, lo que dificulta su lectura:

```powershell
Get-CimInstance -Class Win32_LogicalDisk
```

```Output
DeviceID DriveType ProviderName VolumeName Size          FreeSpace
-------- --------- ------------ ---------- ----          ---------
C:       3                      Local Disk 203912880128  50665070592
```

Podemos convertir el valor de **FreeSpace** en megabytes dividiendo cada valor por 1 MB. Puede hacerlo en un bloque de script de `ForEach-Object` escribiendo:

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {($_.FreeSpace)/1MB}
```

```Output
48318.01171875
```

Desafortunadamente, la salida actual consta de datos sin una etiqueta asociada. Dado que las propiedades de WMI como esta son de solo lectura, no se puede convertir directamente el valor de **FreeSpace**. Si escribe esto:

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
```

Obtiene un mensaje de error:

```Output
"FreeSpace" is a ReadOnly property.
At line:2 char:28
+   ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1MB}
+                            ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : NotSpecified: (:) [], SetValueException
+ FullyQualifiedErrorId : ReadOnlyCIMProperty
```

Puede reorganizar los datos mediante algunas técnicas avanzadas, pero un enfoque más simple es crear un objeto con `Select-Object`.
