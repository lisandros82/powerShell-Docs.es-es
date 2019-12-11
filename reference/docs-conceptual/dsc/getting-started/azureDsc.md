---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,setup
title: Uso de DSC en Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953962"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="20e30-103">Uso de DSC en Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="20e30-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="20e30-104">La configuración de estado deseado (DSC) es compatible con Microsoft Azure a través del [controlador de extensiones de la configuración de estado deseado de Azure](/azure/virtual-machines/extensions/dsc-overview) y mediante la [DSC de Azure Automation](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="20e30-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="20e30-105">Controlador de extensiones de la configuración de estado deseado de Azure</span><span class="sxs-lookup"><span data-stu-id="20e30-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="20e30-106">La extensión de DSC de Azure permite que las máquinas virtuales hospedadas en Microsoft Azure se administren con DSC.</span><span class="sxs-lookup"><span data-stu-id="20e30-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="20e30-107">Para obtener más información, vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="20e30-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="20e30-108">Controlador de extensiones de la configuración de estado deseado de Azure</span><span class="sxs-lookup"><span data-stu-id="20e30-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="20e30-109">VMSS de Windows y configuración de estado deseado con plantillas de Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="20e30-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="20e30-110">Cómo pasar las credenciales al controlador de extensiones de la DSC de Azure</span><span class="sxs-lookup"><span data-stu-id="20e30-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="20e30-111">Historial de la extensión Desired State Configuration de Azure</span><span class="sxs-lookup"><span data-stu-id="20e30-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="20e30-112">DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="20e30-112">Azure Automation DSC</span></span>

<span data-ttu-id="20e30-113">El [servicio Azure Automation](https://azure.microsoft.com/en-us/services/automation/) le permite administrar configuraciones de DSC, recursos y nodos administrados dentro de Azure.</span><span class="sxs-lookup"><span data-stu-id="20e30-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="20e30-114">Para obtener más información, vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="20e30-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="20e30-115">DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="20e30-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="20e30-116">Introducción a DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="20e30-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="20e30-117">Incorporación de máquinas para administrarlas con DSC de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="20e30-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)