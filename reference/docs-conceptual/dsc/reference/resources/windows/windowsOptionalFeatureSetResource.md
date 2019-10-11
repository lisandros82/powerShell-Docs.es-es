---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsOptionalFeatureSet de DSC
ms.openlocfilehash: f378006a6c362ee9890d70dd76fb552dd262a544
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952872"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="ecb64-103">Recurso WindowsOptionalFeatureSet de DSC</span><span class="sxs-lookup"><span data-stu-id="ecb64-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="ecb64-104">Se aplica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="ecb64-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="ecb64-105">El recurso **WindowsOptionalFeatureSet** de la configuración de estado deseado (DSC) de Windows PowerShell proporciona un mecanismo para asegurarse de que las características óptimas están habilitadas en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="ecb64-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="ecb64-106">Este es un [recurso compuesto](../../../resources/authoringResourceComposite.md) que llama el [recurso WindowsOptionalFeature](windowsOptionalFeatureResource.md) de cada una de las características especificadas en la propiedad **Name**.</span><span class="sxs-lookup"><span data-stu-id="ecb64-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="ecb64-107">Este recurso se usa cuando se desea configurar varias características opcionales de Windows para que tengan el mismo estado.</span><span class="sxs-lookup"><span data-stu-id="ecb64-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="ecb64-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ecb64-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="ecb64-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ecb64-109">Properties</span></span>

|<span data-ttu-id="ecb64-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ecb64-110">Property</span></span> |<span data-ttu-id="ecb64-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecb64-111">Description</span></span> |
|---|---|
|<span data-ttu-id="ecb64-112">Nombre</span><span class="sxs-lookup"><span data-stu-id="ecb64-112">Name</span></span> |<span data-ttu-id="ecb64-113">Indica el nombre de las características que desea asegurarse de que están habilitadas o deshabilitadas.</span><span class="sxs-lookup"><span data-stu-id="ecb64-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="ecb64-114">Origen</span><span class="sxs-lookup"><span data-stu-id="ecb64-114">Source</span></span> |<span data-ttu-id="ecb64-115">Sin implementar.</span><span class="sxs-lookup"><span data-stu-id="ecb64-115">Not implemented.</span></span> |
|<span data-ttu-id="ecb64-116">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="ecb64-116">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="ecb64-117">Especifica si DISM se pone en contacto con Windows Update (WU) al buscar los archivos de origen para habilitar características.</span><span class="sxs-lookup"><span data-stu-id="ecb64-117">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="ecb64-118">Si el valor es `$true`, DISM no se pone en contacto con WU.</span><span class="sxs-lookup"><span data-stu-id="ecb64-118">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="ecb64-119">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="ecb64-119">RemoveFilesOnDisable</span></span> |<span data-ttu-id="ecb64-120">Establézcalo en `$true` para quitar todos los archivos asociados con las características cuando el valor de **Ensure** sea **Absent**.</span><span class="sxs-lookup"><span data-stu-id="ecb64-120">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="ecb64-121">LogLevel</span><span class="sxs-lookup"><span data-stu-id="ecb64-121">LogLevel</span></span> |<span data-ttu-id="ecb64-122">El nivel de salida máximo que se muestra en los registros.</span><span class="sxs-lookup"><span data-stu-id="ecb64-122">The maximum output level shown in the logs.</span></span> <span data-ttu-id="ecb64-123">Los valores aceptados son: **ErrorsOnly**, **ErrorsAndWarning**, y **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="ecb64-123">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="ecb64-124">LogPath</span><span class="sxs-lookup"><span data-stu-id="ecb64-124">LogPath</span></span> |<span data-ttu-id="ecb64-125">La ruta de acceso al archivo de registro en el que desea que el proveedor de recursos registre la operación.</span><span class="sxs-lookup"><span data-stu-id="ecb64-125">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ecb64-126">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="ecb64-126">Common properties</span></span>

|<span data-ttu-id="ecb64-127">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ecb64-127">Property</span></span> |<span data-ttu-id="ecb64-128">Descripción</span><span class="sxs-lookup"><span data-stu-id="ecb64-128">Description</span></span> |
|---|---|
|<span data-ttu-id="ecb64-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ecb64-129">DependsOn</span></span> |<span data-ttu-id="ecb64-130">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="ecb64-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ecb64-131">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ecb64-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="ecb64-132">Ensure</span><span class="sxs-lookup"><span data-stu-id="ecb64-132">Ensure</span></span> |<span data-ttu-id="ecb64-133">Especifica si las características están habilitadas.</span><span class="sxs-lookup"><span data-stu-id="ecb64-133">Specifies whether the features are enabled.</span></span> <span data-ttu-id="ecb64-134">Para asegurarse de que las características están habilitadas, establezca esta propiedad en **Enable**.</span><span class="sxs-lookup"><span data-stu-id="ecb64-134">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="ecb64-135">Para asegurarse de que las características están deshabilitadas, establezca la propiedad en **Disable**.</span><span class="sxs-lookup"><span data-stu-id="ecb64-135">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="ecb64-136">El valor predeterminado es **Enable**.</span><span class="sxs-lookup"><span data-stu-id="ecb64-136">The default value is **Enable**.</span></span> |
|<span data-ttu-id="ecb64-137">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="ecb64-137">PsDscRunAsCredential</span></span> |<span data-ttu-id="ecb64-138">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="ecb64-138">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="ecb64-139">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="ecb64-139">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="ecb64-140">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="ecb64-140">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>