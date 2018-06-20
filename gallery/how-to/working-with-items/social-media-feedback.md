---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Envío de comentarios a través de medios sociales o comentarios
ms.openlocfilehash: a8e6097de4a565b504189b0b0488c45b6d78a8b6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188146"
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="9831f-103">Envío de comentarios a través de medios sociales o comentarios</span><span class="sxs-lookup"><span data-stu-id="9831f-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="9831f-104">La Galería de PowerShell admite dos enfoques para que los usuarios proporcionen comentarios públicos sobre un elemento:</span><span class="sxs-lookup"><span data-stu-id="9831f-104">The Powershell Gallery supports two approaches for users to provide public feedback on an item:</span></span>

- <span data-ttu-id="9831f-105">Use los vínculos que se encuentran en el borde de la izquierda para "compartir" un elemento en los sitios de medios sociales de Facebook, LinkedIn o Twitter.</span><span class="sxs-lookup"><span data-stu-id="9831f-105">Use the links on the left edge to "share" an item in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="9831f-106">Use la característica Comentario para publicar comentarios sobre un elemento y para permitir que los autores estén atentos a los comentarios en los elementos que publican.</span><span class="sxs-lookup"><span data-stu-id="9831f-106">Use the Comment feature to post comments on an item, and to allow Authors to watch for comments on items they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="9831f-107">Comentarios en medios sociales</span><span class="sxs-lookup"><span data-stu-id="9831f-107">Social Media Feedback</span></span>

<span data-ttu-id="9831f-108">En el lado izquierdo de la página de cada elemento de la Galería de PowerShell aparecen vínculos a Facebook, LinkedIn y Twitter.</span><span class="sxs-lookup"><span data-stu-id="9831f-108">On the left side of the page for each item in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="9831f-109">Haga clic en estos vínculos para abrir el sitio del medio social y poder compartir rápidamente un vínculo al elemento en cuestión.</span><span class="sxs-lookup"><span data-stu-id="9831f-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the item.</span></span>

<span data-ttu-id="9831f-110">Los usuarios deben iniciar sesión en el sitio que elijan para poder compartir el elemento de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9831f-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery item.</span></span>

<span data-ttu-id="9831f-111">Se aconseja a los usuarios que hagan esto si consideran que recomendarían cierto elemento a otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="9831f-111">Users are encouraged to do this if they find that an item is something they would recommend to others.</span></span>
<span data-ttu-id="9831f-112">La Galería de PowerShell comprobará las veces que se compartió el elemento en cada sitio de medio social e indicará esa información.</span><span class="sxs-lookup"><span data-stu-id="9831f-112">The PowerShell Gallery will check each social media site for "shares" of the item, and display how many times that item has been shared in each of the social media sites.</span></span>
<span data-ttu-id="9831f-113">Como esta acción solo muestra la cantidad de veces que se compartió algún contenido, se interpretará como que a los otros usuarios les gustó el elemento en cuestión.</span><span class="sxs-lookup"><span data-stu-id="9831f-113">Since this shows only the count of times something has been shared, it will be intepreted other users as "liking" the item.</span></span>


## <a name="comments"></a><span data-ttu-id="9831f-114">Comentarios</span><span class="sxs-lookup"><span data-stu-id="9831f-114">Comments</span></span>

<span data-ttu-id="9831f-115">La Galería de PowerShell usa el servicio LiveFyre para permitir que los usuarios comenten en los elementos.</span><span class="sxs-lookup"><span data-stu-id="9831f-115">The PowerShell Gallery uses the LiveFyre service to allow users to comment on items.</span></span>
<span data-ttu-id="9831f-116">Los usuarios que desean dejar recomendaciones o comentarios pueden usar esta característica para brindar comentarios visibles para cualquier persona que visite la página del elemento.</span><span class="sxs-lookup"><span data-stu-id="9831f-116">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the item page.</span></span>
<span data-ttu-id="9831f-117">Los propietarios del elemento pueden seguir estos comentarios y recibir notificaciones cuando alguien publique uno.</span><span class="sxs-lookup"><span data-stu-id="9831f-117">Item owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="9831f-118">El sistema de comentarios se basa en LiveFyre, un servicio independiente no administrado por Microsoft y que requiere un inicio de sesión único para poder usarlo.</span><span class="sxs-lookup"><span data-stu-id="9831f-118">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="9831f-119">La primera vez que decida dejar un comentario o seguir los comentarios sobre alguno de sus elementos, deberá crear una cuenta de LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="9831f-119">The first time you choose to leave a comment or Follow comments on one of your items, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="9831f-120">Si creó una cuenta de LiveFyre y ya inició sesión, puede crear un comentario sobre el elemento y, luego, hacer clic en "Publicar comentario..." El comentario no será visible de inmediato.</span><span class="sxs-lookup"><span data-stu-id="9831f-120">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the item, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="9831f-121">Los administradores de la Galería de PowerShell moderan los comentarios sobre los elementos de la galería y revisan todas las publicaciones antes de que se publiquen y que los demás usuarios puedan verlas.</span><span class="sxs-lookup"><span data-stu-id="9831f-121">Comments for gallery items are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="9831f-122">El propósito de moderar los comentarios es garantizar que cumplen con los lineamientos de comportamiento público coherentes con los [Términos de uso](https://www.powershellgallery.com/policies/Terms) de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9831f-122">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="9831f-123">Se recomienda que los propietarios de los elementos sigan los comentarios que se publican en LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="9831f-123">Item owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="9831f-124">Se requiere una cuenta de LiveFyre y se recomienda usar la misma dirección de correo electrónico que se usa para publicar el elemento en LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="9831f-124">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your item in LiveFyre.</span></span>
<span data-ttu-id="9831f-125">Para seguir los comentarios, inicie sesión en LiveFyre y vaya a cualquier elemento del que sea propietario.</span><span class="sxs-lookup"><span data-stu-id="9831f-125">To Follow comments, log into LiveFyre, and navigate to any item where you are listed as an Owner.</span></span>
<span data-ttu-id="9831f-126">Debajo del cuadro Comentario que aparece en la parte inferior de cada elemento, verá el texto "+Seguir".</span><span class="sxs-lookup"><span data-stu-id="9831f-126">Below the Comment box at the bottom of each item you will see "+Follow".</span></span>
<span data-ttu-id="9831f-127">Una vez que haga clic en esta opción, LiveFyre enviará un correo electrónico a la dirección de correo electrónico registrada cada vez que se haga un comentario sobre el elemento.</span><span class="sxs-lookup"><span data-stu-id="9831f-127">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the item.</span></span>