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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067117"
---
# <a name="validaterange-attribute-declaration"></a>Declaración de atributo ValidateRange

El atributo ValidateRange especifica los valores mínimos y máximo (el rango) para el argumento del parámetro de cmdlet. Este atributo también se puede usar las funciones de Windows PowerShell.

## <a name="syntax"></a>Sintaxis

```csharp
[ValidateRange(object minRange, object maxRange)]
```

#### <a name="parameters"></a>Parámetros

`MinRange` ([System.Object](/dotnet/api/system.object)) necesarios. Especifica el valor mínimo permitido.

`MaxRange` ([System.Object](/dotnet/api/system.object)) necesarios. Especifica el valor máximo permitido.

## <a name="remarks"></a>Observaciones

- El tiempo de ejecución de Windows PowerShell genera un error de construcción cuando el valor de la `MinRange` parámetro es mayor que el valor de la `MaxRange` parámetro.

- El tiempo de ejecución de Windows PowerShell, produce un error de validación en las siguientes condiciones:

    - Cuando el valor del argumento es menor que el `MinRange` límite o mayor que el `MaxRange` límite.

    - Cuando el argumento no es del mismo tipo como el `MinRange` y `MaxRange` parámetros.

- El atributo ValidateRange está definido por el [System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute) clase.

## <a name="see-also"></a>Véase también

[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
