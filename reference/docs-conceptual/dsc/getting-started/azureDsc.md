---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,setup
title: Uso de DSC en Microsoft Azure
ms.openlocfilehash: 6d71b69eea78e775a3e5aaac64bccfa10092b8e6
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870836"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="5c014-103">Uso de DSC en Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="5c014-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="5c014-104">La configuración de estado deseado (DSC) es compatible con Microsoft Azure a través del [controlador de extensiones de la configuración de estado deseado de Azure](/azure/virtual-machines/extensions/dsc-overview) y mediante la [DSC de Azure Automation](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="5c014-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="5c014-105">Controlador de extensiones de la configuración de estado deseado de Azure</span><span class="sxs-lookup"><span data-stu-id="5c014-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="5c014-106">La extensión de DSC de Azure permite que las máquinas virtuales hospedadas en Microsoft Azure se administren con DSC.</span><span class="sxs-lookup"><span data-stu-id="5c014-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span> <span data-ttu-id="5c014-107">Para obtener más información, vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="5c014-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="5c014-108">Controlador de extensiones de la configuración de estado deseado de Azure</span><span class="sxs-lookup"><span data-stu-id="5c014-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="5c014-109">VMSS de Windows y configuración de estado deseado con plantillas de Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="5c014-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="5c014-110">Cómo pasar las credenciales al controlador de extensiones de la DSC de Azure</span><span class="sxs-lookup"><span data-stu-id="5c014-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="5c014-111">Historial de la extensión Desired State Configuration de Azure</span><span class="sxs-lookup"><span data-stu-id="5c014-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="5c014-112">DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="5c014-112">Azure Automation DSC</span></span>

<span data-ttu-id="5c014-113">El [servicio Azure Automation](https://azure.microsoft.com/services/automation/) le permite administrar configuraciones de DSC, recursos y nodos administrados dentro de Azure.</span><span class="sxs-lookup"><span data-stu-id="5c014-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="5c014-114">Para obtener más información, vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="5c014-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="5c014-115">DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="5c014-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="5c014-116">Introducción a DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="5c014-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="5c014-117">Incorporación de máquinas para administrarlas con DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="5c014-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)