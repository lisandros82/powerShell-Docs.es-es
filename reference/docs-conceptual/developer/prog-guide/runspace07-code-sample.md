---
title: Código de ejemplo de RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: b3c2e70d534e8a267b35ae1715bd24277267e0d8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417891"
---
# <a name="runspace07-code-sample"></a>Ejemplo de código Runspace07

Este es el código fuente del ejemplo Runspace07 que se describe en [crear una aplicación de consola que agrega comandos a una canalización](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e). En esta aplicación de ejemplo se crea un espacio de ejecución, se crea una canalización, se agregan dos comandos a la canalización y, a continuación, se ejecuta la canalización. Los comandos que se agregan a la canalización son los cmdlets `Get-Process` y `Measure-Object`.

> [!NOTE]
> Puede descargar el archivo C# de código fuente (runspace07.CS) mediante el kit de desarrollo de software de Microsoft Windows para los componentes de tiempo de ejecución de Windows Vista y Microsoft .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .

## <a name="code-sample"></a>Ejemplo de código

[!code-csharp[Runspace07.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
