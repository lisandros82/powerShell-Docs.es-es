---
title: Código deC#ejemplo de GetProc03 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 126df3092c0722b0fc9d02cb61d3faf0578b8e97
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416132"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="7f50b-102">Código de ejemplo GetProc03 (C#)</span><span class="sxs-lookup"><span data-stu-id="7f50b-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="7f50b-103">En el código siguiente se muestra la implementación de un cmdlet `Get-Process` que puede aceptar la entrada canalizada.</span><span class="sxs-lookup"><span data-stu-id="7f50b-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="7f50b-104">Esta implementación define un parámetro `Name` que acepta la entrada de canalización, recupera información del proceso del equipo local basándose en los nombres proporcionados y, a continuación, usa el método [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) como mecanismo de salida para enviar objetos a la canalización.</span><span class="sxs-lookup"><span data-stu-id="7f50b-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="7f50b-105">Puede descargar el C# archivo de código fuente (getprov03.CS) para este cmdlet Get-proc mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="7f50b-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7f50b-106">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="7f50b-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="7f50b-107">Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="7f50b-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="7f50b-108">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="7f50b-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="7f50b-109">Vea también</span><span class="sxs-lookup"><span data-stu-id="7f50b-109">See Also</span></span>

[<span data-ttu-id="7f50b-110">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f50b-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7f50b-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7f50b-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
