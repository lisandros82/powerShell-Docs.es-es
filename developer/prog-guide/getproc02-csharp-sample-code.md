---
title: GetProc02 (C#) código de ejemplo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 740e8d60b71654b82020d16b2964165f3ee1e600
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862311"
---
# <a name="getproc02-c-sample-code"></a>Código de ejemplo GetProc02 (C#)

El código siguiente muestra la implementación de un `Get-Process` cmdlet que acepta la entrada de línea de comandos. Tenga en cuenta que esta implementación define un `Name` parámetro para permitir la entrada de línea de comandos y lo utiliza el [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como salida mecanismo para enviar el resultado de los objetos a la canalización.

## <a name="code-sample"></a>Ejemplo de código

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a>Véase también

[Windows PowerShell SDK](../windows-powershell-reference.md)