---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso nxScript de DSC para Linux
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077830"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="1c47b-103">Recurso nxScript de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="1c47b-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="1c47b-104">El recurso **nxScript** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para ejecutar scripts de Linux en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="1c47b-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1c47b-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="1c47b-105">Syntax</span></span>

```
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

## <a name="properties"></a><span data-ttu-id="1c47b-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="1c47b-106">Properties</span></span>

|  <span data-ttu-id="1c47b-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="1c47b-107">Property</span></span> |  <span data-ttu-id="1c47b-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="1c47b-108">Description</span></span> |
|---|---|
| <span data-ttu-id="1c47b-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="1c47b-109">GetScript</span></span>| <span data-ttu-id="1c47b-110">Proporciona un script que se ejecuta cuando se invoca el cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx).</span><span class="sxs-lookup"><span data-stu-id="1c47b-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="1c47b-111">El script debe comenzar con el par de caracteres shebang, como por ejemplo: #!/bin/bash.</span><span class="sxs-lookup"><span data-stu-id="1c47b-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="1c47b-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="1c47b-112">SetScript</span></span>| <span data-ttu-id="1c47b-113">Proporciona un script.</span><span class="sxs-lookup"><span data-stu-id="1c47b-113">Provides a script.</span></span> <span data-ttu-id="1c47b-114">Cuando se invoca el cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), el bloque **TestScript** se ejecuta primero.</span><span class="sxs-lookup"><span data-stu-id="1c47b-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="1c47b-115">Si el bloque **TestScript** devuelve un código de salida distinto de 0, se ejecutará el bloque **SetScript**.</span><span class="sxs-lookup"><span data-stu-id="1c47b-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="1c47b-116">Si el bloque **TestScript** devuelve un código de salida de 0, no se ejecutará el bloque **SetScript**.</span><span class="sxs-lookup"><span data-stu-id="1c47b-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="1c47b-117">El script debe comenzar con el par de caracteres shebang, como por ejemplo: `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="1c47b-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="1c47b-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="1c47b-118">TestScript</span></span>| <span data-ttu-id="1c47b-119">Proporciona un script.</span><span class="sxs-lookup"><span data-stu-id="1c47b-119">Provides a script.</span></span> <span data-ttu-id="1c47b-120">Cuando se invoca el cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), se ejecuta este script.</span><span class="sxs-lookup"><span data-stu-id="1c47b-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="1c47b-121">Si devuelve un código de salida distinto de 0, se ejecutará el bloque SetScript.</span><span class="sxs-lookup"><span data-stu-id="1c47b-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="1c47b-122">Si devuelve un código de salida de 0, no se ejecutará el bloque **SetScript**.</span><span class="sxs-lookup"><span data-stu-id="1c47b-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="1c47b-123">El bloque **TestScript** también se ejecuta cuando se invoca el cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx).</span><span class="sxs-lookup"><span data-stu-id="1c47b-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="1c47b-124">Sin embargo, en este caso, el bloque **SetScript** no se ejecutará, independientemente del código de salida que se devuelva del bloque **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="1c47b-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="1c47b-125">El bloque **TestScript** debe devolver un código de salida de 0 si la configuración real coincide con la configuración de estado deseado actual, y un código de salida distinto de 0 si no coincide.</span><span class="sxs-lookup"><span data-stu-id="1c47b-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="1c47b-126">(La configuración de estado deseado actual es la última configuración establecida en el nodo que está usando DSC).</span><span class="sxs-lookup"><span data-stu-id="1c47b-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="1c47b-127">El script debe comenzar con el par de caracteres shebang, como por ejemplo: 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="1c47b-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="1c47b-128">Usuario</span><span class="sxs-lookup"><span data-stu-id="1c47b-128">User</span></span>| <span data-ttu-id="1c47b-129">El usuario con el que se ejecutará el script.</span><span class="sxs-lookup"><span data-stu-id="1c47b-129">The user to run the script as.</span></span>|
| <span data-ttu-id="1c47b-130">Grupo</span><span class="sxs-lookup"><span data-stu-id="1c47b-130">Group</span></span>| <span data-ttu-id="1c47b-131">El grupo con el que se ejecutará el script.</span><span class="sxs-lookup"><span data-stu-id="1c47b-131">The group to run the script as.</span></span>|
| <span data-ttu-id="1c47b-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1c47b-132">DependsOn</span></span> | <span data-ttu-id="1c47b-133">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="1c47b-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1c47b-134">Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="1c47b-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="1c47b-135">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1c47b-135">Example</span></span>

<span data-ttu-id="1c47b-136">En el ejemplo siguiente se muestra el uso del recurso **nxScript** para realizar una administración de configuración adicional.</span><span class="sxs-lookup"><span data-stu-id="1c47b-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

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