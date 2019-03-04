---
title: Dar formato a los parámetros | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251190"
---
# <a name="format-parameters"></a>Parámetros de formato

En la tabla siguiente enumera los nombres recomendados y la funcionalidad para los parámetros que se usan para dar formato o para generar datos.

|Parámetro|Funcionalidad|
|---|---|
|**como**<br>Tipo de datos: Palabra clave|Implemente este parámetro para especificar el formato de salida del cmdlet. Por ejemplo, los valores posibles podrían ser texto o un Script.|
|**archivo binario**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para indicar que el cmdlet controla los valores binarios.|
|**Codificación**<br>Tipo de datos: Palabra clave|Implemente este parámetro para especificar el tipo de codificación que se admite. Por ejemplo, podrían ser los posibles valores ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, bytes y cadena.|
|**NewLine**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que se admiten los caracteres de nueva línea cuando se especifica el parámetro.|
|**ShortName**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que se admiten nombres cortos cuando se especifica el parámetro.|
|**Width**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario puede especificar el ancho del dispositivo de salida.|
|**Wrap**<br>Tipo de datos: SwitchParameter|Implemente este parámetro para que se admite el ajuste de texto cuando se especifica el parámetro.|
## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
