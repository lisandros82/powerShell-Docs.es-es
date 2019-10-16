---
title: Declaración de atributo de alias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370024"
---
# <a name="alias-attribute-declaration"></a>Declaración de atributo de alias

El atributo alias permite al usuario especificar nombres distintos para un parámetro de cmdlet. Los alias se pueden usar para proporcionar accesos directos para un nombre de parámetro o pueden proporcionar nombres diferentes que sean adecuados para diferentes escenarios.

## <a name="syntax"></a>Sintaxis

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parámetros

se requiere `aliasName` (String []). Especifica un conjunto de nombres de alias separados por comas para el parámetro de cmdlet.

## <a name="remarks"></a>Observaciones

- El atributo alias se usa con el atributo Parameter cuando se especifica un parámetro de cmdlet. Para obtener más información sobre cómo declarar estos atributos, vea [cómo declarar parámetros de cmdlet](./how-to-declare-cmdlet-parameters.md).

- Cada nombre de alias debe ser único dentro de un cmdlet. Windows PowerShell no comprueba si hay nombres de alias duplicados.

- El atributo alias se usa una vez para cada parámetro de un cmdlet.

- El atributo alias se define mediante la clase [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) .

## <a name="see-also"></a>Véase también

[Alias de parámetro](./parameter-aliases.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
