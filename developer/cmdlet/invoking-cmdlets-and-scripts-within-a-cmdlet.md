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
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067678"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="0e447-102">Invocación de los cmdlets y los scripts dentro de un cmdlet</span><span class="sxs-lookup"><span data-stu-id="0e447-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="0e447-103">Un cmdlet puede invocar otros cmdlets y scripts en el método del cmdlet de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="0e447-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="0e447-104">Esto le permite agregar la funcionalidad de los cmdlets existentes y las secuencias de comandos al cmdlet sin tener que volver a escribir el código.</span><span class="sxs-lookup"><span data-stu-id="0e447-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="0e447-105">El método de invocación</span><span class="sxs-lookup"><span data-stu-id="0e447-105">The Invoke Method</span></span>

<span data-ttu-id="0e447-106">Todos los cmdlets puede invocar un cmdlet existente mediante una llamada a la [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método dentro de una entrada de procesamiento de método, como [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), que se reemplaza por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0e447-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="0e447-107">Sin embargo, puede invocar solo esos cmdlets que se derivan directamente de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase.</span><span class="sxs-lookup"><span data-stu-id="0e447-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="0e447-108">No se puede invocar un cmdlet que se deriva el [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase.</span><span class="sxs-lookup"><span data-stu-id="0e447-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="0e447-109">El [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método tiene las siguientes variantes.</span><span class="sxs-lookup"><span data-stu-id="0e447-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="0e447-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) esta variante invoca el objeto de cmdlet y devuelve una colección de objetos de tipo "T".</span><span class="sxs-lookup"><span data-stu-id="0e447-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="0e447-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) esta variante invoca el objeto de cmdlet y devuelve un emumerator fuertemente tipado.</span><span class="sxs-lookup"><span data-stu-id="0e447-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="0e447-112">Esta variante permite al usuario utilizar los objetos en la colección para realizar las operaciones personalizadas.</span><span class="sxs-lookup"><span data-stu-id="0e447-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="0e447-113">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="0e447-113">Examples</span></span>

|<span data-ttu-id="0e447-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0e447-114">Example</span></span>|<span data-ttu-id="0e447-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="0e447-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e447-116">Invocar Cmdlets dentro de un Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0e447-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="0e447-117">En este ejemplo se muestra cómo invocar un cmdlet desde dentro de otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0e447-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="0e447-118">Invocar Scripts dentro de un Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0e447-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="0e447-119">En este ejemplo se muestra cómo invocar un script que se proporciona para el cmdlet desde dentro de otro cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0e447-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="0e447-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="0e447-120">See Also</span></span>

[<span data-ttu-id="0e447-121">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e447-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
