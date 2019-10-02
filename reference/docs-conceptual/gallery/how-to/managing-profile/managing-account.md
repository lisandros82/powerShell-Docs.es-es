---
ms.date: 09/05/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Configuración de la cuenta de la Galería de PowerShell
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328036"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="b6af4-103">Configuración de la cuenta de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6af4-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="b6af4-104">La cuenta de la Galería de PowerShell es un nombre públicamente visible que está vinculado a una identidad.</span><span class="sxs-lookup"><span data-stu-id="b6af4-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="b6af4-105">Esa identidad es un identificador de Microsoft, como `user@hotmail.com` o `user@outlook.com`, o una cuenta de Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="b6af4-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="b6af4-106">La Galería de PowerShell ofrece la siguiente configuración de cuenta:</span><span class="sxs-lookup"><span data-stu-id="b6af4-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="b6af4-107">La cuenta de correo electrónico asociada a la cuenta de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6af4-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="b6af4-108">Opciones de notificaciones por correo electrónico enviadas desde la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6af4-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="b6af4-109">La cuenta de usuario asociada a la cuenta de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6af4-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="b6af4-110">La imagen asociada a la cuenta de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6af4-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="b6af4-111">Dirección de correo electrónico</span><span class="sxs-lookup"><span data-stu-id="b6af4-111">Email address</span></span>

<span data-ttu-id="b6af4-112">La dirección de correo electrónico es el destino para las notificaciones de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6af4-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="b6af4-113">No tiene por qué coincidir con la cuenta de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="b6af4-113">It does not have to match the login account.</span></span> <span data-ttu-id="b6af4-114">Puede usar cualquier cuenta de correo electrónico a la que tenga acceso.</span><span class="sxs-lookup"><span data-stu-id="b6af4-114">You may use any email account you have access to.</span></span> <span data-ttu-id="b6af4-115">La Galería de PowerShell nunca proporciona su dirección de correo electrónico directamente a otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="b6af4-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![Cambiar dirección de correo electrónico](../../Images/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="b6af4-117">Cuando indica una nueva dirección de correo electrónico, la Galería de PowerShell envía un correo de comprobación a esa dirección.</span><span class="sxs-lookup"><span data-stu-id="b6af4-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="b6af4-118">El correo de comprobación contiene un vínculo a la Galería de PowerShell para completar el proceso de cambio.</span><span class="sxs-lookup"><span data-stu-id="b6af4-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="b6af4-119">Hasta que finalice el proceso de comprobación, todas las notificaciones se envían a la dirección anterior.</span><span class="sxs-lookup"><span data-stu-id="b6af4-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="b6af4-120">Notificaciones por correo electrónico</span><span class="sxs-lookup"><span data-stu-id="b6af4-120">Email notifications</span></span>

<span data-ttu-id="b6af4-121">La Galería de PowerShell ofrece estas opciones de notificación:</span><span class="sxs-lookup"><span data-stu-id="b6af4-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="b6af4-122">Users can contact me through the PowerShell Gallery (Los usuarios pueden ponerse en contacto conmigo a través de la Galería de PowerShell)</span><span class="sxs-lookup"><span data-stu-id="b6af4-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="b6af4-123">Notify me when an item is pushed to the PowerShell Gallery using my account (Notificarme cuando se inserte un paquete en la Galería de PowerShell mediante mi cuenta)</span><span class="sxs-lookup"><span data-stu-id="b6af4-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![Cambiar dirección de correo electrónico](../../Images/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="b6af4-125">Como se indicó en la página, no se pueden deshabilitar las notificaciones críticas desde la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6af4-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="b6af4-126">Entre ellas se incluyen:</span><span class="sxs-lookup"><span data-stu-id="b6af4-126">These include:</span></span>

- <span data-ttu-id="b6af4-127">Notificaciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="b6af4-127">Security notifications</span></span>
- <span data-ttu-id="b6af4-128">Notificaciones de administración de cuentas de administradores de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b6af4-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="b6af4-129">Notificaciones sobre las pruebas ejecutadas por la Galería de PowerShell para los envíos realizados</span><span class="sxs-lookup"><span data-stu-id="b6af4-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="b6af4-130">Cambiar la cuenta de inicio de sesión</span><span class="sxs-lookup"><span data-stu-id="b6af4-130">Change your login account</span></span>

