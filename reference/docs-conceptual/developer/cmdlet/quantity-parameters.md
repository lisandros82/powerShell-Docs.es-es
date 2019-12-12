---
title: Parámetros de cantidad | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369564"
---
# <a name="quantity-parameters"></a>Parámetros de cantidad

En la tabla siguiente se enumeran los nombres recomendados y la funcionalidad de los parámetros quantity.

|Parámetro|Funcionalidad|
|---|---|
|**Todos**<br>Tipo de datos: booleano|Implemente este parámetro para que `true` indica que todos los recursos se deben actuar en lugar de un subconjunto de recursos predeterminado. Implemente este parámetro para que `false` indique un subconjunto de los recursos.|
|**Asignación**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario pueda especificar el número de elementos que se van a asignar.|
|**BlockCount**<br>Tipo de datos: Int64|Implemente este parámetro para que el usuario pueda especificar el recuento de bloques.|
|**Count**<br>Tipo de datos: Int64|Implemente este parámetro para que el usuario pueda especificar el recuento.|
|**Ámbito**<br>Tipo de datos: palabra clave|Implemente este parámetro para que el usuario pueda especificar el ámbito en el que se va a operar.|

## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
