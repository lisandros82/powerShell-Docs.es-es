---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Script
ms.openlocfilehash: 1163d454972d8ee519d1c55b77bb85979faf3536
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189455"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="51cdf-103">Recurso de DSC Script</span><span class="sxs-lookup"><span data-stu-id="51cdf-103">DSC Script Resource</span></span>


> <span data-ttu-id="51cdf-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="51cdf-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="51cdf-105">El recurso **Script** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para ejecutar bloques de script de Windows PowerShell en nodos de destino.</span><span class="sxs-lookup"><span data-stu-id="51cdf-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="51cdf-106">El recurso `Script` tiene las propiedades `GetScript`, `SetScript` y `TestScript`.</span><span class="sxs-lookup"><span data-stu-id="51cdf-106">The `Script` resource has `GetScript`, `SetScript`, and `TestScript` properties.</span></span> <span data-ttu-id="51cdf-107">Estas propiedades se deben establecer en los bloques de script que se ejecutarán en cada nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="51cdf-107">These properties should be set to script blocks that will run on each target node.</span></span>

<span data-ttu-id="51cdf-108">El bloque de script `GetScript` debe devolver una tabla hash que representa el estado del nodo actual.</span><span class="sxs-lookup"><span data-stu-id="51cdf-108">The `GetScript` script block should return a hashtable representing the state of the current node.</span></span> <span data-ttu-id="51cdf-109">La tabla hash solo debe contener una clave `Result` y el valor debe ser del tipo `String`.</span><span class="sxs-lookup"><span data-stu-id="51cdf-109">The hashtable must only contain one key `Result` and the value must be of type `String`.</span></span> <span data-ttu-id="51cdf-110">No es necesario devolver nada.</span><span class="sxs-lookup"><span data-stu-id="51cdf-110">It is not required to return anything.</span></span> <span data-ttu-id="51cdf-111">DSC no hace nada con la salida de este bloque de script.</span><span class="sxs-lookup"><span data-stu-id="51cdf-111">DSC doesn't do anything with the output of this script block.</span></span>

