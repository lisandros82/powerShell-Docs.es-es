---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsOptionalFeatureSet de DSC
ms.openlocfilehash: 3bf6a993d0ec9ce71c1e9222ddaa3bb429accb15
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="41631-103">Recurso WindowsOptionalFeatureSet de DSC</span><span class="sxs-lookup"><span data-stu-id="41631-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="41631-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="41631-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="41631-105">El recurso **WindowsOptionalFeatureSet** de la configuración de estado deseado (DSC) de Windows PowerShell proporciona un mecanismo para asegurarse de que las características óptimas están habilitadas en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="41631-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="41631-106">Este es un [recurso compuesto](authoringResourceComposite.md) que llama el [recurso WindowsOptionalFeature](windowsOptionalFeatureResource.md) de cada una de las características especificadas en la propiedad `Name`.</span><span class="sxs-lookup"><span data-stu-id="41631-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="41631-107">Este recurso se usa cuando se desea configurar varias características opcionales de Windows para que tengan el mismo estado.</span><span class="sxs-lookup"><span data-stu-id="41631-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="41631-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="41631-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="41631-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="41631-109">Properties</span></span>

|  <span data-ttu-id="41631-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="41631-110">Property</span></span>  |  <span data-ttu-id="41631-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="41631-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="41631-112">Nombre</span><span class="sxs-lookup"><span data-stu-id="41631-112">Name</span></span>| <span data-ttu-id="41631-113">Indica el nombre de las características que desea asegurarse de que están habilitadas o deshabilitadas.</span><span class="sxs-lookup"><span data-stu-id="41631-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>| 
| <span data-ttu-id="41631-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="41631-114">Ensure</span></span>| <span data-ttu-id="41631-115">Especifica si las características están habilitadas.</span><span class="sxs-lookup"><span data-stu-id="41631-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="41631-116">Para asegurarse de que las características están habilitada, establezca esta propiedad en "Enable"; para asegurarse de que están deshabilitadas, establezca la propiedad en "Disable".</span><span class="sxs-lookup"><span data-stu-id="41631-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="41631-117">Origen</span><span class="sxs-lookup"><span data-stu-id="41631-117">Source</span></span>| <span data-ttu-id="41631-118">Sin implementar.</span><span class="sxs-lookup"><span data-stu-id="41631-118">Not implemented.</span></span>|
| <span data-ttu-id="41631-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="41631-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="41631-120">Especifica si DISM se pone en contacto con Windows Update (WU) al buscar los archivos de origen para habilitar características.</span><span class="sxs-lookup"><span data-stu-id="41631-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="41631-121">Si el valor es $true, DISM no se pone en contacto con WU.</span><span class="sxs-lookup"><span data-stu-id="41631-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="41631-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="41631-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="41631-123">Establézcalo en **$true** para quitar todos los archivos asociados con las características cuando se deshabiliten (es decir, cuando el valor de **Ensure** (Asegurar) sea "Absent").</span><span class="sxs-lookup"><span data-stu-id="41631-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="41631-124">LogLevel</span><span class="sxs-lookup"><span data-stu-id="41631-124">LogLevel</span></span>| <span data-ttu-id="41631-125">El nivel de salida máximo que se muestra en los registros.</span><span class="sxs-lookup"><span data-stu-id="41631-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="41631-126">Los valores aceptados son: "ErrorsOnly" (solo se registran los errores), "ErrorsAndWarning" (se registran los errores y las advertencias) y "ErrorsAndWarningAndInformation" (se registran los errores, las advertencias y la información de depuración).</span><span class="sxs-lookup"><span data-stu-id="41631-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="41631-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="41631-127">LogPath</span></span>| <span data-ttu-id="41631-128">La ruta de acceso al archivo de registro en el que desea que el proveedor de recursos registre la operación.</span><span class="sxs-lookup"><span data-stu-id="41631-128">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="41631-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="41631-129">DependsOn</span></span>| <span data-ttu-id="41631-130">Especifica que debe ejecutarse la configuración de otro recurso antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="41631-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="41631-131">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="41631-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
 



