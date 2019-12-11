---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC WindowsProcess
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952842"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="ed1b2-103">Recurso de DSC WindowsProcess</span><span class="sxs-lookup"><span data-stu-id="ed1b2-103">DSC WindowsProcess Resource</span></span>

> <span data-ttu-id="ed1b2-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="ed1b2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="ed1b2-105">El recurso **WindowsProcess** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para configurar procesos en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-105">The **WindowsProcess** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ed1b2-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ed1b2-106">Syntax</span></span>

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="ed1b2-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ed1b2-107">Properties</span></span>

|<span data-ttu-id="ed1b2-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ed1b2-108">Property</span></span> |<span data-ttu-id="ed1b2-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="ed1b2-109">Description</span></span> |
|---|---|
|<span data-ttu-id="ed1b2-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="ed1b2-110">Arguments</span></span> |<span data-ttu-id="ed1b2-111">Indica una cadena de argumentos que se pasa al proceso tal cual.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-111">Indicates a string of arguments to pass to the process as-is.</span></span> <span data-ttu-id="ed1b2-112">Si necesita pasar varios argumentos, colóquelos en esta cadena.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-112">If you need to pass several arguments, put them all in this string.</span></span> |
|<span data-ttu-id="ed1b2-113">Ruta</span><span class="sxs-lookup"><span data-stu-id="ed1b2-113">Path</span></span> |<span data-ttu-id="ed1b2-114">La ruta de acceso al ejecutable del proceso.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-114">The path to the process executable.</span></span> <span data-ttu-id="ed1b2-115">Si este es el nombre de archivo del ejecutable (no la ruta de acceso completa), el recurso de DSC buscará la variable `$env:Path`del entorno para buscar el archivo ejecutable.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-115">If this the file name of the executable (not the fully qualified path), the DSC resource will search the environment `$env:Path` variable to find the executable file.</span></span> <span data-ttu-id="ed1b2-116">Si el valor de esta propiedad es una ruta completa, DSC no usará la variable `$env:Path` para buscar el archivo y generará un error si la ruta de acceso no existe.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-116">If the value of this property is a fully qualified path, DSC will not use the `$env:Path` variable to find the file, and will throw an error if the path does not exist.</span></span> <span data-ttu-id="ed1b2-117">No se permiten rutas de acceso relativas.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-117">Relative paths are not allowed.</span></span> |
|<span data-ttu-id="ed1b2-118">Credential</span><span class="sxs-lookup"><span data-stu-id="ed1b2-118">Credential</span></span> |<span data-ttu-id="ed1b2-119">Indica las credenciales para iniciar el proceso.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-119">Indicates the credentials for starting the process.</span></span> |
|<span data-ttu-id="ed1b2-120">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="ed1b2-120">StandardErrorPath</span></span> |<span data-ttu-id="ed1b2-121">Indica la ruta de acceso del directorio donde se escribirá el error estándar.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-121">Indicates the directory path to write the standard error.</span></span> <span data-ttu-id="ed1b2-122">Se sobrescribirá cualquier archivo existente en la ubicación.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-122">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="ed1b2-123">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="ed1b2-123">StandardInputPath</span></span> |<span data-ttu-id="ed1b2-124">Indica la ubicación de entrada estándar.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-124">Indicates the standard input location.</span></span> |
|<span data-ttu-id="ed1b2-125">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="ed1b2-125">StandardOutputPath</span></span> |<span data-ttu-id="ed1b2-126">Indica la ubicación donde se escribirá la salida estándar.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-126">Indicates the location to write the standard output.</span></span> <span data-ttu-id="ed1b2-127">Se sobrescribirá cualquier archivo existente en la ubicación.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-127">Any existing file there will be overwritten.</span></span> |
|<span data-ttu-id="ed1b2-128">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="ed1b2-128">WorkingDirectory</span></span> |<span data-ttu-id="ed1b2-129">Indica la ubicación que se utilizará como directorio de trabajo actual del proceso.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-129">Indicates the location that will be used as the current working directory for the process.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ed1b2-130">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="ed1b2-130">Common properties</span></span>

|<span data-ttu-id="ed1b2-131">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ed1b2-131">Property</span></span> |<span data-ttu-id="ed1b2-132">Descripción</span><span class="sxs-lookup"><span data-stu-id="ed1b2-132">Description</span></span> |
|---|---|
|<span data-ttu-id="ed1b2-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ed1b2-133">DependsOn</span></span> |<span data-ttu-id="ed1b2-134">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ed1b2-135">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ed1b2-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="ed1b2-136">Ensure</span></span> |<span data-ttu-id="ed1b2-137">Indica si existe el proceso.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-137">Indicates if the process exists.</span></span> <span data-ttu-id="ed1b2-138">Establezca esta propiedad en **Present** para asegurarse de que el proceso exista.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-138">Set this property to **Present** to ensure that the process exists.</span></span> <span data-ttu-id="ed1b2-139">De lo contrario, establézcala en **Absent**.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-139">Otherwise, set it to **Absent**.</span></span> <span data-ttu-id="ed1b2-140">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="ed1b2-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ed1b2-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="ed1b2-142">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="ed1b2-142">Sets the credential for running the entire resource as.</span></span> |