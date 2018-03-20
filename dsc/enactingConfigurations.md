---
ms.date: 2017-10-16
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Establecer configuraciones
ms.openlocfilehash: 01294b85d33e147593299de8ecf46c027a69f7a3
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="enacting-configurations"></a><span data-ttu-id="9aaf6-103">Establecer configuraciones</span><span class="sxs-lookup"><span data-stu-id="9aaf6-103">Enacting configurations</span></span>

><span data-ttu-id="9aaf6-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="9aaf6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9aaf6-105">Hay dos maneras de establecer las configuraciones de la configuración de estado deseado (DSC) de PowerShell: el modo de inserción y el modo de extracción.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-105">There are two ways to enact PowerShell Desired State Configuration (DSC) configurations: push mode and pull mode.</span></span>

## <a name="push-mode"></a><span data-ttu-id="9aaf6-106">Modo de inserción</span><span class="sxs-lookup"><span data-stu-id="9aaf6-106">Push mode</span></span>

<span data-ttu-id="9aaf6-107">![Modo de inserción](images/pushModel.png "Cómo funciona el modo de inserción")</span><span class="sxs-lookup"><span data-stu-id="9aaf6-107">![Push mode](images/pushModel.png "How push mode works")</span></span>

<span data-ttu-id="9aaf6-108">El modo de inserción se refiere a un usuario que aplica activamente una configuración a un nodo de destino mediante una llamada al cmdlet [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).</span><span class="sxs-lookup"><span data-stu-id="9aaf6-108">Push mode refers to a user actively applying a configuration to a target node by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.</span></span>

