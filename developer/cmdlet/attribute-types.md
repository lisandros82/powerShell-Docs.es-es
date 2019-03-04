---
title: Tipos de atributos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9b1026ad-f072-4fca-8052-a2d8eb491c2a
caps.latest.revision: 6
ms.openlocfilehash: 52c75b3ca73706da39029d5b3ead52ff7197a5f1
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2019
ms.locfileid: "56863811"
---
# <a name="attribute-types"></a>Tipos de atributo

Atributos de cmdlet se pueden agrupar según su funcionalidad.
Las siguientes secciones describen los atributos disponibles y describen lo que hace el tiempo de ejecución cuando se invoca el atributo.

## <a name="cmdlet-attributes"></a>Atributos del cmdlet

### <a name="cmdlet"></a>Cmdlet

Identifica una clase de .NET Framework como un cmdlet.
Este es el atributo base necesario.
Para obtener más información, consulte [declaración de atributo de Cmdlet](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Atributos de parámetro

### <a name="parameter"></a>Parámetro

Identifica una propiedad pública de la clase de cmdlet como un parámetro de cmdlet.
Para obtener más información, consulte [declaración de atributo de parámetro](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Especifica uno o varios alias para un parámetro.
Para obtener más información, consulte [la declaración de atributo Alias](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Atributos de validación de argumento

### <a name="validatecount"></a>ValidateCount

Especifica el número mínimo y máximo de argumentos que se permiten para un parámetro de cmdlet.
Para obtener más información, consulte [ValidateCount la declaración de atributo](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Especifica un número mínimo y máximo de caracteres para un argumento de parámetro de cmdlet.
Para obtener más información, consulte [declaración de atributo ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Especifica un patrón de expresión regular que debe coincidir con el argumento del parámetro de cmdlet.
Para obtener más información, consulte [ValidatePattern la declaración de atributo](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Especifica los valores mínimos y máximo para un argumento de parámetro de cmdlet.
Para obtener más información, consulte [ValidateRange la declaración de atributo](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Especifica un conjunto de valores válidos para el argumento del parámetro de cmdlet.
Para obtener más información, consulte [ValidateSet la declaración de atributo](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Windows PowerShell SDK](../windows-powershell-reference.md)
