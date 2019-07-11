---
title: Ejemplo de código RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: 232b282e366c9fad167686337696ef2ccd8b30d8
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734946"
---
# <a name="runspace07-code-sample"></a>Ejemplo de código Runspace07

Aquí está el código fuente para el ejemplo Runspace07 que se describen en [crear una aplicación que agrega comandos de la consola a una canalización](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e). Esta aplicación de ejemplo crea un espacio de ejecución, crea una canalización, agrega dos comandos a la canalización y, a continuación, ejecuta la canalización. Los comandos que se agrega a la canalización son el `Get-Process` y `Measure-Object` cmdlets.

> [!NOTE]
> Puede descargar el C# archivo de código fuente (runspace07.cs) mediante el Microsoft Windows Software Development Kit para Windows Vista y los componentes de Microsoft .NET Framework 3.0 Runtime. Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.

## <a name="code-sample"></a>Ejemplo de código

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)