<span data-ttu-id="9aaf6-109">Después de crear y compilar una configuración, puede establecerla en el modo de inserción con una llamada al cmdlet [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx), estableciendo el parámetro -Path del cmdlet en la ruta de acceso donde se encuentra el MOF de configuración.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-109">After creating and compiling a configuration, you can enact it in push mode by calling the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, setting the -Path parameter of the cmdlet to the path where the configuration MOF is located.</span></span>
<span data-ttu-id="9aaf6-110">Por ejemplo, si el MOF de configuración está ubicado en `C:\DSC\Configurations\localhost.mof`, se aplicaría a la máquina local con el comando siguiente: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span><span class="sxs-lookup"><span data-stu-id="9aaf6-110">For example, if the configuration MOF is located at `C:\DSC\Configurations\localhost.mof`, you would apply it to the local machine with the following command: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`</span></span>

> <span data-ttu-id="9aaf6-111">__Nota__: De forma predeterminada, DSC ejecuta una configuración como un trabajo en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-111">__Note__: By default, DSC runs a configuration as a background job.</span></span> <span data-ttu-id="9aaf6-112">Para ejecutar la configuración de forma interactiva, llame a [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) con el parámetro __-Wait__.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-112">To run the configuration interactively, call the [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) with the __-Wait__ parameter.</span></span>

## <a name="pull-mode"></a><span data-ttu-id="9aaf6-113">Modo de extracción</span><span class="sxs-lookup"><span data-stu-id="9aaf6-113">Pull mode</span></span>

<span data-ttu-id="9aaf6-114">![Modo de extracción](images/pullModel.png "Cómo funciona el modo de extracción")</span><span class="sxs-lookup"><span data-stu-id="9aaf6-114">![Pull Mode](images/pullModel.png "How pull mode works")</span></span>

<span data-ttu-id="9aaf6-115">En el modo de extracción, los clientes de extracción se configuran para obtener sus configuraciones de estado deseado desde un servicio de extracción remoto.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-115">In pull mode, pull clients are configured to get their desired state configurations from a remote pull service.</span></span>
<span data-ttu-id="9aaf6-116">Del mismo modo, el servicio de extracción se ha configurado para hospedar el servicio de DSC y se ha aprovisionado con las configuraciones y los recursos que necesitan los clientes de extracción.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-116">Likewise, the pull service has been set up to host the DSC service, and has been provisioned with the configurations and resources that are required by the pull clients.</span></span>
<span data-ttu-id="9aaf6-117">Cada uno de los clientes de extracción tiene un evento programado que realiza una comprobación periódica del cumplimiento de la configuración del nodo.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-117">Each of the pull clients has a scheduled event that performs a periodic compliance check on the configuration of the node.</span></span>
<span data-ttu-id="9aaf6-118">Cuando el evento se desencadena por primera vez, el administrador de configuración local (LCM) del cliente de extracción realiza una solicitud al servicio de extracción para obtener la configuración especificada en el LCM.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-118">When the event is triggered the first time, the Local Configuration Manager (LCM) on the pull client makes a request to the pull service to get the configuration specified in the LCM.</span></span>
<span data-ttu-id="9aaf6-119">Si dicha configuración existe en el servicio de extracción y pasa las comprobaciones de validación iniciales, la configuración se descarga en el cliente de extracción, donde a continuación el LCM la ejecuta.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-119">If that configuration exists on the pull service, and it passes initial validation checks, the configuration is downloaded to the pull client, where it is then executed by the LCM.</span></span>

<span data-ttu-id="9aaf6-120">El LCM comprueba que el cliente es conforme con la configuración a intervalos regulares especificados por la propiedad **ConfigurationModeFrequencyMins** del LCM.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-120">The LCM checks that the client is in compliance with the configuration at regular intervals specified by the **ConfigurationModeFrequencyMins** property of the LCM.</span></span>
<span data-ttu-id="9aaf6-121">El LCM busca configuraciones actualizadas en el servicio de extracción a intervalos regulares especificados por la propiedad **RefreshModeFrequency** del LCM.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-121">The LCM checks for updated configurations on the pull service at regular intervals specified by the **RefreshModeFrequency** property of the LCM.</span></span>
<span data-ttu-id="9aaf6-122">Para obtener información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](metaConfig.md).</span><span class="sxs-lookup"><span data-stu-id="9aaf6-122">For information about configuring the LCM, see [Configuring the Local Configuration Manager](metaConfig.md).</span></span>

<span data-ttu-id="9aaf6-123">La solución recomendada para hospedar un servicio de extracción es [Azure Automation](https://azure.microsoft.com/services/automation/), el servicio en la nube de DSC.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-123">The recommended solution for hosting a Pull Service, is the DSC cloud service, [Azure Automation](https://azure.microsoft.com/services/automation/).</span></span>
<span data-ttu-id="9aaf6-124">Esta solución hospedada ofrece administración de gráficos, informes y administración centralizada.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-124">This is hosted solution provides graphical management, reporting, and centralized administration.</span></span>

<span data-ttu-id="9aaf6-125">Para más información sobre la configuración de un servicio de extracción de Windows Server, consulte [Configuración de un servidor de extracción web de DSC](pullServer.md).</span><span class="sxs-lookup"><span data-stu-id="9aaf6-125">For more information on setting up a Pull Service on Windows Server, see [Setting up a DSC web pull server](pullServer.md).</span></span>
<span data-ttu-id="9aaf6-126">Sin embargo, debe tener en cuenta que esta implementación tiene características limitadas y requiere que haga cierta integración de manera manual.</span><span class="sxs-lookup"><span data-stu-id="9aaf6-126">Understand however, that this implementation has limited features and does require some "do it yourself" integration.</span></span>

<span data-ttu-id="9aaf6-127">En los temas siguientes se explican los clientes y el servicio de extracción:</span><span class="sxs-lookup"><span data-stu-id="9aaf6-127">The following topics explain pull service and clients:</span></span>

- [<span data-ttu-id="9aaf6-128">Información general de DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="9aaf6-128">Azure Automation DSC Overview</span></span>](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="9aaf6-129">Configuración de un servidor de extracción SMB</span><span class="sxs-lookup"><span data-stu-id="9aaf6-129">Setting up an SMB pull server</span></span>](pullServerSMB.md)
- [<span data-ttu-id="9aaf6-130">Configuración de un cliente de extracción</span><span class="sxs-lookup"><span data-stu-id="9aaf6-130">Configuring a pull client</span></span>](pullClientConfigID.md)
