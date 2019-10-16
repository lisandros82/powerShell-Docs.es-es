---
title: Código de ejemplo de RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: a99d0cc0dd35ae4c1a52e3624a9dd5af2a26c97a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360144"
---
# <a name="runspace05-code-sample"></a>Ejemplo de código Runspace05

Este es el código fuente del ejemplo Runspace05 que se describe en [configuración de un espacio de ejecución con RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). En este ejemplo se muestra cómo se crea la información de configuración del espacio de ejecución, se crea un espacio de ejecución, se crea una canalización con un solo comando y, a continuación, se ejecuta la canalización. El comando que se ejecuta es el cmdlet `Get-Process`.

> [!NOTE]
> Puede descargar el archivo C# de código fuente (runspace05.CS) mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de Microsoft .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de origen descargados están disponibles en el directorio **@no__t ejemplos de 1PowerShell >** .

## <a name="code-sample"></a>Código de ejemplo

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
