---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_unlist_items
ms.openlocfilehash: 8fa09c77e144f14bf0fd3493dff7650897100715
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="unlisting-items"></a><span data-ttu-id="49070-103">Ocultar elementos</span><span class="sxs-lookup"><span data-stu-id="49070-103">Unlisting items</span></span>

<span data-ttu-id="49070-104">**¿Por qué no se ofrece como opción la acción de quitar un elemento de la Galería de PowerShell?**</span><span class="sxs-lookup"><span data-stu-id="49070-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="49070-105">La Galería de PowerShell no permite que los usuarios eliminen sus elementos permanentemente.</span><span class="sxs-lookup"><span data-stu-id="49070-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span> <span data-ttu-id="49070-106">Esto permite que otros usuarios establezcan dependencias con los elementos sin preocuparse de posibles interrupciones en el futuro.</span><span class="sxs-lookup"><span data-stu-id="49070-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span> <span data-ttu-id="49070-107">Por ejemplo, si el módulo de Pester depende del módulo de Azure y este se quita de la Galería, el usuario ya no puede usar el módulo de Pester.</span><span class="sxs-lookup"><span data-stu-id="49070-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="49070-108">En lugar de quitar un elemento, puede ocultarlo.</span><span class="sxs-lookup"><span data-stu-id="49070-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="49070-109">**¿Qué pasa cuando se oculta un elemento en la Galería de PowerShell?**</span><span class="sxs-lookup"><span data-stu-id="49070-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="49070-110">Cuando se oculta un elemento como un módulo o un script en la Galería de PowerShell, se quita de la pestaña Elementos.</span><span class="sxs-lookup"><span data-stu-id="49070-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab.</span></span>
<span data-ttu-id="49070-111">Además, los elementos que se han ocultado no se podrán detectar mediante la barra de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="49070-111">In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="49070-112">La única manera de descargar un elemento que se ha ocultado consiste en especificar el nombre exacto y la versión de dicho elemento.</span><span class="sxs-lookup"><span data-stu-id="49070-112">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="49070-113">Por este motivo, la acción de ocultar un elemento no interrumpe otros módulos o scripts que dependen de él.</span><span class="sxs-lookup"><span data-stu-id="49070-113">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="49070-114">Para ocultar el elemento, visite la página de detalles del elemento y seleccione Eliminar elemento.</span><span class="sxs-lookup"><span data-stu-id="49070-114">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="49070-115">Desactive la casilla Listed (Enumerado) y haga clic en Guardar.</span><span class="sxs-lookup"><span data-stu-id="49070-115">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="49070-116">**¿Cómo se puede quitar un elemento?**</span><span class="sxs-lookup"><span data-stu-id="49070-116">**How can I remove an item?**</span></span>

<span data-ttu-id="49070-117">Si se encuentra en un escenario en el que es necesario eliminar un elemento, póngase en contacto con los administradores de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49070-117">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="49070-118">Los escenarios de eliminación válidos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="49070-118">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="49070-119">Problemas de infracción de los derechos de autor.</span><span class="sxs-lookup"><span data-stu-id="49070-119">Issues of copyright infringement.</span></span>
- <span data-ttu-id="49070-120">El elemento tiene un contenido potencialmente dañino.</span><span class="sxs-lookup"><span data-stu-id="49070-120">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="49070-121">El elemento contiene información confidencial.</span><span class="sxs-lookup"><span data-stu-id="49070-121">Item contains sensitive data.</span></span>

<span data-ttu-id="49070-122">Para enviar una solicitud de eliminación de elemento a los administradores de la Galería de PowerShell, visite la página de detalles del elemento y seleccione Ponerse en contacto con soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="49070-122">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>  


