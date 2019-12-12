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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364584"
---
# <a name="attribute-types"></a>Tipos de atributo

Los atributos de cmdlet se pueden agrupar por funcionalidad.
En las secciones siguientes se describen los atributos disponibles y se describe lo que hace el motor en tiempo de ejecución cuando se invoca el atributo.

## <a name="cmdlet-attributes"></a>Atributos del cmdlet

### <a name="cmdlet"></a>Cmdlet

Identifica una clase .NET Framework como un cmdlet.
Este es el atributo base necesario.
Para obtener más información, vea [declaración de atributos de cmdlet](./cmdlet-attribute-declaration.md).

## <a name="parameter-attributes"></a>Atributos de parámetro

### <a name="parameter"></a>Parámetro

Identifica una propiedad pública de la clase de cmdlet como un parámetro de cmdlet.
Para obtener más información, vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).

### <a name="alias"></a>Alias

Especifica uno o varios alias para un parámetro.
Para obtener más información, vea [declaración de atributo de alias](./alias-attribute-declaration.md).

## <a name="argument-validation-attributes"></a>Atributos de validación de argumentos

### <a name="validatecount"></a>ValidateCount

Especifica el número mínimo y máximo de argumentos permitidos para un parámetro de cmdlet.
Para obtener más información, vea [declaración de atributos de ValidateCount](./validatecount-attribute-declaration.md).

### <a name="validatelength"></a>ValidateLength

Especifica un número mínimo y máximo de caracteres para un argumento de parámetro de cmdlet.
Para obtener más información, vea [declaración de atributos de ValidateLength](./validatelength-attribute-declaration.md).

### <a name="validatepattern"></a>ValidatePattern

Especifica un patrón de expresión regular que el argumento de parámetro de cmdlet debe coincidir.
Para obtener más información, vea [declaración de atributos de ValidatePattern](./validatepattern-attribute-declaration.md).

### <a name="validaterange"></a>ValidateRange

Especifica los valores mínimo y máximo para un argumento de parámetro de cmdlet.
Para obtener más información, vea [declaración de atributos de ValidateRange](./validaterange-attribute-declaration.md).

### <a name="validateset"></a>ValidateSet

Especifica un conjunto de valores válidos para el argumento del parámetro de cmdlet.
Para obtener más información, vea [declaración de atributos de ValidateSet](./validateset-attribute-declaration.md).

## <a name="see-also"></a>Véase también

[Windows PowerShell SDK](../windows-powershell-reference.md)
