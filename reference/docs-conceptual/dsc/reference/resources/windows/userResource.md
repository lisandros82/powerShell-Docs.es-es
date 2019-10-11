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
# <a name="dsc-user-resource"></a><span data-ttu-id="d2c04-103">Recurso de DSC User</span><span class="sxs-lookup"><span data-stu-id="d2c04-103">DSC User Resource</span></span>

> <span data-ttu-id="d2c04-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="d2c04-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="d2c04-105">El recurso **User** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar cuentas de usuarios locales en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="d2c04-105">The **User** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d2c04-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d2c04-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="d2c04-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="d2c04-107">Properties</span></span>

|<span data-ttu-id="d2c04-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="d2c04-108">Property</span></span> |<span data-ttu-id="d2c04-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="d2c04-109">Description</span></span> |
|---|---|
|<span data-ttu-id="d2c04-110">UserName</span><span class="sxs-lookup"><span data-stu-id="d2c04-110">UserName</span></span> |<span data-ttu-id="d2c04-111">Indica el nombre de la cuenta para la que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="d2c04-111">Indicates the account name for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="d2c04-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="d2c04-112">Description</span></span> |<span data-ttu-id="d2c04-113">Indica la descripción que se quiere utilizar para la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="d2c04-113">Indicates the description you want to use for the user account.</span></span> |
|<span data-ttu-id="d2c04-114">Deshabilitada</span><span class="sxs-lookup"><span data-stu-id="d2c04-114">Disabled</span></span> |<span data-ttu-id="d2c04-115">Indica si la cuenta se encuentra habilitada.</span><span class="sxs-lookup"><span data-stu-id="d2c04-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="d2c04-116">Establezca esta propiedad en `$true` para asegurarse de que esta cuenta esté deshabilitada y establézcala como `$false` para asegurarse de que esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="d2c04-116">Set this property to `$true` to ensure that this account is disabled, and set it to `$false` to ensure that it is enabled.</span></span> |
|<span data-ttu-id="d2c04-117">FullName</span><span class="sxs-lookup"><span data-stu-id="d2c04-117">FullName</span></span> |<span data-ttu-id="d2c04-118">Representa una cadena con el nombre completo que quiere utilizar para la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="d2c04-118">Represents a string with the full name you want to use for the user account.</span></span> |
|<span data-ttu-id="d2c04-119">Contraseña</span><span class="sxs-lookup"><span data-stu-id="d2c04-119">Password</span></span> |<span data-ttu-id="d2c04-120">Indica la contraseña que quiere usar para esta cuenta.</span><span class="sxs-lookup"><span data-stu-id="d2c04-120">Indicates the password you want to use for this account.</span></span> |
|<span data-ttu-id="d2c04-121">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="d2c04-121">PasswordChangeNotAllowed</span></span> |<span data-ttu-id="d2c04-122">Indica si el usuario puede cambiar la contraseña.</span><span class="sxs-lookup"><span data-stu-id="d2c04-122">Indicates if the user can change the password.</span></span> <span data-ttu-id="d2c04-123">Establezca esta propiedad en `$true` para asegurarse de que el usuario no pueda cambiar la contraseña y establézcala como `$false` para permitir al usuario cambiar la contraseña.</span><span class="sxs-lookup"><span data-stu-id="d2c04-123">Set this property to `$true` to ensure that the user cannot change the password, and set it to `$false` to allow the user to change the password.</span></span> <span data-ttu-id="d2c04-124">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="d2c04-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="d2c04-125">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="d2c04-125">PasswordChangeRequired</span></span> |<span data-ttu-id="d2c04-126">Indica si el usuario debe cambiar la contraseña en el próximo inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="d2c04-126">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="d2c04-127">Establezca esta propiedad en `$true` si el usuario debe cambiar la contraseña.</span><span class="sxs-lookup"><span data-stu-id="d2c04-127">Set this property to `$true` if the user must change the password.</span></span> <span data-ttu-id="d2c04-128">El valor predeterminado es `$true`.</span><span class="sxs-lookup"><span data-stu-id="d2c04-128">The default value is `$true`.</span></span> |
|<span data-ttu-id="d2c04-129">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="d2c04-129">PasswordNeverExpires</span></span> |<span data-ttu-id="d2c04-130">Indica si la contraseña expirará.</span><span class="sxs-lookup"><span data-stu-id="d2c04-130">Indicates if the password will expire.</span></span> <span data-ttu-id="d2c04-131">Para asegurarse de que la contraseña para esta cuenta no expire nunca, establezca esta propiedad en `$true`.</span><span class="sxs-lookup"><span data-stu-id="d2c04-131">To ensure that the password for this account will never expire, set this property to `$true`.</span></span> <span data-ttu-id="d2c04-132">Establézcala en `$false` si la contraseña expirará.</span><span class="sxs-lookup"><span data-stu-id="d2c04-132">Set it to `$false` if the password will expire.</span></span> <span data-ttu-id="d2c04-133">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="d2c04-133">The default value is `$false`.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d2c04-134">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="d2c04-134">Common properties</span></span>

|<span data-ttu-id="d2c04-135">Propiedad</span><span class="sxs-lookup"><span data-stu-id="d2c04-135">Property</span></span> |<span data-ttu-id="d2c04-136">Descripción</span><span class="sxs-lookup"><span data-stu-id="d2c04-136">Description</span></span> |
|---|---|
|<span data-ttu-id="d2c04-137">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d2c04-137">DependsOn</span></span> |<span data-ttu-id="d2c04-138">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="d2c04-138">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d2c04-139">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d2c04-139">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d2c04-140">Ensure</span><span class="sxs-lookup"><span data-stu-id="d2c04-140">Ensure</span></span> |<span data-ttu-id="d2c04-141">Indica si existe la cuenta.</span><span class="sxs-lookup"><span data-stu-id="d2c04-141">Indicates if the account exists.</span></span> <span data-ttu-id="d2c04-142">Establezca esta propiedad en **Present** para asegurarse de que la cuenta exista y establézcala como **Absent** para asegurarse de que la cuenta no exista.</span><span class="sxs-lookup"><span data-stu-id="d2c04-142">Set this property to **Present** to ensure that the account exists, and set it to **Absent** to ensure that the account does not exist.</span></span> <span data-ttu-id="d2c04-143">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="d2c04-143">The default value is **Present**.</span></span> |
|<span data-ttu-id="d2c04-144">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="d2c04-144">PsDscRunAsCredential</span></span> |<span data-ttu-id="d2c04-145">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="d2c04-145">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="d2c04-146">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="d2c04-146">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="d2c04-147">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="d2c04-147">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="d2c04-148">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d2c04-148">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```