---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Especificación de dependencias entre nodos
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080210"
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="2c32f-103">Especificación de dependencias entre nodos</span><span class="sxs-lookup"><span data-stu-id="2c32f-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="2c32f-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="2c32f-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="2c32f-105">DSC proporciona recursos especiales, **WaitForAll**, **WaitForAny** y **WaitForSome**, que se pueden usar en configuraciones para especificar las dependencias en configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="2c32f-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="2c32f-106">El comportamiento de estos recursos es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="2c32f-106">The behavior of these resources is as follows:</span></span>

- <span data-ttu-id="2c32f-107">**WaitForAll**: se ejecuta si el recurso especificado está en el estado deseado en todos los nodos de destino definidos en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="2c32f-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="2c32f-108">**WaitForAny**: se ejecuta si el recurso especificado está en el estado deseado en al menos uno de los nodos de destino definidos en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="2c32f-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
- <span data-ttu-id="2c32f-109">**WaitForSome**: especifica una propiedad **NodeCount** además de **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="2c32f-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="2c32f-110">El recurso se ejecuta si está en el estado deseado en un número mínimo de nodos (especificado por **NodeCount**) definido por la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="2c32f-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c32f-111">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="2c32f-111">Syntax</span></span>

<span data-ttu-id="2c32f-112">Los recursos **WaitForAll** y **WaitForAny** comparten la misma sintaxis.</span><span class="sxs-lookup"><span data-stu-id="2c32f-112">The **WaitForAll** and **WaitForAny** resources share the same syntax.</span></span> <span data-ttu-id="2c32f-113">Reemplace \<ResourceType\> en el ejemplo siguiente por **WaitForAny** o **WaitForAll**.</span><span class="sxs-lookup"><span data-stu-id="2c32f-113">Replace \<ResourceType\> in the example below with either **WaitForAny** or **WaitForAll**.</span></span>
<span data-ttu-id="2c32f-114">Al igual que la palabra clave **DependsOn**, el nombre debe presentar el formato"[ResourceType]ResourceName".</span><span class="sxs-lookup"><span data-stu-id="2c32f-114">Like the **DependsOn** keyword, you will need to format the name as "[ResourceType]ResourceName".</span></span> <span data-ttu-id="2c32f-115">Si el recurso pertenece a otra [configuración](configurations.md), incluya el valor de **ConfigurationName** en la cadena con formato "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span><span class="sxs-lookup"><span data-stu-id="2c32f-115">If the resource belongs to a separate [Configuration](configurations.md), include the **ConfigurationName** in the formatted string "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]".</span></span> <span data-ttu-id="2c32f-116">El **NodeName** es el equipo, o nodo, en el que debe esperar el recurso actual.</span><span class="sxs-lookup"><span data-stu-id="2c32f-116">The **NodeName** is the computer, or Node, on which the current resource should wait.</span></span>

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

<span data-ttu-id="2c32f-117">El recurso **WaitForSome** tiene una sintaxis similar al ejemplo anterior, pero agrega la clave **NodeCount**.</span><span class="sxs-lookup"><span data-stu-id="2c32f-117">The **WaitForSome** resource has a similar syntax to the example above, but adds the **NodeCount** key.</span></span> <span data-ttu-id="2c32f-118">**NodeCount** indica cuántos nodos debe esperar el recurso actual.</span><span class="sxs-lookup"><span data-stu-id="2c32f-118">The **NodeCount** indicates how many Nodes the current resource should wait on.</span></span>

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

<span data-ttu-id="2c32f-119">Todos los valores de **WaitForXXXX** comparten las claves de la sintaxis siguiente.</span><span class="sxs-lookup"><span data-stu-id="2c32f-119">All **WaitForXXXX** share the following syntax keys.</span></span>

