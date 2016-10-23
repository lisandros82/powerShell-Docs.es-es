---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: psgallery_deploy_to_azure_automation
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: c028bf6145b41c13bccda9543a782b838bd730ff

---

Implementar en Automatización de Azure
===========================

El botón Deploy to Azure Automation (Implementar en Automatización de Azure) en la página de detalles del elemento implementará el elemento desde la Galería de PowerShell en Automatización de Azure.

![Botón Deploy to Azure Automation (Implementar en Automatización de Azure)](Images/DeployToAzureAutomationButton.png)

Al hacer clic en él, se le redirigirá al Portal de administración de Azure, donde deberá iniciar sesión con sus credenciales de la cuenta de Azure.
Si el elemento incluye dependencias, también se implementan en Automatización de Azure.

ADVERTENCIA: Si ya existen en la cuenta de Automation el mismo elemento y versión, al implementarse de nuevo desde la Galería de PowerShell el elemento se sobrescribirá en la cuenta de Automation.

Si se implementa un módulo, aparecerá en la sección Módulos de Automatización de Azure.  Si se implementa un script, aparecerá en la sección Runbooks de Automatización de Azure.

El botón Deploy to Azure Automation (Implementar en Automatización de Azure) se puede deshabilitar mediante la adición de la etiqueta AzureAutomationNotSupported a los metadatos del elemento.

Para obtener más información sobre Automatización de Azure, consulte el [sitio web de Automatización de Azure](http://azure.microsoft.com/en-us/services/automation/).




<!--HONumber=Oct16_HO2-->


