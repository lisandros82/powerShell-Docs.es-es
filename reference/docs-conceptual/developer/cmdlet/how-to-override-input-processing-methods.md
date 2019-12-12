---
title: Cómo invalidar métodos de procesamiento de entrada | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364474"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="596ae-102">Cómo invalidar los métodos de procesamiento de entrada</span><span class="sxs-lookup"><span data-stu-id="596ae-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="596ae-103">En estos ejemplos se muestra cómo sobrescribir los métodos de procesamiento de entrada dentro de un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="596ae-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="596ae-104">Estos métodos se utilizan para realizar las operaciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="596ae-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="596ae-105">El método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) se usa para realizar operaciones de inicio único que son válidas para todos los objetos procesados por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="596ae-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="596ae-106">El tiempo de ejecución de Windows PowerShell llama a este método solo una vez.</span><span class="sxs-lookup"><span data-stu-id="596ae-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="596ae-107">El método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) se usa para procesar los objetos que se pasan al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="596ae-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="596ae-108">El tiempo de ejecución de Windows PowerShell llama a este método para cada objeto que se pasa al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="596ae-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="596ae-109">El método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) se usa para realizar operaciones de procesamiento posteriores de un solo uso.</span><span class="sxs-lookup"><span data-stu-id="596ae-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="596ae-110">El tiempo de ejecución de Windows PowerShell llama a este método solo una vez.</span><span class="sxs-lookup"><span data-stu-id="596ae-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="596ae-111">Para invalidar el método BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="596ae-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="596ae-112">Declare una invalidación protegida del método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .</span><span class="sxs-lookup"><span data-stu-id="596ae-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="596ae-113">La siguiente clase imprime un mensaje de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="596ae-113">The following class prints a sample message.</span></span> <span data-ttu-id="596ae-114">Para usar esta clase, cambie el verbo y el sustantivo en el atributo del cmdlet, cambie el nombre de la clase para que refleje el nuevo verbo y el nombre y, a continuación, agregue la funcionalidad que necesita para la invalidación del método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .</span><span class="sxs-lookup"><span data-stu-id="596ae-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

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

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="596ae-115">Para invalidar el método ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="596ae-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="596ae-116">Declare una invalidación protegida del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="596ae-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="596ae-117">La siguiente clase imprime un mensaje de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="596ae-117">The following class prints a sample message.</span></span> <span data-ttu-id="596ae-118">Para usar esta clase, cambie el verbo y el sustantivo en el atributo del cmdlet, cambie el nombre de la clase para que refleje el nuevo verbo y el nombre y, a continuación, agregue la funcionalidad que necesita para la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="596ae-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

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

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="596ae-119">Para reemplazar el método EndProcessing</span><span class="sxs-lookup"><span data-stu-id="596ae-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="596ae-120">Declare una invalidación protegida del método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="596ae-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="596ae-121">La siguiente clase imprime un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="596ae-121">The following class prints a sample.</span></span> <span data-ttu-id="596ae-122">Para usar esta clase, cambie el verbo y el sustantivo en el atributo del cmdlet, cambie el nombre de la clase para que refleje el nuevo verbo y el nombre y, a continuación, agregue la funcionalidad que necesita para la invalidación del método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="596ae-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="596ae-123">Véase también</span><span class="sxs-lookup"><span data-stu-id="596ae-123">See Also</span></span>

[<span data-ttu-id="596ae-124">System. Management. Automation. cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="596ae-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="596ae-125">System. Management. Automation. cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="596ae-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="596ae-126">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="596ae-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="596ae-127">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="596ae-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
