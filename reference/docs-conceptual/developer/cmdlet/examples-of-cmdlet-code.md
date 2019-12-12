---
title: Ejemplos de código de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364504"
---
# <a name="examples-of-cmdlet-code"></a>Ejemplos de código del cmdlet

Esta sección contiene ejemplos de código de cmdlet que puede usar para comenzar a escribir sus propios cmdlets.

> [!IMPORTANT]
> Si desea instrucciones paso a paso para escribir cmdlets, consulte [tutoriales para escribir cmdlets](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>En esta sección

[Cómo escribir un cmdlet simple](./how-to-write-a-simple-cmdlet.md) En este ejemplo se muestra la estructura básica del código de cmdlet.

[Cómo declarar parámetros de cmdlet](./how-to-declare-cmdlet-parameters.md) En este ejemplo se muestra cómo declarar los distintos tipos de parámetros.

[Cómo declarar conjuntos de parámetros](./how-to-declare-parameter-sets.md) En este ejemplo se muestra cómo declarar conjuntos de parámetros que pueden cambiar la acción que realiza un cmdlet.

[Cómo validar la entrada de parámetros](./how-to-validate-parameter-input.md) En estos ejemplos se muestra cómo validar la entrada de parámetros.

[Cómo declarar parámetros dinámicos](./how-to-declare-dynamic-parameters.md) En este ejemplo se muestra cómo declarar un parámetro que se agrega en tiempo de ejecución.

[Cómo invocar scripts dentro de un cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) En este ejemplo se muestra cómo invocar un script que se proporciona a un cmdlet.

[Cómo invalidar los métodos de procesamiento de entrada](./how-to-override-input-processing-methods.md) En estos ejemplos se muestra la estructura básica usada para invalidar los métodos BeginProcessing, ProcessRecord y EndProcessing.

[Cómo admitir las llamadas a ShouldProcess](./how-to-request-confirmations.md) En este ejemplo se muestra cómo se debe llamar a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) desde un cmdlet.

[Cómo admitir transacciones](./how-to-support-transactions.md) En este ejemplo se muestra cómo indicar que el cmdlet admite transacciones y cómo implementar la acción que se realiza cuando se usa el cmdlet dentro de una transacción.

[Cómo admitir trabajos](./how-to-support-jobs.md) En este ejemplo se muestra cómo admitir trabajos cuando se escriben cmdlets.

[Cómo invocar un cmdlet desde un cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) En este ejemplo se muestra cómo invocar un cmdlet desde otro cmdlet, lo que le permite agregar la funcionalidad del cmdlet invocado al cmdlet que está desarrollando.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
