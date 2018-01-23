---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso ProcessSet de DSC
ms.openlocfilehash: ec1d6a04b5debc22fe2f3b4a4396c385514a3b0c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="94a14-103">Recurso de DSC WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="94a14-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="94a14-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="94a14-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="94a14-105">El recurso **ProcessSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para configurar procesos en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="94a14-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="94a14-106">Este es un [recurso compuesto](authoringResourceComposite.md) que llama al [recurso WindowsProcess](windowsProcessResource.md) de cada uno de los grupos que se especifican en el parámetro `GroupName`.</span><span class="sxs-lookup"><span data-stu-id="94a14-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="94a14-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="94a14-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]   
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="94a14-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="94a14-108">Properties</span></span>
|  <span data-ttu-id="94a14-109">Propiedad</span><span class="sxs-lookup"><span data-stu-id="94a14-109">Property</span></span>  |  <span data-ttu-id="94a14-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="94a14-110">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="94a14-111">Argumentos</span><span class="sxs-lookup"><span data-stu-id="94a14-111">Arguments</span></span>| <span data-ttu-id="94a14-112">Una cadena que tiene argumentos que se pasa al proceso tal cual.</span><span class="sxs-lookup"><span data-stu-id="94a14-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="94a14-113">Si necesita pasar varios argumentos, colóquelos en esta cadena.</span><span class="sxs-lookup"><span data-stu-id="94a14-113">If you need to pass several arguments, put them all in this string.</span></span>| 
| <span data-ttu-id="94a14-114">Ruta</span><span class="sxs-lookup"><span data-stu-id="94a14-114">Path</span></span>| <span data-ttu-id="94a14-115">Las rutas de acceso a los ejecutables del proceso.</span><span class="sxs-lookup"><span data-stu-id="94a14-115">The paths to the process executables.</span></span> <span data-ttu-id="94a14-116">Si estos son los nombres de archivo de los ejecutables (no las rutas de acceso completas), el recurso de DSC buscará la variable **Path** del entorno (`$env:Path`) para buscar los archivos.</span><span class="sxs-lookup"><span data-stu-id="94a14-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="94a14-117">Si los valores de esta propiedad son rutas completas, DSC no usará la variable de entorno **Path** para buscar los archivos y generará un error si alguna de las rutas de acceso no existe.</span><span class="sxs-lookup"><span data-stu-id="94a14-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="94a14-118">No se permiten rutas de acceso relativas.</span><span class="sxs-lookup"><span data-stu-id="94a14-118">Relative paths are not allowed.</span></span>| 
| <span data-ttu-id="94a14-119">Credential</span><span class="sxs-lookup"><span data-stu-id="94a14-119">Credential</span></span>| <span data-ttu-id="94a14-120">Indica las credenciales para iniciar el proceso.</span><span class="sxs-lookup"><span data-stu-id="94a14-120">Indicates the credentials for starting the process.</span></span>| 
| <span data-ttu-id="94a14-121">Ensure</span><span class="sxs-lookup"><span data-stu-id="94a14-121">Ensure</span></span>| <span data-ttu-id="94a14-122">Especifica si los procesos existen.</span><span class="sxs-lookup"><span data-stu-id="94a14-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="94a14-123">Establezca esta propiedad en "Present" para asegurarse de que el proceso exista.</span><span class="sxs-lookup"><span data-stu-id="94a14-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="94a14-124">De lo contrario, establézcala en "Absent".</span><span class="sxs-lookup"><span data-stu-id="94a14-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="94a14-125">El valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="94a14-125">The default is "Present".</span></span>| 
| <span data-ttu-id="94a14-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="94a14-126">StandardErrorPath</span></span>| <span data-ttu-id="94a14-127">La ruta de acceso en la que los procesos escriben los errores estándar.</span><span class="sxs-lookup"><span data-stu-id="94a14-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="94a14-128">Se sobrescribirá cualquier archivo existente en la ubicación.</span><span class="sxs-lookup"><span data-stu-id="94a14-128">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="94a14-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="94a14-129">StandardInputPath</span></span>| <span data-ttu-id="94a14-130">La secuencia desde la que el proceso recibe las entradas estándar.</span><span class="sxs-lookup"><span data-stu-id="94a14-130">The stream from which the process receives standard input.</span></span>| 
| <span data-ttu-id="94a14-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="94a14-131">StandardOutputPath</span></span>| <span data-ttu-id="94a14-132">La ruta de acceso del archivo en la que los procesos escriben las salidas estándar.</span><span class="sxs-lookup"><span data-stu-id="94a14-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="94a14-133">Se sobrescribirá cualquier archivo existente en la ubicación.</span><span class="sxs-lookup"><span data-stu-id="94a14-133">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="94a14-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="94a14-134">WorkingDirectory</span></span>| <span data-ttu-id="94a14-135">La ubicación utilizada como directorio de trabajo actual de los procesos.</span><span class="sxs-lookup"><span data-stu-id="94a14-135">The location used as the current working directory for the processes.</span></span>| 
| <span data-ttu-id="94a14-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="94a14-136">DependsOn</span></span> | <span data-ttu-id="94a14-137">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="94a14-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="94a14-138">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es \`DependsOn = "[ResourceType]ResourceName"\`\`.</span><span class="sxs-lookup"><span data-stu-id="94a14-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>| 

