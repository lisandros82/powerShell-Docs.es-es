---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Ocultar paquetes
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328276"
---
# <a name="unlisting-packages"></a><span data-ttu-id="91208-103">Ocultar paquetes</span><span class="sxs-lookup"><span data-stu-id="91208-103">Unlisting Packages</span></span>

<span data-ttu-id="91208-104">**¿Por qué no se ofrece como opción la acción de quitar un paquete de la Galería de PowerShell?**</span><span class="sxs-lookup"><span data-stu-id="91208-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="91208-105">La Galería de PowerShell no permite que los usuarios eliminen sus paquetes permanentemente.</span><span class="sxs-lookup"><span data-stu-id="91208-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="91208-106">Esto permite que otros usuarios establezcan dependencias con los paquetes sin preocuparse de posibles interrupciones en el futuro.</span><span class="sxs-lookup"><span data-stu-id="91208-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="91208-107">Por ejemplo, si el módulo de Pester depende del módulo de Azure y este se quita de la Galería, el usuario ya no puede usar el módulo de Pester.</span><span class="sxs-lookup"><span data-stu-id="91208-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="91208-108">En lugar de quitar un paquete, puede ocultarlo.</span><span class="sxs-lookup"><span data-stu-id="91208-108">Instead of removing an package, however, you can unlist it instead.</span></span>

<span data-ttu-id="91208-109">**¿Qué pasa cuando se oculta un paquete en la Galería de PowerShell?**</span><span class="sxs-lookup"><span data-stu-id="91208-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="91208-110">Cuando se oculta un paquete como un módulo o un script en la Galería de PowerShell, se quita de la pestaña Paquetes. Además, los paquetes que se han ocultado no se podrán detectar mediante la barra de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="91208-110">Unlisting a package such as module or script on PowerShell Gallery will remove it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="91208-111">La única manera de descargar un paquete que se ha ocultado consiste en especificar el nombre exacto y la versión de dicho paquete.</span><span class="sxs-lookup"><span data-stu-id="91208-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="91208-112">Por este motivo, la acción de ocultar un paquete no interrumpe otros módulos o scripts que dependen de él.</span><span class="sxs-lookup"><span data-stu-id="91208-112">Because of this, the unlisting of an package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="91208-113">Para ocultar el paquete, visite la página de detalles del paquete y seleccione Eliminar paquete.</span><span class="sxs-lookup"><span data-stu-id="91208-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="91208-114">Desactive la casilla Listed (Enumerado) y haga clic en Guardar.</span><span class="sxs-lookup"><span data-stu-id="91208-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="91208-115">**¿Cómo se puede quitar un paquete?**</span><span class="sxs-lookup"><span data-stu-id="91208-115">**How can I remove an package?**</span></span>

<span data-ttu-id="91208-116">Si se encuentra en un escenario en el que es necesario eliminar un paquete, póngase en contacto con los administradores de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91208-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="91208-117">Los escenarios de eliminación válidos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="91208-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="91208-118">Problemas de infracción de los derechos de autor.</span><span class="sxs-lookup"><span data-stu-id="91208-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="91208-119">El paquete tiene un contenido potencialmente dañino.</span><span class="sxs-lookup"><span data-stu-id="91208-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="91208-120">El paquete contiene información confidencial.</span><span class="sxs-lookup"><span data-stu-id="91208-120">Package contains sensitive data.</span></span>

<span data-ttu-id="91208-121">Para enviar una solicitud de eliminación de paquete a los administradores de la Galería de PowerShell, visite la página de detalles del paquete y seleccione Ponerse en contacto con soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="91208-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
