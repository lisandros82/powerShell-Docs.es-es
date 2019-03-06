---
title: RunSpace03 (C#) ejemplo de código | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 0e80f4d850a7c6dc044526a56b92f16eea4040b5
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429914"
---
# <a name="runspace03-c-code-sample"></a>Ejemplo de código Runspace03 (C#)

Este es el C# código fuente de la aplicación de consola que se describe en [crear una aplicación de consola que funciona una secuencia de comandos especificado](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68). Este ejemplo se utiliza el [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) clase para ejecutar un script que recupera procesa la información mediante el uso de la lista de nombres de proceso pasado a la secuencia de comandos. Muestra cómo pasar objetos de entrada a una secuencia de comandos y cómo recuperar los objetos de error, así como los objetos de salida.

> [!NOTE]
> Puede descargar el C# (runspace03.cs) de archivo de código fuente para este ejemplo mediante el Microsoft Windows Software Development Kit para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components. Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.

## <a name="code-sample"></a>Ejemplo de código

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)