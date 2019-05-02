---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Administración de los propietarios de paquetes
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084154"
---
# <a name="managing-package-owners"></a><span data-ttu-id="75688-103">Administración de los propietarios de paquetes</span><span class="sxs-lookup"><span data-stu-id="75688-103">Managing package owners</span></span>

<span data-ttu-id="75688-104">La propiedad de un paquete en la Galería de PowerShell está definida por la persona que publicó el paquete en la Galería.</span><span class="sxs-lookup"><span data-stu-id="75688-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="75688-105">A veces estos metadatos deben administrarse después de la publicación inicial del paquete, lo que significa que los metadatos de propietario deben ser mutables, aunque el paquete en sí no lo es.</span><span class="sxs-lookup"><span data-stu-id="75688-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="75688-106">Todos los propietarios de paquetes son del mismo nivel.</span><span class="sxs-lookup"><span data-stu-id="75688-106">All package owners are peers.</span></span>
<span data-ttu-id="75688-107">Esto significa que cualquier propietario del paquete puede publicar una versión nueva de un paquete.</span><span class="sxs-lookup"><span data-stu-id="75688-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="75688-108">También significa que cualquier propietario del paquete puede quitar a otro propietario del paquete.</span><span class="sxs-lookup"><span data-stu-id="75688-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="75688-109">Ningún propietario tiene más autoridad que los demás propietarios.</span><span class="sxs-lookup"><span data-stu-id="75688-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="75688-110">Establecer el propietario inicial de un paquete</span><span class="sxs-lookup"><span data-stu-id="75688-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="75688-111">Cuando se publica un paquete nuevo en la Galería de PowerShell, el propietario inicial es el usuario que publicó el paquete.</span><span class="sxs-lookup"><span data-stu-id="75688-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="75688-112">Esto se determina mediante la clave de API que se usó en el cmdlet Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="75688-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="75688-113">Agregar propietarios</span><span class="sxs-lookup"><span data-stu-id="75688-113">Adding Owners</span></span>

