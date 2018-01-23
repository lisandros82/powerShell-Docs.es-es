---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC User
ms.openlocfilehash: c1b8487d9adc899950d185036ada3a2fa3747417
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
#<a name="dsc-user-resource"></a><span data-ttu-id="7b6f0-103">Recurso de DSC User#</span><span class="sxs-lookup"><span data-stu-id="7b6f0-103">DSC User Resource#</span></span>

 
><span data-ttu-id="7b6f0-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7b6f0-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>


<span data-ttu-id="7b6f0-105">El recurso __User__ de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para administrar cuentas de usuarios locales en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-105">The __User__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage local user accounts on the target node.</span></span>


##<a name="syntax"></a><span data-ttu-id="7b6f0-106">Sintaxis##</span><span class="sxs-lookup"><span data-stu-id="7b6f0-106">Syntax##</span></span>

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="7b6f0-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="7b6f0-107">Properties</span></span>
|  <span data-ttu-id="7b6f0-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="7b6f0-108">Property</span></span>  |  <span data-ttu-id="7b6f0-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="7b6f0-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="7b6f0-110">UserName</span><span class="sxs-lookup"><span data-stu-id="7b6f0-110">UserName</span></span>| <span data-ttu-id="7b6f0-111">Indica el nombre de la cuenta para la que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-111">Indicates the account name for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="7b6f0-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="7b6f0-112">Description</span></span>| <span data-ttu-id="7b6f0-113">Indica la descripción que se quiere utilizar para la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-113">Indicates the description you want to use for the user account.</span></span>| 
| <span data-ttu-id="7b6f0-114">Deshabilitada</span><span class="sxs-lookup"><span data-stu-id="7b6f0-114">Disabled</span></span>| <span data-ttu-id="7b6f0-115">Indica si la cuenta se encuentra habilitada.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-115">Indicates if the account is enabled.</span></span> <span data-ttu-id="7b6f0-116">Establezca esta propiedad en __$true__ para asegurarse de que esta cuenta esté deshabilitada y establézcala como __$false__ para asegurarse de que esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-116">Set this property to __$true__ to ensure that this account is disabled, and set it to __$false__ to ensure that it is enabled.</span></span>| 
| <span data-ttu-id="7b6f0-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="7b6f0-117">Ensure</span></span>| <span data-ttu-id="7b6f0-118">Indica si existe la cuenta.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-118">Indicates if the account exists.</span></span> <span data-ttu-id="7b6f0-119">Establezca esta propiedad en "Present" para asegurarse de que la cuenta exista y establézcala como "Absent" para asegurarse de que la cuenta no exista.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-119">Set this property to "Present" to ensure that the account exists, and set it to "Absent" to ensure that the account does not exist.</span></span>| 
| <span data-ttu-id="7b6f0-120">FullName</span><span class="sxs-lookup"><span data-stu-id="7b6f0-120">FullName</span></span>| <span data-ttu-id="7b6f0-121">Representa una cadena con el nombre completo que quiere utilizar para la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-121">Represents a string with the full name you want to use for the user account.</span></span>| 
| <span data-ttu-id="7b6f0-122">Contraseña</span><span class="sxs-lookup"><span data-stu-id="7b6f0-122">Password</span></span>| <span data-ttu-id="7b6f0-123">Indica la contraseña que quiere usar para esta cuenta.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-123">Indicates the password you want to use for this account.</span></span> | 
| <span data-ttu-id="7b6f0-124">PasswordChangeNotAllowed</span><span class="sxs-lookup"><span data-stu-id="7b6f0-124">PasswordChangeNotAllowed</span></span>| <span data-ttu-id="7b6f0-125">Indica si el usuario puede cambiar la contraseña.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-125">Indicates if the user can change the password.</span></span> <span data-ttu-id="7b6f0-126">Establezca esta propiedad en __$true__ para asegurarse de que el usuario no pueda cambiar la contraseña y establézcala como __$false__ para permitir al usuario cambiar la contraseña.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-126">Set this property to __$true__ to ensure that the user cannot change the password, and set it to __$false__ to allow the user to change the password.</span></span> <span data-ttu-id="7b6f0-127">El valor predeterminado es __$false__.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-127">The default value is __$false__.</span></span>| 
| <span data-ttu-id="7b6f0-128">PasswordChangeRequired</span><span class="sxs-lookup"><span data-stu-id="7b6f0-128">PasswordChangeRequired</span></span>| <span data-ttu-id="7b6f0-129">Indica si el usuario debe cambiar la contraseña en el próximo inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-129">Indicates if the user must change the password at the next sign in.</span></span> <span data-ttu-id="7b6f0-130">Establezca esta propiedad en __$true__ si el usuario debe cambiar la contraseña.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-130">Set this property to __$true__ if the user must change the password.</span></span> <span data-ttu-id="7b6f0-131">El valor predeterminado es __$true__.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-131">The default value is __$true__.</span></span>| 
| <span data-ttu-id="7b6f0-132">PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="7b6f0-132">PasswordNeverExpires</span></span>| <span data-ttu-id="7b6f0-133">Indica si la contraseña expirará.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-133">Indicates if the password will expire.</span></span> <span data-ttu-id="7b6f0-134">Para asegurarse de que la contraseña para esta cuenta no expire nunca, establezca esta propiedad en __$true__; establézcala en __$false__ si la contraseña expirará.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-134">To ensure that the password for this account will never expire, set this property to __$true__, and set it to __$false__ if the password will expire.</span></span> <span data-ttu-id="7b6f0-135">El valor predeterminado es __$false__.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-135">The default value is __$false__.</span></span>| 
| <span data-ttu-id="7b6f0-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7b6f0-136">DependsOn</span></span> | <span data-ttu-id="7b6f0-137">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7b6f0-138">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7b6f0-138">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 

## <a name="example"></a><span data-ttu-id="7b6f0-139">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="7b6f0-139">Example</span></span>

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```

