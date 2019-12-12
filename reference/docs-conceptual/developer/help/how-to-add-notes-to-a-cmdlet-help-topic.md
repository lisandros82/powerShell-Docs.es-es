---
title: Cómo agregar notas a un tema de ayuda de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361274"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Cómo agregar notas a un tema de Ayuda del cmdlet

En esta sección se describe cómo agregar una sección Notas a un tema de ayuda del cmdlet de® de Windows PowerShell. La sección Notas se usa para explicar los detalles que no se ajustan a las demás secciones estructuradas, como una explicación más detallada de un parámetro. Este contenido podría incluir comentarios sobre cómo funciona el cmdlet con un proveedor específico, algunos usos únicos, pero importantes, del cmdlet o formas de evitar posibles condiciones de error.

No hay ningún límite en el número de notas que puede Agregar a una sección Notas. Por cada nota, agregue un par de etiquetas \<maml: Alert > al nodo \<maml: alertset >. El contenido de cada nota se agrega dentro de un conjunto de etiquetas \<maml: para >. Use las etiquetas en blanco \<maml: para > para el espaciado.

El siguiente código XML muestra un nodo \<maml: alertset > con dos notas. Tenga en cuenta que cada nota tiene una etiqueta opcional \<maml: title > (los títulos se pueden usar para agrupar cualquier conjunto de \<maml: Alert > Tags) y que cada nota tiene una línea en blanco que sigue el contenido para el espaciado.

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



