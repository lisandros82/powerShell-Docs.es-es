---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Envío de comentarios a través de medios sociales o comentarios
ms.openlocfilehash: a8e6097de4a565b504189b0b0488c45b6d78a8b6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Envío de comentarios a través de medios sociales o comentarios

La Galería de PowerShell admite dos enfoques para que los usuarios proporcionen comentarios públicos sobre un elemento:

- Use los vínculos que se encuentran en el borde de la izquierda para "compartir" un elemento en los sitios de medios sociales de Facebook, LinkedIn o Twitter.
- Use la característica Comentario para publicar comentarios sobre un elemento y para permitir que los autores estén atentos a los comentarios en los elementos que publican.

## <a name="social-media-feedback"></a>Comentarios en medios sociales

En el lado izquierdo de la página de cada elemento de la Galería de PowerShell aparecen vínculos a Facebook, LinkedIn y Twitter.
Haga clic en estos vínculos para abrir el sitio del medio social y poder compartir rápidamente un vínculo al elemento en cuestión.

Los usuarios deben iniciar sesión en el sitio que elijan para poder compartir el elemento de la Galería de PowerShell.

Se aconseja a los usuarios que hagan esto si consideran que recomendarían cierto elemento a otros usuarios.
La Galería de PowerShell comprobará las veces que se compartió el elemento en cada sitio de medio social e indicará esa información.
Como esta acción solo muestra la cantidad de veces que se compartió algún contenido, se interpretará como que a los otros usuarios les gustó el elemento en cuestión.


## <a name="comments"></a>Comentarios

La Galería de PowerShell usa el servicio LiveFyre para permitir que los usuarios comenten en los elementos.
Los usuarios que desean dejar recomendaciones o comentarios pueden usar esta característica para brindar comentarios visibles para cualquier persona que visite la página del elemento.
Los propietarios del elemento pueden seguir estos comentarios y recibir notificaciones cuando alguien publique uno.

El sistema de comentarios se basa en LiveFyre, un servicio independiente no administrado por Microsoft y que requiere un inicio de sesión único para poder usarlo.
La primera vez que decida dejar un comentario o seguir los comentarios sobre alguno de sus elementos, deberá crear una cuenta de LiveFyre.

Si creó una cuenta de LiveFyre y ya inició sesión, puede crear un comentario sobre el elemento y, luego, hacer clic en "Publicar comentario..." El comentario no será visible de inmediato.
Los administradores de la Galería de PowerShell moderan los comentarios sobre los elementos de la galería y revisan todas las publicaciones antes de que se publiquen y que los demás usuarios puedan verlas.
El propósito de moderar los comentarios es garantizar que cumplen con los lineamientos de comportamiento público coherentes con los [Términos de uso](https://www.powershellgallery.com/policies/Terms) de la Galería de PowerShell.

Se recomienda que los propietarios de los elementos sigan los comentarios que se publican en LiveFyre.
Se requiere una cuenta de LiveFyre y se recomienda usar la misma dirección de correo electrónico que se usa para publicar el elemento en LiveFyre.
Para seguir los comentarios, inicie sesión en LiveFyre y vaya a cualquier elemento del que sea propietario.
Debajo del cuadro Comentario que aparece en la parte inferior de cada elemento, verá el texto "+Seguir".
Una vez que haga clic en esta opción, LiveFyre enviará un correo electrónico a la dirección de correo electrónico registrada cada vez que se haga un comentario sobre el elemento.