---
title: Palabras clave de ayuda basadas en comentarios | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361364"
---
# <a name="comment-based-help-keywords"></a>Palabras clave de la Ayuda basadas en comentarios

En este tema se enumeran y describen las palabras clave de la ayuda basada en Comentarios.

## <a name="keywords-in-comment-based-help"></a>Palabras clave en la ayuda basada en comentarios

A continuación se muestran palabras clave de ayuda basadas en comentarios válidas. Aparecen en el orden en que suelen aparecer en un tema de ayuda junto con el uso previsto. Estas palabras clave pueden aparecer en cualquier orden en la ayuda basada en comentarios y no distinguen mayúsculas de minúsculas.

Tenga en cuenta que la palabra clave `.ExternalHelp` tiene prioridad sobre las demás palabras clave de ayuda basadas en Comentarios. Cuando `.ExternalHelp` está presente, el cmdlet [Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) no muestra la ayuda basada en comentarios, aunque no encuentre un archivo de ayuda que coincida con el valor de la palabra clave.

`.Synopsis` una breve descripción de la función o el script. Esta palabra clave solo se puede usar una vez en cada tema.

`.Description` una descripción detallada de la función o el script. Esta palabra clave solo se puede usar una vez en cada tema.

`.Parameter` *\<parámetro-Name >* la descripción de un parámetro. Puede incluir una palabra clave `.Parameter` para cada parámetro en la función o el script.

Las palabras clave `.Parameter` pueden aparecer en cualquier orden del bloque de comentario, pero el orden en el que aparecen los parámetros en la declaración de función o instrucción `Param` determina el orden en el que los parámetros aparecen en el tema de ayuda. Para cambiar el orden de los parámetros en el tema de ayuda, cambie el orden de los parámetros en la declaración de función o instrucción `Param`.

También puede especificar una descripción de parámetro colocando un Comentario en la instrucción `Param` inmediatamente antes del nombre de la variable de parámetro. Si utiliza un Comentario de la instrucción `Param` y una palabra clave `.Parameter`, se usa la descripción asociada a la palabra clave `.Parameter` y se omite el comentario de la instrucción `Param`.

`.Example` un comando de ejemplo que usa la función o el script, seguido opcionalmente de la salida de ejemplo y una descripción. Repita esta palabra clave para cada ejemplo.

`.Inputs` los tipos de Microsoft .NET Framework de los objetos que se pueden canalizar a la función o script. También puede incluir una descripción de los objetos de entrada.

`.Outputs` el tipo de .NET Framework de los objetos que devuelve el cmdlet. También puede incluir una descripción de los objetos devueltos.

`.Notes` información adicional sobre la función o el script.

`.Link` el nombre de un tema relacionado. Repita esta palabra clave para cada tema relacionado. Este contenido aparece en la sección vínculos relacionados del tema de ayuda.

El contenido de la palabra clave `.Link` también puede incluir un identificador uniforme de recursos (URI) en una versión en línea del mismo tema de ayuda. La versión en línea se abre cuando se usa el parámetro `Online` de Get-Help. El URI debe comenzar por "http" o "https".

`.Component` la tecnología o característica que usa la función o el script, o a los que está relacionado. Este contenido aparece cuando el comando Get-Help incluye el parámetro `Component` de Get-Help.

`.Role` el rol de usuario para el tema de ayuda. Este contenido aparece cuando el comando Get-Help incluye el parámetro `Role` de Get-Help.

`.Functionality` el uso previsto de la función. Este contenido aparece cuando el comando Get-Help incluye el parámetro `Functionality` de Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` redirige al tema de ayuda del comando especificado. Puede redirigir a los usuarios a cualquier tema de ayuda, incluidos los temas de ayuda de una función, un script, un cmdlet o un proveedor.

`.ForwardHelpCategory` `<Category>` especifica la categoría de ayuda del elemento en ForwardHelpTargetName. Los valores válidos son alias, cmdlet, ArchivoDeAyuda, función, proveedor, general, preguntas más frecuentes, Glosario, comando, ExternalScript, filtro o todo. Use esta palabra clave para evitar conflictos cuando haya comandos con el mismo nombre.

`.RemoteHelpRunspace` `<PSSession-variable>` especifica una sesión que contiene el tema de ayuda. Escriba una variable que contenga una PSSession. Esta palabra clave la usa el cmdlet `Export-PSSession` para buscar los temas de ayuda de los comandos exportados.

`.ExternalHelp` `<XML Help File>` especifica la ruta de acceso o el nombre de un archivo de ayuda basado en XML para el script o la función.

La palabra clave `.ExternalHelp` indica al cmdlet [Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) que obtenga ayuda para el script o la función en un archivo basado en XML. El **.** La palabra clave ExternalHelp es necesaria cuando se usa un archivo de ayuda basado en XML para un script o una función. Sin ella, `Get-Help` no encontrará un archivo de ayuda para la función o el script.

La palabra clave `.ExternalHelp` tiene prioridad sobre las demás palabras clave de ayuda basadas en Comentarios. Cuando `.ExternalHelp` está presente, el cmdlet [Microsoft. PowerShell. Commands. GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) no muestra la ayuda basada en comentarios, aunque no encuentre un archivo de ayuda que coincida con el valor de la palabra clave.

Cuando un módulo de script exporta la función, el valor de `.ExternalHelp` debe ser un nombre de archivo sin una ruta de acceso. `Get-Help` busca el archivo en un subdirectorio específico de la configuración regional del directorio del módulo. No hay ningún requisito para el nombre de archivo, pero se recomienda usar el formato de nombre de archivo siguiente: `<ScriptModule>.psm1-help.xml`.

Si la función no está asociada a un módulo, incluya una ruta de acceso y un nombre de archivo en el valor de **.** Palabra clave ExternalHelp. Si la ruta de acceso especificada al archivo XML contiene subdirectorios específicos de la referencia cultural de la interfaz de usuario, `Get-Help` busca en los subdirectorios de forma recursiva un archivo XML con el nombre de la función o el script de acuerdo con los estándares de reserva de lenguaje establecidos para Windows, del mismo modo que en todos los temas de ayuda basados en XML.

Para obtener más información sobre el formato de archivo de ayuda basado en XML de la ayuda del cmdlet, vea [escribir la ayuda de cmdlet de Windows PowerShell](./writing-help-for-windows-powershell-cmdlets.md).