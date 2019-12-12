---
title: Invocar cmdlets y scripts dentro de un cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364294"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="59b0e-102">Invocación de los cmdlets y los scripts dentro de un cmdlet</span><span class="sxs-lookup"><span data-stu-id="59b0e-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="59b0e-103">Un cmdlet puede invocar otros cmdlets y scripts desde el método de procesamiento de entrada del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59b0e-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="59b0e-104">Esto le permite agregar la funcionalidad de los cmdlets y scripts existentes a su cmdlet sin tener que volver a escribir el código.</span><span class="sxs-lookup"><span data-stu-id="59b0e-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="59b0e-105">Método Invoke</span><span class="sxs-lookup"><span data-stu-id="59b0e-105">The Invoke Method</span></span>

<span data-ttu-id="59b0e-106">Todos los cmdlets pueden invocar un cmdlet existente llamando al método [System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) desde dentro de un método de procesamiento de entrada, como [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), que es reemplazado por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59b0e-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="59b0e-107">Sin embargo, solo puede invocar los cmdlets que derivan directamente de la clase [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="59b0e-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="59b0e-108">No se puede invocar un cmdlet derivado de la clase [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="59b0e-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="59b0e-109">El método [System. Management. Automation. cmdlet. Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) tiene las siguientes variantes.</span><span class="sxs-lookup"><span data-stu-id="59b0e-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="59b0e-110">[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) esta variante invoca el objeto de cmdlet y devuelve una colección de objetos de tipo "T".</span><span class="sxs-lookup"><span data-stu-id="59b0e-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="59b0e-111">[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) esta variante invoca el objeto de cmdlet y devuelve un emumerator fuertemente tipado.</span><span class="sxs-lookup"><span data-stu-id="59b0e-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="59b0e-112">Esta variante permite al usuario utilizar los objetos de la colección para realizar operaciones personalizadas.</span><span class="sxs-lookup"><span data-stu-id="59b0e-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="59b0e-113">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="59b0e-113">Examples</span></span>

|<span data-ttu-id="59b0e-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="59b0e-114">Example</span></span>|<span data-ttu-id="59b0e-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="59b0e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59b0e-116">Invocar cmdlets dentro de un cmdlet</span><span class="sxs-lookup"><span data-stu-id="59b0e-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="59b0e-117">En este ejemplo se muestra cómo invocar un cmdlet desde otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59b0e-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="59b0e-118">Invocar scripts dentro de un cmdlet</span><span class="sxs-lookup"><span data-stu-id="59b0e-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="59b0e-119">En este ejemplo se muestra cómo invocar un script que se proporciona al cmdlet desde otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59b0e-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="59b0e-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="59b0e-120">See Also</span></span>

[<span data-ttu-id="59b0e-121">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="59b0e-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
