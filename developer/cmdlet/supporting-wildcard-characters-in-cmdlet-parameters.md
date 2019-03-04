---
title: Compatibilidad con caracteres comodín en los parámetros de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 296490e4692e72f823be0b00aee90dc8c3dc9131
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862521"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Compatibilidad con caracteres comodín en los parámetros del cmdlet

A menudo, tendrá que diseñar un cmdlet para ejecutar en un grupo de recursos en lugar de en un único recurso. Por ejemplo, un cmdlet posible que deba buscar todos los archivos en un almacén de datos que tienen el mismo nombre o la extensión. Debe proporcionar compatibilidad con caracteres comodín cuando se diseña un cmdlet que se va a ejecutar en un grupo de recursos.

> [!NOTE]
> Uso de caracteres comodín se denomina a veces *comodines*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Cmdlets de PowerShell de Windows que usan caracteres comodín

 Muchos de los cmdlets de Windows PowerShell admiten caracteres comodín para sus valores de parámetro. Por ejemplo, casi todos los cmdlets que tiene un `Name` o `Path` parámetro admite caracteres comodín para estos parámetros. (Aunque la mayoría de los cmdlets que tengan un `Path` parámetro también tienen un `LiteralPath` parámetro que no admite caracteres comodín.) El comando siguiente muestra cómo se usa un carácter comodín para devolver todos los cmdlets de la sesión actual cuyos nombres contienen el verbo Get.

 **PS > get-command get -\***

## <a name="supported-wildcard-characters"></a>Caracteres comodín admitidos

Windows PowerShell es compatible con los siguientes caracteres comodín.

|carácter comodín|Descripción|Ejemplo|Coincidencia|No coincide con|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|Coincide con cero o más caracteres, empezando en la posición especificada|a*|Una, ag, Apple||
|?|Cualquiercarácter coincide con la posición especificada|?n|Una, en, en|se ejecutó|
|[ ]|Coincide con un intervalo de caracteres|[a-l] ook|libro, cook, apariencia|tardó|
|[ ]|Coincide con los caracteres especificados|[bc]ook|libro, cook|look|

Al diseñar los cmdlets que admiten caracteres comodín, se permite para combinaciones de caracteres comodín. Por ejemplo, el siguiente comando usa el `Get-ChildItem` para recuperar todos los archivos .txt que se encuentran en la carpeta c:\Techdocs y que comienzan con las letras "a" a "l".

**get-childitem c:\techdocs\\[a-l]\*.txt**

El comando anterior usa el carácter comodín de intervalo **[a-l]** para especificar el nombre de archivo debe empezar con los caracteres "a" a "l". El comando usa el * carácter comodín como marcador de posición para cualquier carácter entre la primera letra del nombre de archivo y la extensión. txt.

En el ejemplo siguiente se usa un modelo de carácter comodín de intervalo que excluye la letra "d", pero incluye todas las letras de la "a" a "f".

**get-childitem c:\techdocs\\[a-cef]\*.txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Caracteres literales de carácter comodín patrones de control

Si el patrón de carácter comodín que especifique contiene caracteres literales, use el carácter de acento grave (') como carácter de escape. Al especificar caracteres literales mediante programación, utilice un acento grave único. Al especificar los caracteres literales en el símbolo del sistema, use dos graves. Por ejemplo, el siguiente patrón contiene dos corchetes que se deben tener literalmente.

"John Smith \`[*']" (especificado mediante programación)

"John Smith \` \`[*\`']" (especificado en el símbolo del sistema)

Este patrón coincide con "John Smith [Marketing]" o "John Smith [desarrollo de]".

## <a name="cmdlet-output-and-wildcard-characters"></a>Salida del cmdlet y caracteres comodín

Cuando los parámetros de cmdlet admiten caracteres comodín, una operación de cmdlet normalmente genera una salida de la matriz. En ocasiones, no tiene sentido para admitir una matriz de salida porque el usuario podría usar sólo un elemento a la vez. Por ejemplo, el `Set-Location` cmdlet es compatible con una matriz de salida porque el usuario establece una única ubicación. En este caso, el cmdlet todavía admite caracteres comodín, pero fuerza la resolución a una única ubicación.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Clase WildcardPattern](/dotnet/api/system.management.automation.wildcardpattern)
