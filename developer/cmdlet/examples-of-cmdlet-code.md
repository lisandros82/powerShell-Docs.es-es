---
title: Ejemplos de código del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068205"
---
# <a name="examples-of-cmdlet-code"></a>Ejemplos de código del cmdlet

Esta sección contiene ejemplos de código del cmdlet que puede usar para empezar a escribir sus propios cmdlets.

> [!IMPORTANT]
> Si desea instrucciones paso a paso para escribir cmdlets, consulte [tutoriales para escribir Cmdlets](./tutorials-for-writing-cmdlets.md).

## <a name="in-this-section"></a>En esta sección

[Cómo escribir un Cmdlet sencillo](./how-to-write-a-simple-cmdlet.md) en este ejemplo se muestra la estructura básica del código del cmdlet.

[Cómo declarar los parámetros de Cmdlet](./how-to-declare-cmdlet-parameters.md) en este ejemplo se muestra cómo declarar los diferentes tipos de parámetros.

[Cómo declarar el parámetro establece](./how-to-declare-parameter-sets.md) en este ejemplo se muestra cómo declarar los conjuntos de parámetros que pueden cambiar la acción que realiza un cmdlet.

[Cómo validar la entrada del parámetro](./how-to-validate-parameter-input.md) estos ejemplos muestra cómo validar entrada de parámetros.

[Cómo declarar los parámetros dinámicos](./how-to-declare-dynamic-parameters.md) en este ejemplo se muestra cómo declarar un parámetro que se agrega en tiempo de ejecución.

[Cómo invocar los Scripts dentro de un Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) en este ejemplo se muestra cómo invocar un script que se proporciona a un cmdlet.

[Cómo invalidar los métodos de procesamiento de entrada](./how-to-override-input-processing-methods.md) estos ejemplos muestra la estructura básica que se usa para invalidar los métodos de BeginProcessing, ProcessRecord y EndProcessing.

[Cómo la compatibilidad con las llamadas a ShouldProcess](./how-to-request-confirmations.md) este ejemplo se muestra cómo el [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) los métodos deben llamarse desde dentro de un cmdlet.

[Cómo admiten transacciones](./how-to-support-transactions.md) este ejemplo muestra indicar que el cmdlet admite las transacciones y cómo implementar la acción que se realiza cuando se usa el cmdlet dentro de una transacción.

[Cómo admitir trabajos](./how-to-support-jobs.md) este ejemplo muestra cómo admitir los trabajos al escribir cmdlets.

[Cómo invocar un Cmdlet desde dentro de un Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) en este ejemplo se muestra cómo invocar un cmdlet desde dentro de otro cmdlet, que le permite agregar la funcionalidad del cmdlet invocado al cmdlet que está desarrollando.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
