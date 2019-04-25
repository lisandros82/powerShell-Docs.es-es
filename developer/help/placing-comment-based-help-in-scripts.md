---
title: Colocación de Ayuda basada en comentarios en las secuencias de comandos | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083236"
---
# <a name="placing-comment-based-help-in-scripts"></a>Colocación de la Ayuda basada en comentarios en los scripts

En este tema se explica dónde colocar Ayuda basada en comentarios de un script para que el `Get-Help` cmdlet asocia el tema de Ayuda basada en comentarios con secuencias de comandos y no con todas las funciones que podrían estar en la secuencia de comandos.

## <a name="where-to-place-comment-based-help-for-a-script"></a>Dónde colocar Ayuda basada en comentarios de un Script

- Al principio del archivo de script. Ayuda de la secuencia de comandos puede ir precedida de la secuencia de comandos sólo comentarios y las líneas en blanco.

- Al final del archivo de script.

  Si el primer elemento en el cuerpo de la secuencia de comandos (después de la Ayuda) es una declaración de función, debe haber al menos dos líneas en blanco entre el final de la Ayuda de la secuencia de comandos y la declaración de función. En caso contrario, la Ayuda se interpreta como ayuda para la función, no ayuda para la secuencia de comandos.

## <a name="examples-of-help-placement-in-a-script"></a>Ejemplos de una posición de la Ayuda en una secuencia de comandos

 Los ejemplos siguientes muestran cada una de las opciones de selección de ubicación para Ayuda basada en comentarios de un script.

### <a name="help-at-the-beginning-of-a-script"></a>Ayuda al principio de una secuencia de comandos

 El ejemplo siguiente se muestra basada en comentarios al principio de una secuencia de comandos.

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a>Ayuda al final de una secuencia de comandos

 El ejemplo siguiente se muestra basada en comentarios al final de una secuencia de comandos.

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```