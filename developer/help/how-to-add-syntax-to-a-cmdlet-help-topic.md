---
title: Cómo agregar una sintaxis para un tema de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 2e9dbc9ff8f9507f2008cd6e114ba6fec36b10bf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083389"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Cómo agregar una sintaxis a un tema de Ayuda del cmdlet

- [Atributos de parámetro](#Parameter-Attributes)

- [Atributos de valor de parámetro](#Parameter-Value-Attributes)

- [Recopilando información sobre la sintaxis](#Gathering-Syntax-Information)

- [El diagrama de sintaxis XML de codificación](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a>Aspectos que debe conocer sobre el diagrama de sintaxis en la Ayuda de Cmdlet

Antes de empezar a codificar el XML para el diagrama de sintaxis en el archivo de Ayuda de cmdlet, lea esta sección para obtener una visión clara del tipo de datos que necesita para proporcionar, como los atributos de parámetro y cómo esos datos se muestran en el diagrama de sintaxis...

### <a name="parameter-attributes"></a>Atributos de parámetro

- Requerido

  - Si es true, el parámetro debe aparecer en todos los comandos que utilizan el conjunto de parámetros.

  - Si es false, el parámetro es opcional en todos los comandos que utilizan el conjunto de parámetros.

- Posición

  - Si el nombre, el nombre de parámetro es obligatorio.

  - Si es posicional, el nombre del parámetro es opcional. Cuando se omite, el valor del parámetro debe estar en la posición especificada en el comando. Por ejemplo, si el valor es la posición = "1", el valor del parámetro debe ser el primer o el único valor de parámetro en el comando sin nombre.

- Entrada de la canalización

  - Si es true (ByValue), puede canalizar la entrada para el parámetro. La entrada se asocia con ("enlazado a") el parámetro incluso si el nombre de propiedad y el tipo de objeto no coincide con el tipo esperado. ¿Windows PowerShell? componentes de enlace de parámetro intentan convertir la entrada al tipo correcto y se producirá un error en el comando solo cuando no se puede convertir el tipo. Puede asociar solo un parámetro en un conjunto de parámetros por valor.

  - Si es true (ByPropertyName), puede canalizar la entrada para el parámetro. Sin embargo, la entrada está asociada con el parámetro solo cuando el nombre del parámetro coincide con el nombre de una propiedad del objeto de entrada. Por ejemplo, si es el nombre del parámetro `Path`, objetos que canaliza al cmdlet están asociados con ese parámetro solo cuando el objeto tiene una propiedad con el nombre de ruta de acceso.

  - Si true (ByValue, ByPropertyName), puede canalizar la entrada para el parámetro de nombre de propiedad o valor. Puede asociar solo un parámetro en un conjunto de parámetros por valor.

  - Si es false, no se puede canalizar la entrada a este parámetro.

- Uso de comodines

  - Si es true, el texto que el usuario escribe el valor de parámetro puede incluir caracteres comodín.

  - Si es false, el texto que el usuario escribe el valor de parámetro no puede incluir caracteres comodín.

### <a name="parameter-value-attributes"></a>Atributos de valor de parámetro

- Requerido

  - Si es true, el valor especificado debe usarse cada vez que usa el parámetro de un comando.

  - Si es false, el valor del parámetro es opcional. Normalmente, un valor es opcional sólo cuando se encuentra uno de varios valores válidos para un parámetro, como en un tipo enumerado.

El atributo necesario del valor de parámetro es distinto del atributo de un parámetro necesario.

El atributo required de un parámetro indica si el parámetro (y su valor) deben incluirse al invocar el cmdlet. En cambio, el atributo necesario del valor de parámetro se usa solo cuando el parámetro se incluye en el comando. Indica si se debe usar ese valor en particular con el parámetro.

Normalmente, los valores de parámetros que son marcadores de posición son necesarios y valores de parámetros que son literales no son necesarios, porque son uno de varios valores que se pueden usar con el parámetro.

### <a name="gathering-syntax-information"></a>Recopilando información sobre la sintaxis

1. Comience con el nombre del cmdlet.

   ```
   SYNTAX
       Get-Tech
   ```

2. Enumerar todos los parámetros del cmdlet. Escriba un guión (también conocido como "dash" o "signo" (ASCII 45) delante de cada nombre de parámetro. Separe los parámetros en conjuntos de parámetros (algunos cmdlets puede tener solo un parámetro establecido). En este ejemplo, la tecnología Get cmdlet tiene dos conjuntos de parámetros.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Iniciar cada parámetro establecido con el nombre del cmdlet.

   Se enumeran el parámetro predeterminado configurado en primer lugar. El parámetro predeterminado especificado por la clase del cmdlet.

   Para cada conjunto de parámetros, enumere su único parámetro en primer lugar, a menos que existan los parámetros posicionales deben aparecer en primer lugar. En el ejemplo anterior, los parámetros de nombre e identificador son parámetros únicos para los dos conjuntos de parámetros (cada conjunto de parámetros debe tener un parámetro que es único para ese conjunto de parámetros). Esto facilita a los usuarios a identificar qué parámetro debe proporcionar para el parámetro establecido.

   Enumerar los parámetros en el orden en que aparecen en el comando. Si el orden no importa, lista de parámetros relacionados entre sí o, en primer lugar se muestran los parámetros utilizados con más frecuencia.

   No olvide si el cmdlet admite ShouldProcess, se muestran los parámetros WhatIf y Confirm.

   No se enumeran los parámetros comunes (por ejemplo, Verbose, Debug y ErrorAction) en el diagrama de sintaxis. El `Get-Help` cmdlet agrega esa información cuando se muestre el tema de ayuda.

3. Agregue los valores de parámetro. En Windows PowerShell?, se representan los valores de parámetro por su tipo. NET. Sin embargo, el nombre de tipo se puede abreviar, como "string" para System.String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Abreviar como tipos, siempre está claro, como "string" para System.String y "int" para System.Int32 su significado.

   Lista de todos los valores de enumeraciones, por ejemplo, el parámetro - type en el ejemplo anterior, que se puede establecer en "básico" o "avanzado".

   Cambiar los parámetros, como - lista en el ejemplo anterior, no tienen valores.

4. Agregue los corchetes angulares a valores de parámetros que son el marcador de posición, en comparación con los valores de parámetros que son literales.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Incluya los parámetros opcionales y sus valores en corchetes.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Incluya los nombres de parámetros opcionales (para los parámetros posicionales) incluido entre corchetes. El nombre de los parámetros posicionales, por ejemplo, el parámetro Name en el ejemplo siguiente, no es necesario que se incluirán en el comando.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Si un valor de parámetro puede contener varios valores, como una lista de nombres en el parámetro Name, agregue un par de corchetes después directamente el valor del parámetro.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Si el usuario puede elegir entre parámetros o valores de parámetro, como el parámetro de tipo, las opciones en entre llaves y sepárelos con el symbol(;) OR exclusivo.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Si el valor del parámetro debe usar un formato específico, como las comillas o paréntesis, muestran el formato en la sintaxis.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>El diagrama de sintaxis XML de codificación

El nodo de sintaxis de XML comienza inmediatamente después del nodo de la descripción, que termina con la \</maml:description > etiqueta. Para obtener información sobre la recopilación de los datos utilizados en el diagrama de sintaxis, vea [recopilar información sobre la sintaxis](#Gathering-Syntax-Information).

### <a name="adding-a-syntax-node"></a>Agregar un nodo de sintaxis

El diagrama de sintaxis que se muestra en el tema de ayuda se genera a partir de los datos en el nodo de sintaxis de XML. El nodo de sintaxis está dentro de un par de \<: sintaxis de comando > etiquetas. Con cada conjunto de parámetros del cmdlet entre un par de \<syntaxitem: comando > etiquetas. No hay ningún límite al número de \<syntaxitem: comando > etiquetas que se pueden agregar.

El ejemplo siguiente muestra un nodo de sintaxis que tiene nodos de elemento de sintaxis de dos conjuntos de parámetros.

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Agregar el nombre del Cmdlet para el parámetro de conjunto de datos

Cada conjunto de parámetros del cmdlet se especifica en un nodo de elemento de sintaxis. Cada nodo de elemento de sintaxis comienza con un par de \<maml:name > etiquetas que incluyan el nombre del cmdlet.

El ejemplo siguiente incluye un nodo de sintaxis que tiene nodos de elemento de sintaxis de dos conjuntos de parámetros.

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a>Adición de parámetros

Cada parámetro se agrega al nodo de elemento de sintaxis se especifica dentro de un par de \<: parámetro de comando > etiquetas. Necesita un par de \<: parámetro de comando > etiquetas para cada parámetro incluido en el conjunto de parámetros, a excepción de los parámetros comunes proporcionadas por Windows PowerShell?.

Los atributos de la apertura \<: parámetro de comando > etiqueta determinar cómo el parámetro aparece en el diagrama de sintaxis. Para obtener información sobre los atributos de parámetro, vea [atributos de parámetro](#Parameter-Attributes).

> [!NOTE]
> El \<: parámetro de comando > etiqueta admite un elemento secundario \<maml:description > cuyo contenido nunca se muestra. Las descripciones de parámetros se especifican en el nodo de parámetro de XML. Para evitar incoherencias entre la información en el elemento de sintaxis intervención y el nodo de parámetro, omita el (\<maml:description > o déjela en blanco.

El ejemplo siguiente incluye un nodo de elemento de sintaxis para un parámetro de conjunto con dos parámetros.

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
