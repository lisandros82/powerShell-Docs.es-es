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
# <a name="creating-a-powershell-gallery-account"></a>Creación de una cuenta de Galería de PowerShell

Debe crear una cuenta de la Galería de PowerShell antes de publicar contenido en la galería.
Las cuentas de la Galería de PowerShell deben vincularse a una cuenta de inicio de sesión habilitada para correo electrónico. Esta cuenta puede ser una cuenta de Azure Active Directory o un identificador de Microsoft, como una cuenta de correo electrónico de outlook.com o hotmail.com.

Para crear una cuenta de la Galería de PowerShell, vaya a [https://PowerShellGallery.com](https://PowerShellGallery.com) y haga clic en **Iniciar sesión** como se muestra en la imagen siguiente.

![Registro de una cuenta nueva](../../Images/CreateAccount-Register.png)

Para usar una cuenta de Azure Active Directory, seleccione **Cuenta profesional o educativa** e inicie sesión con su cuenta. Para usar un identificador de Microsoft elija **Cuenta personal** e inicie sesión.

Después, se le solicitará crear un nombre de usuario para la Galería de PowerShell. Revise los Términos de uso y la Directiva de privacidad, escriba un nombre de usuario y haga clic en **Registrarse**.

> [!NOTE]
> El nombre de cuenta no se puede cambiar una vez creado. Para más información, vea [Administración de los propietarios de paquetes](managing-package-owners.md).

## <a name="recommended-practices-for-powershell-gallery-accounts"></a>Procedimientos recomendados para cuentas de la Galería de PowerShell

Es importante supervisar activamente la cuenta de correo electrónico que se usa con la cuenta de la Galería de PowerShell. Todas las comunicaciones con los propietarios de paquetes de la Galería de PowerShell se realizan mediante esta dirección de correo electrónico. Si el equipo de operaciones de la Galería de PowerShell no puede ponerse en contacto con el propietario de un paquete, puede que deba eliminarlo.

Las organizaciones que publican en la Galería de PowerShell a menudo crean una cuenta externa única con ese fin. Se recomienda que use el reenvío de correo electrónico para reenviar notificaciones a una dirección dentro de su organización.

Cuando varios propietarios están asociados a un paquete, todas las notificaciones de la Galería de PowerShell se envían a todos los propietarios. Para más información, vea [Administración de los propietarios de paquetes](managing-package-owners.md).
