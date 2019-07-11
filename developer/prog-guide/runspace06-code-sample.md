---
title: Ejemplo de código RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: b6fdad90f7339e941d77646936b1b5952cd65500
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734933"
---
# <a name="runspace06-code-sample"></a>Ejemplo de código Runspace06

Aquí está el código fuente para el ejemplo Runspace06 que se describen en [configurar un espacio de ejecución mediante un Windows PowerShell Snap-in](https://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83). Esta aplicación de ejemplo crea un espacio de ejecución en función de un complemento de Windows PowerShell, que, a continuación, se usa para ejecutar una canalización con un solo comando. Para ello, la aplicación crea la información de configuración del espacio de ejecución, crea un espacio de ejecución, crea una canalización con un solo comando y, a continuación, ejecuta la canalización.

> [!NOTE]
> Puede descargar el C# el archivo de código fuente (runspace06.cs) mediante el Kit del desarrollo de Software de Windows para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components. Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.

## <a name="code-sample"></a>Ejemplo de código

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)