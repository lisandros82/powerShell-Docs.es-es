---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="get-childitem-has--depth-parameter"></a>Get-ChildItem tiene el parámetro -Depth
**Get-ChildItem** tiene ahora un parámetro **–Depth** que se usa con **–Recurse** para limitar la recursividad:

PS C:\\Usuarios\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0

Directorio: C:\\Usuarios\\slee\\Downloads\\Example

Nombre Hora de última escritura Longitud Nombre

---- ------------- ------ ----

d----- 4/14/2015 5:36 PM Depth0

-a---- 4/14/2015 1:19 PM 0 File1.txt

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

PS C:\\Usuarios\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1

Directorio: C:\\Usuarios\\slee\\Downloads\\Example

Nombre Hora de última escritura Longitud Nombre

---- ------------- ------ ----

d----- 4/14/2015 5:36 PM Depth0

-a---- 4/14/2015 1:19 PM 0 File1.txt

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

Directorio: C:\\Usuarios\\slee\\Downloads\\Example\\Depth0

Nombre Hora de última escritura Longitud Nombre

---- ------------- ------ ----

d----- 4/14/2015 5:33 PM Depth1

