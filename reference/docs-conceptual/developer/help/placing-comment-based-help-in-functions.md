---
title: Colocar la ayuda basada en comentarios en las funciones | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367784"
---
# <a name="placing-comment-based-help-in-functions"></a>Colocación de la Ayuda basada en comentarios en las funciones

En este tema se explica dónde colocar la ayuda basada en comentarios de una función para que el cmdlet de `Get-Help` asocie el tema de ayuda basado en comentarios con la función correcta.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Dónde colocar la ayuda basada en comentarios para una función

- Al principio del cuerpo de la función.

- Al final del cuerpo de la función.

- Antes de la palabra clave `Function`. Cuando la función está en un módulo de script o script, no puede haber más de una línea en blanco entre la última línea de la ayuda basada en comentarios y la palabra clave `Function`. De lo contrario, `Get-Help` asocia la ayuda al script, no a la función.

## <a name="examples-of-help-placement-in-a-function"></a>Ejemplos de colocación de la ayuda en una función

 En los siguientes ejemplos se muestra cada una de las tres opciones de selección de ubicación para la ayuda basada en comentarios de una función.

### <a name="help-at-the-beginning-of-a-function-body"></a>Ayuda al principio del cuerpo de una función

 En el ejemplo siguiente se muestra basada en comentarios al principio del cuerpo de una función.

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a>Ayuda al final del cuerpo de una función

 En el ejemplo siguiente se muestra basada en comentarios al final de un cuerpo de función.

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a>Ayuda antes de la palabra clave function

 En los siguientes ejemplos se muestra el comentario basado en la línea antes de la palabra clave function.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```