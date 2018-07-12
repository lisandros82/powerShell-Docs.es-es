---
ms.date: 03/27/2018
contributor: JKeithB
keywords: gallery,powershell,psgallery,GDPR
title: Cumplimiento del RGPD en la Galería de PowerShell
ms.openlocfilehash: 14b82fa07df52f02f0d7577cb0eef70faa4285a2
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893253"
---
# <a name="powershell-gallery-gdpr-compliance"></a>Cumplimiento del RGPD en la Galería de PowerShell

## <a name="overview"></a>Introducción

En mayo de 2018 entra en vigor una ley europea de privacidad, el Reglamento general de protección de datos (RGPD).
El RGPD establece nuevas normas para empresas, organismos gubernamentales, organizaciones sin ánimo de lucro y otras organizaciones que ofrecen bienes y servicios a los ciudadanos de la Unión Europea (UE) o bien que recopilan y analizan datos vinculados a residentes de la UE.
El RGPD se aplica con independencia de la ubicación.

> [!NOTE]
> Este artículo contiene los pasos necesarios para eliminar datos personales de la Galería de PowerShell y se puede usar para cumplir las obligaciones legales relativas al RGPD. Si quiere obtener información general sobre este reglamento, vea la [sección del RGPD del Portal de confianza de servicios](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## <a name="personally-identifiable-data"></a>Datos de identificación personal

La Galería de PowerShell almacena la información siguiente que pueden proporcionar los usuarios y que podría contener información personal:

- Cuenta de la Galería de PowerShell
- Elementos publicados en la Galería de PowerShell
- Comunicaciones por correo electrónico con el equipo de la Galería de PowerShell

La mayoría de los usuarios no crea una cuenta de la Galería de PowerShell.
Dicha cuenta no es necesaria a menos que tenga intención de publicar un elemento o usar la característica "Ponerse en contacto con el propietario" de la Galería de PowerShell.
Aparte de las comunicaciones por correo electrónico iniciadas por un usuario, la Galería de PowerShell no almacena datos de identificación personal de los usuarios que no han creado ninguna cuenta.

Los usuarios que creen una Galería de PowerShell podrán publicar elementos en la Galería de PowerShell.
Se espera que dichos elementos sean código de PowerShell, pero pueden contener otros datos que contengan información personal.
En la información que se indica a continuación se indica cómo obtener todos los elementos publicados en la Galería de PowerShell.

## <a name="dsr-export-of-powershell-gallery-data"></a>Exportación de DSR de los datos de la Galería de PowerShell

En las secciones siguientes se describe de qué forma la Galería de PowerShell admite las solicitudes de interesados (DSR) y se explica cómo exportar la información almacenada en la Galería de PowerShell y solicitar su eliminación.

### <a name="email"></a>Correo electrónico

Entre las comunicaciones por correo electrónico se incluye todo lo siguiente:

- Correos electrónicos enviados a los propietarios de elementos de la Galería de PowerShell, si en los exámenes de análisis de código se ha detectado un problema con algún elemento que estos han publicado en la Galería de PowerShell.
- Correos electrónicos enviados por cualquier persona al equipo de la Galería de PowerShell mediante la dirección de correo electrónico de la página "Póngase en contacto con nosotros" [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com).
- Los usuarios registrados que usen la característica "Ponerse en contacto con el propietario" de la Galería de PowerShell para enviar correos electrónicos al propietario de un elemento de la Galería de PowerShell.

Para los correos electrónicos enviados a la Galería de PowerShell o mediante esta se establece una directiva de retención de 90 días para llevar a cabo las posibles investigaciones de seguridad en caso de que se detecte código malicioso en la Galería de PowerShell.
Los correos electrónicos se eliminan de acuerdo con la directiva mencionada al cabo de 90 días.

Dispone de un término de 90 días para solicitar copias de los correos electrónicos enviados a su dirección de correo electrónico o desde esta y a la Galería de PowerShell o desde esta.
Para solicitar estas comunicaciones, envíe un correo electrónico a [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com) con el asunto "DSR Request for emails relating to this account" (Solicitud de DSR para los correos electrónicos relativos a esta cuenta).
En el cuerpo del mensaje, indique qué información solicita (por ejemplo, recibir todos los correos electrónicos enviados o recibidos en esta dirección de correo electrónico). Todos los correos electrónicos relacionados con su dirección de correo electrónico en los 90 días posteriores a la solicitud se enviarán en un término de 7 días laborables.

### <a name="powershell-gallery-account-information"></a>Información sobre la cuenta de la Galería de PowerShell

Si ha creado una cuenta de la Galería de PowerShell, siga los pasos que se indican a continuación para encontrar toda la información personal almacenada en ella:

1. Inicie sesión en la Galería de PowerShell y haga clic en su nombre de usuario.
2. La siguiente página que se mostrará será la página Cuenta, en la que constará la dirección de correo electrónico usada para la cuenta de la Galería de PowerShell.

Si ha creado más de una cuenta en la Galería de PowerShell, tendrá que repetir estos pasos para cada cuenta.

### <a name="items-in-the-powershell-gallery"></a>Elementos de la Galería de PowerShell

Para facilitar la exportación de elementos publicados en la Galería de PowerShell, hemos publicado el script "GetPSGalleryItemsForAuthor" en la Galería de PowerShell.
Este script exporta una copia de la versión de cada elemento colocado en la Galería de PowerShell a partir de la información sobre el autor almacenada en el elemento.

> [!NOTE]
> El autor se almacena en el manifiesto de un elemento al publicarlo.
> No hay ninguna garantía de que el autor tenga la misma identidad que la de la cuenta que se usa en la Galería de PowerShell.
> Si usa otro valor en el campo Autor, debe proporcionar dicho valor al utilizar este script.

Puede descargar el script usando este comando de PowerShell:

```powershell
Save-Script Get-repository psgallery
```

A continuación podrá ejecutar el script directamente mediante los siguientes comandos de PowerShell:

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

Se le pedirá que proporcione el autor y una carpeta en su sistema donde se deben guardar los elementos.

## <a name="deleting-personal-data-from-the-powershell-gallery"></a>Eliminación de los datos personales de la Galería de PowerShell

Para eliminar la cuenta de la Galería de PowerShell o cualquier elemento suyo de la Galería de PowerShell, envíe un correo electrónico a cgadmin@microsoft.com con el asunto "GDPR Request for items relating to this account" (Solicitud relativa al RGPD para elementos relacionados con esta cuenta).
En el cuerpo del mensaje, indique qué información quiere que se elimine. Por ejemplo:

- Eliminar la versión x.y.z del elemento "X".
- Eliminar todas las versiones del elemento "X".
- Eliminar mi cuenta de la Galería de PowerShell

Los administradores de la Galería de PowerShell responderán en un término de 7 días laborables.
Los elementos especificados se eliminarán durante los 30 días posteriores al envío de la solicitud.