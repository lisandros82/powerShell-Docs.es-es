---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Ocultar elementos
ms.openlocfilehash: bdcceba0ba18ade6a1d0f94602fd8d0f64af8936
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187548"
---
# <a name="unlisting-items"></a><span data-ttu-id="acbff-103">Ocultar elementos</span><span class="sxs-lookup"><span data-stu-id="acbff-103">Unlisting items</span></span>

<span data-ttu-id="acbff-104">**¿Por qué no se ofrece como opción la acción de quitar un elemento de la Galería de PowerShell?**</span><span class="sxs-lookup"><span data-stu-id="acbff-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="acbff-105">La Galería de PowerShell no permite que los usuarios eliminen sus elementos permanentemente.</span><span class="sxs-lookup"><span data-stu-id="acbff-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="acbff-106">Esto permite que otros usuarios establezcan dependencias con los elementos sin preocuparse de posibles interrupciones en el futuro.</span><span class="sxs-lookup"><span data-stu-id="acbff-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="acbff-107">Por ejemplo, si el módulo de Pester depende del módulo de Azure y este se quita de la Galería, el usuario ya no puede usar el módulo de Pester.</span><span class="sxs-lookup"><span data-stu-id="acbff-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="acbff-108">En lugar de quitar un elemento, puede ocultarlo.</span><span class="sxs-lookup"><span data-stu-id="acbff-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="acbff-109">**¿Qué pasa cuando se oculta un elemento en la Galería de PowerShell?**</span><span class="sxs-lookup"><span data-stu-id="acbff-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="acbff-110">Cuando se oculta un elemento como un módulo o un script en la Galería de PowerShell, se quita de la pestaña Elementos. Además, los elementos que se han ocultado no se podrán detectar mediante la barra de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="acbff-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="acbff-111">La única manera de descargar un elemento que se ha ocultado consiste en especificar el nombre exacto y la versión de dicho elemento.</span><span class="sxs-lookup"><span data-stu-id="acbff-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="acbff-112">Por este motivo, la acción de ocultar un elemento no interrumpe otros módulos o scripts que dependen de él.</span><span class="sxs-lookup"><span data-stu-id="acbff-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="acbff-113">Para ocultar el elemento, visite la página de detalles del elemento y seleccione Eliminar elemento.</span><span class="sxs-lookup"><span data-stu-id="acbff-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="acbff-114">Desactive la casilla Listed (Enumerado) y haga clic en Guardar.</span><span class="sxs-lookup"><span data-stu-id="acbff-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="acbff-115">**¿Cómo se puede quitar un elemento?**</span><span class="sxs-lookup"><span data-stu-id="acbff-115">**How can I remove an item?**</span></span>

<span data-ttu-id="acbff-116">Si se encuentra en un escenario en el que es necesario eliminar un elemento, póngase en contacto con los administradores de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="acbff-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="acbff-117">Los escenarios de eliminación válidos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="acbff-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="acbff-118">Problemas de infracción de los derechos de autor.</span><span class="sxs-lookup"><span data-stu-id="acbff-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="acbff-119">El elemento tiene un contenido potencialmente dañino.</span><span class="sxs-lookup"><span data-stu-id="acbff-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="acbff-120">El elemento contiene información confidencial.</span><span class="sxs-lookup"><span data-stu-id="acbff-120">Item contains sensitive data.</span></span>

<span data-ttu-id="acbff-121">Para enviar una solicitud de eliminación de elemento a los administradores de la Galería de PowerShell, visite la página de detalles del elemento y seleccione Ponerse en contacto con soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="acbff-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>