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
# <a name="detailed-information-about-lcm-state"></a><span data-ttu-id="3cff3-102">Información detallada acerca del estado de LCM</span><span class="sxs-lookup"><span data-stu-id="3cff3-102">Detailed information about LCM state</span></span>

<span data-ttu-id="3cff3-103">Hemos realizado mejoras en la exposición de detalles sobre el estado de LCM.</span><span class="sxs-lookup"><span data-stu-id="3cff3-103">We have made improvements in exposing details about the LCM state.</span></span> <span data-ttu-id="3cff3-104">El estado LCMState que devuelve Get-DscLocalConfigurationManager puede contener ahora los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="3cff3-104">The LCMState that is returned by Get-DscLocalConfigurationManager can now contain the following values:</span></span>

* <span data-ttu-id="3cff3-105">**Idle**</span><span class="sxs-lookup"><span data-stu-id="3cff3-105">**Idle**</span></span>
* <span data-ttu-id="3cff3-106">**Busy**</span><span class="sxs-lookup"><span data-stu-id="3cff3-106">**Busy**</span></span>
* <span data-ttu-id="3cff3-107">**PendingReboot**</span><span class="sxs-lookup"><span data-stu-id="3cff3-107">**PendingReboot**</span></span>
* <span data-ttu-id="3cff3-108">**PendingConfiguration**</span><span class="sxs-lookup"><span data-stu-id="3cff3-108">**PendingConfiguration**</span></span>

<span data-ttu-id="3cff3-109">También hemos agregado una propiedad LCMStateDetail que contiene más información sobre el estado.</span><span class="sxs-lookup"><span data-stu-id="3cff3-109">We have also added an LCMStateDetail property that contains more information about the state.</span></span>
