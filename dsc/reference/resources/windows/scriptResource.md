---
ms.date: 08/24/2018
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Script
ms.openlocfilehash: 4eee5625add4d96ade7ababf7f534f597a26712d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076997"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="031ee-103">Recurso de DSC Script</span><span class="sxs-lookup"><span data-stu-id="031ee-103">DSC Script Resource</span></span>

> <span data-ttu-id="031ee-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="031ee-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="031ee-105">El recurso **Script** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para ejecutar bloques de script de Windows PowerShell en nodos de destino.</span><span class="sxs-lookup"><span data-stu-id="031ee-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="031ee-106">El recurso **Script** utiliza las propiedades `GetScript`, `SetScript` y `TestScript` que contienen bloques de scripts que se definen para realizar las operaciones de estado DSC correspondientes.</span><span class="sxs-lookup"><span data-stu-id="031ee-106">The **Script** resource uses `GetScript`, `SetScript`, and `TestScript` properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="031ee-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="031ee-107">Syntax</span></span>

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

> [!NOTE]
> <span data-ttu-id="031ee-108">Los bloques `GetScript`, `TestScript` y `SetScript` se almacenan como cadenas.</span><span class="sxs-lookup"><span data-stu-id="031ee-108">The `GetScript`, `TestScript`, and `SetScript` blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="031ee-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="031ee-109">Properties</span></span>

|<span data-ttu-id="031ee-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="031ee-110">Property</span></span>|<span data-ttu-id="031ee-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="031ee-111">Description</span></span>|
|--------|-----------|
|<span data-ttu-id="031ee-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="031ee-112">GetScript</span></span>|<span data-ttu-id="031ee-113">Un bloque de scripts que devuelve el estado actual del nodo.</span><span class="sxs-lookup"><span data-stu-id="031ee-113">A script block that returns the current state of the Node.</span></span>|
|<span data-ttu-id="031ee-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="031ee-114">SetScript</span></span>|<span data-ttu-id="031ee-115">Un bloque de scripts que usa DSC para aplicar el cumplimiento cuando el nodo no está en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="031ee-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span>|
|<span data-ttu-id="031ee-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="031ee-116">TestScript</span></span>|<span data-ttu-id="031ee-117">Un bloque de scripts que determina si el nodo está en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="031ee-117">A script block that determines if the Node is in the desired state.</span></span>|
|<span data-ttu-id="031ee-118">Credential</span><span class="sxs-lookup"><span data-stu-id="031ee-118">Credential</span></span>| <span data-ttu-id="031ee-119">Indica las credenciales que se usan para ejecutar este script, si se necesitan credenciales.</span><span class="sxs-lookup"><span data-stu-id="031ee-119">Indicates the credentials to use for running this script, if credentials are required.</span></span>|
|<span data-ttu-id="031ee-120">DependsOn</span><span class="sxs-lookup"><span data-stu-id="031ee-120">DependsOn</span></span>| <span data-ttu-id="031ee-121">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="031ee-121">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="031ee-122">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="031ee-122">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>

### <a name="getscript"></a><span data-ttu-id="031ee-123">GetScript</span><span class="sxs-lookup"><span data-stu-id="031ee-123">GetScript</span></span>

<span data-ttu-id="031ee-124">DSC no utiliza la salida de `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="031ee-124">DSC does not use the output from `GetScript`.</span></span> <span data-ttu-id="031ee-125">El cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) ejecuta `GetScript` para recuperar el estado actual de un nodo.</span><span class="sxs-lookup"><span data-stu-id="031ee-125">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes the `GetScript` to retrieve a node's current state.</span></span> <span data-ttu-id="031ee-126">Un valor devuelto no es necesario de `GetScript`.</span><span class="sxs-lookup"><span data-stu-id="031ee-126">A return value is not required from `GetScript`.</span></span> <span data-ttu-id="031ee-127">Si especifica un valor devuelto, debe ser un `hashtable` que contenga una tecla **Result** cuyo valor sea `String`.</span><span class="sxs-lookup"><span data-stu-id="031ee-127">If you specify a return value, it must be a `hashtable` containing a **Result** key whose value is a `String`.</span></span>

### <a name="testscript"></a><span data-ttu-id="031ee-128">TestScript</span><span class="sxs-lookup"><span data-stu-id="031ee-128">TestScript</span></span>

<span data-ttu-id="031ee-129">DSC ejecuta el `TestScript` para determinar si se debe ejecutar el `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="031ee-129">The `TestScript` is executed by DSC to determine if the `SetScript` should be run.</span></span> <span data-ttu-id="031ee-130">Si `TestScript` devuelve `$false`, DSC ejecuta el `SetScript` para devolver al nodo al estado deseado.</span><span class="sxs-lookup"><span data-stu-id="031ee-130">If the `TestScript` returns `$false`, DSC executes the `SetScript` to bring the node back to the desired state.</span></span> <span data-ttu-id="031ee-131">Debe devolver un valor `boolean`.</span><span class="sxs-lookup"><span data-stu-id="031ee-131">It must return a `boolean` value.</span></span> <span data-ttu-id="031ee-132">Un resultado de `$true` indica que el nodo es compatible y que `SetScript` no debe ejecutar.</span><span class="sxs-lookup"><span data-stu-id="031ee-132">A result of `$true` indicates that the node is compliant and `SetScript` should not executed.</span></span>

