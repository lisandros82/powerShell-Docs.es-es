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
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="9e2ba-102">Información detallada acerca del estado de LCM</span><span class="sxs-lookup"><span data-stu-id="9e2ba-102">Detailed information about LCM state</span></span>

<span data-ttu-id="9e2ba-103">Hemos realizado mejoras en la exposición de detalles sobre el estado de LCM.</span><span class="sxs-lookup"><span data-stu-id="9e2ba-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="9e2ba-104">El estado LCMState que devuelve Get-DscLocalConfigurationManager puede contener ahora los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="9e2ba-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="9e2ba-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="9e2ba-105">**Idle**</span></span>
* <span data-ttu-id="9e2ba-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="9e2ba-106">**Busy**</span></span>
* <span data-ttu-id="9e2ba-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="9e2ba-107">**PendingReboot**</span></span>
* <span data-ttu-id="9e2ba-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="9e2ba-108">**PendingConfiguration**</span></span>

<span data-ttu-id="9e2ba-109">También hemos agregado una propiedad LCMStateDetail que contiene más información sobre el estado.</span><span class="sxs-lookup"><span data-stu-id="9e2ba-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>

