---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Package
ms.openlocfilehash: cfa9d53d5ea588b0ec97e5503302a451caa09e03
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-package-resource"></a><span data-ttu-id="ec608-103">Recursos de DSC Package</span><span class="sxs-lookup"><span data-stu-id="ec608-103">DSC Package Resource</span></span>

> <span data-ttu-id="ec608-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="ec608-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ec608-105">El recurso **Package** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para instalar o desinstalar paquetes, como los paquetes de Windows Installer y setup.exe, en un nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="ec608-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec608-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ec608-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="ec608-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ec608-107">Properties</span></span>
|  <span data-ttu-id="ec608-108">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ec608-108">Property</span></span>  |  <span data-ttu-id="ec608-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="ec608-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="ec608-110">Nombre</span><span class="sxs-lookup"><span data-stu-id="ec608-110">Name</span></span>| <span data-ttu-id="ec608-111">Indica el nombre del paquete para el que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="ec608-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="ec608-112">Ruta</span><span class="sxs-lookup"><span data-stu-id="ec608-112">Path</span></span>| <span data-ttu-id="ec608-113">Indica la ruta de acceso donde reside el paquete.</span><span class="sxs-lookup"><span data-stu-id="ec608-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="ec608-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="ec608-114">ProductId</span></span>| <span data-ttu-id="ec608-115">Indica el id. de producto que identifica el paquete.</span><span class="sxs-lookup"><span data-stu-id="ec608-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="ec608-116">Argumentos</span><span class="sxs-lookup"><span data-stu-id="ec608-116">Arguments</span></span>| <span data-ttu-id="ec608-117">Muestra una cadena de argumentos que se pasarán al paquete tal y como se faciliten.</span><span class="sxs-lookup"><span data-stu-id="ec608-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="ec608-118">Credential</span><span class="sxs-lookup"><span data-stu-id="ec608-118">Credential</span></span>| <span data-ttu-id="ec608-119">Proporciona acceso al paquete en un origen remoto.</span><span class="sxs-lookup"><span data-stu-id="ec608-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="ec608-120">Esta propiedad no se utiliza para instalar el paquete.</span><span class="sxs-lookup"><span data-stu-id="ec608-120">This property is not used to install the package.</span></span> <span data-ttu-id="ec608-121">El paquete siempre se instala en el sistema local.</span><span class="sxs-lookup"><span data-stu-id="ec608-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="ec608-122">Ensure</span><span class="sxs-lookup"><span data-stu-id="ec608-122">Ensure</span></span>| <span data-ttu-id="ec608-123">Indica si el paquete está instalado.</span><span class="sxs-lookup"><span data-stu-id="ec608-123">Indicates if the package is installed.</span></span> <span data-ttu-id="ec608-124">Establezca esta propiedad en "Absent" para asegurarse de que el paquete no esté instalado (o se desinstale el paquete si está instalado).</span><span class="sxs-lookup"><span data-stu-id="ec608-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="ec608-125">Establézcala en "Present" (el valor predeterminado) para asegurarse de que el paquete esté instalado.</span><span class="sxs-lookup"><span data-stu-id="ec608-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="ec608-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="ec608-126">LogPath</span></span>| <span data-ttu-id="ec608-127">Indica la ruta de acceso completa donde quiere que el proveedor guarde un archivo de registro para instalar o desinstalar el paquete.</span><span class="sxs-lookup"><span data-stu-id="ec608-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="ec608-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ec608-128">DependsOn</span></span> | <span data-ttu-id="ec608-129">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="ec608-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ec608-130">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es \`DependsOn = "[ResourceType]ResourceName"\`\`.</span><span class="sxs-lookup"><span data-stu-id="ec608-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|
| <span data-ttu-id="ec608-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="ec608-131">ReturnCode</span></span>| <span data-ttu-id="ec608-132">Indica el código de retorno esperado.</span><span class="sxs-lookup"><span data-stu-id="ec608-132">Indicates the expected return code.</span></span> <span data-ttu-id="ec608-133">Si el código de retorno real no a coincide con el valor esperado facilitado aquí, la configuración devolverá un error.</span><span class="sxs-lookup"><span data-stu-id="ec608-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="ec608-134">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ec608-134">Example</span></span>

<span data-ttu-id="ec608-135">En este ejemplo se ejecuta al instalador .msi que se encuentra en la ruta de acceso especificada y tiene el identificador de producto especificado.</span><span class="sxs-lookup"><span data-stu-id="ec608-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

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