---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Script
ms.openlocfilehash: e09e86011fa7dbb2a4d7f28b5032b4328b6f6ec2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953072"
---
# <a name="dsc-script-resource"></a><span data-ttu-id="9310c-103">Recurso de DSC Script</span><span class="sxs-lookup"><span data-stu-id="9310c-103">DSC Script Resource</span></span>

> <span data-ttu-id="9310c-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="9310c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="9310c-105">El recurso **Script** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para ejecutar bloques de script de Windows PowerShell en nodos de destino.</span><span class="sxs-lookup"><span data-stu-id="9310c-105">The **Script** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to run Windows PowerShell script blocks on target nodes.</span></span> <span data-ttu-id="9310c-106">El recurso **Script** utiliza las propiedades **GetScript** , **SetScript** y **TestScript** que contienen bloques de scripts que se definen para realizar las operaciones de estado DSC correspondientes.</span><span class="sxs-lookup"><span data-stu-id="9310c-106">The **Script** resource uses **GetScript**, **SetScript**, and **TestScript** properties that contain script blocks you define to perform the corresponding DSC state operations.</span></span>

## <a name="syntax"></a><span data-ttu-id="9310c-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="9310c-107">Syntax</span></span>

```Syntax
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> <span data-ttu-id="9310c-108">Los bloques **GetScript**, **TestScript** y **SetScript** se almacenan como cadenas.</span><span class="sxs-lookup"><span data-stu-id="9310c-108">**GetScript**, **TestScript**, and **SetScript** blocks are stored as strings.</span></span>

## <a name="properties"></a><span data-ttu-id="9310c-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="9310c-109">Properties</span></span>

|<span data-ttu-id="9310c-110">Propiedad</span><span class="sxs-lookup"><span data-stu-id="9310c-110">Property</span></span> |<span data-ttu-id="9310c-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="9310c-111">Description</span></span> |
|---|---|
|<span data-ttu-id="9310c-112">GetScript</span><span class="sxs-lookup"><span data-stu-id="9310c-112">GetScript</span></span> |<span data-ttu-id="9310c-113">Un bloque de scripts que devuelve el estado actual del nodo.</span><span class="sxs-lookup"><span data-stu-id="9310c-113">A script block that returns the current state of the Node.</span></span> |
|<span data-ttu-id="9310c-114">SetScript</span><span class="sxs-lookup"><span data-stu-id="9310c-114">SetScript</span></span> |<span data-ttu-id="9310c-115">Un bloque de scripts que usa DSC para aplicar el cumplimiento cuando el nodo no está en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="9310c-115">A script block that DSC uses to enforce compliance when the Node is not in the desired state.</span></span> |
|<span data-ttu-id="9310c-116">TestScript</span><span class="sxs-lookup"><span data-stu-id="9310c-116">TestScript</span></span> |<span data-ttu-id="9310c-117">Un bloque de scripts que determina si el nodo está en el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="9310c-117">A script block that determines if the Node is in the desired state.</span></span> |
|<span data-ttu-id="9310c-118">Credential</span><span class="sxs-lookup"><span data-stu-id="9310c-118">Credential</span></span> |<span data-ttu-id="9310c-119">Indica las credenciales que se usan para ejecutar este script, si se necesitan credenciales.</span><span class="sxs-lookup"><span data-stu-id="9310c-119">Indicates the credentials to use for running this script, if credentials are required.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="9310c-120">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="9310c-120">Common properties</span></span>

|<span data-ttu-id="9310c-121">Propiedad</span><span class="sxs-lookup"><span data-stu-id="9310c-121">Property</span></span> |<span data-ttu-id="9310c-122">Descripción</span><span class="sxs-lookup"><span data-stu-id="9310c-122">Description</span></span> |
|---|---|
|<span data-ttu-id="9310c-123">DependsOn</span><span class="sxs-lookup"><span data-stu-id="9310c-123">DependsOn</span></span> |<span data-ttu-id="9310c-124">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="9310c-124">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="9310c-125">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="9310c-125">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="9310c-126">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="9310c-126">PsDscRunAsCredential</span></span> |<span data-ttu-id="9310c-127">Establece la credencial con la que se ejecutará todo el recurso.</span><span class="sxs-lookup"><span data-stu-id="9310c-127">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="9310c-128">Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales.</span><span class="sxs-lookup"><span data-stu-id="9310c-128">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="9310c-129">Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="9310c-129">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="9310c-130">Información adicional</span><span class="sxs-lookup"><span data-stu-id="9310c-130">Additional information</span></span>

#### <a name="getscript"></a><span data-ttu-id="9310c-131">GetScript</span><span class="sxs-lookup"><span data-stu-id="9310c-131">GetScript</span></span>

<span data-ttu-id="9310c-132">DSC no utiliza la salida de **GetScript**.</span><span class="sxs-lookup"><span data-stu-id="9310c-132">DSC does not use the output from **GetScript**.</span></span> <span data-ttu-id="9310c-133">El cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) ejecuta **GetScript** para recuperar el estado actual de un nodo.</span><span class="sxs-lookup"><span data-stu-id="9310c-133">The [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet executes **GetScript** to retrieve a node's current state.</span></span> <span data-ttu-id="9310c-134">Un valor devuelto no es necesario de **GetScript**.</span><span class="sxs-lookup"><span data-stu-id="9310c-134">A return value is not required from **GetScript**.</span></span> <span data-ttu-id="9310c-135">Si especifica un valor devuelto, debe ser una tabla hash que contenga una tecla **Result** cuyo valor sea una cadena.</span><span class="sxs-lookup"><span data-stu-id="9310c-135">If you specify a return value, it must be a hashtable containing a **Result** key whose value is a String.</span></span>

#### <a name="testscript"></a><span data-ttu-id="9310c-136">TestScript</span><span class="sxs-lookup"><span data-stu-id="9310c-136">TestScript</span></span>

<span data-ttu-id="9310c-137">DSC ejecuta **TestScript** para determinar si se debe ejecutar **SetScript**.</span><span class="sxs-lookup"><span data-stu-id="9310c-137">**TestScript** is executed by DSC to determine if **SetScript** should be run.</span></span> <span data-ttu-id="9310c-138">Si **SetScript** devuelve `$false`, DSC ejecuta **SetScript** para devolver al nodo al estado deseado.</span><span class="sxs-lookup"><span data-stu-id="9310c-138">If **TestScript** returns `$false`, DSC executes **SetScript** to bring the node back to the desired state.</span></span> <span data-ttu-id="9310c-139">Debe devolver un valor booleano.</span><span class="sxs-lookup"><span data-stu-id="9310c-139">It must return a boolean value.</span></span> <span data-ttu-id="9310c-140">Un resultado de `$true` indica que el nodo es compatible y que **SetScript** no debe ejecutar.</span><span class="sxs-lookup"><span data-stu-id="9310c-140">A result of `$true` indicates that the node is compliant and **SetScript** should not executed.</span></span>

<span data-ttu-id="9310c-141">El cmdlet [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) ejecuta **TestScript** para recuperar el cumplimiento de los nodos con los recursos **Script**.</span><span class="sxs-lookup"><span data-stu-id="9310c-141">The [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) cmdlet, executes **TestScript** to retrieve the nodes compliance with the **Script** resources.</span></span>
<span data-ttu-id="9310c-142">Pero, en este caso, **SetScript** no se ejecuta, con independencia de lo que devuelva el bloque **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="9310c-142">However, in this case, **SetScript** does not run, no matter what **TestScript** block returns.</span></span>

> [!NOTE]
> <span data-ttu-id="9310c-143">Toda la salida de su **TestScript** es parte de su valor devuelto.</span><span class="sxs-lookup"><span data-stu-id="9310c-143">All output from your **TestScript** is part of its return value.</span></span> <span data-ttu-id="9310c-144">PowerShell interpreta la salida no suprimida como distinta de cero, lo que significa que **TestScript** devolverá `$true`, con independencia del estado del nodo.</span><span class="sxs-lookup"><span data-stu-id="9310c-144">PowerShell interprets unsuppressed output as non-zero, which means that your **TestScript** will return `$true` regardless of your node's state.</span></span> <span data-ttu-id="9310c-145">Esto da como resultado resultados impredecibles, falsos positivos y dificulta la resolución de problemas.</span><span class="sxs-lookup"><span data-stu-id="9310c-145">This results in unpredictable results, false positives, and causes difficulty during troubleshooting.</span></span>

#### <a name="setscript"></a><span data-ttu-id="9310c-146">SetScript</span><span class="sxs-lookup"><span data-stu-id="9310c-146">SetScript</span></span>

<span data-ttu-id="9310c-147">**SetScript** modifica el nodo para aplicar el estado deseado.</span><span class="sxs-lookup"><span data-stu-id="9310c-147">**SetScript** modifies the node to enforce the desired state.</span></span> <span data-ttu-id="9310c-148">Se invoca mediante el DSC si el bloque de scripts **TestScript** devuelve `$false`.</span><span class="sxs-lookup"><span data-stu-id="9310c-148">It is called by DSC if the **TestScript** script block returns `$false`.</span></span> <span data-ttu-id="9310c-149">**SetScript** no debe tener ningún valor devuelto.</span><span class="sxs-lookup"><span data-stu-id="9310c-149">The **SetScript** should have no return value.</span></span>

## <a name="examples"></a><span data-ttu-id="9310c-150">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="9310c-150">Examples</span></span>

### <a name="example-1-write-sample-text-using-a-script-resource"></a><span data-ttu-id="9310c-151">Ejemplo 1: Escribir texto de ejemplo con un recurso de Script</span><span class="sxs-lookup"><span data-stu-id="9310c-151">Example 1: Write sample text using a Script resource</span></span>

<span data-ttu-id="9310c-152">En este ejemplo se comprueba la existencia de `C:\TempFolder\TestFile.txt` en cada nodo.</span><span class="sxs-lookup"><span data-stu-id="9310c-152">This example tests for the existence of `C:\TempFolder\TestFile.txt` on each node.</span></span> <span data-ttu-id="9310c-153">Si no existe, se crea mediante el `SetScript`.</span><span class="sxs-lookup"><span data-stu-id="9310c-153">If it does not exist, it creates it using the `SetScript`.</span></span> <span data-ttu-id="9310c-154">El `GetScript` devuelve el contenido del archivo y su valor devuelto no se utiliza.</span><span class="sxs-lookup"><span data-stu-id="9310c-154">The `GetScript` returns the contents of the file, and its return value is not used.</span></span>

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

### <a name="example-2-compare-version-information-using-a-script-resource"></a><span data-ttu-id="9310c-155">Ejemplo 2: Comparar la información de versión con un recurso de Script</span><span class="sxs-lookup"><span data-stu-id="9310c-155">Example 2: Compare version information using a Script resource</span></span>

<span data-ttu-id="9310c-156">En este ejemplo se recupera la información de la versión *compatible* de un archivo de texto en el equipo de creación y la almacena en la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="9310c-156">This example retrieves the *compliant* version information from a text file on the authoring computer and stores it in the `$version` variable.</span></span> <span data-ttu-id="9310c-157">Al generar el archivo MOF del nodo, DSC reemplaza las variables de `$using:version` en cada bloque de scripts con el valor de la variable `$version`.</span><span class="sxs-lookup"><span data-stu-id="9310c-157">When generating the node's MOF file, DSC replaces the `$using:version` variables in each script block with the value of the `$version` variable.</span></span>
<span data-ttu-id="9310c-158">Durante la ejecución, la versión *compatible* se almacena en un archivo de texto en cada nodo y se compara y actualiza en ejecuciones posteriores.</span><span class="sxs-lookup"><span data-stu-id="9310c-158">During execution, the *compliant* version is stored in a text file on each Node and compared and updated on subsequent executions.</span></span>

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