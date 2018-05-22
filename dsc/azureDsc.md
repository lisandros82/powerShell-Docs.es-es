---
ms.date: 03/15/2018
keywords: dsc,powershell,configuration,setup
title: Uso de DSC en Microsoft Azure
ms.openlocfilehash: d35488c3f66895e930eaa84360f3d3ec9d74e9c7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="using-dsc-on-microsoft-azure"></a>Uso de DSC en Microsoft Azure

La configuración de estado deseado (DSC) es compatible con Microsoft Azure a través del [controlador de extensiones de la configuración de estado deseado de Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) y mediante la [DSC de Azure Automation](/azure/automation/automation-dsc-overview).

## <a name="azure-desired-state-configuration-extension-handler"></a>Controlador de extensiones de la configuración de estado deseado de Azure

La extensión de DSC de Azure permite que las máquinas virtuales hospedadas en Microsoft Azure se administren con DSC.
Para obtener más información, vea los temas siguientes:

- [Controlador de extensiones de la configuración de estado deseado de Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [VMSS de Windows y configuración de estado deseado con plantillas de Azure Resource Manager](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [Cómo pasar las credenciales al controlador de extensiones de la DSC de Azure](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [Historial de la extensión Desired State Configuration de Azure](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>DSC de Azure Automation

El [servicio Azure Automation](https://azure.microsoft.com/services/automation/) le permite administrar configuraciones de DSC, recursos y nodos administrados dentro de Azure. Para obtener más información, vea los temas siguientes:

- [DSC de Azure Automation](/azure/automation/automation-dsc-overview)
- [Introducción a DSC de Azure Automation](/azure/automation/automation-dsc-getting-started)
- [Incorporación de máquinas para administrarlas con DSC de Azure Automation](/azure/automation/automation-dsc-onboarding)