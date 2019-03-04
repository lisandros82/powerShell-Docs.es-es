---
title: La declaración de atributo alias | Microsoft Docs
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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855051"
---
# <a name="alias-attribute-declaration"></a>Declaración de atributo de alias

Alias (atributo) permite al usuario especificar nombres distintos para un parámetro de cmdlet. Alias pueden utilizarse para proporcionar accesos directos de un nombre de parámetro, o estas pueden proporcionar nombres diferentes que son adecuados para diferentes escenarios.

## <a name="syntax"></a>Sintaxis

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parámetros

`aliasName` (String[]) Obligatorio. Especifica un conjunto de alias separados por comas de nombres para el parámetro de cmdlet.

## <a name="remarks"></a>Observaciones

- El atributo de Alias se utiliza con el atributo de parámetro cuando se especifica un parámetro de cmdlet. Para obtener más información acerca de cómo declarar estos atributos, vea [cómo declarar los parámetros de Cmdlet](./how-to-declare-cmdlet-parameters.md).

- Cada nombre de alias debe ser único dentro de un cmdlet. Windows PowerShell no comprueba los nombres de alias duplicados.

- El atributo de Alias se usa una vez para cada parámetro en un cmdlet.

- Alias (atributo) se define mediante el [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) clase.

## <a name="see-also"></a>Véase también

[Alias de parámetro](./parameter-aliases.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
