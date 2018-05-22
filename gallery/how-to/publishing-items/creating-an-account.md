---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Creación de una cuenta de Galería de PowerShell
ms.openlocfilehash: 4a44b51967ea8acdd331f6b3c682fc5884bd2f54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="03850-103">Creación de una cuenta de Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="03850-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="03850-104">Es necesario establecer una cuenta de la Galería de PowerShell antes de publicar contenido en la galería.</span><span class="sxs-lookup"><span data-stu-id="03850-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="03850-105">Las cuentas de la Galería de PowerShell se deben vincular a una cuenta habilitada para recibir correo electrónico de Azure Active Directory o a una cuenta de correo electrónico de Microsoft (con dominio outlook.com, hotmail.com, etc.).</span><span class="sxs-lookup"><span data-stu-id="03850-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="03850-106">Para crear una cuenta de la Galería de PowerShell, vaya a https://PowerShellGallery.com y haga clic en "Register" (Registrarse). Consulte la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="03850-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span>

![Registro de una cuenta nueva](../../Images/CreatingAccount-Register.png)

<span data-ttu-id="03850-108">En la página siguiente, para usar una cuenta de Azure Active Directory, seleccione "Work or School Account" (Cuenta profesional o educativa) e inicie sesión con su cuenta.</span><span class="sxs-lookup"><span data-stu-id="03850-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span>
<span data-ttu-id="03850-109">Para usar una cuenta de Microsoft, como una con dominio hotmail.com o outlook.com, elija "Personal Account" (Cuenta personal) e inicie sesión.</span><span class="sxs-lookup"><span data-stu-id="03850-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span>

<span data-ttu-id="03850-110">Una vez que inicie sesión, se le solicitará crear un nombre de usuario para la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03850-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span>
<span data-ttu-id="03850-111">Revise los Términos de uso y la Directiva de privacidad a las que se proporcionan vínculos, escriba un nombre de usuario y haga clic en Register (Registrarse).</span><span class="sxs-lookup"><span data-stu-id="03850-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="03850-112">Nota: Este nombre de cuenta no se puede cambiar una vez creado.</span><span class="sxs-lookup"><span data-stu-id="03850-112">Note: This account name cannot be changed once it is created.</span></span>
<span data-ttu-id="03850-113">Consulte [Administrar propietarios de elementos](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) para detalles adicionales al respecto.</span><span class="sxs-lookup"><span data-stu-id="03850-113">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="03850-114">Procedimientos recomendados para cuentas de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="03850-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="03850-115">Es importante supervisar activamente la cuenta de correo electrónico que se usa con la cuenta de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03850-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="03850-116">Toda comunicación con los propietarios de elementos de la Galería de PowerShell se realiza por correo electrónico con la dirección asociada a la cuenta de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03850-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="03850-117">Si no podemos ponernos en contacto con el propietario de un elemento, es posible que el equipo de operaciones deba eliminar el elemento en ciertas circunstancias.</span><span class="sxs-lookup"><span data-stu-id="03850-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="03850-118">Las organizaciones que publican en la Galería de PowerShell a menudo crean una cuenta única con ese fin en Outlook.com o en otro dominio de cuenta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="03850-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="03850-119">En muchos casos, no se supervisa con regularidad esa cuenta.</span><span class="sxs-lookup"><span data-stu-id="03850-119">In many cases that account is not regularly monitored.</span></span>
<span data-ttu-id="03850-120">En ese caso, un procedimiento recomendado es usar el reenvío de Outlook para enviar el correo electrónico a otra cuenta, habitualmente una dentro de la organización, que el propietario del elemento sí supervisará.</span><span class="sxs-lookup"><span data-stu-id="03850-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="03850-121">Si un elemento tiene asociados varios propietarios, toda comunicación que provenga de la Galería de PowerShell llegará a todos los propietarios.</span><span class="sxs-lookup"><span data-stu-id="03850-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="03850-122">Consulte [Administrar propietarios de elementos](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) para detalles adicionales sobre cómo agregar propietarios a un elemento.</span><span class="sxs-lookup"><span data-stu-id="03850-122">See [Managing Item Owners](https://msdn.microsoft.com/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span>