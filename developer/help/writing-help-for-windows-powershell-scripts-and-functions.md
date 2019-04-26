---
title: Escribir la Ayuda de funciones y Scripts de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: 98a3f61ff4fa2367f69357173d4e8e14288ff429
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083117"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Escribir la Ayuda de funciones y Scripts de PowerShell

Funciones y scripts de PowerShell deben estar completamente documentadas cada vez que se comparten con otros usuarios.
El `Get-Help` cmdlet muestra los temas de Ayuda de la secuencia de comandos y la función en el mismo formato, tal como muestra la Ayuda de cmdlets y todos los `Get-Help` parámetros funcionan en los temas de Ayuda del script y la función.

Scripts de PowerShell pueden incluir un tema de ayuda acerca de la secuencia de comandos y temas de ayuda sobre cada funciones en la secuencia de comandos.
Las funciones que se comparten con independencia de las secuencias de comandos pueden incluir sus propios temas de ayuda.

Este documento explica el formato y la colocación correcta de los temas de ayuda, y recomienda las directrices para el contenido.

## <a name="types-of-script-and-function-help"></a>Tipos de secuencia de comandos y ayuda con la función

### <a name="comment-based-help"></a>Ayuda basada en comentarios
El tema de ayuda que describe un script o una función puede implementarse como un conjunto de comentarios dentro del script o función.
Al escribir la Ayuda basada en comentarios para una secuencia de comandos y funciones en una secuencia de comandos, paga prestar mucha atención a las reglas para colocar la Ayuda basada en comentarios.
La selección de ubicación determina si el `Get-Help` cmdlet asocia el tema de ayuda con la secuencia de comandos o una función.
Para obtener más información sobre cómo escribir temas de Ayuda basada en comentarios, vea [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Ayuda de comandos basado en XML
El tema de ayuda que describe un script o una función puede implementarse en un archivo XML que utiliza el esquema de la Ayuda de comandos.
Para asociar el script o función con el archivo XML, utilice el `ExternalHelp` comentar la palabra clave seguida de la ruta de acceso y el nombre del archivo XML.

Cuando el `ExternalHelp` comentar la palabra clave está presente, tiene prioridad sobre ayuda basada en comentarios, incluso cuando `Get-Help` no se encuentra un archivo de ayuda que coincida con el valor de la `ExternalHelp` palabra clave.

### <a name="online-help"></a>Ayuda en línea
Puede publicar sus temas de ayuda en Internet y, a continuación, dirigir `Get-Help` para abrir los temas.
Para obtener más información sobre cómo escribir temas de Ayuda basada en comentarios, vea [compatibilidad con la Ayuda en línea](../module/supporting-online-help.md).

No hay ningún método establecida para escribir en él conceptual ("About"), los temas de scripts y funciones.
Sin embargo, puede publicar temas conceptuales en la lista de Internet en los temas y sus direcciones URL en la sección vínculos relacionados de un tema de Ayuda del comando.

## <a name="content-considerations-for-script-and-function-help"></a>Consideraciones sobre el contenido de la secuencia de comandos y la función ayuda

- Si está escribiendo un tema de Ayuda breve con sólo algunas de las secciones de Ayuda de los comandos disponibles, no olvide incluir descripciones claras de los parámetros de script o la función. También debe incluir uno o dos comandos de ejemplo en la sección ejemplos, incluso si decide omitir las descripciones de ejemplo.

- En todas las descripciones, consulte el comando como un script o una función. Esta información ayuda al usuario a entender y administrar el comando.

  Por ejemplo, la descripción detallada siguiente indica que el comando New-tema es una secuencia de comandos. Esto le recuerda a los usuarios que necesitan para especificar la ruta de acceso y nombre completo al ejecutarla.

  > "La secuencia de comandos nuevo tema crea un tema conceptual en blanco para cada nombre de tema en el archivo de entrada..."

  La siguiente descripción detallada indica que `Disable-PSRemoting` es una función. Esta información es especialmente útil para los usuarios cuando la sesión incluye varios comandos con el mismo nombre, algunos de los cuales pueden quedar oculto por un comando con precedencia más alta.

  > El `Disable-PSRemoting` función deshabilita todas las configuraciones de sesión en el equipo local...

- En un tema de Ayuda de la secuencia de comandos, se explica cómo usar el script como un todo. Si está escribiendo también los temas de ayuda para las funciones en la secuencia de comandos, mencionar las funciones en el tema de Ayuda de la secuencia de comandos e incluir referencias a los temas de Ayuda de la función en la sección vínculos relacionados del tema de Ayuda del script. Por el contrario, cuando una función forma parte de una secuencia de comandos, se explica en el tema de ayuda función el papel que desempeña la función en la secuencia de comandos y cómo se puede usar por separado. A continuación, muestre el tema de Ayuda de la secuencia de comandos en la sección vínculos relacionados del tema de ayuda función.

- Al escribir los ejemplos para un tema de Ayuda de la secuencia de comandos, no olvide incluir la ruta de acceso al archivo de script en el comando de ejemplo. Esto le recuerda que los usuarios que debe especificar la ruta de acceso de forma explícita, incluso cuando el script está en el directorio actual.

- En un tema de ayuda función recordar a los usuarios que la función solo existe en la sesión actual y, para usarlo en otras sesiones, deben agregarlo o agregarlo en un perfil de PowerShell.

- `Get-Help` Muestra el tema de ayuda para un script o una función solo cuando se guardan los archivos de tema de ayuda y el archivo de script en las ubicaciones correctas. Por lo tanto, no es útil incluir instrucciones para la instalación de PowerShell, o guardar o instalar el script o una función en un tema de Ayuda de script o la función. En su lugar, incluya las instrucciones de instalación en el documento que se usan para distribuir la secuencia de comandos o la función.

## <a name="see-also"></a>Véase también

 [Escribir XML en los temas de Ayuda de Scripts y funciones](./writing-xml-based-help-topics-for-scripts-and-functions.md)

 [Escribir temas de Ayuda basados en XML para los comandos](./writing-xml-based-help-topics-for-commands.md)

 [Temas de Ayuda basada en comentarios de escritura](./writing-comment-based-help-topics.md)
