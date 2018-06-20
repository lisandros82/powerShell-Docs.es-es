---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC WindowsProcess
ms.openlocfilehash: 72668136a3a51c17c52f762c6f94bec3ed4597b0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187034"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="273e7-103">Recurso de DSC WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="273e7-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="273e7-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="273e7-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="273e7-105">El recurso **WindowsProcess** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para configurar procesos en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="273e7-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="273e7-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="273e7-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="273e7-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="273e7-107">Properties</span></span>
|  <span data-ttu-id="273e7-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="273e7-108">Property</span></span>  |  <span data-ttu-id="273e7-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="273e7-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="273e7-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="273e7-110">Arguments</span></span>| <span data-ttu-id="273e7-111">Indica una cadena de argumentos que se pasa al proceso tal cual.</span><span class="sxs-lookup"><span data-stu-id="273e7-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="273e7-112">Si necesita pasar varios argumentos, colóquelos en esta cadena.</span><span class="sxs-lookup"><span data-stu-id="273e7-112">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="273e7-113">Ruta</span><span class="sxs-lookup"><span data-stu-id="273e7-113">Path</span></span>| <span data-ttu-id="273e7-114">La ruta de acceso al ejecutable del proceso.</span><span class="sxs-lookup"><span data-stu-id="273e7-114">The path to the process executable.</span></span> <span data-ttu-id="273e7-115">Si este es el nombre de archivo del ejecutable (no la ruta de acceso completa), el recurso de DSC buscará la variable **Path** del entorno (`$env:Path`) para buscar el archivo ejecutable.</span><span class="sxs-lookup"><span data-stu-id="273e7-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the executable file.</span></span> <span data-ttu-id="273e7-116">Si el valor de esta propiedad es una ruta completa, DSC no usará la variable de entorno **Path** para buscar el archivo y generará un error si la ruta de acceso no existe.</span><span class="sxs-lookup"><span data-stu-id="273e7-116">If the value of this property is a fully qualified path, DSC will not use the **Path** environment variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="273e7-117">No se permiten rutas de acceso relativas.</span><span class="sxs-lookup"><span data-stu-id="273e7-117">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="273e7-118">Credential</span><span class="sxs-lookup"><span data-stu-id="273e7-118">Credential</span></span>| <span data-ttu-id="273e7-119">Indica las credenciales para iniciar el proceso.</span><span class="sxs-lookup"><span data-stu-id="273e7-119">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="273e7-120">Ensure</span><span class="sxs-lookup"><span data-stu-id="273e7-120">Ensure</span></span>| <span data-ttu-id="273e7-121">Indica si existe el proceso.</span><span class="sxs-lookup"><span data-stu-id="273e7-121">Indicates if the process exists.</span></span> <span data-ttu-id="273e7-122">Establezca esta propiedad en "Present" para asegurarse de que el proceso exista.</span><span class="sxs-lookup"><span data-stu-id="273e7-122">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="273e7-123">De lo contrario, establézcala en "Absent".</span><span class="sxs-lookup"><span data-stu-id="273e7-123">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="273e7-124">El valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="273e7-124">The default is "Present".</span></span>|
| <span data-ttu-id="273e7-125">DependsOn</span><span class="sxs-lookup"><span data-stu-id="273e7-125">DependsOn</span></span> | <span data-ttu-id="273e7-126">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="273e7-126">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="273e7-127">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es \`DependsOn = "[ResourceType]ResourceName"\`\` .</span><span class="sxs-lookup"><span data-stu-id="273e7-127">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\` .</span></span>|
| <span data-ttu-id="273e7-128">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="273e7-128">StandardErrorPath</span></span>| <span data-ttu-id="273e7-129">Indica la ruta de acceso del directorio donde se escribirá el error estándar.</span><span class="sxs-lookup"><span data-stu-id="273e7-129">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="273e7-130">Se sobrescribirá cualquier archivo existente en la ubicación.</span><span class="sxs-lookup"><span data-stu-id="273e7-130">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="273e7-131">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="273e7-131">StandardInputPath</span></span>| <span data-ttu-id="273e7-132">Indica la ubicación de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="273e7-132">Indicates the standard input location.</span></span>|
| <span data-ttu-id="273e7-133">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="273e7-133">StandardOutputPath</span></span>| <span data-ttu-id="273e7-134">Indica la ubicación donde se escribirá la salida estándar.</span><span class="sxs-lookup"><span data-stu-id="273e7-134">Indicates the location to write the standard output.</span></span> <span data-ttu-id="273e7-135">Se sobrescribirá cualquier archivo existente en la ubicación.</span><span class="sxs-lookup"><span data-stu-id="273e7-135">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="273e7-136">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="273e7-136">WorkingDirectory</span></span>| <span data-ttu-id="273e7-137">Indica la ubicación que se utilizará como directorio de trabajo actual del proceso.</span><span class="sxs-lookup"><span data-stu-id="273e7-137">Indicates the location that will be used as the current working directory for the process.</span></span>|