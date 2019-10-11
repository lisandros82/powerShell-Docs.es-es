---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Especificación de dependencias entre nodos
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954112"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="e2c9d-103">Especificación de dependencias entre nodos</span><span class="sxs-lookup"><span data-stu-id="e2c9d-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="e2c9d-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e2c9d-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="e2c9d-105">DSC proporciona recursos especiales, **WaitForAll**, **WaitForAny** y **WaitForSome**, que se pueden usar en configuraciones para especificar las dependencias en configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="e2c9d-106">El comportamiento de estos recursos es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="e2c9d-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="e2c9d-107">**WaitForAll**: se ejecuta si el recurso especificado está en el estado deseado en todos los nodos de destino definidos en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="e2c9d-108">**WaitForAny**: se ejecuta si el recurso especificado está en el estado deseado en al menos uno de los nodos de destino definidos en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="e2c9d-109">**WaitForSome**: especifica una propiedad **NodeCount** además de **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="e2c9d-110">El recurso se ejecuta si está en el estado deseado en un número mínimo de nodos (especificado por **NodeCount**) definido por la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="e2c9d-111">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="e2c9d-111">Syntax</span></span>

<span data-ttu-id="e2c9d-112">Los recursos **WaitForAll** y **WaitForAny** comparten la misma sintaxis.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="e2c9d-113">Reemplace \<ResourceType\> en el ejemplo siguiente por **WaitForAny** o **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="e2c9d-114">Al igual que la palabra clave **DependsOn**, el nombre debe presentar el formato"[ResourceType]ResourceName".</span><span class="sxs-lookup"><span data-stu-id="e2c9d-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="e2c9d-115">Si el recurso pertenece a otra [configuración](configurations.md), incluya el valor de **ConfigurationName** en la cadena con formato "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="e2c9d-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="e2c9d-116">El **NodeName** es el equipo, o nodo, en el que debe esperar el recurso actual.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

<span data-ttu-id="e2c9d-117">El recurso **WaitForSome** tiene una sintaxis similar al ejemplo anterior, pero agrega la clave **NodeCount**.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="e2c9d-118">**NodeCount** indica cuántos nodos debe esperar el recurso actual.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

<span data-ttu-id="e2c9d-119">Todos los valores de **WaitForXXXX** comparten las claves de la sintaxis siguiente.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-119">All **WaitForXXXX** share the following syntax keys.</span></span>

|<span data-ttu-id="e2c9d-120">Propiedad</span><span class="sxs-lookup"><span data-stu-id="e2c9d-120">Property</span></span>|  <span data-ttu-id="e2c9d-121">Descripción</span><span class="sxs-lookup"><span data-stu-id="e2c9d-121">Description</span></span>   |
|---------|---------------------|
| <span data-ttu-id="e2c9d-122">RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="e2c9d-122">RetryIntervalSec</span></span>| <span data-ttu-id="e2c9d-123">El número de segundos antes de reintentar la operación.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-123">The number of seconds before retrying.</span></span> <span data-ttu-id="e2c9d-124">El valor mínimo es 1.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-124">Minimum is 1.</span></span>|
| <span data-ttu-id="e2c9d-125">RetryCount</span><span class="sxs-lookup"><span data-stu-id="e2c9d-125">RetryCount</span></span>| <span data-ttu-id="e2c9d-126">El número máximo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-126">The maximum number of times to retry.</span></span>|
| <span data-ttu-id="e2c9d-127">ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="e2c9d-127">ThrottleLimit</span></span>| <span data-ttu-id="e2c9d-128">El número de máquinas que se pueden conectar de forma simultánea.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-128">Number of machines to connect simultaneously.</span></span> <span data-ttu-id="e2c9d-129">El valor predeterminado es `New-CimSession`.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-129">Default is `New-CimSession` default.</span></span>|
| <span data-ttu-id="e2c9d-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e2c9d-130">DependsOn</span></span> | <span data-ttu-id="e2c9d-131">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e2c9d-132">Para obtener más información, vea [DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="e2c9d-132">For more information, see [DependsOn](resource-depends-on.md)</span></span>|
| <span data-ttu-id="e2c9d-133">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="e2c9d-133">PsDscRunAsCredential</span></span> | <span data-ttu-id="e2c9d-134">Consulte el artículo sobre el [uso de DSC con credenciales de usuario](./runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="e2c9d-134">See [Using DSC with User Credentials](./runAsUser.md)</span></span> |

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="e2c9d-135">Uso de recursos WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="e2c9d-135">Using WaitForXXXX resources</span></span>

<span data-ttu-id="e2c9d-136">Cada recurso **WaitForXXXX** espera a que se completen los recursos especificados en el nodo especificado.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-136">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span>
<span data-ttu-id="e2c9d-137">Otros recursos de la misma configuración pueden entonces *depender* del recurso **WaitForXXXX**  usando la clave **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-137">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="e2c9d-138">Por ejemplo, en la configuración siguiente, el nodo de destino está esperando que el recurso **xADDomain** finalice en el nodo **MyDC** con un número máximo de 30 reintentos, a intervalos de 15 segundos, antes de que el nodo de destino pueda unirse al dominio.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-138">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

<span data-ttu-id="e2c9d-139">De manera predeterminada, los recursos de **WaitForXXX** lo intentan una vez y después se produce un error.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-139">By default the **WaitForXXX** resources try one time and then fail.</span></span> <span data-ttu-id="e2c9d-140">Aunque no es necesario, normalmente la intención será especificar un valor para **RetryCount** y otro para **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-140">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

<span data-ttu-id="e2c9d-141">Cuando se compila la configuración, se generan dos archivos ".mof".</span><span class="sxs-lookup"><span data-stu-id="e2c9d-141">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="e2c9d-142">Aplique ambos archivos ".mof" a los nodos de destino mediante el cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)</span><span class="sxs-lookup"><span data-stu-id="e2c9d-142">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

> [!NOTE]
> <span data-ttu-id="e2c9d-143">Los recursos **WaitForXXX** usan Administración remota de Windows para comprobar el estado de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="e2c9d-143">**WaitForXXX** resources use Windows Remote Management to check the state of other Nodes.</span></span>
> <span data-ttu-id="e2c9d-144">Para obtener más información sobre los requisitos de seguridad y puerto de WinRM, vea [Consideraciones de seguridad de comunicación remota de PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="e2c9d-144">For more information about port and security requirements for WinRM, see [PowerShell Remoting Security Considerations](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2c9d-145">Véase también</span><span class="sxs-lookup"><span data-stu-id="e2c9d-145">See Also</span></span>

- [<span data-ttu-id="e2c9d-146">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="e2c9d-146">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="e2c9d-147">Dependencias de los recursos</span><span class="sxs-lookup"><span data-stu-id="e2c9d-147">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="e2c9d-148">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="e2c9d-148">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="e2c9d-149">Configuración del administrador de configuración local</span><span class="sxs-lookup"><span data-stu-id="e2c9d-149">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
