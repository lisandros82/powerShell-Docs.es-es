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
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Invocación de los cmdlets y los scripts dentro de un cmdlet

Un cmdlet puede invocar otros cmdlets y scripts en el método del cmdlet de procesamiento de entrada. Esto le permite agregar la funcionalidad de los cmdlets existentes y las secuencias de comandos al cmdlet sin tener que volver a escribir el código.

## <a name="the-invoke-method"></a>El método de invocación

Todos los cmdlets puede invocar un cmdlet existente mediante una llamada a la [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método dentro de una entrada de procesamiento de método, como [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), que se reemplaza por el cmdlet. Sin embargo, puede invocar solo esos cmdlets que se derivan directamente de la [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase. No se puede invocar un cmdlet que se deriva el [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase.

El [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) método tiene las siguientes variantes.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) esta variante invoca el objeto de cmdlet y devuelve una colección de objetos de tipo "T".

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) esta variante invoca el objeto de cmdlet y devuelve un emumerator fuertemente tipado. Esta variante permite al usuario utilizar los objetos en la colección para realizar las operaciones personalizadas.

## <a name="examples"></a>Ejemplos

|Ejemplo|Descripción|
|-------------|-----------------|
|[Invocar Cmdlets dentro de un Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|En este ejemplo se muestra cómo invocar un cmdlet desde dentro de otro cmdlet.|
|[Invocar Scripts dentro de un Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|En este ejemplo se muestra cómo invocar un script que se proporciona para el cmdlet desde dentro de otro cmdlet.|

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
