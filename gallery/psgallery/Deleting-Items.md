---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Eliminar elementos
ms.openlocfilehash: f82d80a35f51227c4671bd2b15a7d1c16f0ba0a8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="deleting-items"></a>Eliminar elementos

La Galería de PowerShell no permite eliminar elementos de forma permanente, ya que eso supondría una interrupción para cualquiera que dependa de su disponibilidad.

En su lugar, la Galería de PowerShell permite "ocultar" un elemento, lo que se puede llevar a cabo en la página de administración del elemento en el sitio web.
Cuando se oculta un elemento, ya no aparece en la búsqueda ni en ninguna lista de elementos en la Galería de PowerShell o cuando se usan comandos PowerShellGet.
A pesar de eso, es posible descargarlo si se especifica su versión exacta, que es lo que permite que los scripts automatizados sigan funcionando.

Si surge una situación excepcional y cree que es necesario eliminar uno de los elementos, el equipo de la Galería de PowerShell puede encargarse de ello manualmente.
Por ejemplo, un motivo válido para eliminarlo puede ser un problema relacionado con la infracción de los derechos de autor o con contenido potencialmente dañino.
En ese caso, debe enviar una solicitud de soporte técnico a través de [Galería de PowerShell] (http://www.PowerShellGallery.com)).