<span data-ttu-id="b6af4-131">Para cambiar la cuenta de inicio de sesión, debe haber iniciado sesión con la cuenta actual.</span><span class="sxs-lookup"><span data-stu-id="b6af4-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="b6af4-132">Siga estos pasos para completar el cambio.</span><span class="sxs-lookup"><span data-stu-id="b6af4-132">Use the following steps to complete the change.</span></span>

![Configuración de cuenta de inicio de sesión](../../Images/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="b6af4-134">Haga clic en **Cambiar cuenta**.</span><span class="sxs-lookup"><span data-stu-id="b6af4-134">Click on **Change Account**.</span></span> <span data-ttu-id="b6af4-135">En una ventana emergente se explica que el cambio de la cuenta de inicio de sesión se aplica a todos los usos de dicha cuenta en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6af4-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="b6af4-136">Revise la información y, después, haga clic en **Siguiente** para continuar.</span><span class="sxs-lookup"><span data-stu-id="b6af4-136">Review the information, then click **OK** to continue.</span></span>

   ![Configuración de cuenta de inicio de sesión](../../Images/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="b6af4-138">Se le pedirá que inicie sesión con la _nueva cuenta_.</span><span class="sxs-lookup"><span data-stu-id="b6af4-138">You are then prompted to sign in using the _new account_.</span></span>

   ![Configuración de cuenta de inicio de sesión](../../Images/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="b6af4-140">Al hacer clic en **Siguiente**, verá un mensaje de que ha iniciado sesión con la cuenta actual.</span><span class="sxs-lookup"><span data-stu-id="b6af4-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="b6af4-141">Haga clic en **Sign out and sign in with a different account** (Cerrar sesión e iniciar sesión con una cuenta distinta).</span><span class="sxs-lookup"><span data-stu-id="b6af4-141">Click **Sign out and sign in with a different account**.</span></span>

   ![Configuración de cuenta de inicio de sesión](../../Images/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="b6af4-143">Escriba la contraseña de la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="b6af4-143">Enter the password of the new account.</span></span> <span data-ttu-id="b6af4-144">Después de escribir la contraseña, se le redirigirá a la página Configuración de la cuenta que muestra que se ha actualizado la cuenta de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="b6af4-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>


## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="b6af4-145">Habilitar autenticación de dos factores (2FA)</span><span class="sxs-lookup"><span data-stu-id="b6af4-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="b6af4-146">La autenticación de dos factores se recomienda para todos los usuarios que publiquen manualmente en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6af4-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="b6af4-147">Para habilitar la autenticación de dos factores, la cuenta de inicio de sesión debe tener al menos dos formas de autenticación registradas.</span><span class="sxs-lookup"><span data-stu-id="b6af4-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="b6af4-148">Una es una contraseña y las otras formas pueden ser:</span><span class="sxs-lookup"><span data-stu-id="b6af4-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="b6af4-149">Un número de teléfono que pueda recibir mensajes de texto</span><span class="sxs-lookup"><span data-stu-id="b6af4-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="b6af4-150">Una aplicación de autenticador registrado, como Microsoft Authenticator para teléfono móvil</span><span class="sxs-lookup"><span data-stu-id="b6af4-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="b6af4-151">Estas formas de autenticación deben configurarse en la información de la cuenta AAD o en la configuración de seguridad de cuenta de identificador de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b6af4-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="b6af4-152">Una vez habilitada la 2FA, tendrá que autenticarse con las formas de autenticación configuradas cada vez que inicie sesión en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6af4-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6af4-153">Al habilitar la autenticación de dos factores para el sitio de la Galería de PowerShell no es necesario que habilite 2FA para todos los usos de la cuenta de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="b6af4-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="b6af4-154">Para más información, vea [Acerca de la verificación en dos pasos](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span><span class="sxs-lookup"><span data-stu-id="b6af4-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="b6af4-155">Cambiar la foto de perfil</span><span class="sxs-lookup"><span data-stu-id="b6af4-155">Change your profile picture</span></span>

<span data-ttu-id="b6af4-156">La Galería de PowerShell se basa en Gravatar para almacenar y mostrar la imagen asociada a su perfil.</span><span class="sxs-lookup"><span data-stu-id="b6af4-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="b6af4-157">Para actualizar la imagen del perfil, visite [Gravatar.com](http://www.gravatar.com/).</span><span class="sxs-lookup"><span data-stu-id="b6af4-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
