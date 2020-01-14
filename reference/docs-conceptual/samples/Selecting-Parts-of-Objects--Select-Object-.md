---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Seleccionar partes de objetos Select Object
ms.openlocfilehash: 06b92c7c4c5098c707a7d9f9d9a96e6b6a897f80
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737175"
---
# <a name="selecting-parts-of-objects-select-object"></a>Seleccionar partes de objetos (Select-Object)

Puede usar el cmdlet `Select-Object` para crear objetos de PowerShell personalizados que contengan las propiedades seleccionadas de los objetos que usa para crearlos. Escriba el siguiente comando para crear un nuevo objeto que incluya solamente las propiedades **Name** y **FreeSpace** de la clase **Win32_LogicalDisk** de WMI:

```powershell
Get-CimInstance -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace
```

```Output
Name      FreeSpace
----      ---------
C:      50664845312
```

Con `Select-Object`, puede crear propiedades calculadas. Por lo tanto, puede mostrar **FreeSpace** en gigabytes en lugar de en bytes.

```powershell
Get-CimInstance -Class Win32_LogicalDisk |
  Select-Object -Property Name, @{
    label='FreeSpace'
    expression={($_.FreeSpace/1GB).ToString('F2')}
  }
```

```Output
Name    FreeSpace
----    ---------
C:      47.18
```
