---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Administración de los propietarios de paquetes
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328266"
---
# <a name="managing-package-owners"></a>Administración de los propietarios de paquetes

La propiedad de un paquete en la Galería de PowerShell está definida por la persona que publicó el paquete en la Galería.
A veces estos metadatos deben administrarse después de la publicación inicial del paquete, lo que significa que los metadatos de propietario deben ser mutables, aunque el paquete en sí no lo es.

Todos los propietarios de paquetes son del mismo nivel.
Esto significa que cualquier propietario del paquete puede publicar una versión nueva de un paquete. También significa que cualquier propietario del paquete puede quitar a otro propietario del paquete.
Ningún propietario tiene más autoridad que los demás propietarios.

## <a name="setting-a-packages-initial-owner"></a>Establecer el propietario inicial de un paquete

Cuando se publica un paquete nuevo en la Galería de PowerShell, el propietario inicial es el usuario que publicó el paquete. Esto se determina mediante la clave de API que se usó en el cmdlet Publish-Module.

## <a name="adding-owners"></a>Agregar propietarios

Una vez que se ha publicado un paquete en la Galería de PowerShell, es fácil invitar a otros usuarios para que se conviertan en propietarios de un paquete.

1. [Inicie sesión](https://powershellgallery.com/users/account/LogOn) en la Galería de PowerShell con la cuenta que es el propietario actual de un paquete.
2. Vaya a la página de un paquete en la pestaña Paquetes, buscándola o haciendo clic en su nombre de usuario y en [**Manage My Packages**](https://www.powershellgallery.com/account/Packages) (Administrar mis paquetes).
3. Cuando haya iniciado sesión como propietario de un paquete, verá un vínculo "Manage Owners" (Administrar propietarios) en el lado izquierdo en el que debe hacer clic.
4. Escriba el nombre de usuario de la persona que quiere agregar como propietario y haga clic en Agregar.
5. Se enviará un correo electrónico al nuevo copropietario para invitarlo a que se convierta en propietario de un paquete.
6. Una vez que el usuario haya hecho clic en el vínculo, será un copropietario completo con control total sobre un paquete, lo que incluye la capacidad de quitar a otros usuarios como propietarios.

**NOTA**: Mientras el nuevo propietario no confirme la propiedad, *no* aparecerá como propietario de un paquete.
En la página **Manage Owners** (Administrar propietarios), verá una entrada "pending approval" (pendiente de aprobación) en los propietarios actuales.
Es posible quitar esta invitación, del mismo modo que se pueden quitar otros propietarios.
Este proceso de invitaciones impide que los usuarios agreguen de forma errónea a otros usuarios como propietarios de sus paquetes.

Tenga en cuenta que los metadatos "Authors" (Autores) son exclusivamente texto de forma libre; solo se controla "Owners" (Propietarios).


## <a name="removing-owners"></a>Quitar propietarios

Cuando un paquete tiene varios propietarios y es necesario quitar uno, el proceso es sencillo:

1. [Inicie sesión](https://powershellgallery.com/users/account/LogOn) en la Galería de PowerShell con la cuenta que es el propietario actual de un paquete.
2. Vaya a la página de un paquete en la pestaña Paquetes, buscándola o haciendo clic en su nombre de usuario y en [**Manage My Packages**](https://www.powershellgallery.com/account/Packages) (Administrar mis paquetes).
3. Cuando haya iniciado sesión como propietario de un paquete, verá un vínculo "Manage Owners" (Administrar propietarios) en el lado izquierdo en el que debe hacer clic.
4. Haga clic en el vínculo "Remove" (Quitar) junto al propietario que se va a quitar.



## <a name="transferring-package-ownership"></a>Transferencia de la propiedad de paquetes

En ocasiones recibimos solicitudes de soporte técnico para transferir la propiedad de un paquete de un usuario a otro, pero la mayoría de las veces puede hacerlo usted.
La transferencia de la propiedad de un usuario a otro es simplemente una combinación de las dos funciones anteriores.

1. El propietario actual invita al usuario nuevo a convertirse en copropietario y el usuario nuevo acepta la invitación.
2. El usuario nuevo quita al usuario anterior de la lista de propietarios.

Hemos recibido esta solicitud en un par de formularios, pero el proceso funciona de la misma manera.

- La propiedad del paquete cambia de un desarrollador a otro.
- El paquete se publicó accidentalmente con una cuenta errónea.


## <a name="orphaned-packages"></a>Paquetes huérfanos

Por último, se ha producido otro escenario, aunque no muchas veces.
Consiste en que algunos paquetes se han convertido en huérfanos y la única cuenta de propietario de paquete que existe no se puede usar para agregar nuevos propietarios.
Aquí se proporcionan algunos ejemplos de este escenario:

- La cuenta del propietario está asociada a una dirección de correo electrónico que ya no existe y el usuario ha olvidado la contraseña.
- El propietario registrado ha dejado la empresa que produce el paquete y no es posible ponerse en contacto con él para actualizar la propiedad del paquete.
- Debido a un error que solo ha afectado a algunos paquetes, el paquete no tiene propietario en la galería.

Los administradores de la Galería de PowerShell pueden acceder al vínculo "Manage Owners" (Administrar propietarios) para cualquier paquete.
Si es usted el propietario legítimo de un paquete y no puede ponerse en contacto con el propietario actual para obtener permisos de propiedad, use el vínculo de la Galería "Notificar abuso" para ponerse en contacto con los administradores de la Galería de PowerShell.
Iniciaremos un proceso para comprobar que es el propietario del paquete.
Si llegamos a la conclusión de que usted debe ser el propietario del paquete, usaremos el vínculo "Manage Owners" (Administrar propietarios) para el paquete y le enviaremos una invitación para convertirse en propietario.
Solo lo haremos después de comprobar que debe ser propietario. Este proceso de comprobación varía según las circunstancias.
En ocasiones, usaremos la dirección URL del proyecto del paquete para ponernos en contacto con el propietario del proyecto, pero también podemos usar Twitter, el correo electrónico u otros medios para ponernos en contacto con el propietario del proyecto.
