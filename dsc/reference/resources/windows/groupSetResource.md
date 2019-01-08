---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
description: Proporciona un mecanismo para administrar grupos locales en el nodo de destino.
title: Recurso GroupSet de DSC
ms.openlocfilehash: afe4c4d33ac5620c411481e93d76a1f90c26deb9
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048046"
---
# <a name="dsc-groupset-resource"></a>Recurso GroupSet de DSC

> Se aplica a: Windows PowerShell 5.0

El recurso **GroupSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar grupos locales en el nodo de destino. Este es un [recurso compuesto](../../../resources/authoringResourceComposite.md) que llama el [recurso de grupo](groupResource.md) de cada uno de los grupos que se especifican en el parámetro `GroupName`.

Utilice este recurso cuando desee agregar o quitar la misma lista de miembros de más de un grupo, quitar más de un grupo o agregar más de un grupo con la misma lista de miembros.

## <a name="syntax"></a>Sintaxis

```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   |
|---|---|
| NombreDeGrupo| Los nombres de los grupos para los que quiere garantizar un estado específico.|
| MembersToExclude| Use esta propiedad para quitar a los miembros de la pertenencia existente de los grupos. El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*. Si establece esta propiedad en una configuración, no use la propiedad **Members**. Si lo hace, se generará un error.|
| Credential| Las credenciales necesarias para acceder a los recursos remotos. **Nota**: Esta cuenta debe tener los permisos adecuados de Active Directory para agregar todas las cuentas no locales al grupo; en caso contrario, se producirá un error.
| Ensure| Indica si existen los grupos. Establezca esta propiedad en "Absent" para asegurarse de que los grupos no existan. Si se establece en "Present" (el valor predeterminado), se garantiza que los grupos existan.|
| Miembros| Use esta propiedad para reemplazar la pertenencia al grupo actual con los miembros especificados. El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*. Si establece esta propiedad en una configuración, no use las propiedades **MembersToExclude** ni **MembersToInclude**. Si lo hace, se generará un error.|
| MembersToInclude| Use esta propiedad para agregar miembros a la pertenencia existente al grupo. El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*. Si establece esta propiedad en una configuración, no use la propiedad **Members**. Si lo hace, se generará un error.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"``.|

## <a name="example-1-ensuring-groups-are-present"></a>Ejemplo 1: Grupos de seguridad de que están presentes

En el ejemplo siguiente se muestra cómo asegurarse de que existen dos grupos denominados "myGroup" y "myOtherGroup".

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}

GroupSetTest -ConfigurationData $cd
```

> [!NOTE]
> En este ejemplo se usan las credenciales de texto sin formato por su sencillez. Para más información sobre el cifrado de credenciales en el archivo MOF de configuración, consulte [Proteger el archivo MOF](../../../pull-server/secureMOF.md).
