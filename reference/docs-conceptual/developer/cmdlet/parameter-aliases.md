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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369594"
---
# <a name="parameter-aliases"></a>Alias de parámetro

Los parámetros de cmdlet pueden tener también alias. Puede usar los alias en lugar de los nombres de parámetro al escribir o especificar el parámetro en un comando.

## <a name="benefits-of-using-aliases"></a>Ventajas del uso de alias

Agregar alias a parámetros proporciona las siguientes ventajas.

- Puede proporcionar un acceso directo para que el usuario no tenga que usar el nombre de parámetro completo cuando se llame al cmdlet. Por ejemplo, puede usar el alias "CN" en lugar del nombre de parámetro "ComputerName".

- Puede definir varios alias si desea proporcionar nombres diferentes para el mismo parámetro. Es posible que desee definir varios alias si tiene que trabajar con varios grupos de usuarios que hacen referencia a los mismos datos de maneras diferentes.

- Puede proporcionar compatibilidad con versiones anteriores de los scripts existentes si cambia el nombre de un parámetro.

- Mediante el atributo alias junto con el atributo ValueFromPipelineByName, puede definir un parámetro que permita que el cmdlet se enlace a tipos de objeto diferentes. Por ejemplo, suponga que tiene dos objetos de tipos diferentes y el primer objeto tenía una propiedad Writer y el segundo objeto tenía una propiedad editor. Si el cmdlet tenía un parámetro que tenía los alias del escritor y del editor y el cmdlet aceptó la entrada de canalización en función de los nombres de propiedad, el cmdlet podría enlazarse a ambos objetos mediante los dos alias de parámetro.

Para obtener más información acerca de los alias que se pueden usar con parámetros específicos, vea [nombres de parámetros comunes](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Definir los alias de parámetro

Para definir un alias para un parámetro, declare el atributo alias, tal como se muestra en la siguiente declaración de parámetro. En este ejemplo, se definen varios alias para el mismo parámetro. (Para obtener más información, vea[cómo declarar parámetros de cmdlet](./how-to-declare-cmdlet-parameters.md)).

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

[Nombres de parámetros comunes](./common-parameter-names.md)

[Cómo declarar parámetros de cmdlet](./how-to-declare-cmdlet-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
