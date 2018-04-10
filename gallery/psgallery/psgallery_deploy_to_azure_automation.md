---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 8da4eabead6a419dc0c01c74335c06bf8be25d0c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="7815f-103">Implementar en Automatización de Azure</span><span class="sxs-lookup"><span data-stu-id="7815f-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="7815f-104">El botón Deploy to Azure Automation (Implementar en Automatización de Azure) en la página de detalles del elemento implementará el elemento desde la Galería de PowerShell en Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="7815f-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Botón Deploy to Azure Automation (Implementar en Automatización de Azure)](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="7815f-106">Al hacer clic en él, se le redirigirá al Portal de administración de Azure, donde deberá iniciar sesión con sus credenciales de la cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="7815f-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="7815f-107">Si el elemento incluye dependencias, también se implementan en Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="7815f-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="7815f-108">ADVERTENCIA: Si ya existen en la cuenta de Automation el mismo elemento y versión, al implementarse de nuevo desde la Galería de PowerShell el elemento se sobrescribirá en la cuenta de Automation.</span><span class="sxs-lookup"><span data-stu-id="7815f-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="7815f-109">Si se implementa un módulo, aparecerá en la sección Módulos de Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="7815f-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="7815f-110">Si se implementa un script, aparecerá en la sección Runbooks de Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="7815f-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="7815f-111">El botón Deploy to Azure Automation (Implementar en Automatización de Azure) se puede deshabilitar mediante la adición de la etiqueta AzureAutomationNotSupported a los metadatos del elemento.</span><span class="sxs-lookup"><span data-stu-id="7815f-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="7815f-112">Para obtener más información sobre Automatización de Azure, consulte el [sitio web de Automatización de Azure](http://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="7815f-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/services/automation/).</span></span>