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
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="12635-102">Información detallada acerca del estado de LCM</span><span class="sxs-lookup"><span data-stu-id="12635-102">Detailed information about LCM state</span></span>

<span data-ttu-id="12635-103">Hemos realizado mejoras en la exposición de detalles sobre el estado de LCM.</span><span class="sxs-lookup"><span data-stu-id="12635-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="12635-104">El estado LCMState que devuelve Get-DscLocalConfigurationManager puede contener ahora los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="12635-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="12635-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="12635-105">**Idle**</span></span>
* <span data-ttu-id="12635-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="12635-106">**Busy**</span></span>
* <span data-ttu-id="12635-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="12635-107">**PendingReboot**</span></span>
* <span data-ttu-id="12635-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="12635-108">**PendingConfiguration**</span></span>

<span data-ttu-id="12635-109">También hemos agregado una propiedad LCMStateDetail que contiene más información sobre el estado.</span><span class="sxs-lookup"><span data-stu-id="12635-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
