---
title: Runspace01 (C#) ejemplo de código | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d59f8b7c-e800-4633-aa5b-74d4c57e2706
caps.latest.revision: 6
ms.openlocfilehash: 59320365c4a35c3d71af10273eb21b1ce01e5c0c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081468"
---
# <a name="runspace01-c-code-sample"></a>Ejemplo de código Runspace01 (C#)

Estos son los ejemplos de código para el espacio de ejecución descrito en [crear una aplicación de consola que ejecuta un comando especificado](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e). Para ello, la aplicación invoca un espacio de ejecución y, a continuación, invoca un comando. (Tenga en cuenta que esta aplicación no especifica información de configuración del espacio de ejecución ni explícitamente crear una canalización). Es el comando que se invoca el `Get-Process` cmdlet.

> [!NOTE]
> Puede descargar el C# (runspace01.cs) de archivo de código fuente para este espacio de ejecución usando el Microsoft Windows Software Development Kit para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components. Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.

## <a name="code-sample"></a>Ejemplo de código

[!code-csharp[Runspace01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs#L11-L62 "Runspace01.cs")]

## <a name="see-also"></a>Véase también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)