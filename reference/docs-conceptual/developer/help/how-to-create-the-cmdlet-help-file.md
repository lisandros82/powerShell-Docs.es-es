---
title: Cómo crear el archivo de ayuda de cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 186a8ceecea47564503dc181a76cc314033b6d3f
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996043"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Cómo crear el archivo de Ayuda del cmdlet

En esta sección se describe cómo crear un archivo XML válido que contenga contenido para los temas de ayuda de los cmdlets de Windows PowerShell. En esta sección se describe cómo asignar un nombre al archivo de ayuda, cómo agregar los encabezados XML adecuados y cómo agregar nodos que contendrán las diferentes secciones del contenido de la ayuda del cmdlet.

> [!NOTE]
> Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll-Help. XML ubicados en el directorio de instalación de Windows PowerShell. Por ejemplo, el archivo Microsoft. PowerShell. Commands. Management. dll-Help. xml contiene contenido para algunos de los cmdlets de Windows PowerShell.

### <a name="how-to-create-a-cmdlet-help-file"></a>Cómo crear un archivo de ayuda de cmdlet

1. Cree un archivo de texto y guárdelo con la codificación UTF8. El nombre de archivo debe tener el formato siguiente para que Windows PowerShell pueda detectarlo como un archivo de ayuda de cmdlet.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Agregue los siguientes encabezados XML al archivo de texto. Tenga en cuenta que el archivo se validará con el esquema del lenguaje de modelado de varios agentes (MAML). Actualmente, Windows PowerShell no proporciona ninguna herramienta para validar el archivo.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Agregue un nodo de comando al archivo de ayuda de cmdlet para cada cmdlet en el ensamblado. Cada nodo dentro del nodo comando se relaciona con las distintas secciones del tema de ayuda del cmdlet.

   En la tabla siguiente se muestra el elemento XML para cada nodo, seguido de una descripción de cada nodo.

   |Nodo|Description|
   |----------|-----------------|
   |`<details>`|Agrega contenido para las secciones nombre y Sinopsis del tema de ayuda del cmdlet. Para obtener más información, consulte [Agregar el nombre del cmdlet y la Sinopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Agrega contenido para la sección Descripción del tema de ayuda del cmdlet. Para obtener más información, consulte [Cómo agregar la descripción detallada a un tema de ayuda de un cmdlet](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Agrega contenido para la sección de sintaxis del tema de ayuda del cmdlet. Para obtener más información, consulte [el tema de ayuda agregar sintaxis a un cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Agrega contenido para la sección de parámetros del tema de ayuda del cmdlet. Para obtener más información, vea [el tema de ayuda cómo agregar parámetros a un cmdlet](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Agrega contenido para la sección de entradas del tema de ayuda del cmdlet. Para obtener más información, vea [el tema de ayuda agregar tipos de entrada a un cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Agrega contenido para la sección de resultados del tema de ayuda del cmdlet. Para obtener más información, vea [el tema de ayuda cómo agregar valores devueltos a un cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Agrega contenido a la sección Notas del tema de ayuda del cmdlet. Para obtener más información, consulte [el tema de ayuda agregar notas a un cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Agrega contenido para la sección de ejemplos del tema de ayuda del cmdlet. Para obtener más información, consulte [el tema de ayuda agregar ejemplos a un cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Agrega el contenido de la sección vínculos relacionados del tema de ayuda del cmdlet. Para obtener más información, vea [Cómo agregar vínculos relacionados a un tema de ayuda de cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Ejemplo

 Este es un ejemplo de un nodo de comando que incluye los nodos de las distintas secciones del tema de ayuda del cmdlet.

```xml
<command:command
  xmlns:maml="https://schemas.microsoft.com/maml/2004/10"
  xmlns:command="https://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="https://schemas.microsoft.com/maml/dev/2004/10">
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

## <a name="see-also"></a>Vea también

 [Cómo agregar el nombre y la Sinopsis del cmdlet](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Cómo agregar la descripción detallada a un tema de ayuda de cmdlet](./how-to-add-a-cmdlet-description.md)

 [Cómo agregar sintaxis a un tema de ayuda de cmdlet](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Cómo agregar parámetros a un tema de ayuda de cmdlet](./how-to-add-parameter-information.md)

 [Cómo agregar tipos de entrada a un tema de ayuda de cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Cómo agregar valores devueltos a un tema de ayuda de cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Cómo agregar notas a un tema de ayuda de cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Cómo agregar ejemplos a un tema de ayuda de cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Cómo agregar vínculos relacionados a un tema de ayuda de cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)