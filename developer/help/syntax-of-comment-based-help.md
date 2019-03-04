---
title: Sintaxis de la Ayuda basada en comentarios | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855551"
---
# <a name="syntax-of-comment-based-help"></a>Sintaxis de la Ayuda basada en comentarios

En esta sección se describe la sintaxis de la Ayuda basada en comentarios.

## <a name="syntax-diagram"></a>Diagrama de sintaxis

 La sintaxis de la Ayuda basada en comentarios es como sigue:

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

 Ayuda basada en comentarios se escribe como una serie de comentarios. Puede escribir un símbolo de comentario (#) antes de cada línea de comentarios, o puede usar el "\<#" y "#>" símbolos para crear un bloque de comentario. Todas las líneas dentro del bloque de comentario se interpretan como comentarios.

 Cada sección de la Ayuda basada en comentarios se define mediante una palabra clave y cada palabra clave está precedido por un punto (.). Las palabras clave pueden aparecer en cualquier orden. Los nombres de la palabra clave no distinguen mayúsculas de minúsculas.

 Un bloque de comentario debe contener al menos una palabra clave de ayuda. Algunas de las palabras clave, como ejemplo, pueden aparecer varias veces en el mismo bloque de comentario. El contenido de ayuda para cada palabra clave empieza la línea tras la palabra clave y puede abarcar varias líneas.

 Todas las líneas en un tema de Ayuda basada en comentarios deben ser contiguas. Si un tema de Ayuda basada en comentarios sigue un comentario que no forma parte del tema de ayuda, debe haber al menos una línea en blanco entre la última línea de comentario que no son de ayuda y el comienzo de la Ayuda basada en comentarios.

 Por ejemplo, contiene el siguiente tema de Ayuda basada en comentarios la. Palabra clave de descripción y su valor, que es una descripción de una función o script.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```