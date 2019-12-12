---
title: Cómo agregar sintaxis a un tema de ayuda de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361214"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Cómo agregar una sintaxis a un tema de Ayuda del cmdlet

Antes de empezar a codificar el XML para el diagrama de sintaxis en el archivo de ayuda del cmdlet, lea esta sección para obtener una visión clara del tipo de datos que necesita proporcionar, como los atributos de parámetro y cómo se muestran los datos en el diagrama de sintaxis.

### <a name="parameter-attributes"></a>Atributos de parámetro

- Requerido

  - Si es true, el parámetro debe aparecer en todos los comandos que usan el conjunto de parámetros.

  - Si es false, el parámetro es opcional en todos los comandos que usan el conjunto de parámetros.

- Posición

  - Si se denomina, el nombre del parámetro es obligatorio.

  - Si es posicional, el nombre del parámetro es opcional. Cuando se omite, el valor del parámetro debe estar en la posición especificada en el comando. Por ejemplo, si el valor es position = "1", el valor del parámetro debe ser el primero o el único valor de parámetro sin nombre del comando.

- Entrada de canalización

  - Si es true (ByValue), puede canalizar la entrada al parámetro. La entrada está asociada a ("enlazada a") el parámetro aunque el nombre de la propiedad y el tipo de objeto no coincidan con el tipo esperado. ¿Windows PowerShell? los componentes de enlace de parámetros intentan convertir la entrada al tipo correcto y no se puede realizar el comando solo cuando no se puede convertir el tipo. Solo se puede asociar un parámetro de un conjunto de parámetros por valor.

  - Si es true (ByPropertyName), puede canalizar la entrada al parámetro. Sin embargo, la entrada se asocia al parámetro solo cuando el nombre del parámetro coincide con el nombre de una propiedad del objeto de entrada. Por ejemplo, si el nombre del parámetro es `Path`, los objetos que se canalizan al cmdlet se asocian a ese parámetro solo cuando el objeto tiene una propiedad denominada path.

  - Si es true (ByValue, ByPropertyName), se puede canalizar la entrada al parámetro por nombre de propiedad o por valor. Solo se puede asociar un parámetro de un conjunto de parámetros por valor.

  - Si es false, no se puede canalizar la entrada a este parámetro.

- Comodines

  - Si es true, el texto que el usuario escribe para el valor del parámetro puede incluir caracteres comodín.

  - Si es false, el texto que el usuario escribe para el valor del parámetro no puede incluir caracteres comodín.

### <a name="parameter-value-attributes"></a>Atributos de valor de parámetro

- Requerido

  - Si es true, se debe usar el valor especificado siempre que se use el parámetro en un comando.

  - Si es false, el valor del parámetro es opcional. Normalmente, un valor es opcional solo cuando es uno de varios valores válidos para un parámetro, como en un tipo enumerado.

El atributo required de un valor de parámetro es distinto del atributo required de un parámetro.

El atributo required de un parámetro indica si se debe incluir el parámetro (y su valor) al invocar el cmdlet. En cambio, el atributo required de un valor de parámetro solo se usa cuando el parámetro se incluye en el comando. Indica si se debe usar ese valor concreto con el parámetro.

Normalmente, los valores de parámetro que son marcadores de posición son obligatorios y los valores de parámetro que son literales no son necesarios, ya que se trata de uno de varios valores que se pueden usar con el parámetro.

### <a name="gathering-syntax-information"></a>Recopilar información de sintaxis

1. Comience con el nombre del cmdlet.

   ```
   SYNTAX
       Get-Tech
   ```

