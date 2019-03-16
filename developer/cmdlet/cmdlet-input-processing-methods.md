---
title: Métodos de procesamiento de entrada de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: 065214647dfa6d376b727930fe75140911095faf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059378"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="f9e54-102">Métodos de procesamiento de entrada del cmdlet</span><span class="sxs-lookup"><span data-stu-id="f9e54-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="f9e54-103">Los cmdlets deben invalidar uno o varios de los métodos descritos en este tema para realizar su trabajo de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="f9e54-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="f9e54-104">Estos métodos permiten que el cmdlet realizar el preprocesamiento operaciones, entrada las operaciones de procesamiento y las operaciones de procesamiento posterior a la.</span><span class="sxs-lookup"><span data-stu-id="f9e54-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="f9e54-105">Estos métodos también permiten detener el procesamiento de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9e54-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="f9e54-106">Tareas previas a procesamiento</span><span class="sxs-lookup"><span data-stu-id="f9e54-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="f9e54-107">¿Los cmdlets deben reemplazar el [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método para agregar las operaciones de preprocesamiento que son válidas para todos los registros que se procesarán más adelante mediante el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9e54-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="f9e54-108">Cuando Windows PowerShell procesa una canalización de comandos, Windows PowerShell llama a este método una vez para cada instancia del cmdlet en la canalización.</span><span class="sxs-lookup"><span data-stu-id="f9e54-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="f9e54-109">Para obtener más información acerca de cómo Windows PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="f9e54-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="f9e54-110">¿El código siguiente muestra una implementación de la [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="f9e54-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

<span data-ttu-id="f9e54-111">¿Para obtener un ejemplo más detallado de cómo usar el [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f9e54-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="f9e54-112">¿En este tutorial, el **seleccione Str** cmdlet usa el [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método para generar la expresión regular que se usa para buscar los registros de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="f9e54-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="f9e54-113">Las tareas de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="f9e54-113">Input Processing Tasks</span></span>

<span data-ttu-id="f9e54-114">¿Cmdlets puede invalidar el [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método para procesar la entrada que se envía al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9e54-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="f9e54-115">Cuando Windows PowerShell procesa una canalización de comandos, Windows PowerShell llama a este método para cada registro de entrada que se procesa mediante el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9e54-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="f9e54-116">Para obtener más información acerca de cómo Windows PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="f9e54-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="f9e54-117">¿El código siguiente muestra una implementación de la [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="f9e54-117">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

<span data-ttu-id="f9e54-118">¿Para obtener un ejemplo más detallado de cómo usar el [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f9e54-118">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="f9e54-119">Tareas posteriores al procesamiento</span><span class="sxs-lookup"><span data-stu-id="f9e54-119">Post-Processing Tasks</span></span>

<span data-ttu-id="f9e54-120">¿Los cmdlets deben reemplazar el [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método para agregar las operaciones posteriores al procesamiento que son válidas para todos los registros que se han procesado por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9e54-120">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="f9e54-121">Por ejemplo, podría tener su cmdlet limpiar las variables de objeto cuando finalice de procesamiento.</span><span class="sxs-lookup"><span data-stu-id="f9e54-121">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="f9e54-122">Cuando Windows PowerShell procesa una canalización de comandos, Windows PowerShell llama a este método una vez para cada instancia del cmdlet en la canalización.</span><span class="sxs-lookup"><span data-stu-id="f9e54-122">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="f9e54-123">¿Sin embargo, es importante recordar que el tiempo de ejecución de Windows PowerShell no llame a la [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método si el cmdlet se cancela a medio camino a través de su procesamiento de entrada o si un carácter de terminación se produce error en cualquier parte del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9e54-123">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="f9e54-124">Por este motivo, un cmdlet que requiere la limpieza de objetos debe implementar toda [System.IDisposable](/dotnet/api/System.IDisposable) patrón, incluyendo un finalizador, de modo que el tiempo de ejecución puede llamar a ambos el [ ¿System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) y [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) métodos al final del procesamiento.</span><span class="sxs-lookup"><span data-stu-id="f9e54-124">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="f9e54-125">Para obtener más información acerca de cómo Windows PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="f9e54-125">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="f9e54-126">¿El código siguiente muestra una implementación de la [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.</span><span class="sxs-lookup"><span data-stu-id="f9e54-126">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

<span data-ttu-id="f9e54-127">¿Para obtener un ejemplo más detallado de cómo usar el [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f9e54-127">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9e54-128">Véase también</span><span class="sxs-lookup"><span data-stu-id="f9e54-128">See Also</span></span>

[<span data-ttu-id="f9e54-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="f9e54-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="f9e54-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="f9e54-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="f9e54-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="f9e54-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="f9e54-132">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="f9e54-132">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="f9e54-133">Shell de SDK de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f9e54-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
