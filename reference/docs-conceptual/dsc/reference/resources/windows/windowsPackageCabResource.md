---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsPackageCab de DSC
ms.openlocfilehash: ec465b2c3b1d180ba46ee24a61f2be1129148962
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954642"
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="aa531-103">Recurso WindowsPackageCab de DSC</span><span class="sxs-lookup"><span data-stu-id="aa531-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="aa531-104">Se aplica a: Windows PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="aa531-104">Applies To: Windows PowerShell 5.1</span></span>

<span data-ttu-id="aa531-105">El recurso **WindowsPackageCab** de Desired State Configuration (DSC) de Windows PowerShell ofrece un mecanismo para instalar o desinstalar paquetes de archivos .cab de Windows en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="aa531-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="aa531-106">El nodo de destino debe tener instalado el módulo PowerShell de DISM.</span><span class="sxs-lookup"><span data-stu-id="aa531-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="aa531-107">Para información, consulte [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14) (Uso de DISM en Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="aa531-107">For information, see [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>

## <a name="syntax"></a><span data-ttu-id="aa531-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="aa531-108">Syntax</span></span>

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="aa531-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="aa531-109">Properties</span></span>

|<span data-ttu-id="aa531-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="aa531-110">Property</span></span> |<span data-ttu-id="aa531-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="aa531-111">Description</span></span> |
|---|---|
|<span data-ttu-id="aa531-112">Nombre</span><span class="sxs-lookup"><span data-stu-id="aa531-112">Name</span></span> |<span data-ttu-id="aa531-113">Indica el nombre del paquete para el que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="aa531-113">Indicates the name of the package for you want to ensure a specific state.</span></span> |
|<span data-ttu-id="aa531-114">SourcePath</span><span class="sxs-lookup"><span data-stu-id="aa531-114">SourcePath</span></span> |<span data-ttu-id="aa531-115">Indica la ruta de acceso donde reside el paquete.</span><span class="sxs-lookup"><span data-stu-id="aa531-115">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="aa531-116">LogPath</span><span class="sxs-lookup"><span data-stu-id="aa531-116">LogPath</span></span> |<span data-ttu-id="aa531-117">Indica la ruta de acceso completa donde quiere que el proveedor guarde un archivo de registro para instalar o desinstalar el paquete.</span><span class="sxs-lookup"><span data-stu-id="aa531-117">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="aa531-118">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="aa531-118">Common properties</span></span>

|<span data-ttu-id="aa531-119">Propiedad</span><span class="sxs-lookup"><span data-stu-id="aa531-119">Property</span></span> |<span data-ttu-id="aa531-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="aa531-120">Description</span></span> |
|---|---|
|<span data-ttu-id="aa531-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="aa531-121">DependsOn</span></span> |<span data-ttu-id="aa531-122">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="aa531-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aa531-123">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="aa531-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="aa531-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="aa531-124">Ensure</span></span> |<span data-ttu-id="aa531-125">Indica si el paquete está instalado.</span><span class="sxs-lookup"><span data-stu-id="aa531-125">Indicates if the package is installed.</span></span> <span data-ttu-id="aa531-126">Establezca esta propiedad en**Absent** para asegurarse de que el paquete no esté instalado (o se desinstale el paquete si está instalado).</span><span class="sxs-lookup"><span data-stu-id="aa531-126">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="aa531-127">Establézcala en **Present** para asegurarse de que el paquete esté instalado.</span><span class="sxs-lookup"><span data-stu-id="aa531-127">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="aa531-128">**Ensure** es una propiedad obligatoria en el recurso **WindowsPackageCab**.</span><span class="sxs-lookup"><span data-stu-id="aa531-128">**Ensure** is a required property on the **WindowsPackageCab** resource.</span></span> |
|<span data-ttu-id="aa531-129">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="aa531-129">PsDscRunAsCredential</span></span> |<span data-ttu-id="aa531-130">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="aa531-130">Sets the credential for running the entire resource as.</span></span> |

## <a name="example"></a><span data-ttu-id="aa531-131">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="aa531-131">Example</span></span>

<span data-ttu-id="aa531-132">La configuración de ejemplo siguiente toma parámetros de entrada y se asegura de que el archivo .cab especificado en el parámetro `$Name` esté instalado.</span><span class="sxs-lookup"><span data-stu-id="aa531-132">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```