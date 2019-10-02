---
ms.date: 06/12/2017
contributor: Farehar
keywords: gallery,powershell,psgallery
title: Requerir aceptación de licencia
ms.openlocfilehash: eaed248895d14bd455d2d8d3c2222d8848eeccae
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328216"
---
# <a name="require-license-acceptance"></a>Requerir aceptación de licencia

El texto Requerir la aceptación de la licencia aparece en la página de detalles de elementos correspondientes a los módulos que requieren la aceptación de la licencia. Para ver la licencia del módulo, haga clic en el vínculo "Ver License.txt".

![Requerir la aceptación de la licencia](../../Images/RequireLicenseAcceptance.png)

Se le pedirá a los usuarios que acepten la licencia cuando instalen, guarden o actualicen el módulo mediante PowerShellGet o cuando realicen una implementación en Azure Automation.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Requerir la aceptación de licencia de Implementar en Azure Automation

Si el módulo que se implementa en Azure Automation requiere la aceptación de la licencia, la UI del portal mostrará una advertencia que indica que el módulo requiere la aceptación de la licencia. Si hace clic en Aceptar, indica que está de acuerdo con los términos de licencia.

![Implementar en Azure Automation requiere la aceptación de la licencia](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Más detalles

[Requerir aceptación de la licencia en PowerShellGet](../../concepts/module-license-acceptance.md)
[Sitio web de Azure Automation](/azure/automation)