<span data-ttu-id="51cdf-112">El bloque de script `TestScript` debe determinar si es necesario modificar el nodo actual.</span><span class="sxs-lookup"><span data-stu-id="51cdf-112">The `TestScript` script block should determine if the current node needs to be modified.</span></span> <span data-ttu-id="51cdf-113">Debe devolver `$true` si el nodo está actualizado.</span><span class="sxs-lookup"><span data-stu-id="51cdf-113">It should return `$true` if the node is up-to-date.</span></span> <span data-ttu-id="51cdf-114">Debe devolver `$false` si la configuración del nodo está obsoleta y debe actualizarse por el bloque de script `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="51cdf-114">It should return `$false` if the node's configuration is out-of-date and should be updated by the `SetScript` script block.</span></span> <span data-ttu-id="51cdf-115">El bloque de script `TestScript` se invoca mediante el DSC.</span><span class="sxs-lookup"><span data-stu-id="51cdf-115">The `TestScript` script block is called by DSC.</span></span>

<span data-ttu-id="51cdf-116">El bloque de script `SetScript` debe modificar el nodo.</span><span class="sxs-lookup"><span data-stu-id="51cdf-116">The `SetScript` script block should modify the node.</span></span> <span data-ttu-id="51cdf-117">Se invoca mediante el DSC si el bloque `TestScript` devuelve `$false`.</span><span class="sxs-lookup"><span data-stu-id="51cdf-117">It is called by DSC if the `TestScript` block return `$false`.</span></span>

<span data-ttu-id="51cdf-118">Si necesita usar variables desde el script de configuración en los bloques de script `GetScript`, `TestScript` o `SetScript`, use el ámbito `$using:` (consulte el ejemplo siguiente).</span><span class="sxs-lookup"><span data-stu-id="51cdf-118">If you need to use variables from your configuration script in the `GetScript`, `TestScript`, or `SetScript` script blocks, use the `$using:` scope (see below for an example).</span></span>


## <a name="syntax"></a><span data-ttu-id="51cdf-119">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="51cdf-119">Syntax</span></span>

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="51cdf-120">Propiedades</span><span class="sxs-lookup"><span data-stu-id="51cdf-120">Properties</span></span>

|  <span data-ttu-id="51cdf-121">Propiedad</span><span class="sxs-lookup"><span data-stu-id="51cdf-121">Property</span></span>  |  <span data-ttu-id="51cdf-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="51cdf-122">Description</span></span>   |
|---|---|
| <span data-ttu-id="51cdf-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="51cdf-123">GetScript</span></span>| <span data-ttu-id="51cdf-124">Proporciona un script de bloque de Windows PowerShell que se ejecuta cuando se invoca el cmdlet [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx).</span><span class="sxs-lookup"><span data-stu-id="51cdf-124">Provides a block of Windows PowerShell script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/library/dn407379.aspx) cmdlet.</span></span> <span data-ttu-id="51cdf-125">Este bloque debe devolver una tabla hash.</span><span class="sxs-lookup"><span data-stu-id="51cdf-125">This block must return a hashtable.</span></span> <span data-ttu-id="51cdf-126">La tabla hash solo debe contener una clave **Result** y el valor debe ser del tipo **Cadena**.</span><span class="sxs-lookup"><span data-stu-id="51cdf-126">The hashtable must only contain one key **Result** and the value must be of type **String**.</span></span>|
| <span data-ttu-id="51cdf-127">SetScript</span><span class="sxs-lookup"><span data-stu-id="51cdf-127">SetScript</span></span>| <span data-ttu-id="51cdf-128">Proporciona un bloque de script de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51cdf-128">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="51cdf-129">Cuando se invoca el cmdlet [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx), el bloque **TestScript** se ejecuta primero.</span><span class="sxs-lookup"><span data-stu-id="51cdf-129">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, the **TestScript** block runs first.</span></span> <span data-ttu-id="51cdf-130">Si el bloque **TestScript** devuelve **$false**, se ejecutará el bloque **SetScript**.</span><span class="sxs-lookup"><span data-stu-id="51cdf-130">If the **TestScript** block returns **$false**, the **SetScript** block will run.</span></span> <span data-ttu-id="51cdf-131">Si el bloque **TestScript** devuelve **$true**, no se ejecutará el bloque **SetScript**.</span><span class="sxs-lookup"><span data-stu-id="51cdf-131">If the **TestScript** block returns **$true**, the **SetScript** block will not run.</span></span>|
| <span data-ttu-id="51cdf-132">TestScript</span><span class="sxs-lookup"><span data-stu-id="51cdf-132">TestScript</span></span>| <span data-ttu-id="51cdf-133">Proporciona un bloque de script de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51cdf-133">Provides a block of Windows PowerShell script.</span></span> <span data-ttu-id="51cdf-134">Cuando se invoca el cmdlet [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx), se ejecuta este bloque.</span><span class="sxs-lookup"><span data-stu-id="51cdf-134">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, this block runs.</span></span> <span data-ttu-id="51cdf-135">Si devuelve **$false**, se ejecutará el bloque SetScript.</span><span class="sxs-lookup"><span data-stu-id="51cdf-135">If it returns **$false**, the SetScript block will run.</span></span> <span data-ttu-id="51cdf-136">Si devuelve **$true**, no se ejecutará el bloque SetScript.</span><span class="sxs-lookup"><span data-stu-id="51cdf-136">If it returns **$true**, the SetScript block will not run.</span></span> <span data-ttu-id="51cdf-137">El bloque **TestScript** también se ejecuta cuando se invoca el cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx).</span><span class="sxs-lookup"><span data-stu-id="51cdf-137">The **TestScript** block also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="51cdf-138">Sin embargo, en este caso, el bloque **SetScript** no se ejecutará, independientemente del valor que devuelva el bloque TestScript.</span><span class="sxs-lookup"><span data-stu-id="51cdf-138">However, in this case, the **SetScript** block will not run, no matter what value the TestScript block returns.</span></span> <span data-ttu-id="51cdf-139">El bloque **TestScript** debe devolver True si la configuración real coincide con la configuración de estado deseado actual, y False si no coincide.</span><span class="sxs-lookup"><span data-stu-id="51cdf-139">The **TestScript** block must return True if the actual configuration matches the current desired state configuration, and False if it does not match.</span></span> <span data-ttu-id="51cdf-140">(La configuración de estado deseado actual es la última configuración establecida en el nodo que está usando DSC).</span><span class="sxs-lookup"><span data-stu-id="51cdf-140">(The current desired state configuration is the last configuration enacted on the node that is using DSC.)</span></span>|
| <span data-ttu-id="51cdf-141">Credential</span><span class="sxs-lookup"><span data-stu-id="51cdf-141">Credential</span></span>| <span data-ttu-id="51cdf-142">Indica las credenciales que se usan para ejecutar este script, si se necesitan credenciales.</span><span class="sxs-lookup"><span data-stu-id="51cdf-142">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
| <span data-ttu-id="51cdf-143">DependsOn</span><span class="sxs-lookup"><span data-stu-id="51cdf-143">DependsOn</span></span>| <span data-ttu-id="51cdf-144">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="51cdf-144">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="51cdf-145">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="51cdf-145">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

## <a name="example-1"></a><span data-ttu-id="51cdf-146">Ejemplo 1</span><span class="sxs-lookup"><span data-stu-id="51cdf-146">Example 1</span></span>
```powershell
Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script ScriptExample
    {
        SetScript =
        {
            $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
            $sw.WriteLine("Some sample string")
            $sw.Close()
        }
        TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
        GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
    }
}
```

## <a name="example-2"></a><span data-ttu-id="51cdf-147">Ejemplo 2</span><span class="sxs-lookup"><span data-stu-id="51cdf-147">Example 2</span></span>
```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource –ModuleName 'PSDesiredStateConfiguration'

    Script UpdateConfigurationVersion
    {
        GetScript = {
            $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            return @{ 'Result' = "$currentVersion" }
        }
        TestScript = {
            $state = $GetScript
            if( $state['Result'] -eq $using:version )
            {
                Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                return $true
            }
            Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
            return $false
        }
        SetScript = {
            $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        }
    }
}
```

<span data-ttu-id="51cdf-148">Este recurso está escribiendo la versión de la configuración en un archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="51cdf-148">This resource is writing the configuration's version to a text file.</span></span> <span data-ttu-id="51cdf-149">Esta versión está disponible en el equipo cliente, pero no en cualquiera de los nodos, por lo que debe pasarse a cada uno de los bloques de script del recurso `Script` con el ámbito `using` de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="51cdf-149">This version is available on the client computer, but isn't on any of the nodes, so it has to be passed to each of the `Script` resource's script blocks with PowerShell's `using` scope.</span></span> <span data-ttu-id="51cdf-150">Al generar el archivo MOF del nodo, el valor de la variable `$version` se lee desde un archivo de texto en el equipo cliente.</span><span class="sxs-lookup"><span data-stu-id="51cdf-150">When generating the node's MOF file, the value of the `$version` variable is read from a text file on the client computer.</span></span> <span data-ttu-id="51cdf-151">DSC reemplaza las variables de `$using:version` en cada bloque de script con el valor de la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="51cdf-151">DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>