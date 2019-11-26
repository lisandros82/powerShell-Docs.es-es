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
ms.openlocfilehash: 06b5a06ae20a4bbb2c58eaa1776700aa8f80555c
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416068"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="2b05a-102">Ejemplo de código Runspace03 (C#)</span><span class="sxs-lookup"><span data-stu-id="2b05a-102">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="2b05a-103">Este es el C# código fuente de la aplicación de consola que se describe en "crear una aplicación de consola que ejecuta un script especificado".</span><span class="sxs-lookup"><span data-stu-id="2b05a-103">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="2b05a-104">En este ejemplo se usa la clase [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) para ejecutar un script que recupera información del proceso mediante la lista de nombres de proceso que se pasa al script.</span><span class="sxs-lookup"><span data-stu-id="2b05a-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="2b05a-105">Muestra cómo pasar objetos de entrada a un script y cómo recuperar objetos de error, así como los objetos de salida.</span><span class="sxs-lookup"><span data-stu-id="2b05a-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="2b05a-106">Puede descargar el C# archivo de código fuente (runspace03.CS) para este ejemplo mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="2b05a-106">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="2b05a-107">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="2b05a-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="2b05a-108">Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="2b05a-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="2b05a-109">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="2b05a-109">Code Sample</span></span>

[!code-csharp[Runspace03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs#L11-L88 "Runspace03.cs")]

## <a name="see-also"></a><span data-ttu-id="2b05a-110">Vea también</span><span class="sxs-lookup"><span data-stu-id="2b05a-110">See Also</span></span>

[<span data-ttu-id="2b05a-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b05a-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="2b05a-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2b05a-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
