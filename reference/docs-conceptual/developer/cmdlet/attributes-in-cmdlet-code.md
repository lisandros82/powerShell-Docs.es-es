---
title: Atributos del código de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370004"
---
# <a name="attributes-in-cmdlet-code"></a>Atributos en el código del cmdlet

Para usar la funcionalidad común proporcionada por Windows PowerShell, las clases y las propiedades públicas definidas en el código del cmdlet se representan con atributos. Por ejemplo, la siguiente definición de clase usa el atributo cmdlet para identificar la clase de marco de Microsoft .NET en la que se implementa el cmdlet **Get-proc** . (Este cmdlet se usa como ejemplo en este documento y es similar al cmdlet `Get-Process` proporcionado por Windows PowerShell).

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Estos atributos se consideran metadatos porque su implementación es independiente de la implementación del código de cmdlet. Cuando el tiempo de ejecución de Windows PowerShell ejecuta el cmdlet, reconoce los atributos y, a continuación, realiza la acción adecuada para cada atributo.

Aunque es posible que desee implementar su propia versión de la funcionalidad proporcionada por estos atributos, un buen diseño de los cmdlets usa estas funcionalidades comunes.

Para obtener más información sobre los distintos atributos que se pueden declarar en los cmdlets, vea [tipos de atributos](./attribute-types.md).

## <a name="see-also"></a>Véase también

[Tipos de atributos](./attribute-types.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
