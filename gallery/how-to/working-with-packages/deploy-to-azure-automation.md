---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Implementar en Automatización de Azure
ms.openlocfilehash: dc382b1cf3ceaa787f54c555d01e6bd9ba70e680
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084893"
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
- [Sitio web de Azure Automation](http://azure.microsoft.com/services/automation/)
