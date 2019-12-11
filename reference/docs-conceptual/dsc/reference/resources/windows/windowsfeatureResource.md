---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC WindowsFeature
ms.openlocfilehash: d3384b1f45324df6b6b209f25b64d9d77615ad7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954632"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="fade8-103">Recurso de DSC WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="fade8-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="fade8-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="fade8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="fade8-105">El recurso **WindowsFeature** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para asegurarse de que los roles y las características se agreguen o quiten en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="fade8-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="fade8-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="fade8-106">Syntax</span></span>

```Syntax
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ Source = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="fade8-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="fade8-107">Properties</span></span>

|<span data-ttu-id="fade8-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="fade8-108">Property</span></span> |<span data-ttu-id="fade8-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="fade8-109">Description</span></span> |
|---|---|
|<span data-ttu-id="fade8-110">Nombre</span><span class="sxs-lookup"><span data-stu-id="fade8-110">Name</span></span> |<span data-ttu-id="fade8-111">Indica el nombre del rol o la característica que quiere garantizar que se agregue o se quite.</span><span class="sxs-lookup"><span data-stu-id="fade8-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="fade8-112">Esto es el mismo que la propiedad **Name** del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) y no el nombre para mostrar del rol o la característica.</span><span class="sxs-lookup"><span data-stu-id="fade8-112">This is the same as the **Name** property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span> |
|<span data-ttu-id="fade8-113">Credential</span><span class="sxs-lookup"><span data-stu-id="fade8-113">Credential</span></span> |<span data-ttu-id="fade8-114">Indica las credenciales que se usarán para agregar o quitar el rol o la característica.</span><span class="sxs-lookup"><span data-stu-id="fade8-114">Indicates the credentials to use to add or remove the role or feature.</span></span> |
|<span data-ttu-id="fade8-115">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="fade8-115">IncludeAllSubFeature</span></span> |<span data-ttu-id="fade8-116">Establezca esta propiedad en `$true` para garantizar el estado de todas las subcaracterísticas requeridas con el estado de la característica que se especifique con la propiedad **Name**.</span><span class="sxs-lookup"><span data-stu-id="fade8-116">Set this property to `$true` to ensure the state of all required subfeatures with the state of the feature you specify with the **Name** property.</span></span> |
|<span data-ttu-id="fade8-117">LogPath</span><span class="sxs-lookup"><span data-stu-id="fade8-117">LogPath</span></span> |<span data-ttu-id="fade8-118">Indica la ruta de acceso a un archivo de registro donde quiera que el proveedor de recursos registre la operación.</span><span class="sxs-lookup"><span data-stu-id="fade8-118">Indicates the path to a log file where you want the resource provider to log the operation.</span></span> |
|<span data-ttu-id="fade8-119">Origen</span><span class="sxs-lookup"><span data-stu-id="fade8-119">Source</span></span> |<span data-ttu-id="fade8-120">Indica la ubicación del archivo de origen que se utilizará para la instalación, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="fade8-120">Indicates the location of the source file to use for installation, if necessary.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="fade8-121">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="fade8-121">Common properties</span></span>

|<span data-ttu-id="fade8-122">Propiedad</span><span class="sxs-lookup"><span data-stu-id="fade8-122">Property</span></span> |<span data-ttu-id="fade8-123">Descripción</span><span class="sxs-lookup"><span data-stu-id="fade8-123">Description</span></span> |
|---|---|
|<span data-ttu-id="fade8-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fade8-124">DependsOn</span></span> |<span data-ttu-id="fade8-125">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="fade8-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fade8-126">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="fade8-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="fade8-127">Ensure</span><span class="sxs-lookup"><span data-stu-id="fade8-127">Ensure</span></span> |<span data-ttu-id="fade8-128">Indica si se agrega el rol o la característica.</span><span class="sxs-lookup"><span data-stu-id="fade8-128">Indicates if the role or feature is added.</span></span> <span data-ttu-id="fade8-129">Para asegurarse de que se agrega el rol o la característica, establezca esta propiedad en **Present**.</span><span class="sxs-lookup"><span data-stu-id="fade8-129">To ensure that the role or feature is added, set this property to **Present**.</span></span> <span data-ttu-id="fade8-130">Para asegurarse de que se quita el rol o la característica, establezca la propiedad en **Absent**.</span><span class="sxs-lookup"><span data-stu-id="fade8-130">To ensure that the role or feature is removed, set the property to **Absent**.</span></span> <span data-ttu-id="fade8-131">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="fade8-131">The default value is **Present**.</span></span> |
|<span data-ttu-id="fade8-132">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="fade8-132">PsDscRunAsCredential</span></span> |<span data-ttu-id="fade8-133">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="fade8-133">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="fade8-134">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="fade8-134">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="fade8-135">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="fade8-135">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="fade8-136">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="fade8-136">Example</span></span>

```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```