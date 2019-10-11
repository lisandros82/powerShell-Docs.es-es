---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso nxPackage de DSC para Linux
ms.openlocfilehash: 4091cbbd5e34a84b9011870da4bda93281378347
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954822"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="3430c-103">Recurso nxPackage de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="3430c-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="3430c-104">El recurso **nxPackage** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar paquetes en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="3430c-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="3430c-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="3430c-105">Syntax</span></span>

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="3430c-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="3430c-106">Properties</span></span>

|<span data-ttu-id="3430c-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="3430c-107">Property</span></span> |<span data-ttu-id="3430c-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="3430c-108">Description</span></span> |
|---|---|
|<span data-ttu-id="3430c-109">Nombre</span><span class="sxs-lookup"><span data-stu-id="3430c-109">Name</span></span> |<span data-ttu-id="3430c-110">El nombre del paquete para el que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="3430c-110">The name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="3430c-111">PackageManager</span><span class="sxs-lookup"><span data-stu-id="3430c-111">PackageManager</span></span> |<span data-ttu-id="3430c-112">Los valores admitidos son **yum**, **apt** y **zypper**.</span><span class="sxs-lookup"><span data-stu-id="3430c-112">Supported values are **yum**, **apt**, and **zypper**.</span></span> <span data-ttu-id="3430c-113">Especifica el administrador de paquetes que se utilizará al instalar paquetes.</span><span class="sxs-lookup"><span data-stu-id="3430c-113">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="3430c-114">Si se especifica la propiedad **FilePath**, la ruta de acceso facilitada se usará para instalar el paquete.</span><span class="sxs-lookup"><span data-stu-id="3430c-114">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="3430c-115">De lo contrario, se utilizará un administrador de paquetes para instalar el paquete desde un repositorio configurado previamente.</span><span class="sxs-lookup"><span data-stu-id="3430c-115">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="3430c-116">Si no se facilitan ni **PackageManager** ni **FilePath**, se usará el administrador de paquetes predeterminado del sistema.</span><span class="sxs-lookup"><span data-stu-id="3430c-116">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span> |
|<span data-ttu-id="3430c-117">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="3430c-117">PackageGroup</span></span> |<span data-ttu-id="3430c-118">Si su valor es `$true`, se espera que el valor **Name** sea el nombre de un grupo de paquetes que se usará con un elemento **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="3430c-118">If `$true`, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="3430c-119">La propiedad **PackageGroup** no es válida cuando se proporciona un elemento **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="3430c-119">**PackageGroup** is not valid when providing a **FilePath**.</span></span> |
|<span data-ttu-id="3430c-120">Argumentos</span><span class="sxs-lookup"><span data-stu-id="3430c-120">Arguments</span></span> |<span data-ttu-id="3430c-121">Una cadena de argumentos que se pasarán al paquete tal y como se faciliten.</span><span class="sxs-lookup"><span data-stu-id="3430c-121">A string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="3430c-122">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="3430c-122">ReturnCode</span></span> |<span data-ttu-id="3430c-123">El código de retorno esperado.</span><span class="sxs-lookup"><span data-stu-id="3430c-123">The expected return code.</span></span> <span data-ttu-id="3430c-124">Si el código de retorno real no a coincide con el valor esperado facilitado aquí, la configuración devolverá un error.</span><span class="sxs-lookup"><span data-stu-id="3430c-124">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |
|<span data-ttu-id="3430c-125">FilePath</span><span class="sxs-lookup"><span data-stu-id="3430c-125">FilePath</span></span> |<span data-ttu-id="3430c-126">La ruta de acceso donde reside el paquete.</span><span class="sxs-lookup"><span data-stu-id="3430c-126">The file path where the package resides.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="3430c-127">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="3430c-127">Common properties</span></span>

|<span data-ttu-id="3430c-128">Propiedad</span><span class="sxs-lookup"><span data-stu-id="3430c-128">Property</span></span> |<span data-ttu-id="3430c-129">Descripción</span><span class="sxs-lookup"><span data-stu-id="3430c-129">Description</span></span> |
|---|---|
|<span data-ttu-id="3430c-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="3430c-130">DependsOn</span></span> |<span data-ttu-id="3430c-131">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="3430c-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="3430c-132">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="3430c-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="3430c-133">Ensure</span><span class="sxs-lookup"><span data-stu-id="3430c-133">Ensure</span></span> |<span data-ttu-id="3430c-134">Determina si se debe comprobar si existe el paquete.</span><span class="sxs-lookup"><span data-stu-id="3430c-134">Determines whether to check if the package exists.</span></span> <span data-ttu-id="3430c-135">Establezca esta propiedad en **Present** para asegurarse de que el paquete exista.</span><span class="sxs-lookup"><span data-stu-id="3430c-135">Set this property to **Present** to ensure the package exists.</span></span> <span data-ttu-id="3430c-136">Establézcala en **Absent** para asegurarse de que el paquete no exista.</span><span class="sxs-lookup"><span data-stu-id="3430c-136">Set it to **Absent** to ensure the package does not exist.</span></span> <span data-ttu-id="3430c-137">El valor predeterminado es **Present**.</span><span class="sxs-lookup"><span data-stu-id="3430c-137">The default value is **Present**.</span></span> |

## <a name="example"></a><span data-ttu-id="3430c-138">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="3430c-138">Example</span></span>

<span data-ttu-id="3430c-139">En el ejemplo siguiente se garantiza que el paquete denominado "httpd" está instalado en un equipo Linux, mediante el administrador de paquetes "Yum".</span><span class="sxs-lookup"><span data-stu-id="3430c-139">The following example ensures that the package named "httpd" is installed on a Linux computer, using the "Yum" package manager.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```