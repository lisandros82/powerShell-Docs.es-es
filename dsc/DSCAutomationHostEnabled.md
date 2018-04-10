---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Clave del Registro DSCAutomationHostEnabled
ms.openlocfilehash: 9fd71120b4959a7b14094922b453b05b217f3736
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="74723-103">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="74723-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="74723-104">Clave del Registro DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="74723-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="74723-105">DSC usa la clave del Registro **DSCAutomationHostEnabled** en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** para habilitar la configuración de la máquina en el arranque inicial.</span><span class="sxs-lookup"><span data-stu-id="74723-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="74723-106">DSCAutomationHostEnabled admite tres modos:</span><span class="sxs-lookup"><span data-stu-id="74723-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="74723-107">Valor de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="74723-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="74723-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="74723-108">Description</span></span>   |
|---|---|
<span data-ttu-id="74723-109">0</span><span class="sxs-lookup"><span data-stu-id="74723-109">0</span></span> | <span data-ttu-id="74723-110">Deshabilita la configuración de la máquina en el arranque.</span><span class="sxs-lookup"><span data-stu-id="74723-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="74723-111">1</span><span class="sxs-lookup"><span data-stu-id="74723-111">1</span></span> | <span data-ttu-id="74723-112">Habilita la configuración de la máquina en el arranque.</span><span class="sxs-lookup"><span data-stu-id="74723-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="74723-113">2</span><span class="sxs-lookup"><span data-stu-id="74723-113">2</span></span> | <span data-ttu-id="74723-114">Habilita la configuración de la máquina solo si DSC está en estado pendiente o actual.</span><span class="sxs-lookup"><span data-stu-id="74723-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="74723-115">Este es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="74723-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="74723-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="74723-116">See Also</span></span>

<span data-ttu-id="74723-117">Para obtener un ejemplo de cómo usar esta función para ejecutar configuraciones en el arranque inicial, consulte [Configuración de máquinas virtuales en el arranque inicial mediante DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="74723-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>