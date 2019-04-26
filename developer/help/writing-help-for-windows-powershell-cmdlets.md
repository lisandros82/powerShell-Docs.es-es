---
title: Escritura de ayuda para Cmdlets de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55908d67-7cbe-482a-a105-5a6da93c5311
caps.latest.revision: 4
ms.openlocfilehash: 8d692cf88d1d356886ef973f0989294d6b51ee6d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083168"
---
# <a name="writing-help-for-powershell-cmdlets"></a>Escribir ayuda para Cmdlets de PowerShell

Cmdlets de PowerShell puede ser útiles, pero a menos que los temas de ayuda explicar con claridad lo que hace el cmdlet y cómo usarlo, el cmdlet no puede obtener usa o, aún peor, puede frustrar a los usuarios.
El formato de archivo de Ayuda de cmdlet basado en XML mejora la coherencia, pero muy útil requiere mucho más.

Si nunca ha escrito ayuda del cmdlet, revise las siguientes directrices.
El esquema XML necesario para crear el tema de ayuda se describe en la sección siguiente.
Comience con [crear el archivo de Ayuda de Cmdlet](./how-to-create-the-cmdlet-help-file.md).
Ese tema incluye una descripción de los nodos XML de nivel superior.

## <a name="writing-guidelines-for-cmdlet-help"></a>Directrices de estilo para obtener ayuda de Cmdlet

### <a name="write-well"></a>Escriba
Nada reemplaza un tema bien escrito.
Si no es un escritor profesional, encontrar un sistema de escritura o el editor que le ayudarán a.
Otra alternativa consiste en copiar el texto de ayuda en Microsoft Word y el uso de la gramática y ortografía comprueba para mejorar su trabajo.

### <a name="write-simply"></a>Basta con escribir
Use simple palabras y frases.
Evitar los tecnicismos.
Tenga en cuenta que muchos lectores están equipados solo con un diccionario de idioma extranjero y el tema de ayuda.

### <a name="write-consistently"></a>Escribir de forma coherente
Ayuda para cmdlets relacionados deben ser similares (por ejemplo, get-x y set-x).
Use las descripciones estándares para los parámetros estándares, como **Force** y **InputObject**.
(Copiarlos de Ayuda de los cmdlets principales.) Utilice términos estándares.
Por ejemplo, "uso del parámetro", no "argumento" y use "cmdlet" no "comando" o "command-let".

### <a name="start-the-synopsis-with-a-verb"></a>Comience la sinopsis de con un verbo
El campo Sinopsis, informa al usuario que hace que el cmdlet, no es así o su funcionamiento.
Verbos creación una instrucción basado en tareas que informa a los usuarios si este cmdlet cumple sus requisitos.
Usar los verbos simple como "get", "crear" y "cambiar".
Evite "set", que puede ser poco precisas y elegantes palabras como "modificar".

### <a name="focus-on-objects"></a>Centrarse en los objetos
La mayoría "get" para mostrar los cmdlets algo, pero su función principal es obtener un objeto.
En la Ayuda, se centran en el objeto, por lo que los usuarios sepan que la visualización predeterminada es uno de ellos, y que pueden utilizar los métodos y propiedades del objeto que ha recuperado de ellas de maneras diferentes.

### <a name="write-detailed-descriptions"></a>Escribir una descripción detallada
Enumere brevemente todo lo que el cmdlet puede hacer en la descripción detallada.
Si la función principal consiste en cambiar una propiedad, pero el cmdlet puede cambiar todas las propiedades, esta lista en la descripción detallada.

### <a name="use-conventional-syntax"></a>Utilice la sintaxis convencional
Use el formato de Backus-Naur estándar que es común para Windows y la Ayuda de línea de comandos de UNIX.

### <a name="use-microsoft-net-framework-types-for-parameter-values"></a>Usar tipos de Microsoft .NET Framework para los valores de parámetro
Los marcadores de posición para los valores de parámetro (en las descripciones de sintaxis y parámetros) muestran los tipos de .NET Framework de los objetos que se va a aceptar el parámetro.
El equipo de PowerShell desarrolló esta convención para ayudar a enseñar a los usuarios sobre .NET Framework.

### <a name="write-complete-parameter-descriptions"></a>Escribir las descripciones de parámetros completo
Descripciones de parámetros deben informar a los usuarios de estas dos cosas: utiliza el parámetro realiza (su efecto) y lo que debe escribir los valores de parámetro.

### <a name="write-practical-examples"></a>Escribir ejemplos prácticos
Los ejemplos deberían mostrar cómo usar todos los parámetros, pero lo más importante es mostrar cómo usar el cmdlet en tareas reales.
Comience con un ejemplo sencillo y escribir los ejemplos de cada vez más complejos.
En el último ejemplo, muestra cómo usar el cmdlet en una canalización.

### <a name="use-the-notes-field"></a>Utilice el campo Notas
Utilice el campo Notas para explicar los conceptos que los usuarios necesitan conocer el cmdlet.
También puede usar notas para ayudar a los usuarios a evitar errores comunes.
Evite las direcciones URL cuando cambien.
En su lugar, proporcione los términos de los usuarios a buscar.

### <a name="test-your-help"></a>Probar la Ayuda
Probar la Ayuda, al igual que probar el código.
Tiene amigos y compañeros leen el contenido de ayuda y proporcionan comentarios.
También puede solicitar comentarios de los grupos de noticias.

## <a name="see-also"></a>Véase también

 [Cómo crear el archivo de Ayuda de Cmdlet](./how-to-create-the-cmdlet-help-file.md)

 [Cómo agregar el nombre de Cmdlet y Sinopsis a un tema de Ayuda de Cmdlet](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Cómo agregar la descripción detallada a un tema de Ayuda de Cmdlet](./how-to-add-a-cmdlet-description.md)

 [Cómo agregar una sintaxis para un tema de Ayuda de Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Cómo agregar parámetros a un tema de Ayuda de Cmdlet](./how-to-add-parameter-information.md)

 [Cómo agregar tipos de entrada a un tema de Ayuda de Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Cómo agregar los valores devueltos a un tema de Ayuda de Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Cómo agregar notas a un tema de Ayuda de Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Cómo agregar ejemplos para un tema de Ayuda de Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Cómo agregar vínculos relacionados a un tema de Ayuda de Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)