---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Escribir un recurso de DSC de instancia única (procedimiento recomendado)"
ms.openlocfilehash: 4510bec5b4600334b845831ec6700da01e1a110c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="writing-a-single-instance-dsc-resource-best-practice"></a><span data-ttu-id="f5d3f-103">Escribir un recurso de DSC de instancia única (procedimiento recomendado)</span><span class="sxs-lookup"><span data-stu-id="f5d3f-103">Writing a single-instance DSC resource (best practice)</span></span>

><span data-ttu-id="f5d3f-104">**Nota:** En este tema se describe un procedimiento recomendado para definir un recurso de DSC que permite una sola instancia en una configuración.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-104">**Note:** This topic describes a best practice for defining a DSC resource that allows only a single instance in a configuration.</span></span> <span data-ttu-id="f5d3f-105">Actualmente, no hay ninguna característica de DSC integrada para este fin.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-105">Currently, there is no built-in DSC feature to do this.</span></span> <span data-ttu-id="f5d3f-106">Esto podría cambiar en el futuro.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-106">That might change in the future.</span></span>

<span data-ttu-id="f5d3f-107">Hay situaciones en las que no desea permitir que un recurso se use varias veces en una configuración.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-107">There are situations where you don't want to allow a resource to be used multiple times in a configuration.</span></span> <span data-ttu-id="f5d3f-108">Por ejemplo, en una implementación anterior del recurso [xTimeZone](https://github.com/PowerShell/xTimeZone), una configuración podría llamar al recurso varias veces y establecer la zona horaria en un valor diferente en cada bloque de recursos:</span><span class="sxs-lookup"><span data-stu-id="f5d3f-108">For example, in a previous implementation of the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource, a configuration could call the resource multiple times, setting the time zone to a different setting in each resource block:</span></span>

```powershell
Configuration SetTimeZone 
{ 
    Param 
    ( 
        [String[]]$NodeName = $env:COMPUTERNAME 

    ) 

    Import-DSCResource -ModuleName xTimeZone 
 
 
    Node $NodeName 
    { 
         xTimeZone TimeZoneExample 
         { 
        
            TimeZone = 'Eastern Standard Time' 
         } 

         xTimeZone TimeZoneExample2
         {

            TimeZone = 'Pacific Standard Time'

         }        

    } 
} 
```

