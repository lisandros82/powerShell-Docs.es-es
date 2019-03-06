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
ms.openlocfilehash: 064e7d7ea2ee173bbcdd75a9f3a6c12582afe17b
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429650"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="959c8-102">Ejemplo de código Runspace07</span><span class="sxs-lookup"><span data-stu-id="959c8-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="959c8-103">Aquí está el código fuente para el ejemplo Runspace07 que se describen en [crear una aplicación que agrega comandos de la consola a una canalización](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="959c8-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](http://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="959c8-104">Esta aplicación de ejemplo crea un espacio de ejecución, crea una canalización, agrega dos comandos a la canalización y, a continuación, ejecuta la canalización.</span><span class="sxs-lookup"><span data-stu-id="959c8-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="959c8-105">Los comandos que se agrega a la canalización son el `Get-Process` y `Measure-Object` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="959c8-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="959c8-106">Puede descargar el C# archivo de código fuente (runspace07.cs) mediante el Microsoft Windows Software Development Kit para Windows Vista y los componentes de Microsoft .NET Framework 3.0 Runtime.</span><span class="sxs-lookup"><span data-stu-id="959c8-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="959c8-107">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="959c8-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="959c8-108">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="959c8-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="959c8-109">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="959c8-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="959c8-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="959c8-110">See Also</span></span>

[<span data-ttu-id="959c8-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="959c8-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="959c8-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="959c8-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)