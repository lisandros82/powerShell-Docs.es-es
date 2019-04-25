---
ms.date: 09/11/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Creación de una cuenta de Galería de PowerShell
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084213"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="e3361-103">Creación de una cuenta de Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3361-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="e3361-104">Debe crear una cuenta de la Galería de PowerShell antes de publicar contenido en la galería.</span><span class="sxs-lookup"><span data-stu-id="e3361-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="e3361-105">Las cuentas de la Galería de PowerShell deben vincularse a una cuenta de inicio de sesión habilitada para correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="e3361-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="e3361-106">Esta cuenta puede ser una cuenta de Azure Active Directory o un identificador de Microsoft, como una cuenta de correo electrónico de outlook.com o hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="e3361-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="e3361-107">Para crear una cuenta de la Galería de PowerShell, vaya a [https://PowerShellGallery.com](https://PowerShellGallery.com) y haga clic en **Iniciar sesión** como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="e3361-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Registro de una cuenta nueva](../../Images/CreateAccount-Register.png)

<span data-ttu-id="e3361-109">Para usar una cuenta de Azure Active Directory, seleccione **Cuenta profesional o educativa** e inicie sesión con su cuenta.</span><span class="sxs-lookup"><span data-stu-id="e3361-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="e3361-110">Para usar un identificador de Microsoft elija **Cuenta personal** e inicie sesión.</span><span class="sxs-lookup"><span data-stu-id="e3361-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="e3361-111">Después, se le solicitará crear un nombre de usuario para la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3361-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="e3361-112">Revise los Términos de uso y la Directiva de privacidad, escriba un nombre de usuario y haga clic en **Registrarse**.</span><span class="sxs-lookup"><span data-stu-id="e3361-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="e3361-113">El nombre de cuenta no se puede cambiar una vez creado.</span><span class="sxs-lookup"><span data-stu-id="e3361-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="e3361-114">Para más información, vea [Administración de los propietarios de paquetes](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="e3361-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="e3361-115">Procedimientos recomendados para cuentas de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3361-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="e3361-116">Es importante supervisar activamente la cuenta de correo electrónico que se usa con la cuenta de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3361-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="e3361-117">Todas las comunicaciones con los propietarios de paquetes de la Galería de PowerShell se realizan mediante esta dirección de correo electrónico.</span><span class="sxs-lookup"><span data-stu-id="e3361-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="e3361-118">Si el equipo de operaciones de la Galería de PowerShell no puede ponerse en contacto con el propietario de un paquete, puede que deba eliminarlo.</span><span class="sxs-lookup"><span data-stu-id="e3361-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="e3361-119">Las organizaciones que publican en la Galería de PowerShell a menudo crean una cuenta externa única con ese fin.</span><span class="sxs-lookup"><span data-stu-id="e3361-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="e3361-120">Se recomienda que use el reenvío de correo electrónico para reenviar notificaciones a una dirección dentro de su organización.</span><span class="sxs-lookup"><span data-stu-id="e3361-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="e3361-121">Cuando varios propietarios están asociados a un paquete, todas las notificaciones de la Galería de PowerShell se envían a todos los propietarios.</span><span class="sxs-lookup"><span data-stu-id="e3361-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="e3361-122">Para más información, vea [Administración de los propietarios de paquetes](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="e3361-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
