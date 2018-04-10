---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a>Información detallada acerca del estado de LCM

Hemos realizado mejoras en la exposición de detalles sobre el estado de LCM. El estado LCMState que devuelve Get-DscLocalConfigurationManager puede contener ahora los siguientes valores:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

También hemos agregado una propiedad LCMStateDetail que contiene más información sobre el estado.