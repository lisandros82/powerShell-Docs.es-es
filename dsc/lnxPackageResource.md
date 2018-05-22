---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso nxPackage de DSC para Linux
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="cd272-103">Recurso nxPackage de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="cd272-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="cd272-104">El recurso **nxPackage** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar paquetes en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="cd272-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd272-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="cd272-105">Syntax</span></span>

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="cd272-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="cd272-106">Properties</span></span>

|  <span data-ttu-id="cd272-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="cd272-107">Property</span></span> |  <span data-ttu-id="cd272-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="cd272-108">Description</span></span> |
|---|---|
| <span data-ttu-id="cd272-109">Nombre</span><span class="sxs-lookup"><span data-stu-id="cd272-109">Name</span></span>| <span data-ttu-id="cd272-110">El nombre del paquete para el que quiere garantizar un estado específico.</span><span class="sxs-lookup"><span data-stu-id="cd272-110">The name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="cd272-111">Ensure</span><span class="sxs-lookup"><span data-stu-id="cd272-111">Ensure</span></span>| <span data-ttu-id="cd272-112">Determina si se debe comprobar si existe el paquete.</span><span class="sxs-lookup"><span data-stu-id="cd272-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="cd272-113">Establezca esta propiedad en "Present" para asegurarse de que el paquete exista.</span><span class="sxs-lookup"><span data-stu-id="cd272-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="cd272-114">Establézcala en "Absent" para asegurarse de que el paquete no exista.</span><span class="sxs-lookup"><span data-stu-id="cd272-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="cd272-115">El valor predeterminado es "Present".</span><span class="sxs-lookup"><span data-stu-id="cd272-115">The default value is "Present".</span></span>|
| <span data-ttu-id="cd272-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="cd272-116">PackageManager</span></span>| <span data-ttu-id="cd272-117">Los valores admitidos son "yum", "apt" y "zypper".</span><span class="sxs-lookup"><span data-stu-id="cd272-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="cd272-118">Especifica el administrador de paquetes que se utilizará al instalar paquetes.</span><span class="sxs-lookup"><span data-stu-id="cd272-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="cd272-119">Si se especifica la propiedad **FilePath**, la ruta de acceso facilitada se usará para instalar el paquete.</span><span class="sxs-lookup"><span data-stu-id="cd272-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="cd272-120">De lo contrario, se utilizará un administrador de paquetes para instalar el paquete desde un repositorio configurado previamente.</span><span class="sxs-lookup"><span data-stu-id="cd272-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="cd272-121">Si no se facilitan ni **PackageManager** ni **FilePath**, se usará el administrador de paquetes predeterminado del sistema.</span><span class="sxs-lookup"><span data-stu-id="cd272-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>|
| <span data-ttu-id="cd272-122">FilePath</span><span class="sxs-lookup"><span data-stu-id="cd272-122">FilePath</span></span>| <span data-ttu-id="cd272-123">La ruta de acceso donde reside el paquete.</span><span class="sxs-lookup"><span data-stu-id="cd272-123">The file path where the package resides</span></span>|
| <span data-ttu-id="cd272-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="cd272-124">PackageGroup</span></span>| <span data-ttu-id="cd272-125">Si su valor es **$true**, se espera que el valor **Name** sea el nombre de un grupo de paquetes que se usará con un elemento **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="cd272-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="cd272-126">La propiedad **PackageGroup** no es válida cuando se proporciona un elemento **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="cd272-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>|
| <span data-ttu-id="cd272-127">Argumentos</span><span class="sxs-lookup"><span data-stu-id="cd272-127">Arguments</span></span>| <span data-ttu-id="cd272-128">Una cadena de argumentos que se pasarán al paquete tal y como se faciliten.</span><span class="sxs-lookup"><span data-stu-id="cd272-128">A string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="cd272-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="cd272-129">ReturnCode</span></span>| <span data-ttu-id="cd272-130">El código de retorno esperado.</span><span class="sxs-lookup"><span data-stu-id="cd272-130">The expected return code.</span></span> <span data-ttu-id="cd272-131">Si el código de retorno real no a coincide con el valor esperado facilitado aquí, la configuración devolverá un error.</span><span class="sxs-lookup"><span data-stu-id="cd272-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|
| <span data-ttu-id="cd272-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="cd272-132">DependsOn</span></span> | <span data-ttu-id="cd272-133">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="cd272-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="cd272-134">Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="cd272-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="cd272-135">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="cd272-135">Example</span></span>

<span data-ttu-id="cd272-136">En el ejemplo siguiente se garantiza que el paquete denominado "httpd" está instalado en un equipo Linux, mediante el administrador de paquetes "Yum".</span><span class="sxs-lookup"><span data-stu-id="cd272-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```