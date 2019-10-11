---
ms.date: 10/16/2017
keywords: dsc,powershell,configuration,setup
title: Establecer configuraciones
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953652"
---
# <a name="enacting-configurations"></a><span data-ttu-id="5d740-103">Establecer configuraciones</span><span class="sxs-lookup"><span data-stu-id="5d740-103">Enacting configurations</span></span>

><span data-ttu-id="5d740-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5d740-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="5d740-105">Hay dos maneras de establecer las configuraciones de la configuración de estado deseado (DSC) de PowerShell: el modo de inserción y el modo de extracción.</span><span class="sxs-lookup"><span data-stu-id="5d740-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="5d740-106">Modo de inserción</span><span class="sxs-lookup"><span data-stu-id="5d740-106">Push mode</span></span>

<span data-ttu-id="5d740-107">![Modo de inserción](../images/pushModel.png "Cómo funciona el modo de inserción")</span><span class="sxs-lookup"><span data-stu-id="5d740-107">![Push mode](../images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="5d740-108">El modo de inserción se refiere a un usuario que aplica activamente una configuración a un nodo de destino mediante una llamada al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="5d740-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="5d740-109">Después de crear y compilar una configuración, puede establecerla en el modo de inserción con una llamada al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration), estableciendo el parámetro -Path del cmdlet en la ruta de acceso donde se encuentra el MOF de configuración.</span><span class="sxs-lookup"><span data-stu-id="5d740-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="5d740-110">Por ejemplo, si el MOF de configuración está ubicado en `C:\DSC\Configurations\localhost.mof`, se aplicaría a la máquina local con el comando siguiente: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="5d740-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="5d740-111">__Nota__: De forma predeterminada, DSC ejecuta una configuración como un trabajo en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="5d740-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="5d740-112">Para ejecutar la configuración de forma interactiva, llame a [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) con el parámetro __-Wait__.</span><span class="sxs-lookup"><span data-stu-id="5d740-112">To run the configuration interactively, call the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="5d740-113">Modo de extracción</span><span class="sxs-lookup"><span data-stu-id="5d740-113">Pull mode</span></span>

<span data-ttu-id="5d740-114">![Modo de extracción](../images/pullModel.png "Cómo funciona el modo de extracción")</span><span class="sxs-lookup"><span data-stu-id="5d740-114">![Pull Mode](../images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="5d740-115">En el modo de extracción, los clientes de extracción se configuran para obtener sus configuraciones de estado deseado desde un servicio de extracción remoto.</span><span class="sxs-lookup"><span data-stu-id="5d740-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="5d740-116">Del mismo modo, el servicio de extracción se ha configurado para hospedar el servicio de DSC y se ha aprovisionado con las configuraciones y los recursos que necesitan los clientes de extracción.</span><span class="sxs-lookup"><span data-stu-id="5d740-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="5d740-117">Cada uno de los clientes de extracción tiene un evento programado que realiza una comprobación periódica del cumplimiento de la configuración del nodo.</span><span class="sxs-lookup"><span data-stu-id="5d740-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="5d740-118">Cuando el evento se desencadena por primera vez, el administrador de configuración local (LCM) del cliente de extracción realiza una solicitud al servicio de extracción para obtener la configuración especificada en el LCM.</span><span class="sxs-lookup"><span data-stu-id="5d740-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="5d740-119">Si dicha configuración existe en el servicio de extracción y pasa las comprobaciones de validación iniciales, la configuración se descarga en el cliente de extracción, donde a continuación el LCM la ejecuta.</span><span class="sxs-lookup"><span data-stu-id="5d740-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="5d740-120">El LCM comprueba que el cliente es conforme con la configuración a intervalos regulares especificados por la propiedad **ConfigurationModeFrequencyMins** del LCM.</span><span class="sxs-lookup"><span data-stu-id="5d740-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="5d740-121">El LCM busca configuraciones actualizadas en el servicio de extracción a intervalos regulares especificados por la propiedad **RefreshModeFrequency** del LCM.</span><span class="sxs-lookup"><span data-stu-id="5d740-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="5d740-122">Para obtener información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="5d740-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md).</span></span>

<span data-ttu-id="5d740-123">La solución recomendada para hospedar un servicio de extracción es [Azure Automation](https://azure.microsoft.com/services/automation/), el servicio en la nube de DSC.</span><span class="sxs-lookup"><span data-stu-id="5d740-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="5d740-124">Esta solución hospedada ofrece administración de gráficos, informes y administración centralizada.</span><span class="sxs-lookup"><span data-stu-id="5d740-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="5d740-125">Para más información sobre la configuración de un servicio de extracción de Windows Server, consulte [Configuración de un servidor de extracción web de DSC](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="5d740-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="5d740-126">Sin embargo, debe tener en cuenta que esta implementación tiene características limitadas y requiere que haga cierta integración de manera manual.</span><span class="sxs-lookup"><span data-stu-id="5d740-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="5d740-127">En los temas siguientes se explican los clientes y el servicio de extracción:</span><span class="sxs-lookup"><span data-stu-id="5d740-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="5d740-128">Información general de DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="5d740-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="5d740-129">Configuración de un servidor de extracción SMB</span><span class="sxs-lookup"><span data-stu-id="5d740-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="5d740-130">Configuración de un cliente de extracción</span><span class="sxs-lookup"><span data-stu-id="5d740-130">Configuring a pull client</span></span>](pullClientConfigID.md)
