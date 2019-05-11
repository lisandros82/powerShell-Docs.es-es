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
# <a name="cmdlet-input-processing-methods"></a>Métodos de procesamiento de entrada del cmdlet

Los cmdlets deben invalidar uno o varios de los métodos descritos en este tema para realizar su trabajo de procesamiento de entrada.
Estos métodos permiten que el cmdlet realizar operaciones de procesamiento previo, procesamiento de entrada y el procesamiento posterior.
Estos métodos también permiten detener el procesamiento de cmdlet.
Para obtener un ejemplo más detallado de cómo usar estos métodos, consulte [SelectStr Tutorial](selectstr-tutorial.md).

## <a name="pre-processing-operations"></a>Operaciones previas al procesamiento

Los cmdlets deben reemplazar el [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método para agregar las operaciones de preprocesamiento que son válidas para todos los registros que se procesarán más adelante mediante el cmdlet.
Cuando PowerShell procesa una canalización de comandos, PowerShell llama a este método una vez para cada instancia del cmdlet en la canalización.
Para obtener más información acerca de cómo PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](/previous-versions/ms714429(v=vs.85)).

El código siguiente muestra una implementación del método BeginProcessing.

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a>Las operaciones de procesamiento de entrada

Cmdlets puede invalidar el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método para procesar la entrada que se envía al cmdlet.
Cuando PowerShell procesa una canalización de comandos, PowerShell llama a este método para cada registro de entrada que se procesa mediante el cmdlet.
Para obtener más información acerca de cómo PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](/previous-versions/ms714429(v=vs.85)).

El código siguiente muestra una implementación del método ProcessRecord.

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a>Operaciones posteriores al procesamiento

Los cmdlets deben reemplazar el [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método para agregar las operaciones posteriores al procesamiento que son válidas para todos los registros que se han procesado por el cmdlet.
Por ejemplo, podría tener su cmdlet limpiar las variables de objeto cuando finalice de procesamiento.

Cuando PowerShell procesa una canalización de comandos, PowerShell llama a este método una vez para cada instancia del cmdlet en la canalización.
Sin embargo, es importante recordar que el tiempo de ejecución de PowerShell no llamará al método EndProcessing si se ha cancelado el cmdlet a medio camino a través de su procesamiento de entrada o si se produce un error de terminación en cualquier parte del cmdlet.
Por este motivo, un cmdlet que requiere la limpieza de objetos debe implementar toda [System.IDisposable](/dotnet/api/System.IDisposable) patrón, incluyendo un finalizador, de modo que el tiempo de ejecución puede llamar a ambos el EndProcessing y [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) métodos al final del procesamiento.
Para obtener más información acerca de cómo PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](/previous-versions/ms714429(v=vs.85)).

El código siguiente muestra una implementación del método EndProcessing.

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a>Véase también

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Tutorial de SelectStr](selectstr-tutorial.md)

[System.IDisposable](/dotnet/api/System.IDisposable)

[Shell de SDK de Windows PowerShell](../windows-powershell-reference.md)
