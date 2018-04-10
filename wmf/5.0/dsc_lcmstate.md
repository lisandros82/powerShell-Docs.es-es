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
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="2b8ac-102">Información detallada acerca del estado de LCM</span><span class="sxs-lookup"><span data-stu-id="2b8ac-102">Detailed information about LCM state</span></span>

<span data-ttu-id="2b8ac-103">Hemos realizado mejoras en la exposición de detalles sobre el estado de LCM.</span><span class="sxs-lookup"><span data-stu-id="2b8ac-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="2b8ac-104">El estado LCMState que devuelve Get-DscLocalConfigurationManager puede contener ahora los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="2b8ac-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="2b8ac-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="2b8ac-105">**Idle**</span></span>
* <span data-ttu-id="2b8ac-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="2b8ac-106">**Busy**</span></span>
* <span data-ttu-id="2b8ac-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="2b8ac-107">**PendingReboot**</span></span>
* <span data-ttu-id="2b8ac-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="2b8ac-108">**PendingConfiguration**</span></span>

<span data-ttu-id="2b8ac-109">También hemos agregado una propiedad LCMStateDetail que contiene más información sobre el estado.</span><span class="sxs-lookup"><span data-stu-id="2b8ac-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>