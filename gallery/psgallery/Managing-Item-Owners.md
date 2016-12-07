---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: Administrar propietarios de elementos
ms.technology: powershell
ms.openlocfilehash: 36a3a3079bce642b16f0512ead2b0778b43e5d2d
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="managing-item-owners"></a>Administrar propietarios de elementos

La propiedad de un elemento en la Galería de PowerShell está definida por la persona que publicó el elemento en la Galería.
A veces estos metadatos deben administrarse después de la publicación inicial del elemento, lo que significa que los metadatos de propietario deben ser mutables, aunque el elemento en sí no lo es.

Todos los propietarios del elemento son del mismo nivel. Esto significa que cualquier propietario del elemento puede publicar una versión nueva de un elemento. También significa que cualquier propietario del elemento puede quitar a otro propietario del elemento. Ningún propietario tiene más autoridad que los demás propietarios.  

## <a name="setting-an-items-initial-owner"></a>Establecer el propietario inicial de un elemento 

Cuando se publica un elemento nuevo en la Galería de PowerShell, el propietario inicial es el usuario que publicó el elemento. Esto se determina mediante la clave de API que se usó en el cmdlet Publish-Module.

## <a name="adding-owners"></a>Agregar propietarios

Una vez que se ha publicado un elemento en la Galería de PowerShell, es fácil invitar a otros usuarios para que se conviertan en propietarios de un elemento.

1. [Inicie sesión](https://powershellgallery.com/users/account/LogOn) en la Galería de PowerShell con la cuenta que es el propietario actual de un elemento.
2. Vaya a la página de un elemento a través de la pestaña Elementos, buscándola o haciendo clic en su nombre de usuario y en [**Manage My Items**](https://www.powershellgallery.com/account/Packages) (Administrar mis elementos).
3. Cuando haya iniciado sesión como propietario de un elemento, verá un vínculo "Manage Owners" (Administrar propietarios) en el lado izquierdo. Haga clic en él.
4. Escriba el nombre de usuario de la persona que quiere agregar como propietario y haga clic en Agregar.
5. Se enviará un correo electrónico al nuevo copropietario para invitarlo a que se convierta en propietario de un elemento.
6. Una vez que el usuario haya hecho clic en el vínculo, será un copropietario completo con control total sobre un elemento, lo que incluye la capacidad de quitar a otros usuarios como propietarios.

**NOTA**: Mientras el nuevo propietario no confirme la propiedad, *no* aparecerá como propietario de un elemento.
En la página **Manage Owners** (Administrar propietarios), verá una entrada "pending approval" (pendiente de aprobación) en los propietarios actuales.
Es posible quitar esta invitación, del mismo modo que se pueden quitar otros propietarios.
Este proceso de invitaciones impide que los usuarios agreguen de forma errónea a otros usuarios como propietarios de sus elementos.

Tenga en cuenta que los metadatos "Authors" (Autores) son exclusivamente texto de forma libre; solo se controla "Owners" (Propietarios).


## <a name="removing-owners"></a>Quitar propietarios
Cuando un elemento tiene varios propietarios y es necesario quitar uno, el proceso es sencillo:

1. [Inicie sesión](https://powershellgallery.com/users/account/LogOn) en la Galería de PowerShell con la cuenta que es el propietario actual de un elemento.
2. Vaya a la página de un elemento a través de la pestaña Elementos, buscándola o haciendo clic en su nombre de usuario y en [**Manage My Items**](https://www.powershellgallery.com/account/Packages) (Administrar mis elementos).
3. Cuando haya iniciado sesión como propietario de un elemento, verá un vínculo "Manage Owners" (Administrar propietarios) en el lado izquierdo. Haga clic en él.
4. Haga clic en el vínculo "Remove" (Quitar) junto al propietario que se va a quitar.



## <a name="transferring-item-ownership"></a>Transferir la propiedad de un elemento
En ocasiones recibimos solicitudes de soporte técnico para transferir la propiedad de un elemento de un usuario a otro, pero la mayoría de las veces puede hacerlo usted.
La transferencia de la propiedad de un usuario a otro es simplemente una combinación de las dos funciones anteriores.

1. El propietario actual invita al usuario nuevo a convertirse en copropietario y el usuario nuevo acepta la invitación.
2. El usuario nuevo quita al usuario anterior de la lista de propietarios.

Hemos recibido esta solicitud en un par de formularios, pero el proceso funciona de la misma manera.

* La propiedad del elemento cambia de un desarrollador a otro.
* El elemento se publicó accidentalmente con una cuenta errónea.


## <a name="orphaned-items"></a>Elementos huérfanos
Por último, se ha producido otro escenario, aunque no muchas veces.
Consiste en que algunos elementos se han convertido en huérfanos y la única cuenta de propietario de elemento que existe no se puede usar para agregar nuevos propietarios.
Aquí se proporcionan algunos ejemplos de este escenario:

* La cuenta del propietario está asociada a una dirección de correo electrónico que ya no existe y el usuario ha olvidado la contraseña.
* El propietario registrado ha dejado la empresa que produce el elemento y no es posible ponerse en contacto con él para actualizar la propiedad del elemento.
* Debido a un error que solo ha afectado a algunos elementos, el elemento no tiene propietario en la Galería.

Los administradores de la Galería de PowerShell puede tener acceso al vínculo "Manage Owners" (Administrar propietarios) para cualquier elemento.
Si es usted el propietario legítimo de un elemento y no puede ponerse en contacto con el propietario actual para obtener permisos de propiedad, use el vínculo de la Galería Notificar abuso para ponerse en contacto con los administradores de la Galería de PowerShell.
Iniciaremos un proceso para comprobar que es el propietario del elemento.
Si llegamos a la conclusión de que usted debe ser el propietario del elemento, usaremos el vínculo "Manage Owners" (Administrar propietarios) para el elemento y le enviaremos una invitación para convertirse en propietario.
Solo lo haremos después de comprobar que debe ser propietario. Este proceso de comprobación varía según las circunstancias.
En ocasiones, usaremos la dirección URL del proyecto del elemento para ponernos en contacto con el propietario del proyecto, pero también podemos usar Twitter, el correo electrónico u otros medios para ponernos en contacto con el propietario del proyecto.

