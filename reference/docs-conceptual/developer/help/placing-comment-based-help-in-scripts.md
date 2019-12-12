---
title: Colocar ayuda basada en comentarios en scripts | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361184"
---
# <a name="placing-comment-based-help-in-scripts"></a>Colocación de la Ayuda basada en comentarios en los scripts

En este tema se explica dónde colocar la ayuda basada en comentarios de un script para que el cmdlet de `Get-Help` asocie el tema de ayuda basado en comentarios con scripts y no con las funciones que podrían estar en el script.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Dónde colocar la ayuda basada en comentarios de un script

- Al principio del archivo de script. La ayuda de script solo puede ir precedida del script en los comentarios y las líneas en blanco.

- Al final del archivo de script.

  Si el primer elemento del cuerpo del script (después de la ayuda) es una declaración de función, debe haber al menos dos líneas en blanco entre el final de la ayuda del script y la declaración de la función. De lo contrario, la ayuda se interpreta como ayuda para la función, no ayuda para el script.

## <a name="examples-of-help-placement-in-a-script"></a>Ejemplos de ubicación de la ayuda en un script

 En los siguientes ejemplos se muestra cada una de las opciones de selección de ubicación para la ayuda basada en comentarios de un script.

### <a name="help-at-the-beginning-of-a-script"></a>Ayuda al principio de un script

 En el ejemplo siguiente se muestra basada en comentarios al principio de un script.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Ayuda al final de un script

 En el ejemplo siguiente se muestra basada en comentarios al final de un script.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```