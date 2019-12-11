---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Group
ms.openlocfilehash: 695a914683c6daff44dd2a6c94b6353acf881030
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954662"
---
# <a name="dsc-group-resource"></a>Recurso de DSC Group

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso **Group** de Desired State Configuration (DSC) de Windows PowerShell ofrece un mecanismo para administrar grupos locales en el nodo de destino.

## <a name="syntax"></a>Sintaxis

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|NombreDeGrupo |El nombre del grupo para el que quiere garantizar un estado específico. |
|Credential |Las credenciales necesarias para acceder a los recursos remotos. Esta cuenta debe tener los permisos adecuados de Active Directory para agregar todas las cuentas no locales al grupo; en caso contrario, se producirá un error al ejecutar la configuración en el nodo de destino.
|Descripción |La descripción del grupo. |
|Miembros |Use esta propiedad para reemplazar la pertenencia al grupo actual con los miembros especificados. El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`. Si establece esta propiedad en una configuración, no use las propiedades **MembersToExclude** ni **MembersToInclude**. Si lo hace, se generará un error. |
|MembersToExclude |Use esta propiedad para quitar a los miembros de la pertenencia existente del grupo. El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`. Si establece esta propiedad en una configuración, no use la propiedad **Members**. Si lo hace, se generará un error. |
|MembersToInclude |Use esta propiedad para agregar miembros a la pertenencia existente al grupo. El valor de esta propiedad es una matriz de cadenas del formulario `Domain\UserName`. Si establece esta propiedad en una configuración, no use la propiedad **Members**. Si lo hace, se generará un error. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica si existe el grupo. Establezca esta propiedad en **Absent** para asegurarse de que el grupo no exista. Si se establece en **Present**, se garantiza que el grupo exista. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

## <a name="example-1-ensure-group-is-not-present"></a>Ejemplo 1: Asegurarse de que el grupo no está presente

En el ejemplo siguiente se muestra cómo asegurarse de que no existe un grupo denominado "TestGroup".

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a>Ejemplo 2: Agregar un usuario de dominio a un grupo local

En el ejemplo siguiente se muestra cómo agregar un usuario de Active Directory al grupo de administradores local como parte de una compilación de prácticas en varias máquinas que ya usan un PSCredential para la cuenta de administrador local. Puesto que también se usa para la cuenta de administrador del dominio (después de la promoción del dominio), necesitamos convertir este PSCredential existente en una credencial apta para dominio. Luego podemos agregar un usuario de dominio al grupo de administradores local en el servidor miembro.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a>Ejemplo 3

En el ejemplo siguiente se muestra cómo asegurarse de un grupo local, TigerTeamAdmins, en el servidor TigerTeamSource.Contoso.Com no contiene una cuenta de dominio en particular, Contoso\JerryG.

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```