---
title: Invocar cmdlets y scripts dentro de un cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364294"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Invocación de los cmdlets y los scripts dentro de un cmdlet

Un cmdlet puede invocar otros cmdlets y scripts desde el método de procesamiento de entrada del cmdlet. Esto le permite agregar la funcionalidad de los cmdlets y scripts existentes a su cmdlet sin tener que volver a escribir el código.

## <a name="the-invoke-method"></a>Método Invoke

Todos los cmdlets pueden invocar un cmdlet existente llamando al método [System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) desde dentro de un método de procesamiento de entrada, como [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), que es reemplazado por el cmdlet. Sin embargo, solo puede invocar los cmdlets que derivan directamente de la clase [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . No se puede invocar un cmdlet derivado de la clase [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .

El método [System. Management. Automation. cmdlet. Invoke *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) tiene las siguientes variantes.

[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) esta variante invoca el objeto de cmdlet y devuelve una colección de objetos de tipo "T".

[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) esta variante invoca el objeto de cmdlet y devuelve un emumerator fuertemente tipado. Esta variante permite al usuario utilizar los objetos de la colección para realizar operaciones personalizadas.

## <a name="examples"></a>Ejemplos

|Ejemplo|Descripción|
|-------------|-----------------|
|[Invocar cmdlets dentro de un cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|En este ejemplo se muestra cómo invocar un cmdlet desde otro cmdlet.|
|[Invocar scripts dentro de un cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|En este ejemplo se muestra cómo invocar un script que se proporciona al cmdlet desde otro cmdlet.|

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
