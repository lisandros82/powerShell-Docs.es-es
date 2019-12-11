---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Environment
ms.openlocfilehash: d6d3b4a2086be28fbfa2bf200acef9b13b7b7825
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954722"
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="65088-103">Recursos de DSC Environment</span><span class="sxs-lookup"><span data-stu-id="65088-103">DSC Environment Resource</span></span>

> <span data-ttu-id="65088-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="65088-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="65088-105">El recurso **Environment** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar variables de entorno del sistema.</span><span class="sxs-lookup"><span data-stu-id="65088-105">The **Environment** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="65088-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="65088-106">Syntax</span></span>

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="65088-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="65088-107">Properties</span></span>

|<span data-ttu-id="65088-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="65088-108">Property</span></span> |<span data-ttu-id="65088-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="65088-109">Description</span></span> |
|---|---|
|<span data-ttu-id="65088-110">Nombre</span><span class="sxs-lookup"><span data-stu-id="65088-110">Name</span></span> |<span data-ttu-id="65088-111">Indica el nombre de la variable de entorno para la que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="65088-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="65088-112">Ruta</span><span class="sxs-lookup"><span data-stu-id="65088-112">Path</span></span> |<span data-ttu-id="65088-113">Define la variable de entorno que se está configurando.</span><span class="sxs-lookup"><span data-stu-id="65088-113">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="65088-114">Establezca esta propiedad en `$true` si la variable es la variable **Path**; de lo contrario, establézcala en `$false`.</span><span class="sxs-lookup"><span data-stu-id="65088-114">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="65088-115">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="65088-115">The default is `$false`.</span></span> <span data-ttu-id="65088-116">Si la variable que se está configurando es la variable **Path**, el valor facilitado mediante la propiedad **Value** se anexará al valor existente.</span><span class="sxs-lookup"><span data-stu-id="65088-116">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |
|<span data-ttu-id="65088-117">Value</span><span class="sxs-lookup"><span data-stu-id="65088-117">Value</span></span> |<span data-ttu-id="65088-118">Valor que se asigna a la variable de entorno.</span><span class="sxs-lookup"><span data-stu-id="65088-118">The value to assign to the environment variable.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="65088-119">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="65088-119">Common properties</span></span>

|<span data-ttu-id="65088-120">Propiedad</span><span class="sxs-lookup"><span data-stu-id="65088-120">Property</span></span> |<span data-ttu-id="65088-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="65088-121">Description</span></span> |
|---|---|
|<span data-ttu-id="65088-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="65088-122">DependsOn</span></span> |<span data-ttu-id="65088-123">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="65088-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="65088-124">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="65088-124">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="65088-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="65088-125">Ensure</span></span> |<span data-ttu-id="65088-126">Indica si existe una variable.</span><span class="sxs-lookup"><span data-stu-id="65088-126">Indicates if a variable exists.</span></span> <span data-ttu-id="65088-127">Establezca esta propiedad en **Present** para crear la variable de entorno si no existe o para garantizar que su valor coincida con el que se proporciona mediante la propiedad **Value** si la variable ya existe.</span><span class="sxs-lookup"><span data-stu-id="65088-127">Set this property to **Present** to create the environment variable if it does not exist or to ensure that its value matches what is provided through the **Value** property if the variable already exists.</span></span> <span data-ttu-id="65088-128">Establézcala en **Absent** para eliminar la variable si existe.</span><span class="sxs-lookup"><span data-stu-id="65088-128">Set it to **Absent** to delete the variable if it exists.</span></span> |
|<span data-ttu-id="65088-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="65088-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="65088-130">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="65088-130">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="65088-131">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="65088-131">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="65088-132">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="65088-132">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="65088-133">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="65088-133">Example</span></span>

<span data-ttu-id="65088-134">El ejemplo siguiente se asegura de que TestEnvironmentVariable exista y tenga el valor _TestValue_.</span><span class="sxs-lookup"><span data-stu-id="65088-134">The following example ensures that TestEnvironmentVariable is present and it has the value _TestValue_.</span></span> <span data-ttu-id="65088-135">Si no existe, se crea.</span><span class="sxs-lookup"><span data-stu-id="65088-135">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```