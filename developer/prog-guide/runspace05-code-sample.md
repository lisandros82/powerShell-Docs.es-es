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
ms.openlocfilehash: b16ee45383059c52ce3433699c6b8d2120992431
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429574"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="fca33-102">Ejemplo de código Runspace05</span><span class="sxs-lookup"><span data-stu-id="fca33-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="fca33-103">Este es el código fuente para el que se describe en el ejemplo de Runspace05 [configurando un RunspaceConfiguration de uso de espacio de ejecución](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span><span class="sxs-lookup"><span data-stu-id="fca33-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](http://msdn.microsoft.com/en-us/42681d19-2d05-4975-befd-afb1990e79b2).</span></span> <span data-ttu-id="fca33-104">En este ejemplo se muestra cómo crear la información de configuración del espacio de ejecución, crear un espacio de ejecución, crear una canalización con un solo comando y, a continuación, ejecutar la canalización.</span><span class="sxs-lookup"><span data-stu-id="fca33-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="fca33-105">El comando que se ejecuta es la `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fca33-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="fca33-106">Puede descargar el C# el archivo de código fuente (runspace05.cs) mediante el Microsoft Windows Software Development Kit para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="fca33-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="fca33-107">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="fca33-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="fca33-108">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="fca33-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fca33-109">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="fca33-109">Code Sample</span></span>

[!code-csharp[Runspace05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs#L11-L86 "Runspace05.cs")]

## <a name="see-also"></a><span data-ttu-id="fca33-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="fca33-110">See Also</span></span>

[<span data-ttu-id="fca33-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fca33-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="fca33-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fca33-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)