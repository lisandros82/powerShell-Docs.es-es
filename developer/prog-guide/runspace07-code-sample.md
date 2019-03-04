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
ms.openlocfilehash: 3e016b0e98234797afc8f303a55919228eaf8829
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857931"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="5c657-102">Ejemplo de código Runspace07</span><span class="sxs-lookup"><span data-stu-id="5c657-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="5c657-103">Aquí está el código fuente para el ejemplo Runspace07 que se describen en [crear una aplicación que agrega comandos de la consola a una canalización](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="5c657-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="5c657-104">Esta aplicación de ejemplo crea un espacio de ejecución, crea una canalización, agrega dos comandos a la canalización y, a continuación, ejecuta la canalización.</span><span class="sxs-lookup"><span data-stu-id="5c657-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="5c657-105">Los comandos que se agrega a la canalización son el `Get-Process` y `Measure-Object` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5c657-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="5c657-106">Puede descargar el C# archivo de código fuente (runspace07.cs) mediante el Microsoft Windows Software Development Kit para Windows Vista y los componentes de Microsoft .NET Framework 3.0 Runtime.</span><span class="sxs-lookup"><span data-stu-id="5c657-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5c657-107">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5c657-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="5c657-108">Puede descargar el C# archivo de código fuente (runspace07.cs) mediante el Microsoft Windows Software Development Kit para Windows Vista y los componentes de Microsoft .NET Framework 3.0 Runtime.</span><span class="sxs-lookup"><span data-stu-id="5c657-108">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="5c657-109">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="5c657-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="5c657-110">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="5c657-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5c657-111">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="5c657-111">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="5c657-112">Véase también</span><span class="sxs-lookup"><span data-stu-id="5c657-112">See Also</span></span>

[<span data-ttu-id="5c657-113">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5c657-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="5c657-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5c657-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)