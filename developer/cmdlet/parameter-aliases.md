---
title: Alias de parámetro | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853321"
---
# <a name="parameter-aliases"></a>Alias de parámetro

Los parámetros de cmdlet pueden tener también alias. Puede usar los alias en lugar de los nombres de parámetro cuando escriba o especifique el parámetro en un comando.

## <a name="benefits-of-using-aliases"></a>Ventajas del uso de alias

Agregar alias a parámetros proporciona las siguientes ventajas.

- Puede proporcionar un acceso directo para que el usuario no tiene que usar el nombre de parámetro completo cuando se llama el cmdlet. Por ejemplo, podría utilizar el alias "CN" en lugar del nombre de parámetro "ComputerName".

- Puede definir varios alias si desea proporcionar distintos nombres para el mismo parámetro. Es posible que desee definir varios alias si tiene que trabajar con varios grupos de usuarios que hacen referencia a los mismos datos de maneras diferentes.

- Se puede proporcionar compatibilidad hacia atrás para secuencias de comandos existentes si cambia el nombre de un parámetro.

- Al usar el Alias (atributo) junto con el atributo ValueFromPipelineByName, puede definir un parámetro que permite que el cmdlet enlazar con diferentes tipos de objeto. Por ejemplo, supongamos que tuviera dos objetos de distintos tipos y el primer objeto tenía una propiedad de sistema de escritura y el segundo objeto tenía una propiedad del editor. Si su cmdlet tenía un parámetro que tenían los alias de autor y editor y el cmdlet aceptan entrada de la canalización basada en nombres de propiedad, su cmdlet podría enlazar a los objetos mediante los dos alias de parámetro.

Para obtener más información sobre los alias que puede usarse con parámetros específicos, consulte [comunes de los nombres de parámetro](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Definir los alias de parámetro

Para definir un alias para un parámetro, declare el atributo de Alias, como se muestra en la siguiente declaración de parámetro. En este ejemplo, se definen varios alias para el mismo parámetro. (Para obtener más información, consulte[cómo declarar los parámetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).)

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>Véase también

[Nombres de parámetro comunes](./common-parameter-names.md)

[Cómo declarar los parámetros de Cmdlet](./how-to-declare-cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
