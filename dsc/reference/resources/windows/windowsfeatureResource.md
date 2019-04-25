---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC WindowsFeature
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076708"
---
# <a name="dsc-windowsfeature-resource"></a><span data-ttu-id="f3734-103">Recurso de DSC WindowsFeature</span><span class="sxs-lookup"><span data-stu-id="f3734-103">DSC WindowsFeature Resource</span></span>

> <span data-ttu-id="f3734-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f3734-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f3734-105">El recurso **WindowsFeature** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para asegurarse de que los roles y las características se agreguen o quiten en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="f3734-105">The **WindowsFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f3734-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="f3734-106">Syntax</span></span>

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a><span data-ttu-id="f3734-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="f3734-107">Properties</span></span>

|  <span data-ttu-id="f3734-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="f3734-108">Property</span></span>  |  <span data-ttu-id="f3734-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="f3734-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="f3734-110">Nombre</span><span class="sxs-lookup"><span data-stu-id="f3734-110">Name</span></span>| <span data-ttu-id="f3734-111">Indica el nombre del rol o la característica que quiere garantizar que se agregue o se quite.</span><span class="sxs-lookup"><span data-stu-id="f3734-111">Indicates the name of the role or feature that you want to ensure is added or removed.</span></span> <span data-ttu-id="f3734-112">Esto es el mismo que la propiedad __Name__ del cmdlet [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) y no el nombre para mostrar del rol o la característica.</span><span class="sxs-lookup"><span data-stu-id="f3734-112">This is the same as the __Name__ property from the [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, and not the display name of the role or feature.</span></span>|
| <span data-ttu-id="f3734-113">Credential</span><span class="sxs-lookup"><span data-stu-id="f3734-113">Credential</span></span>| <span data-ttu-id="f3734-114">Indica las credenciales que se usarán para agregar o quitar el rol o la característica.</span><span class="sxs-lookup"><span data-stu-id="f3734-114">Indicates the credentials to use to add or remove the role or feature.</span></span>|
| <span data-ttu-id="f3734-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="f3734-115">Ensure</span></span>| <span data-ttu-id="f3734-116">Indica si se agrega el rol o la característica.</span><span class="sxs-lookup"><span data-stu-id="f3734-116">Indicates if the role or feature is added.</span></span> <span data-ttu-id="f3734-117">Para asegurarse de que el rol o la característica se agregue, establezca esta propiedad en "Present"; para asegurarse de que se quite el rol o característica, establezca la propiedad a "Absent".</span><span class="sxs-lookup"><span data-stu-id="f3734-117">To ensure that the role or feature is added, set this property to "Present" To ensure that the role or feature is removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="f3734-118">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="f3734-118">IncludeAllSubFeature</span></span>| <span data-ttu-id="f3734-119">Establezca esta propiedad en __$true__ para garantizar el estado de todas las subcaracterísticas requeridas con el estado de la característica que se especifique con la propiedad __Name__.</span><span class="sxs-lookup"><span data-stu-id="f3734-119">Set this property to __$true__ to ensure the state of all required subfeatures with the state of the feature you specify with the __Name__ property.</span></span>|
| <span data-ttu-id="f3734-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="f3734-120">LogPath</span></span>| <span data-ttu-id="f3734-121">Indica la ruta de acceso a un archivo de registro donde quiera que el proveedor de recursos registre la operación.</span><span class="sxs-lookup"><span data-stu-id="f3734-121">Indicates the path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="f3734-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f3734-122">DependsOn</span></span>| <span data-ttu-id="f3734-123">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="f3734-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f3734-124">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="f3734-124">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="f3734-125">Origen</span><span class="sxs-lookup"><span data-stu-id="f3734-125">Source</span></span>| <span data-ttu-id="f3734-126">Indica la ubicación del archivo de origen que se utilizará para la instalación, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="f3734-126">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="f3734-127">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f3734-127">Example</span></span>
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```