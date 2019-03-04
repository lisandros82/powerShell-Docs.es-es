---
title: Atributos en el código del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853791"
---
# <a name="attributes-in-cmdlet-code"></a>Atributos en el código del cmdlet

Para usar la funcionalidad común proporcionada por Windows PowerShell, las clases y propiedades públicas definidas en el código del cmdlet se decoran con atributos. Por ejemplo, la definición de clase siguiente utiliza el atributo de Cmdlet para identificar la clase Microsoft .NET Framework en el que el **Get-Proc** cmdlet se implementa. (Este cmdlet se usa como un ejemplo de este documento y es similar a la `Get-Process` cmdlet proporcionado por Windows PowerShell.)

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Estos atributos se consideran los metadatos porque su implementación es independiente de la implementación del código del cmdlet. Cuando el tiempo de ejecución de Windows PowerShell ejecuta el cmdlet, reconoce los atributos y, a continuación, realiza la acción adecuada para cada atributo.

Aunque es posible que desee implementar su propia versión de la funcionalidad proporcionada por estos atributos, el diseño de una buena cmdlet utiliza estas funcionalidades comunes.

Para obtener más información sobre los atributos diferentes que se pueden declarar en los cmdlets, consulte [tipos de atributo](./attribute-types.md).

## <a name="see-also"></a>Véase también

[Tipos de atributos](./attribute-types.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
