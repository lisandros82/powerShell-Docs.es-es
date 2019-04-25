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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081383"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="1deb4-102">Ejemplo de código Runspace03 (C#)</span><span class="sxs-lookup"><span data-stu-id="1deb4-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="1deb4-103">Este es el C# código fuente de la aplicación de consola que se describe en [crear una aplicación de consola que funciona una secuencia de comandos especificado](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span><span class="sxs-lookup"><span data-stu-id="1deb4-103">Here is the C# source code for the console application described in [Creating a Console Application That Runs a Specified Script](http://msdn.microsoft.com/en-us/a93e6006-36db-4bcc-b9da-c5bebf4ffd68).</span></span> <span data-ttu-id="1deb4-104">Este ejemplo se utiliza el [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) clase para ejecutar un script que recupera procesa la información mediante el uso de la lista de nombres de proceso pasado a la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="1deb4-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="1deb4-105">Muestra cómo pasar objetos de entrada a una secuencia de comandos y cómo recuperar los objetos de error, así como los objetos de salida.</span><span class="sxs-lookup"><span data-stu-id="1deb4-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="1deb4-106">Puede descargar el C# (runspace03.cs) de archivo de código fuente para este ejemplo mediante el Microsoft Windows Software Development Kit para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="1deb4-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1deb4-107">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="1deb4-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1deb4-108">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="1deb4-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="1deb4-109">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="1deb4-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="1deb4-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="1deb4-110">See Also</span></span>

[<span data-ttu-id="1deb4-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="1deb4-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1deb4-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1deb4-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)