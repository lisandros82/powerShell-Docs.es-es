---
title: Métodos de procesamiento de entrada de cmdlets | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369874"
---
# <a name="cmdlet-input-processing-methods"></a>Métodos de procesamiento de entrada del cmdlet

Los cmdlets deben invalidar uno o más de los métodos de procesamiento de entrada que se describen en este tema para realizar su trabajo.
Estos métodos permiten que el cmdlet realice operaciones de procesamiento previo, procesamiento de entrada y procesamiento posterior.
Estos métodos también permiten detener el procesamiento de los cmdlets.
Para obtener un ejemplo más detallado sobre cómo usar estos métodos, vea el [tutorial de SelectStr](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>Operaciones previas al procesamiento

Los cmdlets deben invalidar el método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) para agregar las operaciones de preprocesamiento que sean válidas para todos los registros que se procesarán posteriormente mediante el cmdlet.
Cuando PowerShell procesa una canalización de comandos, PowerShell llama a este método una vez por cada instancia del cmdlet en la canalización.
Para obtener más información sobre cómo PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de cmdlets](/previous-versions/ms714429(v=vs.85)).

En el código siguiente se muestra una implementación del método BeginProcessing.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Operaciones de procesamiento de entrada

Los cmdlets pueden invalidar el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) para procesar la entrada que se envía al cmdlet.
Cuando PowerShell procesa una canalización de comandos, PowerShell llama a este método para cada registro de entrada que el cmdlet procesa.
Para obtener más información sobre cómo PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de cmdlets](/previous-versions/ms714429(v=vs.85)).

En el código siguiente se muestra una implementación del método ProcessRecord.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Operaciones posteriores al procesamiento

Los cmdlets deben invalidar el método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) para agregar las operaciones posteriores al procesamiento que sean válidas para todos los registros procesados por el cmdlet.
Por ejemplo, es posible que el cmdlet tenga que limpiar las variables de objeto una vez finalizado el procesamiento.

Cuando PowerShell procesa una canalización de comandos, PowerShell llama a este método una vez por cada instancia del cmdlet en la canalización.
Sin embargo, es importante recordar que el tiempo de ejecución de PowerShell no llamará al método EndProcessing si el cmdlet se cancela a lo largo de su procesamiento de entrada o si se produce un error de terminación en cualquier parte del cmdlet.
Por esta razón, un cmdlet que requiere la limpieza de objetos debe implementar el patrón [System. IDisposable](/dotnet/api/System.IDisposable) completo, incluido un finalizador, de modo que el tiempo de ejecución pueda llamar a los métodos EndProcessing y [System. IDisposable. Dispose](/dotnet/api/System.IDisposable.Dispose) al final del procesamiento.
Para obtener más información sobre cómo PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de cmdlets](/previous-versions/ms714429(v=vs.85)).

En el código siguiente se muestra una implementación del método EndProcessing.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Véase también

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Tutorial de SelectStr](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[SDK de Windows PowerShell Shell](../windows-powershell-reference.md)
