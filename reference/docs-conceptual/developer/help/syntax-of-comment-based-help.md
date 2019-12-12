---
title: Sintaxis de la ayuda basada en comentarios | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367764"
---
# <a name="syntax-of-comment-based-help"></a>Sintaxis de la Ayuda basada en comentarios

En esta sección se describe la sintaxis de la ayuda basada en Comentarios.

## <a name="syntax-diagram"></a>Diagrama de sintaxis

 La sintaxis de la ayuda basada en comentarios es la siguiente:

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Descripción de la sintaxis

 La ayuda basada en comentarios se escribe como una serie de comentarios. Puede escribir un símbolo de comentario (#) antes de cada línea de comentarios, o puede usar los símbolos "\<#" y "# >" para crear un bloque de comentario. Todas las líneas del bloque de comentario se interpretan como comentarios.

 Cada sección de la ayuda basada en comentarios se define mediante una palabra clave y cada palabra clave va precedida de un punto (.). Las palabras clave pueden aparecer en cualquier orden. Los nombres de palabra clave no distinguen mayúsculas de minúsculas.

 Un bloque de comentario debe contener al menos una palabra clave de ayuda. Algunas de las palabras clave, como ejemplo, pueden aparecer muchas veces en el mismo bloque de comentario. El contenido de la ayuda de cada palabra clave comienza en la línea después de la palabra clave y puede abarcar varias líneas.

 Todas las líneas de un tema de ayuda basado en comentarios deben ser contiguas. Si un tema de ayuda basado en comentarios sigue a un comentario que no forma parte del tema de ayuda, debe haber al menos una línea en blanco entre la última línea de comentario que no sea de ayuda y el principio de la ayuda basada en Comentarios.

 Por ejemplo, el siguiente tema de ayuda basado en comentarios contiene el. Palabra clave Description y su valor, que es una descripción de una función o un script.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```