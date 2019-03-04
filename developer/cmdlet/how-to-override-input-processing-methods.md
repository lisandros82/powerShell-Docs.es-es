---
title: Cómo invalidar los métodos de procesamiento de entrada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: eff40a01b60985788ae0e21156fec7ec4e27fcf1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855921"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="7b26b-102">Cómo invalidar los métodos de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="7b26b-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="7b26b-103">Estos ejemplos muestran cómo sobrescribir los métodos dentro de un cmdlet de procesamiento de entrada.</span><span class="sxs-lookup"><span data-stu-id="7b26b-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="7b26b-104">Estos métodos se usan para realizar las siguientes operaciones:</span><span class="sxs-lookup"><span data-stu-id="7b26b-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="7b26b-105">El [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método se utiliza para realizar operaciones de inicio de un solo uso que son válidas para todos los objetos procesados por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7b26b-105">The [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="7b26b-106">El tiempo de ejecución de Windows PowerShell llama a este método solo una vez.</span><span class="sxs-lookup"><span data-stu-id="7b26b-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="7b26b-107">El [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método se utiliza para procesar los objetos que se pasa al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7b26b-107">The [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="7b26b-108">El tiempo de ejecución de Windows PowerShell, llama a este método para cada objeto que se pasa al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7b26b-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="7b26b-109">El [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método se usa para realizar las operaciones de procesamiento de un solo uso posterior.</span><span class="sxs-lookup"><span data-stu-id="7b26b-109">The [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="7b26b-110">El tiempo de ejecución de Windows PowerShell llama a este método solo una vez.</span><span class="sxs-lookup"><span data-stu-id="7b26b-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="7b26b-111">Para invalidar el método BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="7b26b-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="7b26b-112">Declare un reemplazo protegido de la [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="7b26b-112">Declare a protected override of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="7b26b-113">La clase siguiente imprime un mensaje de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="7b26b-113">The following class prints a sample message.</span></span> <span data-ttu-id="7b26b-114">Para usar esta clase, cambie el verbo y sustantivo en el atributo de Cmdlet, cambie el nombre de la clase para reflejar el nuevo verbo y sustantivo y, a continuación, agregar la funcionalidad que necesita para invalidar el [System.Management.Automation.Cmdlet.Beginprocessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="7b26b-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="7b26b-115">Para invalidar el método ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="7b26b-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="7b26b-116">Declare un reemplazo protegido de la [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="7b26b-116">Declare a protected override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="7b26b-117">La clase siguiente imprime un mensaje de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="7b26b-117">The following class prints a sample message.</span></span> <span data-ttu-id="7b26b-118">Para usar esta clase, cambie el verbo y sustantivo en el atributo de Cmdlet, cambie el nombre de la clase para reflejar el nuevo verbo y sustantivo y, a continuación, agregar la funcionalidad que necesita para invalidar el [System.Management.Automation.Cmdlet.Processrecord\* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.</span><span class="sxs-lookup"><span data-stu-id="7b26b-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="7b26b-119">Para invalidar el método EndProcessing</span><span class="sxs-lookup"><span data-stu-id="7b26b-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="7b26b-120">Declare un reemplazo protegido de la [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="7b26b-120">Declare a protected override of the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="7b26b-121">La clase siguiente imprime un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="7b26b-121">The following class prints a sample.</span></span> <span data-ttu-id="7b26b-122">Para usar esta clase, cambie el verbo y sustantivo en el atributo de Cmdlet, cambie el nombre de la clase para reflejar el nuevo verbo y sustantivo y, a continuación, agregar la funcionalidad que necesita para invalidar el [System.Management.Automation.Cmdlet.Endprocessing\* ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.</span><span class="sxs-lookup"><span data-stu-id="7b26b-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a><span data-ttu-id="7b26b-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="7b26b-123">See Also</span></span>

[<span data-ttu-id="7b26b-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="7b26b-124">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="7b26b-125">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="7b26b-125">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="7b26b-126">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="7b26b-126">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="7b26b-127">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7b26b-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
