---
title: Declaración de atributo ValidateRange | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange, described
- ValidateRange attribute
- attributes, ValidateRange
ms.assetid: 1f8066e6-e5d3-4f4e-8948-a90af5dace82
caps.latest.revision: 11
ms.openlocfilehash: 155a406b9855c435041fe175ac7d983a4b4eb8b7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369134"
---
# <a name="validaterange-attribute-declaration"></a>Declaración de atributo ValidateRange

El atributo ValidateRange especifica los valores mínimo y máximo (el intervalo) para el argumento del parámetro del cmdlet. Este atributo también se puede usar en las funciones de Windows PowerShell.

## <a name="syntax"></a>Sintaxis

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parámetros

se requiere `MinRange` ([System. Object](/dotnet/api/system.object)). Especifica el valor mínimo permitido.

se requiere `MaxRange` ([System. Object](/dotnet/api/system.object)). Especifica el valor máximo permitido.

## <a name="remarks"></a>Observaciones

- El tiempo de ejecución de Windows PowerShell genera un error de construcción cuando el valor del parámetro `MinRange` es mayor que el valor del parámetro `MaxRange`.

- El tiempo de ejecución de Windows PowerShell genera un error de validación en las siguientes condiciones:

    - Cuando el valor del argumento es menor que el límite de `MinRange` o mayor que el límite de `MaxRange`.

    - Cuando el argumento no es del mismo tipo que los parámetros `MinRange` y `MaxRange`.

- La clase [System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) define el atributo ValidateRange.

## <a name="see-also"></a>Véase también

[System. Management. Automation. Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
