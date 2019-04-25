---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085803"
---
# <a name="detailed-information-about-lcm-state"></a>Información detallada acerca del estado de LCM

Hemos realizado mejoras en la exposición de detalles sobre el estado de LCM. El estado LCMState que devuelve Get-DscLocalConfigurationManager puede contener ahora los siguientes valores:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

También hemos agregado una propiedad LCMStateDetail que contiene más información sobre el estado.
