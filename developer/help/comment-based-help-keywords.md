---
title: Palabras clave de Ayuda basada en comentarios | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab90ec96-77f5-42e3-9c7e-2f4156ec207f
caps.latest.revision: 6
ms.openlocfilehash: 534a6c9a43326c8a01b2181c7a799286fa4d3997
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301523"
---
# <a name="comment-based-help-keywords"></a>Palabras clave de la Ayuda basadas en comentarios

En este tema se enumera y describe las palabras clave en la Ayuda basada en comentarios.

## <a name="keywords-in-comment-based-help"></a>Palabras clave en la Ayuda basada en comentarios

Los siguientes son válidos basada en comentarios palabras clave de ayuda. Que aparecen en el orden en que normalmente aparecen en un tema de ayuda junto con su uso previsto. Estas palabras clave pueden aparecer en cualquier orden en la Ayuda basada en comentarios y no distinguen mayúsculas de minúsculas.

Tenga en cuenta que el `.ExternalHelp` palabra clave tiene prioridad sobre todas las demás palabras clave de Ayuda basada en comentarios. Cuando `.ExternalHelp` está presente, el [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet no muestra la Ayuda basada en comentarios, incluso cuando no se puede encontrar un archivo de ayuda que coincide con el valor de la palabra clave.

`.Synopsis` Una breve descripción de la función o script. Esta palabra clave puede utilizarse una sola vez en cada tema.

`.Description` Una descripción detallada de la función o script. Esta palabra clave puede utilizarse una sola vez en cada tema.

`.Parameter` *\<Nombre de parámetro >* la descripción de un parámetro. Puede incluir un `.Parameter` palabra clave para cada parámetro de la función o script.

El `.Parameter` palabras clave pueden aparecer en cualquier orden en el bloque de comentario, pero el orden en que los parámetros aparecen en la `Param` declaración de instrucción o función determina el orden en que los parámetros aparecen en el tema de ayuda. Para cambiar el orden de parámetros en el tema de ayuda, cambiar el orden de los parámetros en el `Param` declaración de función o instrucción.

También puede especificar una descripción del parámetro colocando un comentario en el `Param` instrucción inmediatamente antes del nombre de variable de parámetro. Si utiliza ambos un `Param` comentario de la instrucción y un `.Parameter` palabra clave, la descripción asociada a la `.Parameter` se utiliza la palabra clave y el `Param` se omitirá el comentario de la instrucción.

`.Example` Un comando de ejemplo que utiliza la función o script, seguido opcionalmente por salida de ejemplo y una descripción. Repita esta palabra clave para cada ejemplo.

`.Inputs` Los tipos de Microsoft .NET Framework de objetos que se pueden canalizar a la función o script. También puede incluir una descripción de los objetos de entrada.

`.Outputs` El tipo de .NET Framework de los objetos que devuelve el cmdlet. También puede incluir una descripción de los objetos devueltos.

`.Notes` Información adicional acerca de la función o script.

`.Link` El nombre de un tema relacionado. Repita esta palabra clave para cada tema relacionado. Este contenido aparece en la sección vínculos relacionados del tema de ayuda.

El `.Link` contenido de la palabra clave también puede incluir un identificador uniforme de recursos (URI) a una versión en línea del mismo tema de ayuda. Se abre la versión en línea cuando se usa el `Online` parámetros de Get-Help. El URI debe comenzar por "http" o "https".

`.Component` La tecnología o característica que usa la función o un script o que está relacionado. Este contenido aparezca cuando el comando Get-Help incluye el `Component` parámetros de Get-Help.

`.Role` El rol de usuario para el tema de ayuda. Este contenido aparezca cuando el comando Get-Help incluye el `Role` parámetros de Get-Help.

`.Functionality` El uso previsto de la función. Este contenido aparezca cuando el comando Get-Help incluye el `Functionality` parámetros de Get-Help.

`.ForwardHelpTargetName` `<Command-Name>` Redirige al tema de ayuda para el comando especificado. Puede redirigir a los usuarios a cualquier tema de ayuda, incluidos los temas de ayuda para un proveedor, cmdlet, script o función.

`.ForwardHelpCategory` `<Category>` Especifica la categoría de Ayuda del producto en ForwardHelpTargetName. Los valores válidos son Alias, Cmdlet, HelpFile, función, proveedor, generales, preguntas más frecuentes, glosario, comando de script, ExternalScript, filtro o todos. Utilice esta palabra clave para evitar conflictos cuando hay comandos con el mismo nombre.

`.RemoteHelpRunspace` `<PSSession-variable>` Especifica una sesión que contiene el tema de ayuda. Escriba una variable que contenga una PSSession. Esta palabra clave se usa por la `Export-PSSession` para encontrar los temas de ayuda para los comandos exportados.

`.ExternalHelp` `<XML Help File>` Especifica la ruta de acceso o el nombre de un archivo de ayuda basado en XML para el script o la función.

El `.ExternalHelp` palabra clave indica la [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) para obtener ayuda para la secuencia de comandos o la función en un archivo basado en XML. El **. ExternalHelp** palabra clave es necesaria cuando se usa un archivo de ayuda basado en XML para una función o script. Sin él, `Get-Help` no encontrará un archivo de ayuda para la función o script.

El `.ExternalHelp` palabra clave tiene prioridad sobre todas las demás palabras clave de Ayuda basada en comentarios. Cuando `.ExternalHelp` está presente, el [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet no muestra la Ayuda basada en comentarios, incluso cuando no se puede encontrar un archivo de ayuda que coincide con el valor de la palabra clave.

Cuando exporta un módulo de script, el valor de la función `.ExternalHelp` debe ser un nombre de archivo sin una ruta de acceso. `Get-Help` busca el archivo en un subdirectorio específico de configuración regional del directorio de módulo. No hay ningún requisito para el nombre de archivo, pero una práctica recomendada es usar el siguiente formato de nombre de archivo: `<ScriptModule>.psm1-help.xml`.

Cuando la función no está asociada a un módulo, incluya un ruta de acceso y nombre de archivo en el valor de la **. ExternalHelp** palabra clave. Si la ruta de acceso especificada en el archivo XML contiene subdirectorios específicos de la referencia cultural de interfaz de usuario, `Get-Help` busca de forma recursiva los subdirectorios de un archivo XML con el nombre del script o la función de acuerdo con el idioma de reserva estándares establecidos para Windows, igual que lo hace para todos los temas de Ayuda basados en XML.

Para obtener más información sobre el formato de archivo de ayuda basado en XML de Ayuda de cmdlet, consulte [ayuda de Cmdlet de PowerShell de Windows de escritura](./writing-help-for-windows-powershell-cmdlets.md).