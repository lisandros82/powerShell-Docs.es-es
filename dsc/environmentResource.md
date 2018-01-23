---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Environment
ms.openlocfilehash: 9c166d719ba3f168c936278acd6fb5fb7658613e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-environment-resource"></a><span data-ttu-id="c186b-103">Recursos de DSC Environment</span><span class="sxs-lookup"><span data-stu-id="c186b-103">DSC Environment Resource</span></span>

> <span data-ttu-id="c186b-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c186b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c186b-105">El recurso __Environment__ de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar variables de entorno del sistema.</span><span class="sxs-lookup"><span data-stu-id="c186b-105">The __Environment__ resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="c186b-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c186b-106">Syntax</span></span>
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="c186b-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="c186b-107">Properties</span></span>

|  <span data-ttu-id="c186b-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="c186b-108">Property</span></span>  |  <span data-ttu-id="c186b-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="c186b-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="c186b-110">Nombre</span><span class="sxs-lookup"><span data-stu-id="c186b-110">Name</span></span>| <span data-ttu-id="c186b-111">Indica el nombre de la variable de entorno para la que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="c186b-111">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>| 
| <span data-ttu-id="c186b-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="c186b-112">Ensure</span></span>| <span data-ttu-id="c186b-113">Indica si existe una variable.</span><span class="sxs-lookup"><span data-stu-id="c186b-113">Indicates if a variable exists.</span></span> <span data-ttu-id="c186b-114">Establezca esta propiedad en __Present__ para crear la variable de entorno si no existe o para garantizar que su valor coincida con el que se proporciona mediante la propiedad __Value__ si la variable ya existe.</span><span class="sxs-lookup"><span data-stu-id="c186b-114">Set this property to __Present__ to create the environment variable if it does not exist or to ensure that its value matches what is provided through the __Value__ property if the variable already exists.</span></span> <span data-ttu-id="c186b-115">Establézcala en __Absent__ para eliminar la variable si existe.</span><span class="sxs-lookup"><span data-stu-id="c186b-115">Set it to __Absent__ to delete the variable if it exists.</span></span>| 
| <span data-ttu-id="c186b-116">Ruta</span><span class="sxs-lookup"><span data-stu-id="c186b-116">Path</span></span>| <span data-ttu-id="c186b-117">Define la variable de entorno que se está configurando.</span><span class="sxs-lookup"><span data-stu-id="c186b-117">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="c186b-118">Establezca esta propiedad en __$true__ si la variable es la variable __Path__; de lo contrario, establézcala en __$false__.</span><span class="sxs-lookup"><span data-stu-id="c186b-118">Set this property to __$true__ if the variable is the __Path__ variable; otherwise, set it to __$false__.</span></span> <span data-ttu-id="c186b-119">El valor predeterminado es __$false__.</span><span class="sxs-lookup"><span data-stu-id="c186b-119">The default is __$false__.</span></span> <span data-ttu-id="c186b-120">Si la variable que se está configurando es la variable __Path__, el valor facilitado mediante la propiedad __Value__ se anexará al valor existente.</span><span class="sxs-lookup"><span data-stu-id="c186b-120">If the variable being configured is the __Path__ variable, the value provided through the __Value__ property will be appended to the existing value.</span></span>| 
| <span data-ttu-id="c186b-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c186b-121">DependsOn</span></span> | <span data-ttu-id="c186b-122">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="c186b-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c186b-123">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c186b-123">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="c186b-124">Value</span><span class="sxs-lookup"><span data-stu-id="c186b-124">Value</span></span>| <span data-ttu-id="c186b-125">Valor que se asigna a la variable de entorno.</span><span class="sxs-lookup"><span data-stu-id="c186b-125">The value to assign to the environment variable.</span></span>| 

## <a name="example"></a><span data-ttu-id="c186b-126">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c186b-126">Example</span></span>

<span data-ttu-id="c186b-127">El ejemplo siguiente se asegura de que __TestEnvironmentVariable__ exista y tenga el valor __TestValue__.</span><span class="sxs-lookup"><span data-stu-id="c186b-127">The following example ensures that __TestEnvironmentVariable__ is present and it has the value __TestValue__.</span></span> <span data-ttu-id="c186b-128">Si no existe, se crea.</span><span class="sxs-lookup"><span data-stu-id="c186b-128">If it is not present, it creates it.</span></span>

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```

