---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Clave del Registro DSCAutomationHostEnabled
ms.openlocfilehash: 0cecbadc6802938cadb4ffb9745a23e6b98544be
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
><span data-ttu-id="f4fe0-103">Se aplica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f4fe0-103">Applies to: Windows PowerShell 5.0</span></span>

# <a name="dscautomationhostenabled-registry-key"></a><span data-ttu-id="f4fe0-104">Clave del Registro DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="f4fe0-104">DSCAutomationHostEnabled registry key</span></span>

<span data-ttu-id="f4fe0-105">DSC usa la clave del Registro **DSCAutomationHostEnabled** en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** para habilitar la configuración de la máquina en el arranque inicial.</span><span class="sxs-lookup"><span data-stu-id="f4fe0-105">DSC uses the **DSCAutomationHostEnabled** registry key under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** to enable configuration of the machine at initial boot-up.</span></span>
<span data-ttu-id="f4fe0-106">DSCAutomationHostEnabled admite tres modos:</span><span class="sxs-lookup"><span data-stu-id="f4fe0-106">DSCAutomationHostEnabled supports three modes:</span></span>

|  <span data-ttu-id="f4fe0-107">Valor de DSCAutomationHostEnabled</span><span class="sxs-lookup"><span data-stu-id="f4fe0-107">DSCAutomationHostEnabled Value</span></span>  |  <span data-ttu-id="f4fe0-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="f4fe0-108">Description</span></span>   |
|---|---|
<span data-ttu-id="f4fe0-109">0</span><span class="sxs-lookup"><span data-stu-id="f4fe0-109">0</span></span> | <span data-ttu-id="f4fe0-110">Deshabilita la configuración de la máquina en el arranque.</span><span class="sxs-lookup"><span data-stu-id="f4fe0-110">Disable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="f4fe0-111">1</span><span class="sxs-lookup"><span data-stu-id="f4fe0-111">1</span></span> | <span data-ttu-id="f4fe0-112">Habilita la configuración de la máquina en el arranque.</span><span class="sxs-lookup"><span data-stu-id="f4fe0-112">Enable configuring the machine at boot-up.</span></span> |
<span data-ttu-id="f4fe0-113">2</span><span class="sxs-lookup"><span data-stu-id="f4fe0-113">2</span></span> | <span data-ttu-id="f4fe0-114">Habilita la configuración de la máquina solo si DSC está en estado pendiente o actual.</span><span class="sxs-lookup"><span data-stu-id="f4fe0-114">Enable configuring the machine only if DSC is in pending or current state.</span></span> <span data-ttu-id="f4fe0-115">Este es el valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="f4fe0-115">This is the default value.</span></span> |

## <a name="see-also"></a><span data-ttu-id="f4fe0-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="f4fe0-116">See Also</span></span>

<span data-ttu-id="f4fe0-117">Para obtener un ejemplo de cómo usar esta función para ejecutar configuraciones en el arranque inicial, consulte [Configuración de máquinas virtuales en el arranque inicial mediante DSC](bootstrapDsc.md).</span><span class="sxs-lookup"><span data-stu-id="f4fe0-117">For an example of how to use this feature to run configurations at initial boot-up, see [Configure a virtual machines at initial boot-up by using DSC](bootstrapDsc.md).</span></span>