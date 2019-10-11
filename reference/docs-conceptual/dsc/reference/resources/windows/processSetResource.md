---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso ProcessSet de DSC
ms.openlocfilehash: 72925d3a9516f5c0040427773a3b1d66034667bb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953132"
---
# <a name="dsc-processset-resource"></a><span data-ttu-id="b9f77-103">Recurso ProcessSet de DSC</span><span class="sxs-lookup"><span data-stu-id="b9f77-103">DSC ProcessSet Resource</span></span>

> <span data-ttu-id="b9f77-104">Se aplica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="b9f77-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="b9f77-105">El recurso **ProcessSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para configurar procesos en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="b9f77-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9f77-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b9f77-106">Syntax</span></span>

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="b9f77-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="b9f77-107">Properties</span></span>

|<span data-ttu-id="b9f77-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="b9f77-108">Property</span></span> |<span data-ttu-id="b9f77-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="b9f77-109">Description</span></span> |
|---|---|
|<span data-ttu-id="b9f77-110">Ruta</span><span class="sxs-lookup"><span data-stu-id="b9f77-110">Path</span></span> |<span data-ttu-id="b9f77-111">La ruta de acceso al ejecutable del proceso.</span><span class="sxs-lookup"><span data-stu-id="b9f77-111">The path to the process executable.</span></span> <span data-ttu-id="b9f77-112">Si estos son los nombres de archivo de los ejecutables (no las rutas de acceso completas), el recurso de DSC buscará la variable `$env:Path` del entorno para buscar los archivos.</span><span class="sxs-lookup"><span data-stu-id="b9f77-112">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment `$env:Path` variable to find the files.</span></span> <span data-ttu-id="b9f77-113">Si los valores de esta propiedad son rutas completas, DSC no usará la variable de entorno `$env:Path` para buscar los archivos y generará un error si alguna de las rutas de acceso no existe.</span><span class="sxs-lookup"><span data-stu-id="b9f77-113">If the values of this property are fully qualified paths, DSC will not use the `$env:Path` environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="b9f77-114">No se permiten rutas de acceso relativas.</span><span class="sxs-lookup"><span data-stu-id="b9f77-114">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="b9f77-115">Credential</span><span class="sxs-lookup"><span data-stu-id="b9f77-115">Credential</span></span> |<span data-ttu-id="b9f77-116">Indica las credenciales para iniciar el proceso.</span><span class="sxs-lookup"><span data-stu-id="b9f77-116">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="b9f77-117">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="b9f77-117">StandardErrorPath</span></span> |<span data-ttu-id="b9f77-118">La ruta de acceso en la que los procesos escriben los errores estándar.</span><span class="sxs-lookup"><span data-stu-id="b9f77-118">The path to which the processes write standard error.</span></span> <span data-ttu-id="b9f77-119">Se sobrescribirá cualquier archivo existente en la ubicación.</span><span class="sxs-lookup"><span data-stu-id="b9f77-119">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="b9f77-120">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="b9f77-120">StandardInputPath</span></span> |<span data-ttu-id="b9f77-121">La secuencia desde la que el proceso recibe las entradas estándar.</span><span class="sxs-lookup"><span data-stu-id="b9f77-121">The stream from which the process receives standard input.</span></span> |
|<span data-ttu-id="b9f77-122">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="b9f77-122">StandardOutputPath</span></span> |<span data-ttu-id="b9f77-123">La ruta de acceso del archivo en la que los procesos escriben las salidas estándar.</span><span class="sxs-lookup"><span data-stu-id="b9f77-123">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="b9f77-124">Se sobrescribirá cualquier archivo existente en la ubicación.</span><span class="sxs-lookup"><span data-stu-id="b9f77-124">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="b9f77-125">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="b9f77-125">WorkingDirectory</span></span> |<span data-ttu-id="b9f77-126">La ubicación utilizada como directorio de trabajo actual de los procesos.</span><span class="sxs-lookup"><span data-stu-id="b9f77-126">The location used as the current working directory for the processes.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="b9f77-127">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="b9f77-127">Common properties</span></span>

|<span data-ttu-id="b9f77-128">Propiedad</span><span class="sxs-lookup"><span data-stu-id="b9f77-128">Property</span></span> |<span data-ttu-id="b9f77-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="b9f77-129">Description</span></span> |
|---|---|
|<span data-ttu-id="b9f77-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b9f77-130">DependsOn</span></span> |<span data-ttu-id="b9f77-131">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="b9f77-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b9f77-132">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b9f77-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="b9f77-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="b9f77-133">Ensure</span></span> |<span data-ttu-id="b9f77-134">Especifica si los procesos existen.</span><span class="sxs-lookup"><span data-stu-id="b9f77-134">Specifies whether the processes exists.</span></span> <span data-ttu-id="b9f77-135">Establezca esta propiedad en **Present** para asegurarse de que el proceso exista.</span><span class="sxs-lookup"><span data-stu-id="b9f77-135">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="b9f77-136">De lo contrario, establézcala en **Absent**.</span><span class="sxs-lookup"><span data-stu-id="b9f77-136">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="b9f77-137">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="b9f77-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="b9f77-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="b9f77-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="b9f77-139">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="b9f77-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="b9f77-140">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="b9f77-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="b9f77-141">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="b9f77-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>