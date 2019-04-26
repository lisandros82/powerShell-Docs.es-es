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
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067950"
---
# <a name="how-to-override-input-processing-methods"></a>Cómo invalidar los métodos de procesamiento de entrada

Estos ejemplos muestran cómo sobrescribir los métodos dentro de un cmdlet de procesamiento de entrada. Estos métodos se usan para realizar las siguientes operaciones:

- El [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método se utiliza para realizar operaciones de inicio de un solo uso que son válidas para todos los objetos procesados por el cmdlet. El tiempo de ejecución de Windows PowerShell llama a este método solo una vez.

- El [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método se utiliza para procesar los objetos que se pasa al cmdlet. El tiempo de ejecución de Windows PowerShell, llama a este método para cada objeto que se pasa al cmdlet.

- El [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método se usa para realizar las operaciones de procesamiento de un solo uso posterior. El tiempo de ejecución de Windows PowerShell llama a este método solo una vez.

## <a name="to-override-the-beginprocessing-method"></a>Para invalidar el método BeginProcessing

- Declare un reemplazo protegido de la [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método.

La clase siguiente imprime un mensaje de ejemplo. Para usar esta clase, cambie el verbo y sustantivo en el atributo de Cmdlet, cambie el nombre de la clase para reflejar el nuevo verbo y sustantivo y, a continuación, agregar la funcionalidad que necesita para invalidar el [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método.

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

- Declare un reemplazo protegido de la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

La clase siguiente imprime un mensaje de ejemplo. Para usar esta clase, cambie el verbo y sustantivo en el atributo de Cmdlet, cambie el nombre de la clase para reflejar el nuevo verbo y sustantivo y, a continuación, agregar la funcionalidad que necesita para invalidar el [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método.

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

## <a name="to-override-the-endprocessing-method"></a>Para invalidar el método EndProcessing

- Declare un reemplazo protegido de la [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.

La clase siguiente imprime un ejemplo. Para usar esta clase, cambie el verbo y sustantivo en el atributo de Cmdlet, cambie el nombre de la clase para reflejar el nuevo verbo y sustantivo y, a continuación, agregar la funcionalidad que necesita para invalidar el [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método.

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

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
