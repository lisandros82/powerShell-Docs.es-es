---
title: Informe de errores de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364274"
---
# <a name="windows-powershell-error-reporting"></a>Informes de errores de Windows PowerShell

En los temas de esta sección se describe el modo en que los cmdlets notifican errores.

## <a name="in-this-section"></a>En esta sección

[Conceptos de informes de errores](./error-reporting-concepts.md) Describe los dos mecanismos que los cmdlets pueden usar para notificar los errores.

[Errores de terminación](./terminating-errors.md) Describe el método utilizado para notificar los errores de terminación, donde se puede llamar a ese método desde dentro del cmdlet y excepciones que el tiempo de ejecución de Windows PowerShell puede devolver cuando se llama al método.

[Errores de no terminación](./non-terminating-errors.md) Describe el método utilizado para notificar los errores de no terminación y dónde se puede llamar al método desde dentro del cmdlet.

[Mostrar información de errores por categoría](./displaying-error-information.md) Describe las formas en que los usuarios pueden mostrar errores.

[Registros de errores de Windows PowerShell](./windows-powershell-error-records.md) Describe los componentes de un registro de error.

[Interpretar objetos ErrorRecord](./interpreting-errorrecord-objects.md) Describe cómo se interpretan los objetos ErrorRecord.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
