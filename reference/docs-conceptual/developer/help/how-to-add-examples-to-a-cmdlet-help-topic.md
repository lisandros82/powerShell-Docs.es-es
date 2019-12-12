---
title: Cómo agregar ejemplos a un tema de ayuda de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368114"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Cómo agregar ejemplos a un tema de Ayuda del cmdlet

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Aspectos que se deben conocer sobre los ejemplos de la ayuda de cmdlet

- Enumera todos los nombres de parámetro del comando, incluso cuando los nombres de parámetro son opcionales. Esto ayuda al usuario a interpretar el comando fácilmente.

- Evite los alias y los nombres de parámetros parciales, aunque funcionan en Windows PowerShell®.

- En la descripción del ejemplo, explique el razonamiento de la construcción del comando. Explique por qué se eligen determinados parámetros y valores, y cómo se usan las variables.

- Si el comando usa expresiones, explíqueles en detalle.

- Si el comando usa las propiedades y los métodos de los objetos, especialmente las propiedades que no aparecen en la pantalla predeterminada, use el ejemplo como una oportunidad para informar al usuario sobre el objeto.

## <a name="help-views-that-display-examples"></a>Vistas de ayuda que muestran ejemplos

Los ejemplos solo aparecen en las vistas detalladas y completas de la ayuda de los cmdlets.

## <a name="adding-an-examples-node"></a>Agregar un nodo examples

El siguiente XML muestra cómo agregar un nodo examples que contiene un solo nodo de ejemplo. Agregue nodos de ejemplo adicionales para cada uno de los ejemplos que desee incluir en el tema.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Agregar un título de ejemplo

En el código XML siguiente se muestra cómo agregar un título para el ejemplo. El título se usa para establecer el ejemplo, además de otros ejemplos. Windows PowerShell® usa un encabezado estándar que incluye un número de ejemplo secuencial.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Agregar caracteres anteriores

El siguiente XML muestra cómo agregar caracteres, como el símbolo del sistema de Windows PowerShell, que se muestran inmediatamente antes del comando de ejemplo (sin espacios intermedios). Windows PowerShell® usa el símbolo del sistema de Windows PowerShell: C:\PS >.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a>Agregar el comando

El siguiente XML muestra cómo agregar el comando real del ejemplo. Al agregar el comando, escriba el nombre completo (no usar alias) de los cmdlets y parámetros. Además, use caracteres en minúsculas siempre que sea posible.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a>Agregar una descripción

El siguiente XML muestra cómo agregar una descripción para el ejemplo. Windows PowerShell® usa un único conjunto de \<maml: para > Etiquetas para la descripción, aunque se puedan usar \<varias etiquetas maml: para >.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a>Agregar salida de ejemplo

En el código XML siguiente se muestra cómo agregar el resultado del comando. La información de los resultados del comando es opcional, pero en algunos casos resulta útil mostrar el efecto de usar parámetros específicos. Windows PowerShell® usa dos conjuntos de etiquetas \<maml: para > para separar los resultados del comando del comando.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```