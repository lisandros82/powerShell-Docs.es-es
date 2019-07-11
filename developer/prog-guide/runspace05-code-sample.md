---
title: Ejemplo de código RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: abf19d848f6150d005c63bb0fc2ffbe1de405e2a
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734961"
---
# <a name="runspace05-code-sample"></a>Ejemplo de código Runspace05

Este es el código fuente para el que se describe en el ejemplo de Runspace05 [configurando un RunspaceConfiguration de uso de espacio de ejecución](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2). En este ejemplo se muestra cómo crear la información de configuración del espacio de ejecución, crear un espacio de ejecución, crear una canalización con un solo comando y, a continuación, ejecutar la canalización. El comando que se ejecuta es la `Get-Process` cmdlet.

> [!NOTE]
> Puede descargar el C# el archivo de código fuente (runspace05.cs) mediante el Microsoft Windows Software Development Kit para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components. Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.

## <a name="code-sample"></a>Ejemplo de código

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)