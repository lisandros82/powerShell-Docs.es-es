---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Especificación de dependencias entre nodos"
ms.openlocfilehash: f4411161d819d96803f57600646409d5bfe827b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="specifying-cross-node-dependencies"></a><span data-ttu-id="f5b8d-103">Especificación de dependencias entre nodos</span><span class="sxs-lookup"><span data-stu-id="f5b8d-103">Specifying cross-node dependencies</span></span>

> <span data-ttu-id="f5b8d-104">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f5b8d-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="f5b8d-105">DSC proporciona recursos especiales, **WaitForAll**, **WaitForAny** y **WaitForSome**, que se pueden usar en configuraciones para especificar las dependencias en configuraciones de otros nodos.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-105">DSC provides special resources, **WaitForAll**, **WaitForAny**, and **WaitForSome** that can be used in configurations to specify dependencies on configurations on other nodes.</span></span> <span data-ttu-id="f5b8d-106">El comportamiento de estos recursos es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="f5b8d-106">The behavior of these resources is as follows:</span></span>

* <span data-ttu-id="f5b8d-107">**WaitForAll**: se ejecuta si el recurso especificado está en el estado deseado en todos los nodos de destino definidos en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-107">**WaitForAll**: Succeeds if the specified resource is in the desired state on all target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="f5b8d-108">**WaitForAny**: se ejecuta si el recurso especificado está en el estado deseado en al menos uno de los nodos de destino definidos en la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-108">**WaitForAny**: Succeeds if the specified resource is in the desired state on at least one of the target nodes defined in the **NodeName** property.</span></span>
* <span data-ttu-id="f5b8d-109">**WaitForSome**: especifica una propiedad **NodeCount** además de **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-109">**WaitForSome**: Specifies a **NodeCount** property in addition to a **NodeName** property.</span></span> <span data-ttu-id="f5b8d-110">El recurso se ejecuta si está en el estado deseado en un número mínimo de nodos (especificado por **NodeCount**) definido por la propiedad **NodeName**.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-110">The resource succeeds if the resource is in the desired state on a minimum number of nodes (specified by **NodeCount**) defined by the **NodeName** property.</span></span> 

## <a name="using-waitforxxxx-resources"></a><span data-ttu-id="f5b8d-111">Uso de recursos WaitForXXXX</span><span class="sxs-lookup"><span data-stu-id="f5b8d-111">Using WaitForXXXX resources</span></span>

<span data-ttu-id="f5b8d-112">Para usar los recursos **WaitForXXXX**, cree un bloque de recursos de ese tipo de recurso que especifique los nodos y el recurso de DSC que se esperará.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-112">To use the **WaitForXXXX** resources, you create a resource block of that resource type that specifies the DSC resource and node(s) to wait for.</span></span> <span data-ttu-id="f5b8d-113">Después, use la propiedad **DependsOn** en otros bloques de recursos de la configuración para esperar que las condiciones especificadas del nodo **WaitForXXXX** sean correctas.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-113">You then use the **DependsOn** property in any other resource blocks in your configuration to wait for the conditions specified in the **WaitForXXXX** node to succeed.</span></span>

<span data-ttu-id="f5b8d-114">Por ejemplo, en la configuración siguiente, el nodo de destino está esperando que el recurso **xADDomain** finalice en el nodo **MyDC** con un número máximo de 30 reintentos, a intervalos de 15 segundos, antes de que el nodo de destino pueda unirse al dominio.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-114">For example, in the following configuration, the target node is waiting for the **xADDomain** resource to finish on the **MyDC** node with maximum number of 30 retries, at 15-second intervals, before the target node can join the domain.</span></span>

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

><span data-ttu-id="f5b8d-115">**Nota:** De manera predeterminada, los recursos de WaitForXXX lo intentan una vez y después se produce un error.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-115">**Note:** By default the WaitForXXX resources try one time and then fail.</span></span> <span data-ttu-id="f5b8d-116">Aunque no es necesario, normalmente la intención será especificar un recuento y un intervalo de reintentos.</span><span class="sxs-lookup"><span data-stu-id="f5b8d-116">Although it is not required, you will typically want to specify a retry interval and count.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5b8d-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="f5b8d-117">See Also</span></span>
* [<span data-ttu-id="f5b8d-118">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="f5b8d-118">DSC Configurations</span></span>](configurations.md)
* [<span data-ttu-id="f5b8d-119">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="f5b8d-119">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="f5b8d-120">Configuración del administrador de configuración local</span><span class="sxs-lookup"><span data-stu-id="f5b8d-120">Configuring The Local Configuration Manager</span></span>](metaConfig.md)

