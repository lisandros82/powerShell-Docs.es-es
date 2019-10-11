---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsOptionalFeature de DSC
ms.openlocfilehash: 7312edcaeb47427bf4736f466a9ed41bd7c31f6a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954652"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="98e10-103">Recurso WindowsOptionalFeature de DSC</span><span class="sxs-lookup"><span data-stu-id="98e10-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="98e10-104">Se aplica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="98e10-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="98e10-105">El recurso **WindowsOptionalFeature** de la configuración de estado deseado (DSC) de Windows PowerShell proporciona un mecanismo para asegurarse de que las características óptimas están habilitadas en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="98e10-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="98e10-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="98e10-106">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Source = [string[]] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="98e10-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="98e10-107">Properties</span></span>

|<span data-ttu-id="98e10-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="98e10-108">Property</span></span> |<span data-ttu-id="98e10-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="98e10-109">Description</span></span> |
|---|---|
|<span data-ttu-id="98e10-110">Nombre</span><span class="sxs-lookup"><span data-stu-id="98e10-110">Name</span></span> |<span data-ttu-id="98e10-111">Indica el nombre de la característica que desea asegurarse de que está habilitada o deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="98e10-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="98e10-112">Origen</span><span class="sxs-lookup"><span data-stu-id="98e10-112">Source</span></span> |<span data-ttu-id="98e10-113">Sin implementar.</span><span class="sxs-lookup"><span data-stu-id="98e10-113">Not implemented.</span></span> |
|<span data-ttu-id="98e10-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="98e10-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="98e10-115">Especifica si DISM se pone en contacto con Windows Update (WU) al buscar los archivos de origen para habilitar una característica.</span><span class="sxs-lookup"><span data-stu-id="98e10-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="98e10-116">Si el valor es `$true`, DISM no se pone en contacto con WU.</span><span class="sxs-lookup"><span data-stu-id="98e10-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="98e10-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="98e10-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="98e10-118">Establézcalo en `$true` para quitar todos los archivos asociados con la característica cuando el valor de **Ensure** sea **Absent**.</span><span class="sxs-lookup"><span data-stu-id="98e10-118">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="98e10-119">LogLevel</span><span class="sxs-lookup"><span data-stu-id="98e10-119">LogLevel</span></span> |<span data-ttu-id="98e10-120">El nivel de salida máximo que se muestra en los registros.</span><span class="sxs-lookup"><span data-stu-id="98e10-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="98e10-121">Los valores aceptados son: **ErrorsOnly**, **ErrorsAndWarning**, y **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="98e10-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="98e10-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="98e10-122">LogPath</span></span> |<span data-ttu-id="98e10-123">La ruta de acceso al archivo de registro en el que desea que el proveedor de recursos registre la operación.</span><span class="sxs-lookup"><span data-stu-id="98e10-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="98e10-124">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="98e10-124">Common properties</span></span>

|<span data-ttu-id="98e10-125">Propiedad</span><span class="sxs-lookup"><span data-stu-id="98e10-125">Property</span></span> |<span data-ttu-id="98e10-126">Descripción</span><span class="sxs-lookup"><span data-stu-id="98e10-126">Description</span></span> |
|---|---|
|<span data-ttu-id="98e10-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="98e10-127">DependsOn</span></span> |<span data-ttu-id="98e10-128">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="98e10-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="98e10-129">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="98e10-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="98e10-130">Ensure</span><span class="sxs-lookup"><span data-stu-id="98e10-130">Ensure</span></span> |<span data-ttu-id="98e10-131">Especifica si la característica está habilitada.</span><span class="sxs-lookup"><span data-stu-id="98e10-131">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="98e10-132">Para asegurarse de que la característica está habilitada, establezca esta propiedad en _Enable_.</span><span class="sxs-lookup"><span data-stu-id="98e10-132">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="98e10-133">Para asegurarse de que la característica está deshabilitada, establezca esta propiedad en _Disable_.</span><span class="sxs-lookup"><span data-stu-id="98e10-133">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="98e10-134">El valor predeterminado es _Enable_.</span><span class="sxs-lookup"><span data-stu-id="98e10-134">The default value is _Enable_.</span></span> |
|<span data-ttu-id="98e10-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="98e10-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="98e10-136">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="98e10-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="98e10-137">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="98e10-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="98e10-138">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="98e10-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>