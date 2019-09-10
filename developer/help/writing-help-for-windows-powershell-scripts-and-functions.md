---
title: Escribir ayuda para scripts y funciones de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 859a6e22-75b1-43d4-ba62-62c107803b37
caps.latest.revision: 7
ms.openlocfilehash: af989fb2eeba6b68f2e3e6506f3f60d5be6f7d8a
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848105"
---
# <a name="writing-help-for-powershell-scripts-and-functions"></a>Escribir ayuda para scripts y funciones de PowerShell

Los scripts y las funciones de PowerShell deben estar completamente documentados siempre que se compartan con otros usuarios.
El `Get-Help` cmdlet muestra los temas de ayuda de la función y el script en el mismo formato que muestra la ayuda para los cmdlets `Get-Help` , y todos los parámetros funcionan en los temas de ayuda de scripts y funciones.

Los scripts de PowerShell pueden incluir un tema de ayuda sobre el script y los temas de ayuda acerca de cada una de las funciones del script.
Las funciones que se comparten con independencia de los scripts pueden incluir sus propios temas de ayuda.

En este documento se explica el formato y la ubicación correcta de los temas de ayuda, y se sugieren instrucciones para el contenido.

## <a name="types-of-script-and-function-help"></a>Tipos de ayuda de scripts y funciones

### <a name="comment-based-help"></a>Ayuda basada en comentarios
El tema de ayuda que describe un script o una función se puede implementar como un conjunto de comentarios dentro del script o la función.
Al escribir ayuda basada en comentarios para un script y para las funciones de un script, preste especial atención a las reglas para colocar la ayuda basada en Comentarios.
La selección de ubicación determina `Get-Help` si el cmdlet asocia el tema de ayuda con el script o una función.
Para obtener más información sobre cómo escribir temas de ayuda basados en comentarios, vea [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

### <a name="xml-based-command-help"></a>Ayuda de comandos basada en XML
El tema de ayuda que describe un script o una función se puede implementar en un archivo XML que utiliza el esquema de ayuda del comando.
Para asociar el script o la función al archivo XML, use `ExternalHelp` la palabra clave comment seguida de la ruta de acceso y el nombre del archivo XML.

Cuando la `ExternalHelp` palabra clave comment está presente, tiene prioridad sobre la ayuda basada en comentarios, incluso `Get-Help` cuando no encuentra un archivo de ayuda que coincida con el `ExternalHelp` valor de la palabra clave.

### <a name="online-help"></a>Ayuda en línea
Puede publicar los temas de ayuda en Internet y, a continuación `Get-Help` , dirigir para abrir los temas.
Para obtener más información acerca de cómo escribir temas de ayuda basados en comentarios, consulte [Supporting online help](../module/supporting-online-help.md).

No hay ningún método establecido para escribir temas conceptuales ("About") para scripts y funciones.
Sin embargo, puede publicar temas conceptuales en la lista de Internet los temas y sus direcciones URL en la sección vínculos relacionados de un tema de ayuda del comando.

## <a name="content-considerations-for-script-and-function-help"></a>Consideraciones de contenido para la ayuda de scripts y funciones

- Si está escribiendo un tema de ayuda muy breve con solo algunas de las secciones de ayuda de comandos disponibles, asegúrese de incluir descripciones claras de los parámetros de la función o el script. Incluya también uno o dos comandos de ejemplo en la sección ejemplos, aunque decida omitir las descripciones de ejemplo.

- En todas las descripciones, consulte el comando como un script o una función. Esta información ayuda al usuario a entender y administrar el comando.

  Por ejemplo, la descripción detallada siguiente indica que el comando New-topic es un script. Esto recuerda a los usuarios que necesitan especificar la ruta de acceso y el nombre completo cuando lo ejecutan.

  > "El script New-topic crea un tema conceptual en blanco para cada nombre de tema del archivo de entrada..."

  La descripción detallada siguiente indica que `Disable-PSRemoting` es una función. Esta información es especialmente útil para los usuarios cuando la sesión incluye varios comandos con el mismo nombre, algunos de los cuales podrían estar ocultos por un comando con mayor precedencia.

  > La `Disable-PSRemoting` función deshabilita todas las configuraciones de sesión en el equipo local...

- En un tema de ayuda de script, explique cómo usar el script en su conjunto. Si también está escribiendo temas de ayuda para las funciones del script, mencione las funciones del tema de ayuda del script e incluya referencias a los temas de ayuda de la función en la sección vínculos relacionados del tema de ayuda del script. Por el contrario, cuando una función forma parte de un script, explique en el tema de ayuda función el rol que desempeña la función en el script y cómo podría usarse de forma independiente. A continuación, muestre el tema de ayuda de script en la sección vínculos relacionados del tema de ayuda de la función.

- Al escribir ejemplos para un tema de ayuda de script, asegúrese de incluir la ruta de acceso al archivo de script en el comando de ejemplo. Esto recuerda a los usuarios que deben especificar la ruta de acceso explícitamente, incluso cuando el script está en el directorio actual.

- En el tema de ayuda de una función, recuerde a los usuarios que la función solo existe en la sesión actual y, para usarla en otras sesiones, necesitan agregarla o agregarla a un perfil de PowerShell.

- `Get-Help`muestra el tema de ayuda de un script o función solo cuando el archivo de script y los archivos de tema de ayuda se guardan en las ubicaciones correctas. Por lo tanto, no es útil incluir instrucciones para instalar PowerShell o guardar o instalar el script o la función en un tema de ayuda de script o función. En su lugar, incluya las instrucciones de instalación del documento que use para distribuir el script o la función.

## <a name="see-also"></a>Véase también

[Escribir temas de ayuda basados en comentarios](./writing-comment-based-help-topics.md)
