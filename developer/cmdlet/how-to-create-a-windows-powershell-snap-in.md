---
title: Cómo crear un complemento de PowerShell de Windows | Microsoft Docs
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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055944"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Cómo crear un complemento de Windows PowerShell

Un complemento de Windows PowerShell proporciona un mecanismo para registrar los conjuntos de cmdlets y el otro proveedor de Windows PowerShell con el shell, lo que permite ampliar la funcionalidad del shell. Un complemento de Windows PowerShell puede registrar todos los cmdlets y proveedores en un único ensamblado, o puede registrar una lista específica de los cmdlets y proveedores.

Ensamblados de complementos deben instalarse en un directorio protegido, justo como se haría con otros sistemas operativos. En caso contrario, los usuarios malintencionados pueden reemplazar un ensamblado con código no seguro.

## <a name="windows-powershell-snap-in-classes"></a>Clases de complemento de PowerShell de Windows

Todas las clases de complemento de Windows PowerShell que se derivan de la [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) o [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) clases.

## <a name="examples"></a>Ejemplos

[Escribir un complemento Windows PowerShell](./writing-a-windows-powershell-snap-in.md): En este ejemplo se muestra cómo crear un complemento que se usa para registrar todos los cmdlets y proveedores en un ensamblado.

[Escribir un complemento personalizado de Windows PowerShell](./writing-a-custom-windows-powershell-snap-in.md): En este ejemplo se muestra cómo crear un complemento personalizado que se usa para registrar un conjunto específico de los cmdlets y proveedores que podrían existan o no en un único ensamblado.

## <a name="see-also"></a>Véase también

[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Registrar los Cmdlets](./registering-cmdlets.md)

[Shell de SDK de Windows PowerShell](../windows-powershell-reference.md)
