---
title: Instrucción OutputType del atributo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365344"
---
# <a name="outputtype-attribute-declaration"></a>Declaración de atributo OutputType

El atributo `OutputType` identifica los tipos de .NET Framework devueltos por un cmdlet, una función o un script.

## <a name="syntax"></a>Sintaxis

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parámetros

Se requiere el tipo (`string[]` o `Type[]`). Especifica los tipos devueltos por la función de cmdlet o el script.

ParameterSetName (String []) opcional. Especifica los conjuntos de parámetros que devuelven los tipos especificados en el parámetro `type`.

providerCmdlet opcional. Especifica el cmdlet de proveedor que devuelve los tipos especificados en el parámetro `type`.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
