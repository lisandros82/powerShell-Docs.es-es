---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso nxScript de DSC para Linux
ms.openlocfilehash: a7f2114aba47bb581cdd19168e784b79dfc5b6ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953192"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="c72a8-103">Recurso nxScript de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="c72a8-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="c72a8-104">El recurso **nxScript** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para ejecutar scripts de Linux en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="c72a8-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c72a8-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c72a8-105">Syntax</span></span>

```Syntax
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="c72a8-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="c72a8-106">Properties</span></span>

|<span data-ttu-id="c72a8-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="c72a8-107">Property</span></span> |<span data-ttu-id="c72a8-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="c72a8-108">Description</span></span> |
|---|---|
|<span data-ttu-id="c72a8-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="c72a8-109">GetScript</span></span> |<span data-ttu-id="c72a8-110">Proporciona un script para devolver el estado actual de la máquina.</span><span class="sxs-lookup"><span data-stu-id="c72a8-110">Provides a script to return current status of the machine.</span></span> <span data-ttu-id="c72a8-111">Este script se ejecuta al invocar el script [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer).</span><span class="sxs-lookup"><span data-stu-id="c72a8-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="c72a8-112">El script debe comenzar con el par de caracteres shebang, como por ejemplo: `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="c72a8-112">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="c72a8-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="c72a8-113">SetScript</span></span> |<span data-ttu-id="c72a8-114">Proporciona un script que define el estado correcto de la máquina.</span><span class="sxs-lookup"><span data-stu-id="c72a8-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="c72a8-115">Cuando se invoca el script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), el bloque **TestScript** se ejecuta primero.</span><span class="sxs-lookup"><span data-stu-id="c72a8-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="c72a8-116">Si el bloque **TestScript** devuelve un código de salida distinto de 0, se ejecutará el bloque **SetScript**.</span><span class="sxs-lookup"><span data-stu-id="c72a8-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="c72a8-117">Si el bloque **TestScript** devuelve un código de salida de 0, no se ejecutará el bloque **SetScript**.</span><span class="sxs-lookup"><span data-stu-id="c72a8-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="c72a8-118">El script debe comenzar con el par de caracteres shebang, como por ejemplo: `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="c72a8-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="c72a8-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="c72a8-119">TestScript</span></span> |<span data-ttu-id="c72a8-120">Proporciona un script que evalúa si el nodo tiene actualmente el estado correcto.</span><span class="sxs-lookup"><span data-stu-id="c72a8-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="c72a8-121">Cuando se invoca el script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), este se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="c72a8-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="c72a8-122">Si devuelve un código de salida distinto de 0, se ejecutará el bloque **SetScript**.</span><span class="sxs-lookup"><span data-stu-id="c72a8-122">If it returns an exit code other than 0, the **SetScript** will run.</span></span> <span data-ttu-id="c72a8-123">Si devuelve un código de salida de 0, no se ejecutará el bloque **SetScript**.</span><span class="sxs-lookup"><span data-stu-id="c72a8-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="c72a8-124">El bloque **TestScript** también se ejecuta cuando se invoca el script [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer).</span><span class="sxs-lookup"><span data-stu-id="c72a8-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="c72a8-125">Sin embargo, en este caso, el bloque **SetScript** no se ejecutará, independientemente del código de salida que se devuelva del bloque **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="c72a8-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="c72a8-126">El bloque **TestScript** debe tener contenido y debe devolver un código de salida de 0 si la configuración real coincide con la configuración del estado deseado actual, y un código de salida distinto de 0 si no coincide.</span><span class="sxs-lookup"><span data-stu-id="c72a8-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="c72a8-127">La configuración de estado deseado actual es la última configuración establecida en el nodo que está usando DSC.</span><span class="sxs-lookup"><span data-stu-id="c72a8-127">The current desired state configuration is the last configuration enacted on the node that is using DSC.</span></span> <span data-ttu-id="c72a8-128">El script debe comenzar con el par de caracteres shebang, como por ejemplo: `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="c72a8-128">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="c72a8-129">Usuario</span><span class="sxs-lookup"><span data-stu-id="c72a8-129">User</span></span> |<span data-ttu-id="c72a8-130">El usuario con el que se ejecutará el script.</span><span class="sxs-lookup"><span data-stu-id="c72a8-130">The user to run the script as.</span></span> |
|<span data-ttu-id="c72a8-131">Grupo</span><span class="sxs-lookup"><span data-stu-id="c72a8-131">Group</span></span> |<span data-ttu-id="c72a8-132">El grupo con el que se ejecutará el script.</span><span class="sxs-lookup"><span data-stu-id="c72a8-132">The group to run the script as.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="c72a8-133">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="c72a8-133">Common properties</span></span>

|<span data-ttu-id="c72a8-134">Propiedad</span><span class="sxs-lookup"><span data-stu-id="c72a8-134">Property</span></span> |<span data-ttu-id="c72a8-135">Descripción</span><span class="sxs-lookup"><span data-stu-id="c72a8-135">Description</span></span> |
|---|---|
|<span data-ttu-id="c72a8-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c72a8-136">DependsOn</span></span> |<span data-ttu-id="c72a8-137">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="c72a8-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c72a8-138">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c72a8-138">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="c72a8-139">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c72a8-139">Example</span></span>

<span data-ttu-id="c72a8-140">En el ejemplo siguiente se muestra el uso del recurso **nxScript** para realizar una administración de configuración adicional.</span><span class="sxs-lookup"><span data-stu-id="c72a8-140">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
    }
}
```
