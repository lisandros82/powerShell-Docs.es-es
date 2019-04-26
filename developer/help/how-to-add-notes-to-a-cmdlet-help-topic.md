---
title: Cómo agregar notas a un tema de Ayuda de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083423"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Cómo agregar notas a un tema de Ayuda del cmdlet

En esta sección se describe cómo agregar una sección de notas a un tema de Ayuda de cmdlet Windows PowerShell®. La sección Notas se utiliza para explicar los detalles que no se ajustan fácilmente a las demás secciones estructuradas, como una explicación más detallada de un parámetro. Este contenido puede incluir comentarios acerca de cómo funciona el cmdlet con un proveedor concreto, algunos usos únicos, aunque importantes, del cmdlet o las formas de evitar posibles condiciones de error.

No hay ningún límite al número de notas de la que se pueden agregar a una sección de notas. Para cada nota, agregue un par de \<maml:alert > etiquetas para el \<maml:alertset > nodo. Se agrega el contenido de cada nota dentro de un conjunto de \<maml: para > etiquetas. Use espacio en blanco \<maml: para > etiquetas para el espaciado.

El siguiente XML muestra un \<maml:alertset > nodo con dos nodos. Tenga en cuenta que todas las notas tiene un elemento opcional \<maml: Title > etiqueta (títulos pueden utilizarse para agrupar cualquier conjunto de \<maml:alert > etiquetas), y que todas las notas tiene una línea en blanco que siguen al contenido para el espaciado.

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



