---
title: Ejemplo deC#código Runspace01 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 39e7d49b51942da51a581ab33dbe46ab848ca1c3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366644"
---
# <a name="runspace01-c-code-sample"></a>Ejemplo de código Runspace01 (C#)

Estos son los ejemplos de código para el espacio de ejecución que se describe en [crear una aplicación de consola que ejecuta un comando especificado](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program). Para ello, la aplicación invoca un espacio de ejecución y, a continuación, invoca un comando. (Tenga en cuenta que esta aplicación no especifica información de configuración del espacio de ejecución ni crea explícitamente una canalización). El comando que se invoca es el cmdlet `Get-Process`.

> [!NOTE]
> Puede descargar el C# archivo de código fuente (runspace01.CS) de este espacio de ejecución mediante el kit de desarrollo de software de Microsoft Windows para los componentes de tiempo de ejecución de Windows Vista y Microsoft .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de origen descargados están disponibles en el directorio **@no__t ejemplos de 1PowerShell >** .

## <a name="code-sample"></a>Código de ejemplo

[!code-csharp[Runspace01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
