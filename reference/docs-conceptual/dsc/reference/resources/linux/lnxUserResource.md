---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso nxUser de DSC para Linux
ms.openlocfilehash: 6d7b52809741813af7fa80b1c6372b267aff4777
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954802"
---
# <a name="dsc-for-linux-nxuser-resource"></a>Recurso nxUser de DSC para Linux

El recurso **nxUser** de Desired State Configuration (DSC) de PowerShell ofrece un mecanismo para administrar usuarios locales en un nodo de Linux.

## <a name="syntax"></a>Sintaxis

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Indica el nombre de la cuenta para la que quiere garantizar un estado específico. |
|---|---|
|UserName |Especifica la ubicación donde desea garantizar el estado de un archivo o directorio. |
|FullName |Una cadena que contiene el nombre completo que se usará para la cuenta de usuario. |
|Descripción |La descripción de la cuenta de usuario. |
|Contraseña |El hash de la contraseña de los usuarios en el formato adecuado para el equipo Linux. Normalmente, es un hash SHA-512 o SHA-256 con sal. En Debian y Ubuntu Linux, este valor se puede generar con el comando `mkpasswd`. Para otras distribuciones de Linux, puede utilizarse el método de cifrado de la biblioteca de cifrado de Python para generar el hash. |
|Deshabilitada |Indica si la cuenta se encuentra habilitada. Establezca esta propiedad en `$true` para asegurarse de que esta cuenta esté deshabilitada y establézcala como `$false` para asegurarse de que esté habilitada. |
|PasswordChangeRequired |Indica si el usuario puede cambiar la contraseña. Establezca esta propiedad en `$true` para asegurarse de que el usuario no pueda cambiar la contraseña y establézcala como `$false` para permitir al usuario cambiar la contraseña. El valor predeterminado es `$false`. Esta propiedad solo se evalúa si la cuenta de usuario no existía anteriormente y se está creando. |
|HomeDirectory |El directorio principal del usuario. |
|GroupID |El identificador de grupo principal del usuario. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Especifica si la cuenta existe. Establezca esta propiedad en **Present** para asegurarse de que la cuenta exista y establézcala como **Absent** para asegurarse de que la cuenta no exista. |

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se asegura de que el usuario "monuser" exista y de que sea un miembro del grupo "DBusers".

```powershell
Import-DSCResource -Module nx

Node $node
{
   nxUser UserExample{
      UserName = "monuser"
      Description = "Monitoring user"
      Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
      Ensure = "Present"
      HomeDirectory = "/home/monuser"
   }

   nxGroup GroupExample{
      GroupName = "DBusers"
      Ensure = "Present"
      MembersToInclude = "monuser"
      DependsOn = "[nxUser]UserExample"
   }
}
```