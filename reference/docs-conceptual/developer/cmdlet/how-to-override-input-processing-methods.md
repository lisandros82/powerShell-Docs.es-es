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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364474"
---
# <a name="how-to-override-input-processing-methods"></a>Cómo invalidar los métodos de procesamiento de entrada

En estos ejemplos se muestra cómo sobrescribir los métodos de procesamiento de entrada dentro de un cmdlet. Estos métodos se utilizan para realizar las operaciones siguientes:

- El método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) se usa para realizar operaciones de inicio único que son válidas para todos los objetos procesados por el cmdlet. El tiempo de ejecución de Windows PowerShell llama a este método solo una vez.

- El método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) se usa para procesar los objetos que se pasan al cmdlet. El tiempo de ejecución de Windows PowerShell llama a este método para cada objeto que se pasa al cmdlet.

- El método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) se usa para realizar operaciones de procesamiento posteriores de un solo uso. El tiempo de ejecución de Windows PowerShell llama a este método solo una vez.

## <a name="to-override-the-beginprocessing-method"></a>Para invalidar el método BeginProcessing

- Declare una invalidación protegida del método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .

La siguiente clase imprime un mensaje de ejemplo. Para usar esta clase, cambie el verbo y el sustantivo en el atributo del cmdlet, cambie el nombre de la clase para que refleje el nuevo verbo y el nombre y, a continuación, agregue la funcionalidad que necesita para la invalidación de [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) forma.

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

## <a name="to-override-the-processrecord-method"></a>Para invalidar el método ProcessRecord

- Declare una invalidación protegida del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

La siguiente clase imprime un mensaje de ejemplo. Para usar esta clase, cambie el verbo y el sustantivo en el atributo del cmdlet, cambie el nombre de la clase para que refleje el nuevo verbo y el nombre y, a continuación, agregue la funcionalidad que necesita para la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .

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

## <a name="to-override-the-endprocessing-method"></a>Para reemplazar el método EndProcessing

- Declare una invalidación protegida del método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .

La siguiente clase imprime un ejemplo. Para usar esta clase, cambie el verbo y el sustantivo en el atributo del cmdlet, cambie el nombre de la clase para que refleje el nuevo verbo y el nombre y, a continuación, agregue la funcionalidad que necesita para la invalidación del método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .

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

## <a name="see-also"></a>Véase también

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
