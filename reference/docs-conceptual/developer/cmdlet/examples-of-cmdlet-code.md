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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364504"
---
# <a name="examples-of-cmdlet-code"></a><span data-ttu-id="a7d59-102">Ejemplos de código del cmdlet</span><span class="sxs-lookup"><span data-stu-id="a7d59-102">Examples of Cmdlet Code</span></span>

<span data-ttu-id="a7d59-103">Esta sección contiene ejemplos de código de cmdlet que puede usar para comenzar a escribir sus propios cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a7d59-103">This section contains examples of cmdlet code that you can use to start writing your own cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a7d59-104">Si desea instrucciones paso a paso para escribir cmdlets, consulte [tutoriales para escribir cmdlets](./tutorials-for-writing-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="a7d59-104">If you want step-by-step instructions for writing cmdlets, see [Tutorials for Writing Cmdlets](./tutorials-for-writing-cmdlets.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a7d59-105">En esta sección</span><span class="sxs-lookup"><span data-stu-id="a7d59-105">In This Section</span></span>

<span data-ttu-id="a7d59-106">[Cómo escribir un cmdlet simple](./how-to-write-a-simple-cmdlet.md) En este ejemplo se muestra la estructura básica del código de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7d59-106">[How to Write a Simple Cmdlet](./how-to-write-a-simple-cmdlet.md) This example shows the basic structure of cmdlet code.</span></span>

<span data-ttu-id="a7d59-107">[Cómo declarar parámetros de cmdlet](./how-to-declare-cmdlet-parameters.md) En este ejemplo se muestra cómo declarar los distintos tipos de parámetros.</span><span class="sxs-lookup"><span data-stu-id="a7d59-107">[How to Declare Cmdlet Parameters](./how-to-declare-cmdlet-parameters.md) This example shows how to declare the different types of parameters.</span></span>

<span data-ttu-id="a7d59-108">[Cómo declarar conjuntos de parámetros](./how-to-declare-parameter-sets.md) En este ejemplo se muestra cómo declarar conjuntos de parámetros que pueden cambiar la acción que realiza un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7d59-108">[How to Declare Parameter Sets](./how-to-declare-parameter-sets.md) This example shows how to declare sets of parameters that can change the action a cmdlet performs.</span></span>

<span data-ttu-id="a7d59-109">[Cómo validar la entrada de parámetros](./how-to-validate-parameter-input.md) En estos ejemplos se muestra cómo validar la entrada de parámetros.</span><span class="sxs-lookup"><span data-stu-id="a7d59-109">[How to Validate Parameter Input](./how-to-validate-parameter-input.md) These examples show how to validate parameter input.</span></span>

<span data-ttu-id="a7d59-110">[Cómo declarar parámetros dinámicos](./how-to-declare-dynamic-parameters.md) En este ejemplo se muestra cómo declarar un parámetro que se agrega en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="a7d59-110">[How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md) This example shows how to declare a parameter that is added at runtime.</span></span>

<span data-ttu-id="a7d59-111">[Cómo invocar scripts dentro de un cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) En este ejemplo se muestra cómo invocar un script que se proporciona a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7d59-111">[How to Invoke Scripts Within a Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md) This example shows how to invoke a script that is supplied to a cmdlet.</span></span>

<span data-ttu-id="a7d59-112">[Cómo invalidar los métodos de procesamiento de entrada](./how-to-override-input-processing-methods.md) En estos ejemplos se muestra la estructura básica usada para invalidar los métodos BeginProcessing, ProcessRecord y EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="a7d59-112">[How To Override Input Processing Methods](./how-to-override-input-processing-methods.md) These examples show the basic structure used to override the BeginProcessing, ProcessRecord, and EndProcessing methods.</span></span>

<span data-ttu-id="a7d59-113">[Cómo admitir las llamadas a ShouldProcess](./how-to-request-confirmations.md) En este ejemplo se muestra cómo se debe llamar a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) desde un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7d59-113">[How to Support ShouldProcess Calls](./how-to-request-confirmations.md) This example shows how the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods should be called from within a cmdlet.</span></span>

<span data-ttu-id="a7d59-114">[Cómo admitir transacciones](./how-to-support-transactions.md) En este ejemplo se muestra cómo indicar que el cmdlet admite transacciones y cómo implementar la acción que se realiza cuando se usa el cmdlet dentro de una transacción.</span><span class="sxs-lookup"><span data-stu-id="a7d59-114">[How to Support Transactions](./how-to-support-transactions.md) This example shows how to indicate that the cmdlet supports transactions and how to implement the action that is taken when the cmdlet is used within a transaction.</span></span>

<span data-ttu-id="a7d59-115">[Cómo admitir trabajos](./how-to-support-jobs.md) En este ejemplo se muestra cómo admitir trabajos cuando se escriben cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a7d59-115">[How to Support Jobs](./how-to-support-jobs.md) This example shows how to support jobs when you write cmdlets.</span></span>

<span data-ttu-id="a7d59-116">[Cómo invocar un cmdlet desde un cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) En este ejemplo se muestra cómo invocar un cmdlet desde otro cmdlet, lo que le permite agregar la funcionalidad del cmdlet invocado al cmdlet que está desarrollando.</span><span class="sxs-lookup"><span data-stu-id="a7d59-116">[How to Invoke a Cmdlet From Within a Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7d59-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="a7d59-117">See Also</span></span>

[<span data-ttu-id="a7d59-118">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7d59-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
