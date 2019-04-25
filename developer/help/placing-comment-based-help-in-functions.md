---
title: Colocación de Ayuda basada en comentarios en las funciones de | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083202"
---
# <a name="placing-comment-based-help-in-functions"></a>Colocación de la Ayuda basada en comentarios en las funciones

En este tema se explica dónde colocar Ayuda basada en comentarios de una función para que el `Get-Help` cmdlet asocia el tema de Ayuda basada en comentarios de la función correcta.

## <a name="where-to-place-comment-based-help-for-a-function"></a>Dónde colocar Ayuda basada en comentarios de una función

- Al principio del cuerpo de función.

- Al final del cuerpo de función.

- Antes de la `Function` palabra clave. Cuando la función está en un script o un módulo de script, no puede haber más de una línea en blanco entre la última línea de la Ayuda basada en comentarios y `Function` palabra clave. En caso contrario, `Get-Help` asocia la ayuda con la secuencia de comandos, no con la función.

## <a name="examples-of-help-placement-in-a-function"></a>Ejemplos de una posición de la Ayuda en una función

 Los ejemplos siguientes muestran cada una de las opciones de colocación de tres para Ayuda basada en comentarios de una función.

### <a name="help-at-the-beginning-of-a-function-body"></a>Ayuda al principio de un cuerpo de función

 El ejemplo siguiente se muestra basada en comentarios al principio de un cuerpo de función.

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

### <a name="help-at-the-end-of-a-function-body"></a>Ayuda al final de un cuerpo de función

 El ejemplo siguiente se muestra basada en comentarios al final del cuerpo de una función.

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

### <a name="help-before-the-function-keyword"></a>Ayudar a antes de la palabra clave Function

 Los ejemplos siguientes se muestra basada en comentarios en la línea antes de la palabra clave function.

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```