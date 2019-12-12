---
title: Atributos de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369964"
---
# <a name="cmdlet-attributes"></a>Atributos del cmdlet

Windows PowerShell define varios atributos que puede usar para agregar una funcionalidad común a los cmdlets sin necesidad de implementar esa funcionalidad en su propio código. Esto incluye el atributo de cmdlet que identifica una clase de Microsoft .NET Framework como una clase de cmdlet, el atributo OutputType que especifica los tipos de .NET Framework devueltos por el cmdlet, el atributo Parameter que identifica las propiedades públicas como cmdlet y mucho más.

## <a name="in-this-section"></a>En esta sección

[Atributos del código de cmdlet](./attributes-in-cmdlet-code.md) Describe la ventaja de usar atributos en el código del cmdlet.

[Tipos de atributos](./attribute-types.md) Describe los diferentes atributos que pueden decorar una clase de cmdlet.

[Declaración de atributo de alias](./alias-attribute-declaration.md) Describe cómo definir alias para un nombre de parámetro de cmdlet.

[Declaración de atributo de cmdlet](./cmdlet-attribute-declaration.md) Describe cómo definir una clase .NET Framework como un cmdlet.

[Declaración de atributos de credenciales](./credential-attribute-declaration.md) Describe cómo agregar compatibilidad para convertir la entrada de cadena en un objeto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) .

[OutputType (declaración de atributo](./outputtype-attribute-declaration.md) ) Describe cómo especificar los tipos de .NET Framework devueltos por el cmdlet.

[Declaración de atributo de parámetro](./parameter-attribute-declaration.md) Describe cómo definir los parámetros de un cmdlet.

[Declaración de atributos de ValidateCount](./validatecount-attribute-declaration.md) Describe cómo definir el número de argumentos permitidos para un parámetro.

[Declaración de atributos de ValidateLength](./validatelength-attribute-declaration.md) Describe cómo definir la longitud (en caracteres) de un argumento de parámetro.

[Declaración de atributos de ValidatePattern](./validatepattern-attribute-declaration.md) Describe cómo definir los patrones válidos para un argumento de parámetro.

[Declaración de atributos de ValidateRange](./validaterange-attribute-declaration.md) Describe cómo definir el intervalo válido para un argumento de parámetro.

[Declaración de atributos de ValidateSet](./validateset-attribute-declaration.md) Describe cómo definir los valores posibles para un argumento de parámetro.

## <a name="reference"></a>Referencia

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