<span data-ttu-id="f5d3f-109">Esto se debe al funcionamiento de las claves de recursos de DSC.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-109">This is because of the way DSC resource keys work.</span></span> <span data-ttu-id="f5d3f-110">Un recurso debe tener al menos una propiedad de clave.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-110">A resource must have at least one key property.</span></span> <span data-ttu-id="f5d3f-111">Una instancia de recursos se considera única si la combinación de los valores de todas sus propiedades de clave es única.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-111">A resource instance is considered unique if the combination of the values of all of its key properties is unique.</span></span> <span data-ttu-id="f5d3f-112">En su implementación anterior, el recurso [xTimeZone](https://github.com/PowerShell/xTimeZone) tenía una sola propiedad, **TimeZone**, que debía ser una clave obligatoriamente.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-112">In its previous implementation, the [xTimeZone](https://github.com/PowerShell/xTimeZone) resource had only one property--**TimeZone**, which was required to be a key.</span></span> <span data-ttu-id="f5d3f-113">Por este motivo, una configuración como la anterior se compilaría y ejecutaría sin previo aviso.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-113">Because of this, a configuration such as the one above would compile and run without warning.</span></span> <span data-ttu-id="f5d3f-114">Cada uno de los bloques del recurso **xTimeZone** se considera único.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-114">Each of the **xTimeZone** resource blocks is considered unique.</span></span> <span data-ttu-id="f5d3f-115">Esto provocaría que la configuración se aplicara repetidamente al nodo, avanzando y retrocediendo la zona horaria.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-115">This would cause the configuration to be repeatedly applied to the node, cycling the timezone back and forth.</span></span>

<span data-ttu-id="f5d3f-116">Para garantizar que una configuración pudiera establecer la zona horaria de un nodo de destino solo una vez, el recurso se actualizó para agregar una segunda propiedad, **IsSingleInstance**, que se convirtió en la propiedad de clave.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-116">To ensure that a configuration could set the time zone for a target node only once, the resource was updated to add a second property, **IsSingleInstance**, that became the key property.</span></span> <span data-ttu-id="f5d3f-117">La propiedad **IsSingleInstance** estaba limitada a un único valor, "Yes", mediante **ValueMap**.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-117">The **IsSingleInstance** was limited to a single value, "Yes" by using a **ValueMap**.</span></span> <span data-ttu-id="f5d3f-118">El esquema MOF anterior del recurso era:</span><span class="sxs-lookup"><span data-stu-id="f5d3f-118">The old MOF schema for the resource was:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="f5d3f-119">El esquema MOF actualizado del recurso era:</span><span class="sxs-lookup"><span data-stu-id="f5d3f-119">The updated MOF schema for the resource is:</span></span>

```powershell
[ClassVersion("1.0.0.0"), FriendlyName("xTimeZone")]
class xTimeZone : OMI_BaseResource
{
    [Key, Description("Specifies the resource is a single instance, the value must be 'Yes'"), ValueMap{"Yes"}, Values{"Yes"}] String IsSingleInstance;
    [Required, Description("Specifies the TimeZone.")] String TimeZone;
};
```

<span data-ttu-id="f5d3f-120">El script de recursos también se actualizó para usar el nuevo parámetro.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-120">The resource script was also updated to use the new parameter.</span></span> <span data-ttu-id="f5d3f-121">Este es el script de recursos anterior:</span><span class="sxs-lookup"><span data-stu-id="f5d3f-121">Here is the old resource script:</span></span>

```powershell
function Get-TargetResource
{
    [CmdletBinding()]
    [OutputType([Hashtable])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Get the current TimeZone
    $CurrentTimeZone = Get-TimeZone

    $returnValue = @{
        TimeZone = $CurrentTimeZone
        IsSingleInstance = 'Yes'
    }

    #Output the target resource
    $returnValue
}


function Set-TargetResource
{
    [CmdletBinding(SupportsShouldProcess=$true)]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )
    
    #Output the result of Get-TargetResource function.
    $CurrentTimeZone = Get-TimeZone
    
    if($PSCmdlet.ShouldProcess("'$TimeZone'","Replace the System Time Zone"))
    {
        try
        {
            if($CurrentTimeZone -ne $TimeZone)
            {
                Write-Verbose -Verbose "Setting the TimeZone"
                Set-TimeZone -TimeZone $TimeZone}
            else
            {
                Write-Verbose -Verbose "TimeZone already set to $TimeZone"
            }
        }
        catch
        {
            $ErrorMsg = $_.Exception.Message
            Write-Verbose -Verbose $ErrorMsg
        }
    }
}


function Test-TargetResource
{
    [CmdletBinding()]
    [OutputType([Boolean])]
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateSet('Yes')]
        [String]
        $IsSingleInstance, 

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $TimeZone
    )

    #Output from Get-TargetResource
    $CurrentTimeZone = Get-TimeZone

    if($TimeZone -eq $CurrentTimeZone)
    {
        return $true
    }
    else
    {
        return $false
    }
}

Function Get-TimeZone {
    [CmdletBinding()]
    param()

    & tzutil.exe /g
}

Function Set-TimeZone {
    [CmdletBinding()]
    param(
        [Parameter(Mandatory=$true)]
        [System.String]
        $TimeZone
    )

    try
    {
        & tzutil.exe /s $TimeZone
    }
    catch
    {
        $ErrorMsg = $_.Exception.Message
        Write-Verbose $ErrorMsg
    }
}

Export-ModuleMember -Function *-TargetResource
```

<span data-ttu-id="f5d3f-122">Observe que la propiedad **TimeZone** ya no es una clave.</span><span class="sxs-lookup"><span data-stu-id="f5d3f-122">Notice that the **TimeZone** property is no longer a key.</span></span> <span data-ttu-id="f5d3f-123">Ahora, si una configuración intenta establecer la zona horaria dos veces (con dos bloques **xTimeZone** diferentes y valores de **TimeZone** diferentes), al intentar compilar la configuración se producirá un error:</span><span class="sxs-lookup"><span data-stu-id="f5d3f-123">Now, if a configuration attempts to set the time zone twice (by using two different **xTimeZone** blocks with different **TimeZone** values), attempting to compile the configuration will cause an error:</span></span>

```powershell
Test-ConflictingResources : A conflict was detected between resources '[xTimeZone]TimeZoneExample (::15::10::xTimeZone)' and 
'[xTimeZone]TimeZoneExample2 (::22::10::xTimeZone)' in node 'CONTOSO-CLIENT'. Resources have identical key properties but there are differences in the 
following non-key properties: 'TimeZone'. Values 'Eastern Standard Time' don't match values 'Pacific Standard Time'. Please update these property 
values so that they are identical in both cases.
At line:271 char:9
+         Test-ConflictingResources $keywordName $canonicalizedValue $k ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : ConflictingDuplicateResource,Test-ConflictingResources
Errors occurred while processing configuration 'SetTimeZone'.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3705 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (SetTimeZone:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```
   
