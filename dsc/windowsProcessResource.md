---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC WindowsProcess
ms.openlocfilehash: ec77209637d574a0e530f4cce283e1ad98701cdb
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="958ce-103">Recurso de DSC WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="958ce-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="958ce-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="958ce-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="958ce-105">El recurso **WindowsProcess** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para configurar procesos en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="958ce-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="958ce-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="958ce-106">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="958ce-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="958ce-107">Properties</span></span>
|  <span data-ttu-id="958ce-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="958ce-108">Property</span></span>  |  <span data-ttu-id="958ce-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="958ce-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="958ce-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="958ce-110">Arguments</span></span>| <span data-ttu-id="958ce-111">Indica una cadena de argumentos que se pasa al proceso tal cual.</span><span class="sxs-lookup"><span data-stu-id="958ce-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="958ce-112">Si necesita pasar varios argumentos, colóquelos en esta cadena.</span><span class="sxs-lookup"><span data-stu-id="958ce-112">If you need to pass several arguments, put them all in this string.</span></span>| 
| <span data-ttu-id="958ce-113">Ruta</span><span class="sxs-lookup"><span data-stu-id="958ce-113">Path</span></span>| <span data-ttu-id="958ce-114">La ruta de acceso al ejecutable del proceso.</span><span class="sxs-lookup"><span data-stu-id="958ce-114">The path to the process executable.</span></span> <span data-ttu-id="958ce-115">Si este es el nombre de archivo del ejecutable (no la ruta de acceso completa), el recurso de DSC buscará la variable **Path** del entorno (`$env:Path`) para buscar el archivo ejecutable.</span><span class="sxs-lookup"><span data-stu-id="958ce-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="958ce-116">Si el valor de esta propiedad es una ruta completa, DSC no usará la variable de entorno **Path** para buscar el archivo y generará un error si la ruta de acceso no existe.</span><span class="sxs-lookup"><span data-stu-id="958ce-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="958ce-117">No se permiten rutas de acceso relativas.</span><span class="sxs-lookup"><span data-stu-id="958ce-117">Relative paths are not allowed.</span></span>| 
| <span data-ttu-id="958ce-118">Credential</span><span class="sxs-lookup"><span data-stu-id="958ce-118">Credential</span></span>| <span data-ttu-id="958ce-119">Indica las credenciales para iniciar el proceso.</span><span class="sxs-lookup"><span data-stu-id="958ce-119">Indicates the credentials for starting the process.</span></span>| 
| <span data-ttu-id="958ce-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="958ce-120">Ensure</span></span>| <span data-ttu-id="958ce-121">Indica si existe el proceso.</span><span class="sxs-lookup"><span data-stu-id="958ce-121">Indicates if the process exists.</span></span> <span data-ttu-id="958ce-122">Establezca esta propiedad en "Present" para asegurarse de que el proceso exista.</span><span class="sxs-lookup"><span data-stu-id="958ce-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="958ce-123">De lo contrario, establézcala en "Absent".</span><span class="sxs-lookup"><span data-stu-id="958ce-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="958ce-124">El valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="958ce-124">The default is "Present".</span></span>| 
| <span data-ttu-id="958ce-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="958ce-125">DependsOn</span></span> | <span data-ttu-id="958ce-126">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="958ce-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="958ce-127">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es \`DependsOn = "[ResourceType]ResourceName"\`\` .</span><span class="sxs-lookup"><span data-stu-id="958ce-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>| 
| <span data-ttu-id="958ce-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="958ce-128">StandardErrorPath</span></span>| <span data-ttu-id="958ce-129">Indica la ruta de acceso del directorio donde se escribirá el error estándar.</span><span class="sxs-lookup"><span data-stu-id="958ce-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="958ce-130">Se sobrescribirá cualquier archivo existente en la ubicación.</span><span class="sxs-lookup"><span data-stu-id="958ce-130">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="958ce-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="958ce-131">StandardInputPath</span></span>| <span data-ttu-id="958ce-132">Indica la ubicación de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="958ce-132">Indicates the standard input location.</span></span>| 
| <span data-ttu-id="958ce-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="958ce-133">StandardOutputPath</span></span>| <span data-ttu-id="958ce-134">Indica la ubicación donde se escribirá la salida estándar.</span><span class="sxs-lookup"><span data-stu-id="958ce-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="958ce-135">Se sobrescribirá cualquier archivo existente en la ubicación.</span><span class="sxs-lookup"><span data-stu-id="958ce-135">Any existing file there will be overwritten.</span></span>| 
| <span data-ttu-id="958ce-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="958ce-136">WorkingDirectory</span></span>| <span data-ttu-id="958ce-137">Indica la ubicación que se utilizará como directorio de trabajo actual del proceso.</span><span class="sxs-lookup"><span data-stu-id="958ce-137">Indicates the location that will be used as the current working directory for the process.</span></span>| 

