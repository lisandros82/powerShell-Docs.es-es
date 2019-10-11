---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso nxEnvironment de DSC para Linux
ms.openlocfilehash: 55c1b2402e23c1042ed48b40c1084aa63c515b36
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953232"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="4ce5d-103">Recurso nxEnvironment de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="4ce5d-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="4ce5d-104">El recurso **nxEnvironment** de Desired State Configuration (DSC) de PowerShell ofrece un mecanismo para administrar variables de entorno del sistema en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4ce5d-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="4ce5d-105">Syntax</span></span>

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="4ce5d-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="4ce5d-106">Properties</span></span>

|<span data-ttu-id="4ce5d-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="4ce5d-107">Property</span></span> |<span data-ttu-id="4ce5d-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="4ce5d-108">Description</span></span> |
|---|---|
|<span data-ttu-id="4ce5d-109">Nombre</span><span class="sxs-lookup"><span data-stu-id="4ce5d-109">Name</span></span> |<span data-ttu-id="4ce5d-110">Indica el nombre de la variable de entorno para la que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="4ce5d-111">Value</span><span class="sxs-lookup"><span data-stu-id="4ce5d-111">Value</span></span> |<span data-ttu-id="4ce5d-112">Valor que se asigna a la variable de entorno.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-112">The value to assign to the environment variable.</span></span> |
|<span data-ttu-id="4ce5d-113">Ruta</span><span class="sxs-lookup"><span data-stu-id="4ce5d-113">Path</span></span> |<span data-ttu-id="4ce5d-114">Define la variable de entorno que se está configurando.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-114">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="4ce5d-115">Establezca esta propiedad en `$true` si la variable es la variable **Path**; de lo contrario, establézcala en `$false`.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-115">Set this property to `$true` if the variable is the **Path** variable; otherwise, set it to `$false`.</span></span> <span data-ttu-id="4ce5d-116">El valor predeterminado es `$false`.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-116">The default is `$false`.</span></span> <span data-ttu-id="4ce5d-117">Si la variable que se está configurando es la variable **Path**, el valor facilitado mediante la propiedad **Value** se anexará al valor existente.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-117">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4ce5d-118">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="4ce5d-118">Common properties</span></span>

|<span data-ttu-id="4ce5d-119">Propiedad</span><span class="sxs-lookup"><span data-stu-id="4ce5d-119">Property</span></span> |<span data-ttu-id="4ce5d-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="4ce5d-120">Description</span></span> |
|---|---|
|<span data-ttu-id="4ce5d-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4ce5d-121">DependsOn</span></span> |<span data-ttu-id="4ce5d-122">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4ce5d-123">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4ce5d-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="4ce5d-124">Ensure</span></span> |<span data-ttu-id="4ce5d-125">Determina si se debe comprobar si existe la variable de entorno.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-125">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="4ce5d-126">Establezca esta propiedad en **Present** para asegurarse de que la variable exista.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-126">Set this property to **Present** to ensure the variable exists.</span></span> <span data-ttu-id="4ce5d-127">Establézcala en **absent** para asegurarse de que la variable no exista.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-127">Set it to **Absent** to ensure the variable does not exist.</span></span> <span data-ttu-id="4ce5d-128">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-128">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="4ce5d-129">Información adicional</span><span class="sxs-lookup"><span data-stu-id="4ce5d-129">Additional Information</span></span>

- <span data-ttu-id="4ce5d-130">Si **Path** no está presente o se establece en `$false`, las variables de entorno se administran en `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-130">If **Path** is absent or set to `$false`, environment variables are managed in `/etc/environment`.</span></span>
  <span data-ttu-id="4ce5d-131">Los programas o scripts pueden requerir una configuración para que el archivo `/etc/environment` acceda a las variables de entorno administradas.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-131">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
- <span data-ttu-id="4ce5d-132">Si **Path** se establece en `$true`, la variable de entorno se administra en el archivo `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-132">If **Path** is set to `$true`, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="4ce5d-133">Este archivo se creará si no existe.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-133">This file will be created if it does not exist.</span></span> <span data-ttu-id="4ce5d-134">Si **Ensure** se establece en **Absent** y **Path** se establece en `$true`, solo se quitará una variable de entorno de `/etc/profile.d/DSCenvironment.sh` y no de otros archivos.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-134">If **Ensure** is set to **Absent** and **Path** is set to `$true`, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="4ce5d-135">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4ce5d-135">Example</span></span>

<span data-ttu-id="4ce5d-136">En el ejemplo siguiente se muestra cómo utilizar el recurso **nxEnvironment** para asegurarse de que **TestEnvironmentVariable** existe y tiene el valor "Test-Value".</span><span class="sxs-lookup"><span data-stu-id="4ce5d-136">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="4ce5d-137">Si **TestEnvironmentVariable** no existe, se creará.</span><span class="sxs-lookup"><span data-stu-id="4ce5d-137">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```