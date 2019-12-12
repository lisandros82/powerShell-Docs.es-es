---
title: Código de ejemplo de RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: c3ae45ae9587bd130bbe9bb65ef47dc246f6e465
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417922"
---
# <a name="runspace06-code-sample"></a>Ejemplo de código Runspace06

Este es el código fuente del ejemplo Runspace06 que se describe en [configuración de un espacio de ejecución mediante un complemento de Windows PowerShell](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83). Esta aplicación de ejemplo crea un espacio de ejecución basado en un complemento de Windows PowerShell, que se usa para ejecutar una canalización con un solo comando. Para ello, la aplicación crea la información de configuración del espacio de ejecución, crea un espacio de ejecución, crea una canalización con un solo comando y, a continuación, ejecuta la canalización.

> [!NOTE]
> Puede descargar el archivo C# de código fuente (runspace06.CS) mediante el kit de desarrollo de software de Windows para Windows Vista y los componentes de tiempo de ejecución de Microsoft .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .

## <a name="code-sample"></a>Ejemplo de código

[!code-csharp[Runspace06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
