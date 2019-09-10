---
title: Ejemplo deC#código RunSpace03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ac8ab99-1856-4d6f-b30d-c0a18b8dd1fc
caps.latest.revision: 6
ms.openlocfilehash: 9afdb97b8ae2919f091ca5bacccedbe37c2e1584
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848032"
---
# <a name="runspace03-c-code-sample"></a>Ejemplo de código Runspace03 (C#)

Este es el C# código fuente de la aplicación de consola que se describe en "crear una aplicación de consola que ejecuta un script especificado". En este ejemplo se usa la clase [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) para ejecutar un script que recupera información del proceso mediante la lista de nombres de proceso que se pasa al script. Muestra cómo pasar objetos de entrada a un script y cómo recuperar objetos de error, así como los objetos de salida.

> [!NOTE]
> Puede descargar el C# archivo de código fuente (runspace03.CS) para este ejemplo mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de Microsoft .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
> Los archivos de código fuente descargados  **\<** están disponibles en el directorio de ejemplos de PowerShell >.

## <a name="code-sample"></a>Código de ejemplo

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a>Vea también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)