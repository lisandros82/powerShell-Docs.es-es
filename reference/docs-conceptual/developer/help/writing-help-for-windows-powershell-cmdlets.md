---
title: Escribir ayuda para cmdlets de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361074"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Escribir ayuda para cmdlets de PowerShell

Los cmdlets de PowerShell pueden ser útiles, pero a menos que los temas de ayuda expliquen claramente lo que hace el cmdlet y cómo usarlos, puede que el cmdlet no se use o, incluso peor, pueda frustrar a los usuarios.
El formato de archivo de ayuda de cmdlet basado en XML mejora la coherencia, pero una gran ayuda requiere mucho más.

Si nunca ha escrito la ayuda de los cmdlets, revise las siguientes directrices.
El esquema XML necesario para crear el tema de ayuda del cmdlet se describe en la sección siguiente.
Empiece por [crear el archivo de ayuda del cmdlet](./how-to-create-the-cmdlet-help-file.md).
En ese tema se incluye una descripción de los nodos XML de nivel superior.

## <a name="writing-guidelines-for-cmdlet-help"></a>Instrucciones de escritura para la ayuda de cmdlet

### <a name="write-well"></a>Escribir bien
Nada reemplaza un tema bien escrito.
Si no es un redactor profesional, busque un escritor o editor que le ayude.
Otra alternativa es copiar el texto de ayuda en Microsoft Word y usar la gramática y las comprobaciones ortográficas para mejorar el trabajo.

### <a name="write-simply"></a>Escribir simplemente
Usar palabras y frases simples.
Evite jerga.
Tenga en cuenta que muchos lectores están equipados solo con un diccionario de idioma externo y el tema de ayuda.

### <a name="write-consistently"></a>Escribir de forma coherente
La ayuda para los cmdlets relacionados debe ser similar (por ejemplo, Get-x y set-x).
Use las descripciones estándar para los parámetros estándar, como **Force** e **InputObject**.
(Cópielos de la ayuda para los cmdlets principales). Usar términos estándar.
Por ejemplo, use "parámetro", no "argument" y use "cmdlet" no "Command" o "Command-Let".

### <a name="start-the-synopsis-with-a-verb"></a>Iniciar el resumen con un verbo
El campo Sinopsis informa al usuario de lo que hace el cmdlet, no de lo que es o cómo funciona.
Los verbos crean una instrucción basada en tareas que informa a los usuarios si este cmdlet cumple sus requisitos.
Use verbos simples como "Get", "Create" y "Change".
Evite "SET", que puede ser una palabra vaga y decorativa como "modificar".

### <a name="focus-on-objects"></a>Centrarse en objetos
La mayoría de los cmdlets "Get" muestran algo, pero su función principal es obtener un objeto.
En su ayuda, céntrese en el objeto para que los usuarios sepan que la presentación predeterminada es uno de muchos y que pueden usar los métodos y las propiedades del objeto que recuperó para ellos de maneras diferentes.

### <a name="write-detailed-descriptions"></a>Escribir descripciones detalladas
Enumere brevemente todo lo que puede hacer el cmdlet en la descripción detallada.
Si la función principal es cambiar una propiedad, pero el cmdlet puede cambiar todas las propiedades, se muestra en la descripción detallada.

### <a name="use-conventional-syntax"></a>Usar sintaxis convencional
Use el formato de Backus-Naur estándar, que es común para la ayuda de la línea de comandos de Windows y UNIX.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Usar tipos de Microsoft .NET Framework para los valores de parámetro
Los marcadores de posición para los valores de parámetro (en las descripciones de sintaxis y parámetros) muestran los tipos de .NET Framework de los objetos que aceptará el parámetro.
El equipo de PowerShell desarrolló esta Convención para ayudar a enseñar a los usuarios sobre el .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Escribir descripciones completas de parámetros
Las descripciones de los parámetros deben informar a los usuarios de dos cosas: Qué hace el parámetro (su efecto) y qué deben escribir para los valores de parámetro.

### <a name="write-practical-examples"></a>Escribir ejemplos prácticos
En los ejemplos se debe mostrar cómo usar todos los parámetros, pero lo más importante es mostrar cómo usar el cmdlet en tareas del mundo real.
Comience con un ejemplo sencillo y escriba ejemplos cada vez más complejos.
En el ejemplo final, muestre cómo usar el cmdlet en una canalización.

### <a name="use-the-notes-field"></a>Usar el campo notas
Use el campo notas para explicar los conceptos que los usuarios necesitan para comprender el cmdlet.
También puede usar notas para ayudar a los usuarios a evitar errores comunes.
Evite las direcciones URL a medida que cambien.
En su lugar, proporcione a los usuarios los términos que desea buscar.

### <a name="test-your-help"></a>Probar su ayuda
Pruebe la ayuda del mismo modo que prueba el código.
Haga que sus amigos y compañeros lean el contenido de la ayuda y proporcionen Comentarios.
También puede solicitar comentarios de los grupos de noticias.

## <a name="see-also"></a>Véase también

 [Cómo crear el archivo de ayuda de cmdlet](./how-to-create-the-cmdlet-help-file.md)

 [Cómo agregar el nombre y la Sinopsis del cmdlet a un tema de ayuda de cmdlet](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Cómo agregar la descripción detallada a un tema de ayuda de cmdlet](./how-to-add-a-cmdlet-description.md)

 [Cómo agregar sintaxis a un tema de ayuda de cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Cómo agregar parámetros a un tema de ayuda de cmdlet](./how-to-add-parameter-information.md)

 [Cómo agregar tipos de entrada a un tema de ayuda de cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Cómo agregar valores devueltos a un tema de ayuda de cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Cómo agregar notas a un tema de ayuda de cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Cómo agregar ejemplos a un tema de ayuda de cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Cómo agregar vínculos relacionados a un tema de ayuda de cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)