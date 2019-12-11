---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Package
ms.openlocfilehash: efac07b4b051564cadd5aa1542a6afda6cd453ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953152"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="42031-103">Recursos de DSC Package</span><span class="sxs-lookup"><span data-stu-id="42031-103">DSC Package Resource</span></span>

> <span data-ttu-id="42031-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="42031-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="42031-105">El recurso **Package** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para instalar o desinstalar paquetes, como los paquetes de Windows Installer y setup.exe, en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="42031-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="42031-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="42031-106">Syntax</span></span>

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="42031-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="42031-107">Properties</span></span>

|<span data-ttu-id="42031-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="42031-108">Property</span></span> |<span data-ttu-id="42031-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="42031-109">Description</span></span> |
|---|---|
|<span data-ttu-id="42031-110">Nombre</span><span class="sxs-lookup"><span data-stu-id="42031-110">Name</span></span> |<span data-ttu-id="42031-111">Indica el nombre del paquete para el que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="42031-111">Indicates the name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="42031-112">Ruta</span><span class="sxs-lookup"><span data-stu-id="42031-112">Path</span></span> |<span data-ttu-id="42031-113">Indica la ruta de acceso donde reside el paquete.</span><span class="sxs-lookup"><span data-stu-id="42031-113">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="42031-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="42031-114">ProductId</span></span> |<span data-ttu-id="42031-115">Indica el id. de producto que identifica el paquete.</span><span class="sxs-lookup"><span data-stu-id="42031-115">Indicates the product ID that uniquely identifies the package.</span></span> |
|<span data-ttu-id="42031-116">Argumentos</span><span class="sxs-lookup"><span data-stu-id="42031-116">Arguments</span></span> |<span data-ttu-id="42031-117">Muestra una cadena de argumentos que se pasarán al paquete tal y como se faciliten.</span><span class="sxs-lookup"><span data-stu-id="42031-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="42031-118">Credential</span><span class="sxs-lookup"><span data-stu-id="42031-118">Credential</span></span> |<span data-ttu-id="42031-119">Proporciona acceso al paquete en un origen remoto.</span><span class="sxs-lookup"><span data-stu-id="42031-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="42031-120">Esta propiedad no se utiliza para instalar el paquete.</span><span class="sxs-lookup"><span data-stu-id="42031-120">This property is not used to install the package.</span></span> <span data-ttu-id="42031-121">El paquete siempre se instala en el sistema local.</span><span class="sxs-lookup"><span data-stu-id="42031-121">The package is always installed on the local system.</span></span> |
|<span data-ttu-id="42031-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="42031-122">LogPath</span></span> |<span data-ttu-id="42031-123">Indica la ruta de acceso completa donde quiere que el proveedor guarde un archivo de registro para instalar o desinstalar el paquete.</span><span class="sxs-lookup"><span data-stu-id="42031-123">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |
|<span data-ttu-id="42031-124">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="42031-124">ReturnCode</span></span> |<span data-ttu-id="42031-125">Indica el código de retorno esperado.</span><span class="sxs-lookup"><span data-stu-id="42031-125">Indicates the expected return code.</span></span> <span data-ttu-id="42031-126">Si el código de retorno real no a coincide con el valor esperado facilitado aquí, la configuración devolverá un error.</span><span class="sxs-lookup"><span data-stu-id="42031-126">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="42031-127">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="42031-127">Common properties</span></span>

|<span data-ttu-id="42031-128">Propiedad</span><span class="sxs-lookup"><span data-stu-id="42031-128">Property</span></span> |<span data-ttu-id="42031-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="42031-129">Description</span></span> |
|---|---|
|<span data-ttu-id="42031-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="42031-130">DependsOn</span></span> |<span data-ttu-id="42031-131">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="42031-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="42031-132">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="42031-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="42031-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="42031-133">Ensure</span></span> |<span data-ttu-id="42031-134">Indica si el paquete está instalado.</span><span class="sxs-lookup"><span data-stu-id="42031-134">Indicates if the package is installed.</span></span> <span data-ttu-id="42031-135">Establezca esta propiedad en**Absent** para asegurarse de que el paquete no esté instalado (o se desinstale el paquete si está instalado).</span><span class="sxs-lookup"><span data-stu-id="42031-135">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="42031-136">Establézcala en **Present** para asegurarse de que el paquete esté instalado.</span><span class="sxs-lookup"><span data-stu-id="42031-136">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="42031-137">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="42031-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="42031-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="42031-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="42031-139">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="42031-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="42031-140">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="42031-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="42031-141">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="42031-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="42031-142">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="42031-142">Example</span></span>

<span data-ttu-id="42031-143">En este ejemplo se ejecuta al instalador .msi que se encuentra en la ruta de acceso especificada y tiene el identificador de producto especificado.</span><span class="sxs-lookup"><span data-stu-id="42031-143">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```