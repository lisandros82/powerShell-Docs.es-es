---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Seleccionar partes de objetos Select Object
ms.technology: powershell
ms.assetid: 72e64b1a-d351-4500-9da3-24d8a71d7a92
ms.openlocfilehash: 5e0ca5110d7e35e49da3db779d9d495ea6b78e67
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
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

