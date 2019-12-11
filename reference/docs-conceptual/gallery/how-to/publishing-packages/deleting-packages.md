---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Eliminación de paquetes
ms.openlocfilehash: 6bfb43b95e51d38bd606198cb8d2d9af0aa0be1e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327936"
---
# <a name="deleting-packages"></a>Eliminación de paquetes

La Galería de PowerShell no permite eliminar paquetes de forma permanente, ya que eso supondría una interrupción para cualquiera que dependa de su disponibilidad.

En su lugar, la Galería de PowerShell permite "ocultar" un paquete, lo que se puede llevar a cabo en la página de administración del paquete en el sitio web.
Cuando se oculta un paquete, ya no aparece en la búsqueda ni en ninguna lista de paquetes en la Galería de PowerShell o cuando se usan comandos PowerShellGet.
A pesar de eso, es posible descargarlo si se especifica su versión exacta, que es lo que permite que los scripts automatizados sigan funcionando.

Si surge una situación excepcional y cree que es necesario eliminar uno de los paquetes, el equipo de la Galería de PowerShell puede encargarse de ello manualmente.
Por ejemplo, un motivo válido para eliminarlo puede ser un problema relacionado con la infracción de los derechos de autor o con contenido potencialmente dañino.
En ese caso, debe enviar una solicitud de soporte técnico a través de la [Galería de PowerShell](https://www.PowerShellGallery.com).
