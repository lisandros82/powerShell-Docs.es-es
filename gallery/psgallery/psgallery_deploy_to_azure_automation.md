---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="ea0a3-103">Implementar en Automatización de Azure</span><span class="sxs-lookup"><span data-stu-id="ea0a3-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="ea0a3-104">El botón Deploy to Azure Automation (Implementar en Automatización de Azure) en la página de detalles del elemento implementará el elemento desde la Galería de PowerShell en Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="ea0a3-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Botón Deploy to Azure Automation (Implementar en Automatización de Azure)](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="ea0a3-106">Al hacer clic en él, se le redirigirá al Portal de administración de Azure, donde deberá iniciar sesión con sus credenciales de la cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="ea0a3-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="ea0a3-107">Si el elemento incluye dependencias, también se implementan en Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="ea0a3-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="ea0a3-108">ADVERTENCIA: Si ya existen en la cuenta de Automation el mismo elemento y versión, al implementarse de nuevo desde la Galería de PowerShell el elemento se sobrescribirá en la cuenta de Automation.</span><span class="sxs-lookup"><span data-stu-id="ea0a3-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="ea0a3-109">Si se implementa un módulo, aparecerá en la sección Módulos de Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="ea0a3-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="ea0a3-110">Si se implementa un script, aparecerá en la sección Runbooks de Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="ea0a3-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="ea0a3-111">El botón Deploy to Azure Automation (Implementar en Automatización de Azure) se puede deshabilitar mediante la adición de la etiqueta AzureAutomationNotSupported a los metadatos del elemento.</span><span class="sxs-lookup"><span data-stu-id="ea0a3-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="ea0a3-112">Para obtener más información sobre Automatización de Azure, consulte el [sitio web de Automatización de Azure](http://azure.microsoft.com/en-us/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="ea0a3-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/en-us/services/automation/).</span></span>

