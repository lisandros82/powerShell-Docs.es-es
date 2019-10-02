---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Implementar en Automatización de Azure
ms.openlocfilehash: 707691e24a77647064e60da0d9a31ad5eece1c59
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327916"
---
# <a name="deploy-to-azure-automation"></a>Implementar en Automatización de Azure

El botón Deploy to Azure Automation (Implementar en Azure Automation) en la página de detalles del paquete implementará el paquete desde la Galería de PowerShell en Azure Automation.

![Botón Deploy to Azure Automation (Implementar en Automatización de Azure)](../../Images/DeployToAzureAutomationButton.png)

Al hacer clic en él, se le redirigirá al Portal de administración de Azure, donde deberá iniciar sesión con sus credenciales de la cuenta de Azure.
Si el paquete incluye dependencias, también se implementan en Azure Automation.

> [!WARNING]
> Si ya existen en la cuenta de Automation el mismo paquete y la misma versión, al implementarse de nuevo desde la Galería de PowerShell el paquete se sobrescribirá en la cuenta de Automation.

Si se implementa un módulo, aparecerá en la sección Módulos de Automatización de Azure.  Si se implementa un script, aparecerá en la sección Runbooks de Automatización de Azure.

El botón Deploy to Azure Automation (Implementar en Azure Automation) se puede deshabilitar mediante la adición de la etiqueta AzureAutomationNotSupported a los metadatos del paquete.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Requerir la aceptación de licencia de Implementar en Azure Automation

Si el módulo que se implementa en Azure Automation requiere la aceptación de la licencia, la UI del portal mostrará una advertencia que indica que el módulo requiere la aceptación de la licencia. Si hace clic en Aceptar, indica que está de acuerdo con los términos de licencia.

![Implementar en Azure Automation requiere la aceptación de la licencia](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Más detalles

- [Requerir la aceptación de la licencia en PowerShellGet](../../concepts/module-license-acceptance.md)
- [Requerir la aceptación de la licencia en la Galería de PowerShell](packages-that-require-license-acceptance.md)
- [Sitio web de Azure Automation](https://azure.microsoft.com/services/automation/)
