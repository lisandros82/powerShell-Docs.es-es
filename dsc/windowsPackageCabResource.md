---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsPackageCab de DSC
ms.openlocfilehash: af45956c1fe8cffa1d7fd779847eded9e3f6b51e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="880ba-103">Recurso WindowsPackageCab de DSC</span><span class="sxs-lookup"><span data-stu-id="880ba-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="880ba-104">Se aplica a: Windows PowerShell 5.1 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="880ba-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="880ba-105">El recurso **WindowsPackageCab** de Desired State Configuration (DSC) de Windows PowerShell ofrece un mecanismo para instalar o desinstalar paquetes de archivos .cab de Windows en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="880ba-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="880ba-106">El nodo de destino debe tener instalado el módulo PowerShell de DISM.</span><span class="sxs-lookup"><span data-stu-id="880ba-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="880ba-107">Para información, consulte [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14) (Uso de DISM en Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="880ba-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="880ba-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="880ba-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="880ba-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="880ba-109">Properties</span></span>

|  <span data-ttu-id="880ba-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="880ba-110">Property</span></span>  |  <span data-ttu-id="880ba-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="880ba-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="880ba-112">Nombre</span><span class="sxs-lookup"><span data-stu-id="880ba-112">Name</span></span>| <span data-ttu-id="880ba-113">Indica el nombre del paquete para el que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="880ba-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="880ba-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="880ba-114">Ensure</span></span>| <span data-ttu-id="880ba-115">Indica si el paquete está instalado.</span><span class="sxs-lookup"><span data-stu-id="880ba-115">Indicates if the package is installed.</span></span> <span data-ttu-id="880ba-116">Establezca esta propiedad en "Absent" para asegurarse de que el paquete no esté instalado (o se desinstale el paquete si está instalado).</span><span class="sxs-lookup"><span data-stu-id="880ba-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="880ba-117">Establézcala en "Present" (el valor predeterminado) para asegurarse de que el paquete esté instalado.</span><span class="sxs-lookup"><span data-stu-id="880ba-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="880ba-118">Ruta</span><span class="sxs-lookup"><span data-stu-id="880ba-118">Path</span></span>| <span data-ttu-id="880ba-119">Indica la ruta de acceso donde reside el paquete.</span><span class="sxs-lookup"><span data-stu-id="880ba-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="880ba-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="880ba-120">LogPath</span></span>| <span data-ttu-id="880ba-121">Indica la ruta de acceso completa donde quiere que el proveedor guarde un archivo de registro para instalar o desinstalar el paquete.</span><span class="sxs-lookup"><span data-stu-id="880ba-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="880ba-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="880ba-122">DependsOn</span></span> | <span data-ttu-id="880ba-123">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="880ba-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="880ba-124">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es \`DependsOn = "[ResourceType]ResourceName"\`\`.</span><span class="sxs-lookup"><span data-stu-id="880ba-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="880ba-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="880ba-125">Example</span></span>

<span data-ttu-id="880ba-126">La configuración de ejemplo siguiente toma parámetros de entrada y se asegura de que el archivo .cab especificado en el parámetro `$Name` esté instalado.</span><span class="sxs-lookup"><span data-stu-id="880ba-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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