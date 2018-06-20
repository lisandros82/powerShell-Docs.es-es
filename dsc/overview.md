---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Información general sobre la configuración de estado deseado de Windows PowerShell
ms.openlocfilehash: c9069d7c9ce9c614330e36a42233b00363660a4b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187483"
---
# <a name="windows-powershell-desired-state-configuration-overview"></a><span data-ttu-id="d8fe9-103">Información general sobre la configuración de estado deseado de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8fe9-103">Windows PowerShell Desired State Configuration Overview</span></span>

> <span data-ttu-id="d8fe9-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d8fe9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d8fe9-105">DSC es una plataforma de administración de PowerShell que le permite administrar su infraestructura de desarrollo y TI con configuración como código.</span><span class="sxs-lookup"><span data-stu-id="d8fe9-105">DSC is a management platform in PowerShell that enables you to manage your IT and development infrastructure with configuration as code.</span></span>

- <span data-ttu-id="d8fe9-106">Para información general de las ventajas empresariales de usar DSC, consulte [Información general sobre la configuración de estado deseado para responsables de toma de decisiones](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="d8fe9-106">For an overview of the business benefits of using DSC, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>
- <span data-ttu-id="d8fe9-107">Para obtener información general de las ventajas de ingeniería de usar DSC, consulte [Información general sobre la configuración de estado deseado para ingenieros](DscForEngineers.md).</span><span class="sxs-lookup"><span data-stu-id="d8fe9-107">For an overview of the engineering benefits of using DSC, see [Desired State Configuration Overview for Engineers](DscForEngineers.md).</span></span>
- <span data-ttu-id="d8fe9-108">Para empezar a usar DSC rápidamente, consulte [Inicio rápido de la configuración de estado deseado](quickStart.md).</span><span class="sxs-lookup"><span data-stu-id="d8fe9-108">To start using DSC quickly, see [DSC quick start](quickStart.md).</span></span>

## <a name="key-concepts"></a><span data-ttu-id="d8fe9-109">Conceptos clave</span><span class="sxs-lookup"><span data-stu-id="d8fe9-109">Key Concepts</span></span>

<span data-ttu-id="d8fe9-110">DSC es una plataforma declarativa que se usa para la configuración, implementación y administración de sistemas.</span><span class="sxs-lookup"><span data-stu-id="d8fe9-110">DSC is a declarative platform used for configuration, deployment, and management of systems.</span></span> <span data-ttu-id="d8fe9-111">Consta de tres componentes principales:</span><span class="sxs-lookup"><span data-stu-id="d8fe9-111">It consists of three primary components:</span></span>

- <span data-ttu-id="d8fe9-112">Las [configuraciones](configurations.md) son scripts de PowerShell declarativos que definen y configuran instancias de recursos.</span><span class="sxs-lookup"><span data-stu-id="d8fe9-112">[Configurations](configurations.md) are declarative PowerShell scripts which define and configure instances of resources.</span></span>
    <span data-ttu-id="d8fe9-113">Cuando ejecuta la configuración, DSC (y los recursos a los que llama la configuración) simplemente "hará que sea así", asegurándose de que el sistema exista en el estado que disponga la configuración.</span><span class="sxs-lookup"><span data-stu-id="d8fe9-113">Upon running the configuration, DSC (and the resources being called by the configuration) will simply “make it so”, ensuring that the system exists in the state laid out by the configuration.</span></span>
    <span data-ttu-id="d8fe9-114">Las configuraciones DSC también son idempotentes: el administrador de configuración local (LCM) seguirá garantizando que las máquinas estén configuradas en el estado que la configuración declare.</span><span class="sxs-lookup"><span data-stu-id="d8fe9-114">DSC configurations are also idempotent: the Local Configuration Manager (LCM) will continue to ensure that machines are configured in whatever state the configuration declares.</span></span>
- <span data-ttu-id="d8fe9-115">Los [recursos](resources.md) son la parte "hacer que sea así" de DSC.</span><span class="sxs-lookup"><span data-stu-id="d8fe9-115">[Resources](resources.md) are the "make it so" part of DSC.</span></span> <span data-ttu-id="d8fe9-116">Contienen el código que coloca y mantiene el destino de una configuración en el estado especificado.</span><span class="sxs-lookup"><span data-stu-id="d8fe9-116">They contain the code that put and keep the target of a configuration in the specified state.</span></span>
    <span data-ttu-id="d8fe9-117">Los recursos residen en los módulos de PowerShell y pueden escribirse para modelar algo tan genérico como un archivo o un proceso de Windows, o algo tan específico como un servidor IIS o una VM que se ejecuta en Azure.</span><span class="sxs-lookup"><span data-stu-id="d8fe9-117">Resources reside in PowerShell modules and can be written to model something as generic as a file or a Windows process, or as specific as an IIS server or a VM running in Azure.</span></span>
- <span data-ttu-id="d8fe9-118">El [administrador de configuración local (LCM)](metaConfig.md) es el motor mediante el que DSC facilita la interacción entre recursos y configuraciones.</span><span class="sxs-lookup"><span data-stu-id="d8fe9-118">The [Local Configuration Manager (LCM)](metaConfig.md) is the engine by which DSC facilitates the interaction between resources and configurations.</span></span>
    <span data-ttu-id="d8fe9-119">El LCM sondea periódicamente el sistema mediante el flujo de control que han implementado los recursos para asegurarse de que se mantiene el estado que ha definido una configuration.</span><span class="sxs-lookup"><span data-stu-id="d8fe9-119">The LCM regularly polls the system using the control flow implemented by resources to ensure that the state defined by a configuration is maintained.</span></span>
    <span data-ttu-id="d8fe9-120">Si el sistema está fuera del estado, el LCM llama al código de los recursos para "hacer que sea así" según la declaración de la configuration.</span><span class="sxs-lookup"><span data-stu-id="d8fe9-120">If the system is out of state, the LCM makes calls to the code in resources to “make it so” according to the configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8fe9-121">Véase también</span><span class="sxs-lookup"><span data-stu-id="d8fe9-121">See Also</span></span>

- [<span data-ttu-id="d8fe9-122">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="d8fe9-122">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="d8fe9-123">Recursos de DSC</span><span class="sxs-lookup"><span data-stu-id="d8fe9-123">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="d8fe9-124">Configuración del administrador de configuración local</span><span class="sxs-lookup"><span data-stu-id="d8fe9-124">Configuring The Local Configuration Manager</span></span>](metaConfig.md)