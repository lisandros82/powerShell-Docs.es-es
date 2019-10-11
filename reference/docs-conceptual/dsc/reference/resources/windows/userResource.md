---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC User
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953012"
---
# <a name="dsc-user-resource"></a>Recurso de DSC User

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso **User** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar cuentas de usuarios locales en el nodo de destino.

## <a name="syntax"></a>Sintaxis

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|UserName |Indica el nombre de la cuenta para la que quiere garantizar un estado específico. |
|Descripción |Indica la descripción que se quiere utilizar para la cuenta de usuario. |
|Deshabilitada |Indica si la cuenta se encuentra habilitada. Establezca esta propiedad en `$true` para asegurarse de que esta cuenta esté deshabilitada y establézcala como `$false` para asegurarse de que esté habilitada. |
|FullName |Representa una cadena con el nombre completo que quiere utilizar para la cuenta de usuario. |
|Contraseña |Indica la contraseña que quiere usar para esta cuenta. |
|PasswordChangeNotAllowed |Indica si el usuario puede cambiar la contraseña. Establezca esta propiedad en `$true` para asegurarse de que el usuario no pueda cambiar la contraseña y establézcala como `$false` para permitir al usuario cambiar la contraseña. El valor predeterminado es `$false`. |
|PasswordChangeRequired |Indica si el usuario debe cambiar la contraseña en el próximo inicio de sesión. Establezca esta propiedad en `$true` si el usuario debe cambiar la contraseña. El valor predeterminado es `$true`. |
|PasswordNeverExpires |Indica si la contraseña expirará. Para asegurarse de que la contraseña para esta cuenta no expire nunca, establezca esta propiedad en `$true`. Establézcala en `$false` si la contraseña expirará. El valor predeterminado es `$false`. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica si existe la cuenta. Establezca esta propiedad en **Present** para asegurarse de que la cuenta exista y establézcala como **Absent** para asegurarse de que la cuenta no exista. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Ejemplo

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```