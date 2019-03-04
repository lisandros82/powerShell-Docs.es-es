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
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853921"
---
# <a name="cmdlet-attributes"></a>Atributos del cmdlet

Windows PowerShell define varios atributos que puede usar para agregar funcionalidad común a los cmdlets sin necesidad de implementar esa funcionalidad dentro de su propio código. Esto incluye el atributo de Cmdlet que identifica una clase de Microsoft .NET Framework como una clase de cmdlet, el atributo OutputType que especifica los tipos de .NET Framework devueltos por el cmdlet, el atributo de parámetro que identifica las propiedades públicas como el cmdlet los parámetros y mucho más.

## <a name="in-this-section"></a>En esta sección

[Atributos en el código del Cmdlet](./attributes-in-cmdlet-code.md) describe la ventaja de uso de atributos en el código del cmdlet.

[Tipos de atributo](./attribute-types.md) se describen los atributos diferentes que pueden decorar una clase de cmdlet.

[La declaración de atributo alias](./alias-attribute-declaration.md) se describe cómo definir los alias para un nombre de parámetro de cmdlet.

[Declaración de atributo de cmdlet](./cmdlet-attribute-declaration.md) se describe cómo definir una clase de .NET Framework como un cmdlet.

[Declaración de atributo de credenciales](./credential-attribute-declaration.md) se describe cómo agregar compatibilidad para convertir la entrada de cadena en un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objeto.

[Atributo OutputType declaración](./outputtype-attribute-declaration.md) describe cómo especificar los tipos de .NET Framework devueltos por el cmdlet.

[Declaración de atributo de parámetro](./parameter-attribute-declaration.md) se describe cómo definir los parámetros de un cmdlet.

[Declaración de atributo ValidateCount](./validatecount-attribute-declaration.md) se describe cómo definir cuántos argumentos están permitidos para un parámetro.

[Declaración de atributo ValidateLength](./validatelength-attribute-declaration.md) se describe cómo definir la longitud (en caracteres) de un argumento de parámetro.

[Declaración de atributo ValidatePattern](./validatepattern-attribute-declaration.md) se describe cómo definir los patrones válidos para un argumento de parámetro.

[Declaración de atributo ValidateRange](./validaterange-attribute-declaration.md) se describe cómo definir el intervalo válido para un argumento de parámetro.

[Declaración de atributo ValidateSet](./validateset-attribute-declaration.md) se describe cómo definir los valores posibles para un argumento de parámetro.

## <a name="reference"></a>Referencia

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
