---
ms.date: 09/10/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Administración de claves de API
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084365"
---
# <a name="managing-api-keys"></a>Administración de claves de API

La Galería de PowerShell admite la creación de varias claves de API para admitir toda una variedad de requisitos de publicación. Una clave de API puede aplicar a uno o varios paquetes, concede privilegios específicos y tiene una fecha de expiración.

> [!IMPORTANT]
> Los usuarios que publicaron en la Galería de PowerShell antes de la introducción de claves de API con ámbito tendrán una "clave de API de acceso completo". Las claves de acceso completo no tienen las mejoras de seguridad que están integradas en las claves de API con ámbito. Las claves de acceso completo nunca expiran y se aplican a todos lo que pertenece al usuario. Si se elimina esta clave, no se puede volver a crear.

En esta imagen se muestran las opciones disponibles al crear una clave de API con ámbito.

![Crear claves de API](../../Images/PSGallery_KeyScoped.png)

En este ejemplo, hemos creado una clave de API denominada **AzureRMDataFactory**. Este valor de clave puede usarse para insertar paquetes con nombres que empiecen por 'AzureRM.DataFactory' y es válido durante 365 días. Este es un escenario típico en el que los distintos equipos de la misma organización trabajan en paquetes diferentes. Los miembros del equipo tienen una clave que les concede privilegios para el paquete específico en el que trabajan.
El valor de expiración impide el uso de claves obsoletas u olvidadas.

## <a name="using-glob-patterns"></a>Uso de patrones globales

Si trabaja en varios paquetes, puede usar patrones globales para hacer coincidir varios paquetes como un grupo. Los permisos de clave de API se aplican a todos los nuevos paquetes que coincidan con el patrón global. Por ejemplo, en el ejemplo anterior se usa el valor 'AzureRM.DataFactory*' para **Patrón global**. Puede insertar un paquete denominado 'AzureRm.DataFactoryV2.Netcore' con esta clave, puesto que el paquete coincide con el patrón global.

## <a name="create-api-keys-securely"></a>Crear claves de API de forma segura

Por motivos de seguridad, un valor de clave recién creado nunca se muestra en la pantalla y solo está disponible con el botón Copiar, como se muestra aquí.

![Obtener el nuevo valor de clave de API](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> Solo se puede copiar el valor de clave de API inmediatamente después de crearlo o actualizarlo. No se mostrará y no se podrá acceder a él de nuevo después de actualizar la página. Si pierde el valor de clave, debe usar la función Regenerar y copiar la clave después de regenerarla de nuevo.

## <a name="key-permissions-and-expiration"></a>Expiración y permisos de clave

Las claves de API con ámbito pueden asignar cualquiera de los siguientes permisos:

- Insertar nuevos paquetes
- Insertar paquetes nuevos o actualizados
- Quitar paquetes de la lista

Cada clave nueva tiene una fecha de expiración. El valor de expiración se mide en días. Los valores posibles para la expiración son:

- 1 día
- 90 días
- 180 días
- 270 días
- 365 días (valor predeterminado)

Esta configuración no puede cambiarse una vez creada la clave. No se puede crear una nueva clave que no expira nunca.

## <a name="editing-and-deleting-existing-api-keys"></a>Editar y eliminar claves de API existentes

Puede cambiar algunos valores de una clave existente. Como se indicó anteriormente, no se puede modificar el ámbito de seguridad para una clave de API existente o cambiar la expiración. En la captura de pantalla siguiente se muestran las opciones que pueden cambiarse:

![Obtener el nuevo valor de clave de API](../../Images/PSGallery_EditAPIKey.png)

Para cambiar los paquetes controlados por una clave, puede elegir paquetes individuales de la lista o cambiar el patrón global.

Al hacer clic en **Regenerar** se crea un nuevo valor de clave. Al igual que cuando creó inicialmente la clave, también deberá **Copiar** el valor de clave inmediatamente después de actualizarlo. La opción **Copiar** no está disponible una vez que se sale de esta página.

Al hacer clic en **Eliminar** se muestra un mensaje de confirmación. Una vez que se elimina una clave, no se puede usar.

## <a name="key-expiration"></a>Expiración de claves

Diez días antes de la expiración, la Galería de PowerShell envía un mensaje de advertencia al titular de la cuenta de la clave de API. Tras la expiración, la clave queda inutilizable. Se muestra un mensaje de advertencia en la parte superior de la página de administración de claves de API que muestra qué claves ya no son válidas. Puede generar un nuevo valor de clave.
