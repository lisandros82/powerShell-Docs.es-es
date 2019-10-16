---
title: Compatibilidad con caracteres comodín en los parámetros del cmdlet
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365314"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Compatibilidad con caracteres comodín en los parámetros del cmdlet

A menudo, tendrá que diseñar un cmdlet para que se ejecute en un grupo de recursos, en lugar de hacerlo en un solo recurso. Por ejemplo, un cmdlet puede necesitar Buscar todos los archivos de un almacén de datos que tengan el mismo nombre o extensión. Debe proporcionar compatibilidad con caracteres comodín al diseñar un cmdlet que se ejecutará en un grupo de recursos.

> [!NOTE]
> El uso de caracteres comodín a veces se conoce como *comodines*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Cmdlets de Windows PowerShell que usan caracteres comodín

 Muchos cmdlets de Windows PowerShell admiten caracteres comodín para sus valores de parámetro. Por ejemplo, casi todos los cmdlets que tienen un parámetro `Name` o `Path` admiten caracteres comodín para estos parámetros. (Aunque la mayoría de los cmdlets que tienen un parámetro `Path` también tienen un parámetro `LiteralPath` que no admite caracteres comodín). El siguiente comando muestra cómo se usa un carácter comodín para devolver todos los cmdlets de la sesión actual cuyo nombre contiene el verbo GET.

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>Caracteres comodín admitidos

Windows PowerShell admite los siguientes caracteres comodín.

| N |                             Descripción                             |  Ejemplo   |     Coincidencia      | No coincide |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | Coincide con cero o más caracteres, empezando en la posición especificada | `a*`       | A, AG, Apple     |                |
| ?        | Coincide con cualquier carácter que se encuentra en la posición especificada                     | `?n`       | , En, en       | ejecuta            |
| [ ]      | Coincide con un intervalo de caracteres                                       | `[a-l]ook` | libro, Cook, mire | Nook, tardó     |
| [ ]      | Coincide con los caracteres especificados                                    | `[bn]ook`  | libro, Nook       | Cook, mire     |

Al diseñar cmdlets que admiten caracteres comodín, permita combinaciones de caracteres comodín. Por ejemplo, el siguiente comando usa el cmdlet `Get-ChildItem` para recuperar todos los archivos. txt que se encuentran en la carpeta c:\Techdocs y que comienzan con las letras "a" a "l".

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

El comando anterior usa el carácter comodín de intervalo `[a-l]` para especificar que el nombre de archivo debe empezar con los caracteres "a" a "l" y usa el carácter comodín `*` como marcador de posición para los caracteres entre la primera letra del nombre de archivo y el archivo **. txt.** extensión.

En el ejemplo siguiente se usa un patrón de caracteres comodín de intervalo que excluye la letra "d", pero se incluyen todas las demás Letras de la "a" a la "f".

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Controlar caracteres literales en patrones de caracteres comodín

Si el patrón de carácter comodín que especifica contiene caracteres literales que no deben interpretarse como caracteres comodín, use el carácter de acento grave (`` ` ``) como carácter de escape. Cuando especifique caracteres literales int en la API de PowerShell, use una sola marca de paso. Cuando especifique caracteres literales en el símbolo del sistema de PowerShell, use dos TICs.

Por ejemplo, el siguiente patrón contiene dos corchetes que deben tomarse literalmente.

Cuando se usa en la API de PowerShell, use:

- "John Smith \` [* ']"

Cuando se usa desde el símbolo del sistema de PowerShell:

- "John Smith \` @ no__t-1 [* \` ']"

Este patrón coincide con "John Smith [marketing]" o "John Smith [desarrollo]". Por ejemplo:

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Resultados de cmdlet y caracteres comodín

Cuando los parámetros de cmdlet admiten caracteres comodín, la operación normalmente genera una salida de matriz.
En ocasiones, no tiene sentido admitir una salida de matriz porque el usuario podría usar un solo elemento. Por ejemplo, el cmdlet `Set-Location` no admite la salida de matriz porque el usuario establece una sola ubicación. En esta instancia, el cmdlet sigue admitiendo caracteres comodín, pero fuerza la resolución en una sola ubicación.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Clase WildcardPattern](/dotnet/api/system.management.automation.wildcardpattern)
