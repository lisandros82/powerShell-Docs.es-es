---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsFeatureSet de DSC
ms.openlocfilehash: 1758d248dde4fdee57bd01c157a3f9a8340d6194
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952962"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="841d4-103">Recurso WindowsFeatureSet de DSC</span><span class="sxs-lookup"><span data-stu-id="841d4-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="841d4-104">Se aplica a: Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="841d4-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="841d4-105">El recurso **WindowsFeatureSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para asegurarse de que los roles y las características se agreguen o quiten en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="841d4-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span> <span data-ttu-id="841d4-106">Este es un [recurso compuesto](../../../resources/authoringResourceComposite.md) que llama al [recurso WindowsFeature](windowsfeatureResource.md) de cada una de las características especificadas en la propiedad **Name**.</span><span class="sxs-lookup"><span data-stu-id="841d4-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="841d4-107">Este recurso se usa cuando se desea configurar varias características de Windows para que tengan el mismo estado.</span><span class="sxs-lookup"><span data-stu-id="841d4-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="841d4-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="841d4-108">Syntax</span></span>

```Syntax
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [Boolean] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="841d4-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="841d4-109">Properties</span></span>

|  <span data-ttu-id="841d4-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="841d4-110">Property</span></span>  |  <span data-ttu-id="841d4-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="841d4-111">Description</span></span>   |
|---|---|
|<span data-ttu-id="841d4-112">Nombre</span><span class="sxs-lookup"><span data-stu-id="841d4-112">Name</span></span> |<span data-ttu-id="841d4-113">Los nombres de los roles o características que quiere garantizar que se agreguen o se quiten.</span><span class="sxs-lookup"><span data-stu-id="841d4-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="841d4-114">Estos son los mismos que con la propiedad **Name** del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) y no el nombre para mostrar de los roles o características.</span><span class="sxs-lookup"><span data-stu-id="841d4-114">This is the same as the **Name** property of the [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature?view=winserver2012r2-ps) cmdlet, and not the display name of the roles or features.</span></span> |
|<span data-ttu-id="841d4-115">Origen</span><span class="sxs-lookup"><span data-stu-id="841d4-115">Source</span></span> |<span data-ttu-id="841d4-116">Indica la ubicación del archivo de origen que se utilizará para la instalación, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="841d4-116">Indicates the location of the source file to use for installation, if necessary.</span></span> |
|<span data-ttu-id="841d4-117">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="841d4-117">IncludeAllSubFeature</span></span> |<span data-ttu-id="841d4-118">Establezca esta propiedad en `$true` para incluir todas las subcaracterísticas requeridas de las características que se especifican con la propiedad **Name**.</span><span class="sxs-lookup"><span data-stu-id="841d4-118">Set this property to `$true` to include all required subfeatures with of the features you specify with the **Name** property.</span></span> |
|<span data-ttu-id="841d4-119">Credential</span><span class="sxs-lookup"><span data-stu-id="841d4-119">Credential</span></span> |<span data-ttu-id="841d4-120">Las credenciales que se usarán para agregar o quitar los roles o las características.</span><span class="sxs-lookup"><span data-stu-id="841d4-120">The credentials to use to add or remove the roles or features.</span></span> |
|<span data-ttu-id="841d4-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="841d4-121">LogPath</span></span> |<span data-ttu-id="841d4-122">La ruta de acceso al archivo de registro en el que desea que el proveedor de recursos registre la operación.</span><span class="sxs-lookup"><span data-stu-id="841d4-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="841d4-123">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="841d4-123">Common properties</span></span>

|<span data-ttu-id="841d4-124">Propiedad</span><span class="sxs-lookup"><span data-stu-id="841d4-124">Property</span></span> |<span data-ttu-id="841d4-125">Descripción</span><span class="sxs-lookup"><span data-stu-id="841d4-125">Description</span></span> |
|---|---|
|<span data-ttu-id="841d4-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="841d4-126">DependsOn</span></span> |<span data-ttu-id="841d4-127">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="841d4-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="841d4-128">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="841d4-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="841d4-129">Ensure</span><span class="sxs-lookup"><span data-stu-id="841d4-129">Ensure</span></span> |<span data-ttu-id="841d4-130">Indica si se agregan las funciones o características.</span><span class="sxs-lookup"><span data-stu-id="841d4-130">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="841d4-131">Para asegurarse de que se agregan los roles o características, establezca esta propiedad en **Present**.</span><span class="sxs-lookup"><span data-stu-id="841d4-131">To ensure that the roles or features are added, set this property to **Present**.</span></span> <span data-ttu-id="841d4-132">Para asegurarse de que se quitan los roles o características, establezca la propiedad en **Absent**.</span><span class="sxs-lookup"><span data-stu-id="841d4-132">To ensure that the roles or features are removed, set the property to **Absent**.</span></span> <span data-ttu-id="841d4-133">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="841d4-133">The default value is **Present**.</span></span> |
|<span data-ttu-id="841d4-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="841d4-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="841d4-135">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="841d4-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="841d4-136">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="841d4-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="841d4-137">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="841d4-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="841d4-138">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="841d4-138">Example</span></span>

<span data-ttu-id="841d4-139">La siguiente configuración garantiza que las características de **Web Server** (IIS) y del **servidor SMTP**, y todas las subcaracterísticas de cada uno, se instalan.</span><span class="sxs-lookup"><span data-stu-id="841d4-139">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```