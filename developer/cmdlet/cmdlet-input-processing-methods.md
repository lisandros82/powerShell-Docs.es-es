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
ms.openlocfilehash: 7f8d25e03707052b1d5b62e245caae360da11d0b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794950"
---
# <a name="cmdlet-input-processing-methods"></a>Métodos de procesamiento de entrada del cmdlet

Los cmdlets deben invalidar uno o varios de los métodos descritos en este tema para realizar su trabajo de procesamiento de entrada. Estos métodos permiten que el cmdlet realizar el preprocesamiento operaciones, entrada las operaciones de procesamiento y las operaciones de procesamiento posterior a la. Estos métodos también permiten detener el procesamiento de cmdlet.

## <a name="pre-processing-tasks"></a>Tareas previas a procesamiento

¿Los cmdlets deben reemplazar el [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método para agregar las operaciones de preprocesamiento que son válidas para todos los registros que se procesarán más adelante mediante el cmdlet. Cuando Windows PowerShell procesa una canalización de comandos, Windows PowerShell llama a este método una vez para cada instancia del cmdlet en la canalización. Para obtener más información acerca de cómo Windows PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

¿El código siguiente muestra una implementación de la [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método.

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

¿Para obtener un ejemplo más detallado de cómo usar el [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md). ¿En este tutorial, el **seleccione Str** cmdlet usa el [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) método para generar la expresión regular que se usa para buscar los registros de procesamiento de entrada.

## <a name="input-processing-tasks"></a>Las tareas de procesamiento de entrada

¿Cmdlets puede invalidar el [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método para procesar la entrada que se envía al cmdlet. Cuando Windows PowerShell procesa una canalización de comandos, Windows PowerShell llama a este método para cada registro de entrada que se procesa mediante el cmdlet. Para obtener más información acerca de cómo Windows PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

¿El código siguiente muestra una implementación de la [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.

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

¿Para obtener un ejemplo más detallado de cómo usar el [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).

## <a name="post-processing-tasks"></a>Tareas posteriores al procesamiento

¿Los cmdlets deben reemplazar el [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método para agregar las operaciones posteriores al procesamiento que son válidas para todos los registros que se han procesado por el cmdlet. Por ejemplo, podría tener su cmdlet limpiar las variables de objeto cuando finalice de procesamiento.

Cuando Windows PowerShell procesa una canalización de comandos, Windows PowerShell llama a este método una vez para cada instancia del cmdlet en la canalización. ¿Sin embargo, es importante recordar que el tiempo de ejecución de Windows PowerShell no llame a la [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) método si el cmdlet se cancela a medio camino a través de su procesamiento de entrada o si un carácter de terminación se produce error en cualquier parte del cmdlet. Por este motivo, un cmdlet que requiere la limpieza de objetos debe implementar toda [System.Idisposable](/dotnet/api/System.IDisposable) patrón, incluyendo un finalizador, de modo que el tiempo de ejecución puede llamar a ambos el [ ¿System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) y [System.Idisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) métodos al final del procesamiento. Para obtener más información acerca de cómo Windows PowerShell invoca la canalización de comandos, consulte [ciclo de vida de procesamiento de Cmdlet](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).

¿El código siguiente muestra una implementación de la [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método.

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

¿Para obtener un ejemplo más detallado de cómo usar el [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) método, consulte [SelectStr Tutorial](./selectstr-tutorial.md).

## <a name="see-also"></a>Véase también

[System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[System.Idisposable](/dotnet/api/System.IDisposable)

[Shell de SDK de Windows PowerShell](../windows-powershell-reference.md)