<span data-ttu-id="2c32f-120">|  Property  |  Description   | | RetryIntervalSec| El número de segundos antes de reintentar.</span><span class="sxs-lookup"><span data-stu-id="2c32f-120">|  Property  |  Description   | | RetryIntervalSec| The number of seconds before retrying.</span></span> <span data-ttu-id="2c32f-121">El valor mínimo es 1.| | RetryCount| El número máximo de veces que se reintentará.| | ThrottleLimit| Número de equipos que se pueden conectar simultáneamente.</span><span class="sxs-lookup"><span data-stu-id="2c32f-121">Minimum is 1.| | RetryCount| The maximum number of times to retry.| | ThrottleLimit| Number of machines to connect simultaneously.</span></span> <span data-ttu-id="2c32f-122">El valor predeterminado es `New-CimSession`.| | DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="2c32f-122">Default is `New-CimSession` default.| | DependsOn | Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2c32f-123">Para obtener más información, consulte [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | Consulte [Using DSC with User Credentials](./runAsUser.md) (Uso de DSC con credenciales de usuario) |</span><span class="sxs-lookup"><span data-stu-id="2c32f-123">For more information, see [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | See [Using DSC with User Credentials](./runAsUser.md) |</span></span>


## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="2c32f-124">Uso de recursos WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="2c32f-124">Using WaitForXXXX resources</span></span>

<span data-ttu-id="2c32f-125">Cada recurso **WaitForXXXX** espera a que se completen los recursos especificados en el nodo especificado.</span><span class="sxs-lookup"><span data-stu-id="2c32f-125">Each **WaitForXXXX** resource waits for the specified resources to complete on the specified Node.</span></span> <span data-ttu-id="2c32f-126">Otros recursos de la misma configuración pueden entonces *depender* del recurso **WaitForXXXX**  usando la clave **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="2c32f-126">Other resources in the same Configuration can then *depend on* the **WaitForXXXX** resource using the **DependsOn** key.</span></span>

<span data-ttu-id="2c32f-127">Por ejemplo, en la configuración siguiente, el nodo de destino está esperando que el recurso **xADDomain** finalice en el nodo **MyDC** con un número máximo de 30 reintentos, a intervalos de 15 segundos, antes de que el nodo de destino pueda unirse al dominio.</span><span class="sxs-lookup"><span data-stu-id="2c32f-127">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

<span data-ttu-id="2c32f-128">Cuando se compila la configuración, se generan dos archivos ".mof".</span><span class="sxs-lookup"><span data-stu-id="2c32f-128">When you compile the Configuration, two ".mof" files are generated.</span></span> <span data-ttu-id="2c32f-129">Aplique ambos archivos ".mof" a los nodos de destino mediante el cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)</span><span class="sxs-lookup"><span data-stu-id="2c32f-129">Apply both ".mof" files to the target Nodes using the [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet</span></span>

><span data-ttu-id="2c32f-130">**Nota:** De manera predeterminada, los recursos de WaitForXXX lo intentan una vez y después se produce un error.</span><span class="sxs-lookup"><span data-stu-id="2c32f-130">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="2c32f-131">Aunque no es necesario, normalmente la intención será especificar un valor para **RetryCount** y otro para **RetryIntervalSec**.</span><span class="sxs-lookup"><span data-stu-id="2c32f-131">Although it is not required, you will typically want to specify a **RetryCount** and **RetryIntervalSec**.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c32f-132">Véase también</span><span class="sxs-lookup"><span data-stu-id="2c32f-132">See Also</span></span>

- [<span data-ttu-id="2c32f-133">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="2c32f-133">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="2c32f-134">Dependencias de los recursos</span><span class="sxs-lookup"><span data-stu-id="2c32f-134">Use Resource Dependencies</span></span>](resource-depends-on.md)
- [<span data-ttu-id="2c32f-135">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="2c32f-135">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="2c32f-136">Configuración del administrador de configuración local</span><span class="sxs-lookup"><span data-stu-id="2c32f-136">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
