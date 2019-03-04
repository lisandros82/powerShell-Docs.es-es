---
title: Informes de errores de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856161"
---
# <a name="windows-powershell-error-reporting"></a>Informes de errores de Windows PowerShell

Los temas de esta sección describen cómo los cmdlets informan de errores.

## <a name="in-this-section"></a>En esta sección

[Conceptos de error Reporting](./error-reporting-concepts.md) se describen los dos mecanismos que puede usar los cmdlets para informar de errores.

[La terminación](./terminating-errors.md) describe el método utilizado para notificar la terminación de errores, donde ese método puede llamarse desde dentro el cmdlet y las excepciones que se pueden devolver el tiempo de ejecución de Windows PowerShell cuando se llama al método.

[Errores de no terminación](./non-terminating-errors.md) describe el método utilizado para notificar errores de no terminación y que ese método puede llamarse desde dentro del cmdlet.

[Mostrar información de Error por categoría](./displaying-error-information.md) se describen las formas en que los usuarios pueden mostrar el error.

[Registros de Error de Windows PowerShell](./windows-powershell-error-records.md) describe los componentes de un registro de errores.

[Interpretación de los objetos de ErrorRecord](./interpreting-errorrecord-objects.md) explica cómo se interpretan ErrorRecord objetos.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
