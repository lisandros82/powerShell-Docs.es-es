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
ms.openlocfilehash: ffc45f6b80a2b7ed22f27d083d042b1de7f353f6
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "59983905"
---
# <a name="validatecount-attribute-declaration"></a>Declaración de atributo ValidateCount

El atributo ValidateCount especifica el número mínimo y máximo de argumentos que se permite para un parámetro de cmdlet.

## <a name="syntax"></a>Sintaxis

```csharp
[ValidateCount(int minLength, int maxlength)]
```

#### <a name="parameters"></a>Parámetros

`MinLength` ([System.Int32][]) necesarios. Especifica el número mínimo de argumentos.

`MaxLength`([System.Int32][]) necesarios. Especifica el número máximo de argumentos.

## <a name="remarks"></a>Observaciones

- Para obtener más información acerca de cómo declarar este atributo, vea [cómo validar un número de argumentos][].

- Cuando este atributo no se invoca, el parámetro de cmdlet correspondiente puede tener cualquier número de argumentos.

- El tiempo de ejecución de Windows PowerShell, produce un error en las siguientes condiciones:

    - El `MinLength` y `MaxLength` parámetros de atributo no son de tipo [System.Int32][].

    - El valor de la `MaxLength` parámetro de atributo es menor que el valor de la `MinLength` parámetro de atributo.

- El atributo ValidateCount está definido por el [System.Management.Automation.ValidateCountAttribute][] clase.

## <a name="see-also"></a>Véase también

[System.Management.Automation.ValidateCountAttribute][]

[Cómo validar un número de argumentos][]

[Escribir un cmdlet de Windows PowerShell][]

[Cómo validar un número de argumentos]: how-to-validate-an-argument-count.md
[Escribir un cmdlet de Windows PowerShell]: writing-a-windows-powershell-cmdlet.md

[System.Int32]: /dotnet/api/System.Int32
[System.Management.Automation.ValidateCountAttribute]: /dotnet/api/System.Management.Automation.ValidateCountAttribute
