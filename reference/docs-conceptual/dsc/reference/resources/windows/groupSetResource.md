---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
description: Proporciona un mecanismo para administrar grupos locales en el nodo de destino.
title: Recurso GroupSet de DSC
ms.openlocfilehash: d36274741b2c96a0852f384ccf5d187ac8d27131
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953182"
---
# <a name="dsc-groupset-resource"></a>Recurso GroupSet de DSC

> Se aplica a: Windows PowerShell 5.x

El recurso **GroupSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar grupos locales en el nodo de destino. Este es un [recurso compuesto](../../../resources/authoringResourceComposite.md) que llama el [recurso de grupo](groupResource.md) de cada uno de los grupos que se especifican en el parámetro `GroupName`.

Utilice este recurso cuando desee agregar o quitar la misma lista de miembros de más de un grupo, quitar más de un grupo o agregar más de un grupo con la misma lista de miembros.

## <a name="syntax"></a>Sintaxis

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Members = [string[]] ]
    [ Description = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|NombreDeGrupo |Los nombres de los grupos para los que quiere garantizar un estado específico. |
|Miembros |Use esta propiedad para reemplazar la pertenencia al grupo actual con los miembros especificados. El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`. Si establece esta propiedad en una configuración, no use las propiedades **MembersToExclude** ni **MembersToInclude**. Si lo hace, se generará un error. |
|Descripción |La descripción del grupo. |
|MembersToInclude |Use esta propiedad para agregar miembros a la pertenencia existente al grupo. El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`. Si establece esta propiedad en una configuración, no use la propiedad **Members**. Si lo hace, se generará un error. |
|MembersToExclude |Use esta propiedad para quitar a los miembros de la pertenencia existente de los grupos. El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`. Si establece esta propiedad en una configuración, no use la propiedad **Members**. Si lo hace, se generará un error. |
|Credential |Las credenciales necesarias para acceder a los recursos remotos. Esta cuenta debe tener los permisos adecuados de Active Directory para agregar todas las cuentas no locales al grupo; en caso contrario, se producirá un error. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica si existen los grupos. Establezca esta propiedad en **Absent** para asegurarse de que los grupos no existan. Si se establece en **Present**, se garantiza que los grupos existan. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

## <a name="example-1-ensuring-groups-are-present"></a>Ejemplo 1: Cómo asegurarse de que existen grupos

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