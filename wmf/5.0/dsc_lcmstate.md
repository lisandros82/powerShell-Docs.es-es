---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="detailed-information-about-lcm-state"></a>Información detallada acerca del estado de LCM

Hemos realizado mejoras en la exposición de detalles sobre el estado de LCM. El estado LCMState que devuelve Get-DscLocalConfigurationManager puede contener ahora los siguientes valores:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

También hemos agregado una propiedad LCMStateDetail que contiene más información sobre el estado.

