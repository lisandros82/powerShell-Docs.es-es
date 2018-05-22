---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsPackageCab de DSC
ms.openlocfilehash: 8c4de193c8ea787dd125436f86aa0b5eafdb1509
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-windowspackagecab-resource"></a><span data-ttu-id="489ed-103">Recurso WindowsPackageCab de DSC</span><span class="sxs-lookup"><span data-stu-id="489ed-103">DSC WindowsPackageCab Resource</span></span>

> <span data-ttu-id="489ed-104">Se aplica a: Windows PowerShell 5.1 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="489ed-104">Applies To: Windows PowerShell 5.1 and later</span></span>

<span data-ttu-id="489ed-105">El recurso **WindowsPackageCab** de Desired State Configuration (DSC) de Windows PowerShell ofrece un mecanismo para instalar o desinstalar paquetes de archivos .cab de Windows en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="489ed-105">The **WindowsPackageCab** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall Windows cabinet (.cab) packages on a target node.</span></span>

<span data-ttu-id="489ed-106">El nodo de destino debe tener instalado el módulo PowerShell de DISM.</span><span class="sxs-lookup"><span data-stu-id="489ed-106">The target node must have the DISM PowerShell module installed.</span></span> <span data-ttu-id="489ed-107">Para información, consulte [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14) (Uso de DISM en Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="489ed-107">For information, see [Use DISM in Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).</span></span>


## <a name="syntax"></a><span data-ttu-id="489ed-108">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="489ed-108">Syntax</span></span>

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="489ed-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="489ed-109">Properties</span></span>

|  <span data-ttu-id="489ed-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="489ed-110">Property</span></span>  |  <span data-ttu-id="489ed-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="489ed-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="489ed-112">Nombre</span><span class="sxs-lookup"><span data-stu-id="489ed-112">Name</span></span>| <span data-ttu-id="489ed-113">Indica el nombre del paquete para el que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="489ed-113">Indicates the name of the package for you want to ensure a specific state.</span></span>|
| <span data-ttu-id="489ed-114">Ensure</span><span class="sxs-lookup"><span data-stu-id="489ed-114">Ensure</span></span>| <span data-ttu-id="489ed-115">Indica si el paquete está instalado.</span><span class="sxs-lookup"><span data-stu-id="489ed-115">Indicates if the package is installed.</span></span> <span data-ttu-id="489ed-116">Establezca esta propiedad en "Absent" para asegurarse de que el paquete no esté instalado (o se desinstale el paquete si está instalado).</span><span class="sxs-lookup"><span data-stu-id="489ed-116">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="489ed-117">Establézcala en "Present" (el valor predeterminado) para asegurarse de que el paquete esté instalado.</span><span class="sxs-lookup"><span data-stu-id="489ed-117">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="489ed-118">Ruta</span><span class="sxs-lookup"><span data-stu-id="489ed-118">Path</span></span>| <span data-ttu-id="489ed-119">Indica la ruta de acceso donde reside el paquete.</span><span class="sxs-lookup"><span data-stu-id="489ed-119">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="489ed-120">LogPath</span><span class="sxs-lookup"><span data-stu-id="489ed-120">LogPath</span></span>| <span data-ttu-id="489ed-121">Indica la ruta de acceso completa donde quiere que el proveedor guarde un archivo de registro para instalar o desinstalar el paquete.</span><span class="sxs-lookup"><span data-stu-id="489ed-121">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="489ed-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="489ed-122">DependsOn</span></span> | <span data-ttu-id="489ed-123">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="489ed-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="489ed-124">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es \`DependsOn = "[ResourceType]ResourceName"\`\`.</span><span class="sxs-lookup"><span data-stu-id="489ed-124">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|

## <a name="example"></a><span data-ttu-id="489ed-125">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="489ed-125">Example</span></span>

<span data-ttu-id="489ed-126">La configuración de ejemplo siguiente toma parámetros de entrada y se asegura de que el archivo .cab especificado en el parámetro `$Name` esté instalado.</span><span class="sxs-lookup"><span data-stu-id="489ed-126">The following example configuration takes input parameters, and ensures that the .cab file specified by the `$Name` parameter is installed.</span></span>

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