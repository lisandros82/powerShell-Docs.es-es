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
<a name="deploy-to-azure-automation"></a>Implementar en Automatización de Azure
===========================

El botón Deploy to Azure Automation (Implementar en Automatización de Azure) en la página de detalles del elemento implementará el elemento desde la Galería de PowerShell en Automatización de Azure.

![Botón Deploy to Azure Automation (Implementar en Automatización de Azure)](Images/DeployToAzureAutomationButton.png)

Al hacer clic en él, se le redirigirá al Portal de administración de Azure, donde deberá iniciar sesión con sus credenciales de la cuenta de Azure.
Si el elemento incluye dependencias, también se implementan en Automatización de Azure.

ADVERTENCIA: Si ya existen en la cuenta de Automation el mismo elemento y versión, al implementarse de nuevo desde la Galería de PowerShell el elemento se sobrescribirá en la cuenta de Automation.

Si se implementa un módulo, aparecerá en la sección Módulos de Automatización de Azure.  Si se implementa un script, aparecerá en la sección Runbooks de Automatización de Azure.

El botón Deploy to Azure Automation (Implementar en Automatización de Azure) se puede deshabilitar mediante la adición de la etiqueta AzureAutomationNotSupported a los metadatos del elemento.

Para obtener más información sobre Automatización de Azure, consulte el [sitio web de Automatización de Azure](http://azure.microsoft.com/en-us/services/automation/).

