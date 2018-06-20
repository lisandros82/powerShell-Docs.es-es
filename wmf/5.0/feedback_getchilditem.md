---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221908"
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
