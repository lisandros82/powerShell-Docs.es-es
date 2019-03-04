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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863331"
---
# <a name="how-to-add-parameter-information"></a>Cómo agregar información de parámetros

En esta sección se describe cómo agregar contenido que se muestra en la sección de parámetros del tema de Ayuda de cmdlet. La sección de parámetros del tema de ayuda enumera cada uno de los parámetros del cmdlet y proporciona una descripción detallada de cada parámetro.

El contenido de la sección de parámetros debe ser coherente con el contenido de la sección de sintaxis del tema de ayuda. Es responsabilidad del autor de ayuda para asegurarse de que el nodo de la sintaxis y los parámetros contiene elementos XML similar.

> [!NOTE]
> Para obtener una vista completa de un archivo de ayuda, abra uno de los archivos dll Help.xml ubicado en el directorio de instalación de Windows PowerShell. Por ejemplo, el archivo Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenido para varios de los cmdlets de Windows PowerShell.

### <a name="to-add-parameters"></a>Para agregar parámetros

1. Abra el archivo de Ayuda de cmdlet y busque el nodo de comando para el cmdlet que está documentando. Si va a agregar un nuevo cmdlet, que deberá crear un nuevo nodo de comando. El archivo de Ayuda contiene un nodo de comando para cada cmdlet que se va a proporcionar contenido de ayuda. Este es un ejemplo de un nodo en blanco del comando.

    ```xml
    <command:command>
    </command:command>
    ```

2. Dentro del nodo de comandos, busque el nodo de la descripción y agregar un nodo de parámetros como se muestra a continuación. Se permite un único nodo de parámetros y debe seguir inmediatamente el nodo de sintaxis.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. Dentro del nodo de parámetros, agregue un nodo de parámetro para cada parámetro del cmdlet tal como se muestra a continuación.

   En este ejemplo, se agrega un nodo de parámetro para tres parámetros.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Dado que son las mismas etiquetas XML que se usan en el nodo de sintaxis y dado que los parámetros se especifican aquí deben coincidir con los parámetros especificados por el nodo de sintaxis, puede copiar los nodos de parámetro desde el nodo de sintaxis y péguelos en el nodo de parámetros. Sin embargo, no olvide copiar solo una instancia de un nodo de parámetro, incluso si se especifica el parámetro en múltiples conjuntos de parámetros en la sintaxis.

4. Para cada parámetro de conjunto de nodos, los valores de atributo que definen las características de cada parámetro. Estos atributos incluyen lo siguiente: era necesario, uso de comodines, pipelineinput y posición.

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

5. Para cada nodo de parámetro, agregue el nombre del parámetro. Este es un ejemplo del nombre de parámetro que se agrega al nodo de parámetro.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Para cada nodo de parámetro, agregue la descripción del parámetro. Este es un ejemplo de la descripción del parámetro que se agrega al nodo de parámetro.

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

   Este es un ejemplo del tipo de .NET Framework parámetro agregado al nodo de parámetro.

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

8. Para cada nodo de parámetro, agregue el valor predeterminado del parámetro. La siguiente frase se agrega a la descripción del parámetro cuando se muestra el contenido: "DefaultValue" es el valor predeterminado.

   Este es un ejemplo del valor de parámetro predeterminado se agrega al nodo de parámetro.

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

9. Para cada parámetro que tenga varios valores, agregar un nodo de los valores posibles.

   Este es un ejemplo de la de un nodo de los valores posibles que se define dos valores posibles para el parámetro

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

Estas son algunas cosas que recordar cuando se agregan parámetros.

- No se muestran los atributos del parámetro en todas las vistas del tema de Ayuda de cmdlet. Sin embargo, se muestran en una tabla siguiendo la descripción del parámetro cuando el usuario pide para la versión completa (Get-Help \<cmdletname >-completa) o un parámetro (Get-Help \<cmdletname >-parámetro) del tema de la vista.

- La descripción del parámetro es una de las partes más importantes de un tema de Ayuda de cmdlet. La descripción debe ser breve, así como completa. Además, recuerde que, si la descripción del parámetro es demasiado larga, por ejemplo, cuando dos parámetros interactúan entre sí, puede agregar más contenido en la sección Notas del tema de Ayuda de cmdlet.

  La descripción del parámetro proporciona dos tipos de información.

- ¿Qué hace el cmdlet cuando se usa el parámetro.

- Es lo que un valor válido para el parámetro.

- Dado que los valores de parámetros se expresan como objetos de .NET Framework, los usuarios necesitan obtener más información acerca de estos valores de la que tendrían en la Ayuda de línea de comandos tradicionales. Indicar al usuario qué tipo de datos del parámetro está diseñado para aceptar e incluyen ejemplos.

El valor predeterminado del parámetro es el valor que se usa si el parámetro no se especifica en la línea de comandos. Tenga en cuenta que el valor predeterminado es opcional y no es necesario para algunos parámetros, como los parámetros necesarios. Sin embargo, debe especificar un valor predeterminado para la mayoría de los parámetros opcional.

El valor predeterminado ayuda al usuario a entender el efecto de no usar el parámetro. Describe el valor predeterminado muy concreto, como la "Current directory" o "Windows PowerShell directorio de instalación ($pshome)" para una ruta de acceso opcional. También puede escribir una frase que describe el valor predeterminado, por ejemplo, la siguiente frase usada para el `PassThru` parámetro: "Si no se especifica PassThru, el cmdlet no pasar objetos a través de la canalización."  Además, dado que se muestra el valor contrario el nombre del campo "**valor predeterminado**", no es necesario incluir el término "default value" en la entrada.

El valor predeterminado del parámetro no se muestra en todas las vistas del tema de Ayuda de cmdlet. Sin embargo, se muestra en una tabla (junto con los atributos de parámetro) siguiendo la descripción del parámetro cuando el usuario pide para la versión completa (Get-Help \<cmdletname >-full) o un parámetro (Get-Help \<cmdletname >-parámetro) vista del tema.

El siguiente XML muestra un par de `<dev:defaultValue>` etiquetas agregadas a la `<command:parameter>` nodo. Tenga en cuenta que el valor predeterminado sigue inmediatamente después del cierre `</command:parameterValue>` etiqueta (cuando se especifica el valor del parámetro) o el cierre `</maml:description>` etiqueta de la descripción del parámetro. Nombre.

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

Agregue valores para los tipos enumerados

Si el parámetro tiene varios valores o un tipo enumerado, puede usar un elemento opcional \<dev:possibleValues > nodo. Este nodo permite especificar un nombre y una descripción de varios valores.

Tenga en cuenta que las descripciones de los valores enumerados no aparecen en cualquiera de las predeterminadas vistas de ayuda mostradas por el `Get-Help` cmdlet, pero otros visores de ayuda pueden mostrar este contenido en sus vistas.

El siguiente XML muestra un `<dev:possibleValues>` nodo con dos valores especificados.

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