---
title: Declaración de atributo OutputType | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97a98ee-ffc0-42f0-a9a6-b0717b39c798
caps.latest.revision: 5
ms.openlocfilehash: 7aa6fa407e509a31c4066c4f73ae01b02b2f338c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067610"
---
# <a name="outputtype-attribute-declaration"></a>Declaración de atributo OutputType

El `OutputType` atributo identifica los tipos de .NET Framework devueltos por un cmdlet, función o script.

## <a name="syntax"></a>Sintaxis

```csharp
[OutputType(params string[] type)]
[OutputType(params Type[] type)]
[OutputType(params string[] type, Named Parameters...)]
[OutputType(params Type[] type, Named Parameters...)]
```

#### <a name="parameters"></a>Parámetros

Tipo (`string[]` o `Type[]`) necesarios. Especifica los tipos devueltos por la función del cmdlet o script.

ParameterSetName (string[]) Optional. Especifica los conjuntos de parámetros que devuelven los tipos especificados en el `type` parámetro.

providerCmdlet opcional. Especifica el cmdlet de proveedor que devuelve los tipos especificados en el `type` parámetro.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
