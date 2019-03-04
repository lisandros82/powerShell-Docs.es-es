---
title: Cómo crear el archivo de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858981"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Cómo crear el archivo de Ayuda del cmdlet

En esta sección se describe cómo crear un archivo XML válido que contiene el contenido de los temas de Ayuda de cmdlet de Windows PowerShell. Esta sección describe cómo asignar un nombre de archivo de ayuda, cómo agregar los encabezados adecuados de XML y cómo agregar nodos que va a contener las diferentes secciones del contenido de la Ayuda de cmdlet.

> [!NOTE]
> Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll Help.xml ubicado en el directorio de instalación de Windows PowerShell. Por ejemplo, el archivo Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenido para varios de los cmdlets de Windows PowerShell.

### <a name="how-to-create-a-cmdlet-help-file"></a>Cómo crear un archivo de Ayuda de Cmdlet

1. Cree un archivo de texto y guárdelo con la codificación UTF8. El nombre de archivo debe tener el formato siguiente para que Windows PowerShell lo detectará como un archivo de Ayuda de cmdlet.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Agregue los siguientes encabezados XML al archivo de texto. Tenga en cuenta que el archivo se validará con respecto al esquema de lenguaje de modelado Multiagente (MAML). Actualmente, Windows PowerShell no proporciona ninguna herramienta para validar el archivo.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Agregar un nodo de comandos al archivo de Ayuda de cmdlet para cada cmdlet en el ensamblado. Cada nodo dentro del nodo de comando se relaciona con las diferentes secciones del tema de Ayuda de cmdlet.

   La tabla siguiente muestra el elemento XML para cada nodo, seguido de una descripción de cada nodo.

   |Nodo|Descripción|
   |----------|-----------------|
   |`<details>`|Agrega el contenido de las secciones de nombre y una sinopsis del tema de ayuda. Para obtener más información, consulte [cómo agregar el nombre del Cmdlet y Sinopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Agrega el contenido de la sección de descripción del tema de Ayuda de cmdlet. Para obtener más información, consulte [cómo agregar la descripción detallada para un tema de Ayuda de Cmdlet](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Agrega el contenido de la sección de sintaxis del tema de Ayuda de cmdlet. Para obtener más información, consulte [cómo agregar sintaxis para un tema de Ayuda de Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Agrega el contenido de la sección de parámetros del tema de Ayuda de cmdlet. Para obtener más información, consulte [cómo agregar parámetros a un tema de Ayuda de Cmdlet](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Agrega el contenido de la sección entradas de tema de Ayuda de cmdlet. Para obtener más información, consulte [cómo agregar tipos de entrada a un tema de Ayuda de Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Agrega el contenido de la sección de salidas del tema de Ayuda de cmdlet. Para obtener más información, consulte [cómo agregar los valores devueltos para un tema de Ayuda de Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Agrega contenido a la sección Notas del tema de Ayuda de cmdlet. Para obtener más información, consulte [cómo agregar notas a un tema de Ayuda de Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Agrega el contenido de la sección de ejemplos del tema de Ayuda de cmdlet. Para obtener más información, consulte [cómo agregar ejemplos para un tema de Ayuda de Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Agrega el contenido de la sección vínculos relacionados del tema de Ayuda de cmdlet. Para obtener más información, consulte [cómo agregar vínculos relacionados a un tema de Ayuda de Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Ejemplo

 Este es un ejemplo de un nodo de comandos que incluya los nodos para las distintas secciones del tema de Ayuda de cmdlet.

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>Véase también

 [Cómo agregar el nombre del Cmdlet y Sinopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Cómo agregar la descripción detallada a un tema de Ayuda de Cmdlet](./how-to-add-a-cmdlet-description.md)

 [Cómo agregar una sintaxis para un tema de Ayuda de Cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Cómo agregar parámetros a un tema de Ayuda de Cmdlet](./how-to-add-parameter-information.md)

 [Cómo agregar tipos de entrada a un tema de Ayuda de Cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Cómo agregar los valores devueltos a un tema de Ayuda de Cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Cómo agregar notas a un tema de Ayuda de Cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Cómo agregar ejemplos para un tema de Ayuda de Cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Cómo agregar vínculos relacionados a un tema de Ayuda de Cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)