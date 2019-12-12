---
title: Cómo crear un complemento de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364434"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Cómo crear un complemento de Windows PowerShell

Un complemento de Windows PowerShell proporciona un mecanismo para registrar conjuntos de cmdlets y otro proveedor de Windows PowerShell con el Shell, lo que extiende la funcionalidad del shell. Un complemento de Windows PowerShell puede registrar todos los cmdlets y proveedores en un solo ensamblado, o puede registrar una lista específica de cmdlets y proveedores.

Los ensamblados de complementos deben instalarse en un directorio protegido, de la misma forma que con otros sistemas operativos. De lo contrario, los usuarios malintencionados pueden reemplazar un ensamblado con código no seguro.

## <a name="windows-powershell-snap-in-classes"></a>Clases de complemento de Windows PowerShell

Todas las clases de complemento de Windows PowerShell se derivan de las clases [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) o [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .

## <a name="examples"></a>Ejemplos

[Escribir un complemento de Windows PowerShell: en](./writing-a-windows-powershell-snap-in.md)este ejemplo se muestra cómo crear un complemento que se usa para registrar todos los cmdlets y proveedores de un ensamblado.

[Escribir un complemento personalizado de Windows PowerShell: en](./writing-a-custom-windows-powershell-snap-in.md)este ejemplo se muestra cómo crear un complemento personalizado que se usa para registrar un conjunto específico de cmdlets y proveedores que podrían existir o no en un único ensamblado.

## <a name="see-also"></a>Véase también

[System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Registrar cmdlets](./registering-cmdlets.md)

[SDK de Windows PowerShell Shell](../windows-powershell-reference.md)
