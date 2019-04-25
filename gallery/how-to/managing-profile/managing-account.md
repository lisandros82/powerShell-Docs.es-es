---
ms.date: 09/05/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Configuración de la cuenta de la Galería de PowerShell
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084527"
---
# <a name="powershell-gallery-account-settings"></a>Configuración de la cuenta de la Galería de PowerShell

La cuenta de la Galería de PowerShell es un nombre públicamente visible que está vinculado a una identidad. Esa identidad es un identificador de Microsoft, como `user@hotmail.com` o `user@outlook.com`, o una cuenta de Azure Active Directory (AAD).

La Galería de PowerShell ofrece la siguiente configuración de cuenta:

- La cuenta de correo electrónico asociada a la cuenta de la Galería de PowerShell
- Opciones de notificaciones por correo electrónico enviadas desde la Galería de PowerShell
- La cuenta de usuario asociada a la cuenta de la Galería de PowerShell
- La imagen asociada a la cuenta de la Galería de PowerShell

## <a name="email-address"></a>Dirección de correo electrónico

La dirección de correo electrónico es el destino para las notificaciones de la Galería de PowerShell. No tiene por qué coincidir con la cuenta de inicio de sesión. Puede usar cualquier cuenta de correo electrónico a la que tenga acceso. La Galería de PowerShell nunca proporciona su dirección de correo electrónico directamente a otros usuarios.

![Cambiar dirección de correo electrónico](../../Images/PSGallery_AcccountEmailAddress.png)

Cuando indica una nueva dirección de correo electrónico, la Galería de PowerShell envía un correo de comprobación a esa dirección. El correo de comprobación contiene un vínculo a la Galería de PowerShell para completar el proceso de cambio. Hasta que finalice el proceso de comprobación, todas las notificaciones se envían a la dirección anterior.

## <a name="email-notifications"></a>Notificaciones por correo electrónico

La Galería de PowerShell ofrece estas opciones de notificación:

- Users can contact me through the PowerShell Gallery (Los usuarios pueden ponerse en contacto conmigo a través de la Galería de PowerShell)
- Notify me when an item is pushed to the PowerShell Gallery using my account (Notificarme cuando se inserte un paquete en la Galería de PowerShell mediante mi cuenta)

![Cambiar dirección de correo electrónico](../../Images/PSGallery_AccountEmailOptions.png)

Como se indicó en la página, no se pueden deshabilitar las notificaciones críticas desde la Galería de PowerShell.
Entre ellas se incluyen:

- Notificaciones de seguridad
- Notificaciones de administración de cuentas de administradores de la Galería de PowerShell
- Notificaciones sobre las pruebas ejecutadas por la Galería de PowerShell para los envíos realizados

## <a name="change-your-login-account"></a>Cambiar la cuenta de inicio de sesión

Para cambiar la cuenta de inicio de sesión, debe haber iniciado sesión con la cuenta actual. Siga estos pasos para completar el cambio.

![Configuración de cuenta de inicio de sesión](../../Images/PSGallery_LoginAccountSettings.png)

1. Haga clic en **Cambiar cuenta**. En una ventana emergente se explica que el cambio de la cuenta de inicio de sesión se aplica a todos los usos de dicha cuenta en la Galería de PowerShell. Revise la información y, después, haga clic en **Siguiente** para continuar.

   ![Configuración de cuenta de inicio de sesión](../../Images/PSGallery_LoginAccountChange-1.png)

2. Se le pedirá que inicie sesión con la _nueva cuenta_.

   ![Configuración de cuenta de inicio de sesión](../../Images/PSGallery_LoginAccountChange-2.png)

3. Al hacer clic en **Siguiente**, verá un mensaje de que ha iniciado sesión con la cuenta actual.
   Haga clic en **Sign out and sign in with a different account** (Cerrar sesión e iniciar sesión con una cuenta distinta).

   ![Configuración de cuenta de inicio de sesión](../../Images/PSGallery_LoginAccountChange-3.png)

4. Escriba la contraseña de la nueva cuenta. Después de escribir la contraseña, se le redirigirá a la página Configuración de la cuenta que muestra que se ha actualizado la cuenta de inicio de sesión.


## <a name="enable-two-factor-authentication-2fa"></a>Habilitar autenticación de dos factores (2FA)

La autenticación de dos factores se recomienda para todos los usuarios que publiquen manualmente en la Galería de PowerShell. Para habilitar la autenticación de dos factores, la cuenta de inicio de sesión debe tener al menos dos formas de autenticación registradas. Una es una contraseña y las otras formas pueden ser:

- Un número de teléfono que pueda recibir mensajes de texto
- Una aplicación de autenticador registrado, como Microsoft Authenticator para teléfono móvil

Estas formas de autenticación deben configurarse en la información de la cuenta AAD o en la configuración de seguridad de cuenta de identificador de Microsoft.

Una vez habilitada la 2FA, tendrá que autenticarse con las formas de autenticación configuradas cada vez que inicie sesión en la Galería de PowerShell.

> [!IMPORTANT]
> Al habilitar la autenticación de dos factores para el sitio de la Galería de PowerShell no es necesario que habilite 2FA para todos los usos de la cuenta de inicio de sesión. Para más información, vea [Acerca de la verificación en dos pasos](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).

## <a name="change-your-profile-picture"></a>Cambiar la foto de perfil

La Galería de PowerShell se basa en Gravatar para almacenar y mostrar la imagen asociada a su perfil. Para actualizar la imagen del perfil, visite [Gravatar.com](http://www.gravatar.com/).
