---
title: Cómo agregar ejemplos para un tema de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 5e8d1df6b423bfd2cd6b0a64a8875dea9c3fb4ef
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083474"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Cómo agregar ejemplos a un tema de Ayuda del cmdlet

- [Cosas que saber acerca de los ejemplos en la Ayuda de Cmdlet](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [Las vistas que se muestran ejemplos de ayuda](#Help-Views-that-Display-Examples)

- [Agregar un nodo de ejemplos](#Adding-an-Examples-Node)

- [Agregar delante los caracteres adicionales.](#Adding-Preceding-Characters)

- [Agrega el comando](#Adding-the-Command)

- [Agregar una descripción](#Adding-a-Description)

- [Adición de salida de ejemplo](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Cosas que saber acerca de los ejemplos en la Ayuda de Cmdlet

- Enumera todos los nombres de parámetro en el comando, incluso cuando los nombres de parámetro son opcionales. Esto ayuda al usuario a interpretar el comando fácilmente.

- Evite los alias y nombres de parámetros parciales, incluso aunque funcionan en Windows PowerShell®.

- En la descripción del ejemplo, explique el racional para la construcción del comando. Explique por qué eligió determinados parámetros y valores, y cómo usar variables.

- Si el comando usa las expresiones, explicaremos con detalle.

- Si el comando usa las propiedades y métodos de objetos, especialmente las propiedades que no aparecen en la pantalla predeterminada, use el ejemplo como una oportunidad de indicar al usuario sobre el objeto.

## <a name="help-views-that-display-examples"></a>Las vistas que se muestran ejemplos de ayuda

Ejemplos solo aparecen en las vistas completa y detallada de la Ayuda del cmdlet.

## <a name="adding-an-examples-node"></a>Agregar un nodo de ejemplos

El siguiente XML muestra cómo agregar un nodo de ejemplos que contiene un único nodo de ejemplo. Agregar nodos de ejemplo adicional para cada ejemplos que van a incluir en el tema.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Agregar un título de ejemplo

El siguiente XML muestra cómo agregar un título para el ejemplo. El título se usa para establecer el ejemplo además de otros ejemplos. Windows PowerShell® utiliza un encabezado estándar que incluye una serie secuencial de ejemplo.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Agregar delante los caracteres adicionales.

El siguiente XML muestra cómo agregar caracteres, como el símbolo del sistema de Windows PowerShell, que se muestran inmediatamente antes del comando de ejemplo (sin espacios intermedios). Windows PowerShell® usa el símbolo del sistema de Windows PowerShell: C:\PS>.

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

## <a name="adding-the-command"></a>Agrega el comando

El siguiente XML muestra cómo agregar el comando real del ejemplo. Al agregar el comando, escriba el nombre completo (no utilice alias) de los cmdlets y parámetros. Además, usar caracteres en minúsculas siempre que sea posible.

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

El siguiente XML muestra cómo agregar una descripción para el ejemplo. Windows PowerShell® utiliza un conjunto único de \<maml: para > etiquetas de la descripción, aunque varios \<maml: para > etiquetas se pueden usar.

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

## <a name="adding-example-output"></a>Adición de salida de ejemplo

El siguiente XML muestra cómo agregar la salida del comando. La información de los resultados del comando es opcional, pero en algunos casos es útil mostrar el efecto del uso de parámetros específicos. Windows PowerShell® usa dos conjuntos de espacio en blanco \<maml: para > etiquetas para separar la salida del comando del comando.

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