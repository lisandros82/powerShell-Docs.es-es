---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Seleccionar partes de objetos Select Object
ms.openlocfilehash: 4d4c89f0b5103e4701a3af3cd07fcd7c8f1c697f
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030106"
---
# <a name="selecting-parts-of-objects-select-object"></a>Seleccionar partes de objetos (Select-Object)

Puede usar el cmdlet **Select-Object** para crear nuevos objetos de Windows PowerShell personalizados que contengan las propiedades seleccionadas de los objetos que use para crearlos. Escriba el siguiente comando para crear un nuevo objeto que incluya solamente las propiedades Name y FreeSpace de la clase WMI Win32_LogicalDisk:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace

Name                                    FreeSpace
----                                    ---------
C:                                      50664845312
```

No puede ver el tipo de datos después de emitir este comando, pero si canaliza la salida para Get-Member después de Select-Object, puede indicar que tiene un nuevo tipo de objeto, PSCustomObject:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace| Get-Member

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       System.Boolean Equals(Object obj)
GetHashCode Method       System.Int32 GetHashCode()
GetType     Method       System.Type GetType()
ToString    Method       System.String ToString()
FreeSpace   NoteProperty  FreeSpace=...
Name        NoteProperty System.String Name=C:
```

Select-Object tiene muchos usos. Uno de ellos es replicar datos que se puedan modificar posteriormente. Ahora podemos gestionar el problema detectado a través de la sección anterior. Podemos actualizar el valor de FreeSpace en nuestros objetos recién creados y la salida incluirá la etiqueta descriptiva:

```
Get-WmiObject -Class Win32_LogicalDisk | Select-Object -Property Name,FreeSpace | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0; $_}
Name                                                                  FreeSpace
----                                                                  ---------
C:                                                                48317.7265625
```
