---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Group
ms.openlocfilehash: 123e09b54a923af942a15f80fa7291c555b4235f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077354"
---
# <a name="dsc-group-resource"></a>Recurso de DSC Group

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

El recurso Group de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar grupos locales en el nodo de destino.

## <a name="syntax"></a>Sintaxis

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   |
|---|---|
| NombreDeGrupo| El nombre del grupo para el que quiere garantizar un estado específico.|
| Credential| Las credenciales necesarias para acceder a los recursos remotos. **Nota**: Esta cuenta debe tener los permisos adecuados de Active Directory para agregar todas las cuentas no locales al grupo; en caso contrario, se producirá un error al ejecutar la configuración en el nodo de destino.
| Descripción| La descripción del grupo.|
| Ensure| Indica si existe el grupo. Establezca esta propiedad en "Absent" para asegurarse de que el grupo no exista. Si se establece en "Present" (el valor predeterminado), se garantiza que el grupo exista.|
| Miembros| Use esta propiedad para reemplazar la pertenencia al grupo actual con los miembros especificados. El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*. Si establece esta propiedad en una configuración, no use las propiedades **MembersToExclude** ni **MembersToInclude**. Si lo hace, se generará un error.|
| MembersToExclude| Use esta propiedad para quitar a los miembros de la pertenencia existente del grupo. El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*. Si establece esta propiedad en una configuración, no use la propiedad **Members**. Si lo hace, se generará un error.|
| MembersToInclude| Use esta propiedad para agregar miembros a la pertenencia existente al grupo. El valor de esta propiedad es una matriz de cadenas del formulario *Domain*\\*UserName*. Si establece esta propiedad en una configuración, no use la propiedad **Members**. Si lo hace, se generará un error.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"``.|

## <a name="example-1"></a>Ejemplo 1

En el ejemplo siguiente se muestra cómo asegurarse de que no existe un grupo denominado "TestGroup".

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a>Ejemplo 2

En el ejemplo siguiente se muestra cómo agregar un usuario de Active Directory al grupo de administradores local como parte de una compilación de prácticas en varias máquinas que ya usan un PSCredential para la cuenta de administrador local.
Puesto que también se usa para la cuenta de administrador del dominio (después de la promoción del dominio), necesitamos convertir este PSCredential existente en una credencial apta para dominio.
Luego podemos agregar un usuario de dominio al grupo de administradores local en el servidor miembro.

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