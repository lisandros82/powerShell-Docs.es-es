---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219868"
---
# <a name="detailed-information-about-lcm-state"></a>Información detallada acerca del estado de LCM

Hemos realizado mejoras en la exposición de detalles sobre el estado de LCM. El estado LCMState que devuelve Get-DscLocalConfigurationManager puede contener ahora los siguientes valores:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

También hemos agregado una propiedad LCMStateDetail que contiene más información sobre el estado.
