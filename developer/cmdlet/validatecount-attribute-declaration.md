---
title: Declaración de atributo ValidateCount | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes, ValidateCount
- ValidateCount attribute, described
- ValidateCount attribute
ms.assetid: 516af1ef-2c2e-408d-84bc-865f5bccf761
caps.latest.revision: 11
ms.openlocfilehash: 1a7b5ea340fe5212d003c97a9017278d6c631355
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859161"
---
# <a name="validatecount-attribute-declaration"></a>Declaración de atributo ValidateCount

El atributo ValidateCount especifica el número mínimo y máximo de argumentos que se permite para un parámetro de cmdlet.

## <a name="syntax"></a>Sintaxis

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parámetros

`MinLength` ([System.Int32](/dotnet/api/System.Int32)) necesarios. Especifica el número mínimo de argumentos.

`MaxLength`([System.Int32](/dotnet/api/System.Int32)) necesarios. Especifica el número máximo de argumentos.

## <a name="remarks"></a>Observaciones

- Para obtener más información acerca de cómo declarar este atributo, vea [cómo declarar las reglas de validación de entrada](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b).

- Cuando este atributo no se invoca, el parámetro de cmdlet correspondiente puede tener cualquier número de argumentos.

- El tiempo de ejecución de Windows PowerShell, produce un error en las siguientes condiciones:

    - El `MinLength` y `MaxLength` parámetros de atributo no son de tipo [System.Int32](/dotnet/api/System.Int32).

    - El valor de la `MaxLength` parámetro de atributo es menor que el valor de la `MinLength` parámetro de atributo.

- El atributo ValidateCount está definido por el [System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount) clase.

## <a name="see-also"></a>Véase también

[System.Management.Automation.Validatecount](/dotnet/api/System.Management.Automation.ValidateCount)

[Cómo declarar las reglas de validación de entrada](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Cómo declarar las reglas de validación de entrada](http://msdn.microsoft.com/en-us/544c2100-62ba-4be4-b2a2-cc0d4e4fc45b)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
