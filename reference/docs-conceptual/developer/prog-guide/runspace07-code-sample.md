---
title: Código de ejemplo de RunSpace07 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ad306d9-45c2-4d55-8e64-fdcba43402c5
caps.latest.revision: 6
ms.openlocfilehash: b3c2e70d534e8a267b35ae1715bd24277267e0d8
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417891"
---
# <a name="runspace07-code-sample"></a><span data-ttu-id="11864-102">Ejemplo de código Runspace07</span><span class="sxs-lookup"><span data-stu-id="11864-102">RunSpace07 Code Sample</span></span>

<span data-ttu-id="11864-103">Este es el código fuente del ejemplo Runspace07 que se describe en [crear una aplicación de consola que agrega comandos a una canalización](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span><span class="sxs-lookup"><span data-stu-id="11864-103">Here is the source code for the Runspace07 sample described in [Creating a Console Application That Adds Commands to a Pipeline](https://msdn.microsoft.com/en-us/01eb7808-e97b-4905-80be-9e2fa38c262e).</span></span> <span data-ttu-id="11864-104">En esta aplicación de ejemplo se crea un espacio de ejecución, se crea una canalización, se agregan dos comandos a la canalización y, a continuación, se ejecuta la canalización.</span><span class="sxs-lookup"><span data-stu-id="11864-104">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, and then executes the pipeline.</span></span> <span data-ttu-id="11864-105">Los comandos que se agregan a la canalización son los cmdlets `Get-Process` y `Measure-Object`.</span><span class="sxs-lookup"><span data-stu-id="11864-105">The commands added to the pipeline are the `Get-Process` and `Measure-Object` cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="11864-106">Puede descargar el archivo C# de código fuente (runspace07.CS) mediante el kit de desarrollo de software de Microsoft Windows para los componentes de tiempo de ejecución de Windows Vista y Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="11864-106">You can download the C# source file (runspace07.cs) using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="11864-107">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="11864-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="11864-108">Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="11864-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="11864-109">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="11864-109">Code Sample</span></span>

[!code-csharp[Runspace07.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace07/Runspace07.cs#L11-L108 "Runspace07.cs")]

## <a name="see-also"></a><span data-ttu-id="11864-110">Vea también</span><span class="sxs-lookup"><span data-stu-id="11864-110">See Also</span></span>

[<span data-ttu-id="11864-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="11864-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="11864-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="11864-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
