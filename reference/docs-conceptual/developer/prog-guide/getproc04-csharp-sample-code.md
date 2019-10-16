---
title: Código deC#ejemplo de GetProc04 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 439ba3f3-91b1-46a4-8d07-9af6edb71bc4
caps.latest.revision: 5
ms.openlocfilehash: e8d9ae69c0d9da23b3e9a807e30ee76ba83af604
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366784"
---
# <a name="getproc04-c-sample-code"></a>Código de ejemplo GetProc04 (C#)

En el código siguiente se muestra la implementación de un cmdlet `Get-Process` que informa de errores de no terminación. Esta implementación llama al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) para informar de los errores de no terminación.

> [!NOTE]
> Puede descargar el C# archivo de código fuente (getprov04.CS) para este cmdlet Get-proc mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de origen descargados están disponibles en el directorio **@no__t ejemplos de 1PowerShell >** .

## <a name="code-sample"></a>Código de ejemplo

[!code-csharp[GetProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample04/GetProcessSample04.cs#L11-L98 "GetProcessSample04.cs")]

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
