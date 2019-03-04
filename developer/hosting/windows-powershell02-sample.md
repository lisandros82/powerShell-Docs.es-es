---
title: Ejemplo de Windows PowerShell02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861071"
---
# <a name="windows-powershell02-sample"></a>Ejemplo Windows PowerShell02

Este ejemplo muestra cómo ejecutar comandos de forma asincrónica mediante el uso de los espacios de ejecución de un grupo de espacio de ejecución. El ejemplo genera una lista de comandos y, a continuación, ejecuta esos comandos mientras el motor de Windows PowerShell abre un espacio de ejecución de la agrupación cuando sea necesario.

## <a name="requirements"></a>Requisitos

- Este ejemplo requiere Windows PowerShell 2.0.

## <a name="demonstrates"></a>Demostraciones

Este ejemplo muestra lo siguiente:

- Creación de un objeto RunspacePool con un número mínimo y máximo de espacios de ejecución pueda estar abiertos al mismo tiempo.

- Creación de una lista de comandos.

- Ejecute los comandos de forma asincrónica.

- Una llamada a la [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) método para ver cuántos espacios de ejecución son gratuitas.

- Capturar la salida del comando con el [System.Management.Automation.Powershell.Endinvoke*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.

## <a name="example"></a>Ejemplo

Este ejemplo muestra cómo abrir los espacios de ejecución de un grupo de espacio de ejecución y cómo ejecutar de forma asincrónica comandos en esos espacios de ejecución.

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a>Véase también

[Escribir una aplicación de Host de PowerShell de Windows](./writing-a-windows-powershell-host-application.md)