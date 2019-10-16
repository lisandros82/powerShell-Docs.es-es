---
title: Parámetros de formato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369754"
---
# <a name="format-parameters"></a>Parámetros de formato

En la tabla siguiente se enumeran los nombres recomendados y la funcionalidad de los parámetros que se usan para dar formato o generar datos.

|Parámetro|Funcionalidad|
|---|---|
|**Aplicar**<br>Tipo de datos: palabra clave|Implemente este parámetro para especificar el formato de salida del cmdlet. Por ejemplo, los valores posibles pueden ser texto o script.|
|**Binario**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para indicar que el cmdlet controla los valores binarios.|
|**Codificación**<br>Tipo de datos: palabra clave|Implemente este parámetro para especificar el tipo de codificación que se admite. Por ejemplo, los valores posibles pueden ser ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, byte y String.|
|**NewLine**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que se admitan los caracteres de nueva línea cuando se especifique el parámetro.|
|**Corto**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que se admitan nombres cortos cuando se especifique el parámetro.|
|**Ancho**<br>Tipo de datos: Int32|Implemente este parámetro para que el usuario pueda especificar el ancho del dispositivo de salida.|
|**Concluir**<br>Tipo de datos: Parámetrodemodificador|Implemente este parámetro para que se admita el ajuste de texto cuando se especifique el parámetro.|
## <a name="see-also"></a>Véase también

[Parámetros de cmdlet](./cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