<span data-ttu-id="75688-114">Una vez que se ha publicado un paquete en la Galería de PowerShell, es fácil invitar a otros usuarios para que se conviertan en propietarios de un paquete.</span><span class="sxs-lookup"><span data-stu-id="75688-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="75688-115">[Inicie sesión](https://powershellgallery.com/users/account/LogOn) en la Galería de PowerShell con la cuenta que es el propietario actual de un paquete.</span><span class="sxs-lookup"><span data-stu-id="75688-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="75688-116">Vaya a la página de un paquete en la pestaña Paquetes, buscándola o haciendo clic en su nombre de usuario y en [**Manage My Packages**](https://www.powershellgallery.com/account/Packages) (Administrar mis paquetes).</span><span class="sxs-lookup"><span data-stu-id="75688-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="75688-117">Cuando haya iniciado sesión como propietario de un paquete, verá un vínculo "Manage Owners" (Administrar propietarios) en el lado izquierdo en el que debe hacer clic.</span><span class="sxs-lookup"><span data-stu-id="75688-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="75688-118">Escriba el nombre de usuario de la persona que quiere agregar como propietario y haga clic en Agregar.</span><span class="sxs-lookup"><span data-stu-id="75688-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="75688-119">Se enviará un correo electrónico al nuevo copropietario para invitarlo a que se convierta en propietario de un paquete.</span><span class="sxs-lookup"><span data-stu-id="75688-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="75688-120">Una vez que el usuario haya hecho clic en el vínculo, será un copropietario completo con control total sobre un paquete, lo que incluye la capacidad de quitar a otros usuarios como propietarios.</span><span class="sxs-lookup"><span data-stu-id="75688-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="75688-121">**NOTA**: Mientras el nuevo propietario no confirme la propiedad, *no* aparecerá como propietario de un paquete.</span><span class="sxs-lookup"><span data-stu-id="75688-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="75688-122">En la página **Manage Owners** (Administrar propietarios), verá una entrada "pending approval" (pendiente de aprobación) en los propietarios actuales.</span><span class="sxs-lookup"><span data-stu-id="75688-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="75688-123">Es posible quitar esta invitación, del mismo modo que se pueden quitar otros propietarios.</span><span class="sxs-lookup"><span data-stu-id="75688-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="75688-124">Este proceso de invitaciones impide que los usuarios agreguen de forma errónea a otros usuarios como propietarios de sus paquetes.</span><span class="sxs-lookup"><span data-stu-id="75688-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="75688-125">Tenga en cuenta que los metadatos "Authors" (Autores) son exclusivamente texto de forma libre; solo se controla "Owners" (Propietarios).</span><span class="sxs-lookup"><span data-stu-id="75688-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="75688-126">Quitar propietarios</span><span class="sxs-lookup"><span data-stu-id="75688-126">Removing Owners</span></span>

<span data-ttu-id="75688-127">Cuando un paquete tiene varios propietarios y es necesario quitar uno, el proceso es sencillo:</span><span class="sxs-lookup"><span data-stu-id="75688-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="75688-128">[Inicie sesión](https://powershellgallery.com/users/account/LogOn) en la Galería de PowerShell con la cuenta que es el propietario actual de un paquete.</span><span class="sxs-lookup"><span data-stu-id="75688-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="75688-129">Vaya a la página de un paquete en la pestaña Paquetes, buscándola o haciendo clic en su nombre de usuario y en [**Manage My Packages**](https://www.powershellgallery.com/account/Packages) (Administrar mis paquetes).</span><span class="sxs-lookup"><span data-stu-id="75688-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="75688-130">Cuando haya iniciado sesión como propietario de un paquete, verá un vínculo "Manage Owners" (Administrar propietarios) en el lado izquierdo en el que debe hacer clic.</span><span class="sxs-lookup"><span data-stu-id="75688-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="75688-131">Haga clic en el vínculo "Remove" (Quitar) junto al propietario que se va a quitar.</span><span class="sxs-lookup"><span data-stu-id="75688-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="75688-132">Transferencia de la propiedad de paquetes</span><span class="sxs-lookup"><span data-stu-id="75688-132">Transferring Package Ownership</span></span>

<span data-ttu-id="75688-133">En ocasiones recibimos solicitudes de soporte técnico para transferir la propiedad de un paquete de un usuario a otro, pero la mayoría de las veces puede hacerlo usted.</span><span class="sxs-lookup"><span data-stu-id="75688-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="75688-134">La transferencia de la propiedad de un usuario a otro es simplemente una combinación de las dos funciones anteriores.</span><span class="sxs-lookup"><span data-stu-id="75688-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="75688-135">El propietario actual invita al usuario nuevo a convertirse en copropietario y el usuario nuevo acepta la invitación.</span><span class="sxs-lookup"><span data-stu-id="75688-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="75688-136">El usuario nuevo quita al usuario anterior de la lista de propietarios.</span><span class="sxs-lookup"><span data-stu-id="75688-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="75688-137">Hemos recibido esta solicitud en un par de formularios, pero el proceso funciona de la misma manera.</span><span class="sxs-lookup"><span data-stu-id="75688-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="75688-138">La propiedad del paquete cambia de un desarrollador a otro.</span><span class="sxs-lookup"><span data-stu-id="75688-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="75688-139">El paquete se publicó accidentalmente con una cuenta errónea.</span><span class="sxs-lookup"><span data-stu-id="75688-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="75688-140">Paquetes huérfanos</span><span class="sxs-lookup"><span data-stu-id="75688-140">Orphaned Packages</span></span>

<span data-ttu-id="75688-141">Por último, se ha producido otro escenario, aunque no muchas veces.</span><span class="sxs-lookup"><span data-stu-id="75688-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="75688-142">Consiste en que algunos paquetes se han convertido en huérfanos y la única cuenta de propietario de paquete que existe no se puede usar para agregar nuevos propietarios.</span><span class="sxs-lookup"><span data-stu-id="75688-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="75688-143">Aquí se proporcionan algunos ejemplos de este escenario:</span><span class="sxs-lookup"><span data-stu-id="75688-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="75688-144">La cuenta del propietario está asociada a una dirección de correo electrónico que ya no existe y el usuario ha olvidado la contraseña.</span><span class="sxs-lookup"><span data-stu-id="75688-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="75688-145">El propietario registrado ha dejado la empresa que produce el paquete y no es posible ponerse en contacto con él para actualizar la propiedad del paquete.</span><span class="sxs-lookup"><span data-stu-id="75688-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="75688-146">Debido a un error que solo ha afectado a algunos paquetes, el paquete no tiene propietario en la galería.</span><span class="sxs-lookup"><span data-stu-id="75688-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="75688-147">Los administradores de la Galería de PowerShell pueden acceder al vínculo "Manage Owners" (Administrar propietarios) para cualquier paquete.</span><span class="sxs-lookup"><span data-stu-id="75688-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="75688-148">Si es usted el propietario legítimo de un paquete y no puede ponerse en contacto con el propietario actual para obtener permisos de propiedad, use el vínculo de la Galería "Notificar abuso" para ponerse en contacto con los administradores de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75688-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="75688-149">Iniciaremos un proceso para comprobar que es el propietario del paquete.</span><span class="sxs-lookup"><span data-stu-id="75688-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="75688-150">Si llegamos a la conclusión de que usted debe ser el propietario del paquete, usaremos el vínculo "Manage Owners" (Administrar propietarios) para el paquete y le enviaremos una invitación para convertirse en propietario.</span><span class="sxs-lookup"><span data-stu-id="75688-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="75688-151">Solo lo haremos después de comprobar que debe ser propietario. Este proceso de comprobación varía según las circunstancias.</span><span class="sxs-lookup"><span data-stu-id="75688-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="75688-152">En ocasiones, usaremos la dirección URL del proyecto del paquete para ponernos en contacto con el propietario del proyecto, pero también podemos usar Twitter, el correo electrónico u otros medios para ponernos en contacto con el propietario del proyecto.</span><span class="sxs-lookup"><span data-stu-id="75688-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
