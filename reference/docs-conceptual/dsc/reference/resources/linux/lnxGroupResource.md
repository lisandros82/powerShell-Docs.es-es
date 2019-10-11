---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso nxGroup de DSC para Linux
ms.openlocfilehash: 098ae2e8ab183934ec3c185c0fd237731b1353dc
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953212"
---
# <a name="dsc-for-linux-nxgroup-resource"></a>Recurso nxGroup de DSC para Linux

El recurso **nxGroup** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar grupos locales en un nodo de Linux.

## <a name="syntax"></a>Sintaxis

```Syntax
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ PreferredGroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present } ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|NombreDeGrupo |Especifica el nombre del grupo para el que quiere garantizar un estado específico. |
|Miembros |Especifica a los miembros que forman el grupo. |
|MembersToInclude |Especifica los usuarios que quiera garantizar que sean miembros del grupo. |
|MembersToExclude |Especifica los usuarios que quiera garantizar que no sean miembros del grupo. |
|PreferredGroupID |Establece el identificador de grupo en el valor proporcionado, si es posible. Si el identificador de grupo está actualmente en uso, se utiliza el siguiente identificador de grupo disponible. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina si se debe comprobar si existe el grupo. Establezca esta propiedad en **Present** para asegurarse de que el grupo exista. Establézcala en **Absent** para asegurarse de que el grupo no exista. El valor predeterminado es **Present**. |

## <a name="example"></a>Ejemplo

El ejemplo siguiente se asegura de que el usuario "monuser" exista y de que sea un miembro del grupo "DBusers".

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```