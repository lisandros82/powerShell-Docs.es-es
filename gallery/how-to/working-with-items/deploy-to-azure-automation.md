---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Implementar en Automatización de Azure
ms.openlocfilehash: ced67809387a85e089259edf6b091d68e58ba6a7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="cfece-103">Implementar en Automatización de Azure</span><span class="sxs-lookup"><span data-stu-id="cfece-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="cfece-104">El botón Deploy to Azure Automation (Implementar en Automatización de Azure) en la página de detalles del elemento implementará el elemento desde la Galería de PowerShell en Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="cfece-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Botón Deploy to Azure Automation (Implementar en Automatización de Azure)](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="cfece-106">Al hacer clic en él, se le redirigirá al Portal de administración de Azure, donde deberá iniciar sesión con sus credenciales de la cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="cfece-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="cfece-107">Si el elemento incluye dependencias, también se implementan en Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="cfece-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="cfece-108">Si ya existen en la cuenta de Automation el mismo elemento y versión, al implementarse de nuevo desde la Galería de PowerShell el elemento se sobrescribirá en la cuenta de Automation.</span><span class="sxs-lookup"><span data-stu-id="cfece-108">If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="cfece-109">Si se implementa un módulo, aparecerá en la sección Módulos de Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="cfece-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="cfece-110">Si se implementa un script, aparecerá en la sección Runbooks de Automatización de Azure.</span><span class="sxs-lookup"><span data-stu-id="cfece-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="cfece-111">El botón Deploy to Azure Automation (Implementar en Automatización de Azure) se puede deshabilitar mediante la adición de la etiqueta AzureAutomationNotSupported a los metadatos del elemento.</span><span class="sxs-lookup"><span data-stu-id="cfece-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="cfece-112">Requerir la aceptación de licencia de Implementar en Azure Automation</span><span class="sxs-lookup"><span data-stu-id="cfece-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="cfece-113">Si el módulo que se implementa en Azure Automation requiere la aceptación de la licencia, la UI del portal mostrará una advertencia que indica que el módulo requiere la aceptación de la licencia.</span><span class="sxs-lookup"><span data-stu-id="cfece-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="cfece-114">Si hace clic en Aceptar, indica que está de acuerdo con los términos de licencia.</span><span class="sxs-lookup"><span data-stu-id="cfece-114">By clicking OK, you are accepting license terms.'</span></span>

![Implementar en Azure Automation requiere la aceptación de la licencia](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="cfece-116">Más detalles</span><span class="sxs-lookup"><span data-stu-id="cfece-116">More details</span></span>

- [<span data-ttu-id="cfece-117">Requerir la aceptación de la licencia en PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="cfece-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="cfece-118">Requerir la aceptación de la licencia en la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="cfece-118">Require License Acceptance in PowerShell Gallery</span></span>](items-that-require-license-acceptance.md)
- [<span data-ttu-id="cfece-119">Sitio web de Azure Automation</span><span class="sxs-lookup"><span data-stu-id="cfece-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
