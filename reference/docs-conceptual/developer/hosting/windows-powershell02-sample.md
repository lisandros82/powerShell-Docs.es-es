---
title: Ejemplo de PowerShell02 de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: db7ff3a2dbd92f562379d206db494ab92ef08736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367304"
---
# <a name="windows-powershell02-sample"></a>Ejemplo Windows PowerShell02

En este ejemplo se muestra cómo ejecutar comandos de forma asincrónica mediante los espacios de ejecución de un grupo de espacio de ejecución. En el ejemplo se genera una lista de comandos y, a continuación, se ejecutan esos comandos mientras el motor de Windows PowerShell abre un espacio de ejecución desde el grupo cuando es necesario.

## <a name="requirements"></a>Requisitos

- Este ejemplo requiere Windows PowerShell 2,0.

## <a name="demonstrates"></a>Demuestra

Este ejemplo muestra lo siguiente:

- Crear un objeto RunspacePool con un número mínimo y máximo de espacios de tiempo permitidos que estén abiertos al mismo tiempo.

- Crear una lista de comandos.

- Ejecutar los comandos de forma asincrónica.

- Llamada al método [System. Management. Automation. espacios de Runspacepool. Getavailablerunspaces *](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) para ver cuántos espacios de administración son gratis.

- Capturar la salida del comando con el método [System. Management. Automation. PowerShell. EndInvoke *](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo abrir los espacios de ejecución de un grupo de espacio de ejecución y cómo ejecutar comandos de forma asincrónica en esos espacios de ejecución.

[!code-csharp[PowerShell02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Véase también

[Escritura de una aplicación host de Windows PowerShell](./writing-a-windows-powershell-host-application.md)
