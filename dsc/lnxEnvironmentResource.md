---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso nxEnvironment de DSC para Linux
ms.openlocfilehash: 6d1d5e578e9a7ddda0e70063f86867de2e87a52e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxenvironment-resource"></a><span data-ttu-id="d3992-103">Recurso nxEnvironment de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="d3992-103">DSC for Linux nxEnvironment Resource</span></span>

<span data-ttu-id="d3992-104">El recurso **nxEnvironment** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar variables de entorno del sistema en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="d3992-104">The **nxEnvironment** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage system environment variables on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d3992-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="d3992-105">Syntax</span></span>

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="d3992-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="d3992-106">Properties</span></span>

|  <span data-ttu-id="d3992-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="d3992-107">Property</span></span> |  <span data-ttu-id="d3992-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="d3992-108">Description</span></span> |
|---|---|
| <span data-ttu-id="d3992-109">Nombre</span><span class="sxs-lookup"><span data-stu-id="d3992-109">Name</span></span>| <span data-ttu-id="d3992-110">Indica el nombre de la variable de entorno para la que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="d3992-110">Indicates the name of the environment variable for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="d3992-111">Value</span><span class="sxs-lookup"><span data-stu-id="d3992-111">Value</span></span>| <span data-ttu-id="d3992-112">Valor que se asigna a la variable de entorno.</span><span class="sxs-lookup"><span data-stu-id="d3992-112">The value to assign to the environment variable.</span></span>|
| <span data-ttu-id="d3992-113">Ensure</span><span class="sxs-lookup"><span data-stu-id="d3992-113">Ensure</span></span>| <span data-ttu-id="d3992-114">Determina si se debe comprobar si existe la variable de entorno.</span><span class="sxs-lookup"><span data-stu-id="d3992-114">Determines whether to check if the variable exists.</span></span> <span data-ttu-id="d3992-115">Establezca esta propiedad en "Present" para asegurarse de que la variable exista.</span><span class="sxs-lookup"><span data-stu-id="d3992-115">Set this property to "Present" to ensure the variable exists.</span></span> <span data-ttu-id="d3992-116">Establézcala en "Absent" para asegurarse de que la variable no exista.</span><span class="sxs-lookup"><span data-stu-id="d3992-116">Set it to "Absent" to ensure the variable does not exist.</span></span> <span data-ttu-id="d3992-117">El valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="d3992-117">The default value is "Present".</span></span>|
| <span data-ttu-id="d3992-118">Ruta</span><span class="sxs-lookup"><span data-stu-id="d3992-118">Path</span></span>| <span data-ttu-id="d3992-119">Define la variable de entorno que se está configurando.</span><span class="sxs-lookup"><span data-stu-id="d3992-119">Defines the environment variable that is being configured.</span></span> <span data-ttu-id="d3992-120">Establezca esta propiedad en **$true** si la variable es la variable **Path**; de lo contrario, establézcala en **$false**.</span><span class="sxs-lookup"><span data-stu-id="d3992-120">Set this property to **$true** if the variable is the **Path** variable; otherwise, set it to **$false**.</span></span> <span data-ttu-id="d3992-121">El valor predeterminado es **$false**.</span><span class="sxs-lookup"><span data-stu-id="d3992-121">The default is **$false**.</span></span> <span data-ttu-id="d3992-122">Si la variable que se está configurando es la variable **Path**, el valor facilitado mediante la propiedad **Value** se anexará al valor existente.</span><span class="sxs-lookup"><span data-stu-id="d3992-122">If the variable being configured is the **Path** variable, the value provided through the **Value** property will be appended to the existing value.</span></span>|
| <span data-ttu-id="d3992-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d3992-123">DependsOn</span></span> | <span data-ttu-id="d3992-124">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="d3992-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d3992-125">Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d3992-125">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="d3992-126">Información adicional</span><span class="sxs-lookup"><span data-stu-id="d3992-126">Additional Information</span></span>

* <span data-ttu-id="d3992-127">Si **Path** no está presente o se establece en **$false**, las variables de entorno se administran en `/etc/environment`.</span><span class="sxs-lookup"><span data-stu-id="d3992-127">If **Path** is absent or set to **$false**, environment variables are managed in `/etc/environment`.</span></span> <span data-ttu-id="d3992-128">Los programas o scripts pueden requerir una configuración para que el archivo `/etc/environment` acceda a las variables de entorno administradas.</span><span class="sxs-lookup"><span data-stu-id="d3992-128">Your programs or scripts may require configuration to source the `/etc/environment` file to access the managed environment variables.</span></span>
* <span data-ttu-id="d3992-129">Si **Path** se establece en **$true**, la variable de entorno se administra en el archivo `/etc/profile.d/DSCenvironment.sh`.</span><span class="sxs-lookup"><span data-stu-id="d3992-129">If **Path** is set to **$true**, the environment variable is managed in the file `/etc/profile.d/DSCenvironment.sh`.</span></span> <span data-ttu-id="d3992-130">Este archivo se creará si no existe.</span><span class="sxs-lookup"><span data-stu-id="d3992-130">This file will be created if it does not exist.</span></span> <span data-ttu-id="d3992-131">Si **Ensure** se establece en "Absent" y **Path** se establece en **$true**, solo se quitará una variable de entorno de `/etc/profile.d/DSCenvironment.sh` y no de otros archivos.</span><span class="sxs-lookup"><span data-stu-id="d3992-131">If **Ensure** is set to "Absent" and **Path** is set to **$true**, an existing environment variable will only be removed from `/etc/profile.d/DSCenvironment.sh` and not from other files.</span></span>

## <a name="example"></a><span data-ttu-id="d3992-132">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="d3992-132">Example</span></span>

<span data-ttu-id="d3992-133">En el ejemplo siguiente se muestra cómo utilizar el recurso **nxEnvironment** para asegurarse de que **TestEnvironmentVariable** existe y tiene el valor "Test-Value".</span><span class="sxs-lookup"><span data-stu-id="d3992-133">The following example shows how to use the **nxEnvironment** resource to ensure that **TestEnvironmentVariable** is present and has the value "Test-Value".</span></span> <span data-ttu-id="d3992-134">Si **TestEnvironmentVariable** no existe, se creará.</span><span class="sxs-lookup"><span data-stu-id="d3992-134">If **TestEnvironmentVariable** is not present, it will be created.</span></span>

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```