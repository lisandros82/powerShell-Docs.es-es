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
ms.openlocfilehash: 2b5ac097e8a52832b0f8cfb93b84eef56fc64858
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854601"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="15077-102">Ejemplo de código Runspace05</span><span class="sxs-lookup"><span data-stu-id="15077-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="15077-103">Este es el código fuente para el que se describe en el ejemplo de Runspace05 [configurando un RunspaceConfiguration de uso de espacio de ejecución](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="15077-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="15077-104">En este ejemplo se muestra cómo crear la información de configuración del espacio de ejecución, crear un espacio de ejecución, crear una canalización con un solo comando y, a continuación, ejecutar la canalización.</span><span class="sxs-lookup"><span data-stu-id="15077-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="15077-105">El comando que se ejecuta es la `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="15077-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="15077-106">Puede descargar el C# el archivo de código fuente (runspace05.cs) mediante el Microsoft Windows Software Development Kit para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="15077-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="15077-107">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="15077-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="15077-108">Puede descargar el C# el archivo de código fuente (runspace05.cs) mediante el Microsoft Windows Software Development Kit para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="15077-108">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="15077-109">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="15077-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="15077-110">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="15077-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="15077-111">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="15077-111">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="15077-112">Véase también</span><span class="sxs-lookup"><span data-stu-id="15077-112">See Also</span></span>

[<span data-ttu-id="15077-113">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="15077-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="15077-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="15077-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)