<span data-ttu-id="031ee-133">El cmdlet [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) ejecuta el `TestScript` para recuperar el cumplimiento de los nodos con los recursos **Script**.</span><span class="sxs-lookup"><span data-stu-id="031ee-133">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes the `TestScript` to retrieve the nodes compliance with the  **Script** resources.</span></span> <span data-ttu-id="031ee-134">Sin embargo, en este caso, el `SetScript` no se ejecuta, con independencia de lo que devuelva el bloque `TestScript`.</span><span class="sxs-lookup"><span data-stu-id="031ee-134">However, in this case, the `SetScript` does not run, no matter what the `TestScript` block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="031ee-135">Toda la salida de su `TestScript` es parte de su valor devuelto.</span><span class="sxs-lookup"><span data-stu-id="031ee-135">All output from your `TestScript` is part of its return value.</span></span> <span data-ttu-id="031ee-136">PowerShell interpreta la salida no suprimida como distinta de cero, lo que significa que `TestScript` devolverá `$true`, con independencia del estado del nodo.</span><span class="sxs-lookup"><span data-stu-id="031ee-136">PowerShell interprets unsuppressed output as non-zero, which means that your `TestScript` will return `$true` regardless of your node's state.</span></span>
> <span data-ttu-id="031ee-137">Esto da como resultado resultados impredecibles, falsos positivos y dificulta la resolución de problemas.</span><span class="sxs-lookup"><span data-stu-id="031ee-137">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

### <a name="setscript"></a><span data-ttu-id="031ee-138">SetScript</span><span class="sxs-lookup"><span data-stu-id="031ee-138">SetScript</span></span>

<span data-ttu-id="031ee-139">El `SetScript` modifica el nodo para aplicar el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="031ee-139">The `SetScript` modifies the node to enforce the desired state.</span></span> <span data-ttu-id="031ee-140">Se invoca mediante el DSC si el bloque de scripts `TestScript` devuelve `$false`.</span><span class="sxs-lookup"><span data-stu-id="031ee-140">It is called by DSC if the `TestScript` script block returns `$false`.</span></span> <span data-ttu-id="031ee-141">El `SetScript` no debe tener ningún valor devuelto.</span><span class="sxs-lookup"><span data-stu-id="031ee-141">The `SetScript` should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="031ee-142">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="031ee-142">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="031ee-143">Ejemplo 1: Escribir texto de ejemplo con un recurso de Script</span><span class="sxs-lookup"><span data-stu-id="031ee-143">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="031ee-144">En este ejemplo se comprueba la existencia de `C:\TempFolder\TestFile.txt` en cada nodo.</span><span class="sxs-lookup"><span data-stu-id="031ee-144">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="031ee-145">Si no existe, se crea mediante el `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="031ee-145">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="031ee-146">El `GetScript` devuelve el contenido del archivo y su valor devuelto no se utiliza.</span><span class="sxs-lookup"><span data-stu-id="031ee-146">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="031ee-147">Ejemplo 2: Comparar la información de versión con un recurso de Script</span><span class="sxs-lookup"><span data-stu-id="031ee-147">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="031ee-148">En este ejemplo se recupera la información de la versión *compatible* de un archivo de texto en el equipo de creación y la almacena en la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="031ee-148">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="031ee-149">Al generar el archivo MOF del nodo, DSC reemplaza las variables de `$using:version` en cada bloque de scripts con el valor de la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="031ee-149">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span> <span data-ttu-id="031ee-150">Durante la ejecución, la versión *compatible* se almacena en un archivo de texto en cada nodo y se compara y actualiza en ejecuciones posteriores.</span><span class="sxs-lookup"><span data-stu-id="031ee-150">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

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
}
```
