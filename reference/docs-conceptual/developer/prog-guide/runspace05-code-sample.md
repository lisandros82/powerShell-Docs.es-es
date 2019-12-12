---
title: Código de ejemplo de RunSpace05 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 979403376c5e694b686aaf77a2cb787d765cb883
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417929"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="7a654-102">Ejemplo de código Runspace05</span><span class="sxs-lookup"><span data-stu-id="7a654-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="7a654-103">Este es el código fuente del ejemplo Runspace05 que se describe en [configuración de un espacio de ejecución con RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="7a654-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="7a654-104">En este ejemplo se muestra cómo se crea la información de configuración del espacio de ejecución, se crea un espacio de ejecución, se crea una canalización con un solo comando y, a continuación, se ejecuta la canalización.</span><span class="sxs-lookup"><span data-stu-id="7a654-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="7a654-105">El comando que se ejecuta es el cmdlet `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="7a654-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="7a654-106">Puede descargar el archivo C# de código fuente (runspace05.CS) mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="7a654-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7a654-107">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="7a654-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="7a654-108">Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="7a654-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7a654-109">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="7a654-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="7a654-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="7a654-110">See Also</span></span>

[<span data-ttu-id="7a654-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7a654-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7a654-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7a654-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
