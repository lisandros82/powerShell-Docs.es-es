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
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670306"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="81c3d-102">Métodos de procesamiento de entrada del cmdlet</span><span class="sxs-lookup"><span data-stu-id="81c3d-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="81c3d-103">Los cmdlets deben invalidar uno o varios de los métodos descritos en este tema para realizar su trabajo de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="81c3d-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="81c3d-104">Estos métodos permiten que el cmdlet realizar operaciones de procesamiento previo, procesamiento de entrada y el procesamiento posterior.</span><span class="sxs-lookup"><span data-stu-id="81c3d-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="81c3d-105">Estos métodos también permiten detener el procesamiento de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="81c3d-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="81c3d-106">Para obtener un ejemplo más detallado de cómo usar estos métodos, consulte [SelectStr Tutorial](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="81c3d-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="81c3d-107">Operaciones previas al procesamiento</span><span class="sxs-lookup"><span data-stu-id="81c3d-107">Pre-Processing Operations</span></span>

<span data-ttu-id="81c3d-108">Los cmdlets deben reemplazar el [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método para agregar las operaciones de preprocesamiento que son válidas para todos los registros que se procesarán más adelante mediante el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="81c3d-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="81c3d-109">Cuando PowerShell procesa una canalización de comandos, PowerShell llama a este método una vez para cada instancia del cmdlet en la canalización.</span><span class="sxs-lookup"><span data-stu-id="81c3d-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="81c3d-110">Para obtener más información acerca de cómo PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="81c3d-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="81c3d-111">El código siguiente muestra una implementación del método BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="81c3d-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="81c3d-112">Las operaciones de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="81c3d-112">Input Processing Operations</span></span>

<span data-ttu-id="81c3d-113">Cmdlets puede invalidar el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para procesar la entrada que se envía al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="81c3d-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="81c3d-114">Cuando PowerShell procesa una canalización de comandos, PowerShell llama a este método para cada registro de entrada que se procesa mediante el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="81c3d-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="81c3d-115">Para obtener más información acerca de cómo PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="81c3d-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="81c3d-116">El código siguiente muestra una implementación del método ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="81c3d-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="81c3d-117">Operaciones posteriores al procesamiento</span><span class="sxs-lookup"><span data-stu-id="81c3d-117">Post-Processing Operations</span></span>

<span data-ttu-id="81c3d-118">Los cmdlets deben reemplazar el [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método para agregar las operaciones posteriores al procesamiento que son válidas para todos los registros que se han procesado por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="81c3d-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="81c3d-119">Por ejemplo, podría tener su cmdlet limpiar las variables de objeto cuando finalice de procesamiento.</span><span class="sxs-lookup"><span data-stu-id="81c3d-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="81c3d-120">Cuando PowerShell procesa una canalización de comandos, PowerShell llama a este método una vez para cada instancia del cmdlet en la canalización.</span><span class="sxs-lookup"><span data-stu-id="81c3d-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="81c3d-121">Sin embargo, es importante recordar que el tiempo de ejecución de PowerShell no llamará al método EndProcessing si se ha cancelado el cmdlet a medio camino a través de su procesamiento de entrada o si se produce un error de terminación en cualquier parte del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="81c3d-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="81c3d-122">Por este motivo, un cmdlet que requiere la limpieza de objetos debe implementar toda [System.IDisposable](/dotnet/api/System.IDisposable) patrón, incluyendo un finalizador, de modo que el tiempo de ejecución puede llamar a ambos el EndProcessing y [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) métodos al final del procesamiento.</span><span class="sxs-lookup"><span data-stu-id="81c3d-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="81c3d-123">Para obtener más información acerca de cómo PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="81c3d-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="81c3d-124">El código siguiente muestra una implementación del método EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="81c3d-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="81c3d-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="81c3d-125">See Also</span></span>

[<span data-ttu-id="81c3d-126">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="81c3d-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="81c3d-127">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="81c3d-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="81c3d-128">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="81c3d-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="81c3d-129">Tutorial de SelectStr</span><span class="sxs-lookup"><span data-stu-id="81c3d-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="81c3d-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="81c3d-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="81c3d-131">Shell de SDK de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="81c3d-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