2. Enumera todos los parámetros del cmdlet. Escriba un guion (también conocido como "guion" o "signo menos" (ASCII 45) antes de cada nombre de parámetro. Separe los parámetros en conjuntos de parámetros (algunos cmdlets pueden tener solo un conjunto de parámetros). En este ejemplo, el cmdlet Get-Tech tiene dos conjuntos de parámetros.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Inicie cada conjunto de parámetros con el nombre del cmdlet.

   Enumere primero el conjunto de parámetros predeterminado. La clase de cmdlet especifica el parámetro predeterminado.

   Para cada conjunto de parámetros, enumere primero su parámetro único, a menos que haya parámetros posicionales que deban aparecer en primer lugar. En el ejemplo anterior, los parámetros Name e ID son únicos para los dos conjuntos de parámetros (cada conjunto de parámetros debe tener un parámetro que sea único para ese conjunto de parámetros). Esto facilita a los usuarios identificar qué parámetro deben proporcionar para el conjunto de parámetros.

   Enumere los parámetros en el orden en que deberían aparecer en el comando. Si el orden no importa, enumere los parámetros relacionados o Enumere primero los parámetros que se usan con más frecuencia.

   Asegúrese de enumerar los parámetros WhatIf y CONFIRM si el cmdlet admite ShouldProcess.

   No enumere los parámetros comunes (como verbose, Debug y ErrorAction) en el diagrama de sintaxis. El cmdlet `Get-Help` agrega esa información cuando se muestra el tema de ayuda.

3. Agregue los valores de parámetro. En Windows PowerShell, los valores de parámetro se representan mediante su tipo .NET. Sin embargo, el nombre de tipo se puede abreviar como, por ejemplo, "String" para System. String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Abrevie los tipos siempre que su significado sea claro, como "String" para System. String e "int" para System. Int32.

   Enumera todos los valores de enumeraciones, como el parámetro-type en el ejemplo anterior, que se puede establecer en "Basic" o "Advanced".

   Los parámetros de modificador, como-List en el ejemplo anterior, no tienen valores.

4. Agregue corchetes angulares a los valores de los parámetros que son marcadores de posición, en comparación con los valores de parámetro que son literales.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Incluya los parámetros opcionales y sus valores entre corchetes.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Incluya los nombres de parámetros opcionales (para los parámetros posicionales) entre corchetes. El nombre de los parámetros que son posicionales, como el parámetro name en el ejemplo siguiente, no tienen que incluirse en el comando.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Si un valor de parámetro puede contener varios valores, como una lista de nombres en el parámetro name, agregue un par de corchetes directamente después del valor del parámetro.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Si el usuario puede elegir entre parámetros o valores de parámetros, como el parámetro de tipo, incluya las opciones entre llaves y sepárelas con el símbolo OR exclusivo (;).

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Si el valor del parámetro debe usar un formato específico, como comillas o paréntesis, muestre el formato en la sintaxis.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Codificar el XML del diagrama de sintaxis

El nodo de sintaxis del XML comienza inmediatamente después del nodo de descripción, que finaliza con la etiqueta \</maml: Description >. Para obtener información sobre cómo recopilar los datos que se usan en el diagrama de sintaxis, vea [recopilar información de sintaxis](#gathering-syntax-information).

### <a name="adding-a-syntax-node"></a>Agregar un nodo de sintaxis

El diagrama de sintaxis que se muestra en el tema de ayuda del cmdlet se genera a partir de los datos del nodo sintaxis del XML. El nodo de sintaxis se incluye en un par si \<comando: sintaxis > etiquetas. Con cada conjunto de parámetros del cmdlet incluido en un par de \<comando: syntaxitem > etiquetas. No hay ningún límite en el número de \<comando: syntaxitem > etiquetas que puede Agregar.

En el ejemplo siguiente se muestra un nodo de sintaxis que tiene nodos de elemento de sintaxis para dos conjuntos de parámetros.

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Agregar el nombre del cmdlet a los datos del conjunto de parámetros

Cada conjunto de parámetros del cmdlet se especifica en un nodo de elemento de sintaxis. Cada nodo de elemento de sintaxis comienza con un par de \<maml: nombre > etiquetas que incluyen el nombre del cmdlet.

En el ejemplo siguiente se incluye un nodo de sintaxis que tiene nodos de elemento de sintaxis para dos conjuntos de parámetros.

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

### <a name="adding-parameters"></a>Agregar parámetros

Cada parámetro agregado al nodo elemento de sintaxis se especifica dentro de un par de \<comando: Parameter > Tags. Necesita un par de \<comando: Parameter > Etiquetas para cada parámetro incluido en el conjunto de parámetros, con la excepción de los parámetros comunes proporcionados por Windows PowerShell.

Los atributos de la etiqueta de apertura \<comando: parámetro > determinan cómo aparece el parámetro en el diagrama de sintaxis. Para obtener información sobre los atributos de parámetro, vea [atributos de parámetro](#parameter-attributes).

> [!NOTE]
> La etiqueta del comando \<: Parameter > admite un elemento secundario \<maml: Description > cuyo contenido nunca se muestra. Las descripciones de los parámetros se especifican en el nodo de parámetro de XML. Para evitar incoherencias entre la información del elemento de sintaxis Bodes y el nodo de parámetro, omita (\<maml: Description > o déjelo vacío.

En el ejemplo siguiente se incluye un nodo elemento de sintaxis para un conjunto de parámetros con dos parámetros.

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
