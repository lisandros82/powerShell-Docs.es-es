---
title: Invocar los Cmdlets y Scripts dentro de un Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855191"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="1855d-102">Invocación de los cmdlets y los scripts dentro de un cmdlet</span><span class="sxs-lookup"><span data-stu-id="1855d-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="1855d-103">Un cmdlet puede invocar otros cmdlets y scripts en el método del cmdlet de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="1855d-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="1855d-104">Esto le permite agregar la funcionalidad de los cmdlets existentes y las secuencias de comandos al cmdlet sin tener que volver a escribir el código.</span><span class="sxs-lookup"><span data-stu-id="1855d-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="1855d-105">El método de invocación</span><span class="sxs-lookup"><span data-stu-id="1855d-105">The Invoke Method</span></span>

<span data-ttu-id="1855d-106">Todos los cmdlets puede invocar un cmdlet existente mediante una llamada a la [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método dentro de una entrada de procesamiento de método, como [ System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), que se reemplaza por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1855d-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="1855d-107">Sin embargo, puede invocar solo esos cmdlets que se derivan directamente de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase.</span><span class="sxs-lookup"><span data-stu-id="1855d-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="1855d-108">No se puede invocar un cmdlet que se deriva el [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase.</span><span class="sxs-lookup"><span data-stu-id="1855d-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="1855d-109">El [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método tiene las siguientes variantes.</span><span class="sxs-lookup"><span data-stu-id="1855d-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="1855d-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) esta variante invoca el objeto de cmdlet y devuelve una colección de objetos de tipo "T".</span><span class="sxs-lookup"><span data-stu-id="1855d-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="1855d-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) esta variante invoca el objeto de cmdlet y devuelve un emumerator fuertemente tipado.</span><span class="sxs-lookup"><span data-stu-id="1855d-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="1855d-112">Esta variante permite al usuario utilizar los objetos en la colección para realizar las operaciones personalizadas.</span><span class="sxs-lookup"><span data-stu-id="1855d-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="1855d-113">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="1855d-113">Examples</span></span>

|<span data-ttu-id="1855d-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="1855d-114">Example</span></span>|<span data-ttu-id="1855d-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="1855d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1855d-116">Invocar Cmdlets dentro de un Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1855d-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="1855d-117">En este ejemplo se muestra cómo invocar un cmdlet desde dentro de otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1855d-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="1855d-118">Invocar Scripts dentro de un Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1855d-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="1855d-119">En este ejemplo se muestra cómo invocar un script que se proporciona para el cmdlet desde dentro de otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1855d-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="1855d-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="1855d-120">See Also</span></span>

[<span data-ttu-id="1855d-121">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1855d-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
