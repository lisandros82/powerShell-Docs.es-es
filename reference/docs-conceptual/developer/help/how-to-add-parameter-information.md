---
title: Cómo agregar información de parámetros | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361234"
---
# <a name="how-to-add-parameter-information"></a>Cómo agregar información de parámetros

En esta sección se describe cómo agregar el contenido que se muestra en la sección parámetros del tema de ayuda del cmdlet. La sección de parámetros del tema de ayuda enumera cada uno de los parámetros del cmdlet y proporciona una descripción detallada de cada parámetro.

El contenido de la sección de parámetros debe ser coherente con el contenido de la sección de sintaxis del tema de ayuda. Es responsabilidad del autor de la ayuda asegurarse de que los nodos sintaxis y parámetros contienen elementos XML similares.

> [!NOTE]
> Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll-Help. XML ubicados en el directorio de instalación de Windows PowerShell. Por ejemplo, el archivo Microsoft. PowerShell. Commands. Management. dll-Help. xml contiene contenido para algunos de los cmdlets de Windows PowerShell.

### <a name="to-add-parameters"></a>Para agregar parámetros

1. Abra el archivo de ayuda del cmdlet y busque el nodo de comando del cmdlet que está documentando. Si va a agregar un nuevo cmdlet, tendrá que crear un nuevo nodo de comandos. El archivo de ayuda contendrá un nodo de comando para cada cmdlet para el que proporcione el contenido de la ayuda. A continuación se muestra un ejemplo de un nodo de comando en blanco.

    ```xml
    <command:command>
    </command:command>
    ```

2. En el nodo comando, busque el nodo Descripción y agregue un nodo parámetros, como se muestra a continuación. Solo se permite un nodo de parámetros y debe seguir inmediatamente al nodo de sintaxis.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. En el nodo parámetros, agregue un nodo de parámetro para cada parámetro del cmdlet, como se muestra a continuación.

   En este ejemplo, se agrega un nodo de parámetro para tres parámetros.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Dado que se trata de las mismas etiquetas XML que se usan en el nodo sintaxis, y dado que los parámetros especificados aquí deben coincidir con los parámetros especificados por el nodo sintaxis, puede copiar los nodos de parámetros del nodo sintaxis y pegarlos en el nodo parámetros. Sin embargo, asegúrese de copiar solo una instancia de un nodo de parámetro, incluso si el parámetro se especifica en varios conjuntos de parámetros en la sintaxis.

4. Para cada nodo de parámetro, establezca los valores de atributo que definen las características de cada parámetro. Entre estos atributos se incluyen los siguientes: required, comodines, pipelineinput y position.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. Para cada nodo de parámetro, agregue el nombre del parámetro. Este es un ejemplo del nombre de parámetro agregado al nodo de parámetro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Para cada nodo de parámetro, agregue la descripción del parámetro. Este es un ejemplo de la descripción del parámetro que se ha agregado al nodo parámetro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. Para cada nodo de parámetro, agregue el tipo de .NET Framework del parámetro. El tipo de parámetro se muestra junto con el nombre del parámetro.

   Este es un ejemplo del parámetro .NET Framework tipo agregado al nodo de parámetro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. Para cada nodo de parámetro, agregue el valor predeterminado del parámetro. Cuando se muestra el contenido, se agrega la frase siguiente a la descripción del parámetro: "DefaultValue" es el valor predeterminado.

   Este es un ejemplo del valor predeterminado del parámetro que se agrega al nodo parámetro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. Para cada parámetro que tenga varios valores, agregue un nodo valores posibles.

   Este es un ejemplo del nodo valores posibles que define dos valores posibles para el parámetro.

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

Estos son algunos aspectos que debe recordar al agregar parámetros.

- Los atributos del parámetro no se muestran en todas las vistas del tema de ayuda del cmdlet. Sin embargo, se muestran en una tabla que sigue la descripción del parámetro cuando el usuario solicita la vista completa (Get-Help \<cmdletname >-Full) o el parámetro (Get-Help \<cmdletname >-Parameter) del tema.

- La descripción del parámetro es una de las partes más importantes de un tema de ayuda de cmdlet. La descripción debe ser breve, así como exhaustiva. Además, recuerde que si la descripción del parámetro es demasiado larga, como cuando dos parámetros interactúan entre sí, puede agregar más contenido en la sección Notas del tema de ayuda del cmdlet.

  La descripción del parámetro proporciona dos tipos de información.

- Lo que hace el cmdlet cuando se usa el parámetro.

- Qué es un valor válido para el parámetro.

- Dado que los valores de los parámetros se expresan como .NET Framework objetos, los usuarios necesitan más información sobre estos valores que en una ayuda de línea de comandos tradicional. Indique al usuario el tipo de datos que el parámetro está diseñado para aceptar e incluya ejemplos.

El valor predeterminado del parámetro es el valor que se usa si el parámetro no se especifica en la línea de comandos. Tenga en cuenta que el valor predeterminado es opcional y no es necesario para algunos parámetros, como los parámetros necesarios. Sin embargo, debe especificar un valor predeterminado para la mayoría de los parámetros opcionales.

El valor predeterminado ayuda al usuario a entender el efecto de no usar el parámetro. Describa el valor predeterminado en concreto, como el "directorio actual" o el "directorio de instalación de Windows PowerShell ($pshome)" para una ruta de acceso opcional. También puede escribir una frase que describa el valor predeterminado, como la siguiente oración utilizada para el parámetro `PassThru`: "si no se especifica PassThru, el cmdlet no pasa los objetos por la canalización".  Además, dado que el valor se muestra de forma opuesta al nombre de campo "**default Value**", no es necesario incluir el término "default Value" en la entrada.

El valor predeterminado del parámetro no se muestra en todas las vistas del tema de ayuda del cmdlet. Sin embargo, se muestra en una tabla (junto con los atributos de parámetro) a continuación de la descripción del parámetro cuando el usuario solicita la vista completa (Get-Help \<cmdletname >-Full) o el parámetro (Get-Help \<cmdletname >-Parameter) del tema.

El siguiente código XML muestra un par de etiquetas `<dev:defaultValue>` agregadas al nodo `<command:parameter>`. Observe que el valor predeterminado sigue inmediatamente después de la etiqueta de cierre `</command:parameterValue>` (cuando se especifica el valor del parámetro) o la etiqueta de cierre `</maml:description>` de la descripción del parámetro. Name.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

Agregar valores para tipos enumerados

Si el parámetro tiene varios valores o valores de un tipo enumerado, puede utilizar un nodo opcional \<dev: possibleValues >. Este nodo le permite especificar un nombre y una descripción para varios valores.

Tenga en cuenta que las descripciones de los valores enumerados no aparecen en ninguna de las vistas de ayuda predeterminadas que muestra el cmdlet `Get-Help`, pero otros visores de ayuda pueden mostrar este contenido en sus vistas.

El siguiente código XML muestra un nodo `<dev:possibleValues>` con dos valores especificados.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```