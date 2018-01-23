---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsOptionalFeature de DSC
ms.openlocfilehash: d9b8cc316255f06d2de71fedc47ce4472cc8b382
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="04691-103">Recurso WindowsOptionalFeature de DSC</span><span class="sxs-lookup"><span data-stu-id="04691-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="04691-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="04691-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="04691-105">El recurso **WindowsOptionalFeature** de la configuración de estado deseado (DSC) de Windows PowerShell proporciona un mecanismo para asegurarse de que las características óptimas están habilitadas en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="04691-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="04691-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="04691-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="04691-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="04691-107">Properties</span></span>

|  <span data-ttu-id="04691-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="04691-108">Property</span></span>  |  <span data-ttu-id="04691-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="04691-109">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="04691-110">Nombre</span><span class="sxs-lookup"><span data-stu-id="04691-110">Name</span></span>| <span data-ttu-id="04691-111">Indica el nombre de la característica que desea asegurarse de que está habilitada o deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="04691-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>| 
| <span data-ttu-id="04691-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="04691-112">Ensure</span></span>| <span data-ttu-id="04691-113">Especifica si la característica está habilitada.</span><span class="sxs-lookup"><span data-stu-id="04691-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="04691-114">Para asegurarse de que la característica está habilitada, establezca esta propiedad en "Enable"; para asegurarse de que está deshabilitada, establezca la propiedad en "Disable".</span><span class="sxs-lookup"><span data-stu-id="04691-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="04691-115">Origen</span><span class="sxs-lookup"><span data-stu-id="04691-115">Source</span></span>| <span data-ttu-id="04691-116">Sin implementar.</span><span class="sxs-lookup"><span data-stu-id="04691-116">Not implemented.</span></span>|
| <span data-ttu-id="04691-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="04691-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="04691-118">Especifica si DISM se pone en contacto con Windows Update (WU) al buscar los archivos de origen para habilitar una característica.</span><span class="sxs-lookup"><span data-stu-id="04691-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="04691-119">Si el valor es $true, DISM no se pone en contacto con WU.</span><span class="sxs-lookup"><span data-stu-id="04691-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="04691-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="04691-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="04691-121">Establézcalo en **$true** para quitar todos los archivos asociados con la característica cuando se deshabilite (es decir, cuando el valor de **Ensure** (Asegurar) sea "Absent").</span><span class="sxs-lookup"><span data-stu-id="04691-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="04691-122">LogLevel</span><span class="sxs-lookup"><span data-stu-id="04691-122">LogLevel</span></span>| <span data-ttu-id="04691-123">El nivel de salida máximo que se muestra en los registros.</span><span class="sxs-lookup"><span data-stu-id="04691-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="04691-124">Los valores aceptados son: "ErrorsOnly" (solo se registran los errores), "ErrorsAndWarning" (se registran los errores y las advertencias) y "ErrorsAndWarningAndInformation" (se registran los errores, las advertencias y la información de depuración).</span><span class="sxs-lookup"><span data-stu-id="04691-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="04691-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="04691-125">LogPath</span></span>| <span data-ttu-id="04691-126">La ruta de acceso al archivo de registro en el que desea que el proveedor de recursos registre la operación.</span><span class="sxs-lookup"><span data-stu-id="04691-126">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="04691-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="04691-127">DependsOn</span></span>| <span data-ttu-id="04691-128">Especifica que debe ejecutarse la configuración de otro recurso antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="04691-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="04691-129">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="04691-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
 



