---
title: Runspace01 (VB.NET) ejemplo de código | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12ee5382-95ba-41c7-8291-7f69a6f63514
caps.latest.revision: 7
ms.openlocfilehash: fbc90a6736d841fe184b86ab143809ad23c7977a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856061"
---
# <a name="runspace01-vbnet-code-sample"></a><span data-ttu-id="fdcf4-102">Ejemplo de código Runspace01 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="fdcf4-102">Runspace01 (VB.NET) Code Sample</span></span>

<span data-ttu-id="fdcf4-103">Estos son los ejemplos de código para el espacio de ejecución descrito en [crear una aplicación de consola que ejecuta un comando especificado](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="fdcf4-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="fdcf4-104">Para ello, la aplicación invoca un espacio de ejecución y, a continuación, invoca un comando.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="fdcf4-105">(Tenga en cuenta que esta aplicación no especifica información de configuración del espacio de ejecución ni explícitamente crear una canalización). Es el comando que se invoca el `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline.) The command that is invoked is the `Get-Process` cmdlet.</span></span>
<span data-ttu-id="fdcf4-106">Estos son los ejemplos de código para el espacio de ejecución descrito en [crear una aplicación de consola que ejecuta un comando especificado](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span><span class="sxs-lookup"><span data-stu-id="fdcf4-106">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](http://msdn.microsoft.com/en-us/793a6570-a072-4799-840b-172f28ce620e).</span></span> <span data-ttu-id="fdcf4-107">Para ello, la aplicación invoca un espacio de ejecución y, a continuación, invoca un comando.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-107">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="fdcf4-108">(Tenga en cuenta que esta aplicación no especifica información de configuración del espacio de ejecución ni explícitamente crear una canalización). Es el comando que se invoca el `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-108">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline.) The command that is invoked is the `Get-Process` cmdlet.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fdcf4-109">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="fdcf4-109">Code Sample</span></span>

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Module Runspace01
        ' <summary>
        ' This sample uses the RunspaceInvoke class to execute
        ' the get-process cmdlet synchronously. The name and
        ' handlecount are then extracted from  the PSObjects
        ' returned and displayed.
        ' </summary>
        ' <param name="args">Unused</param>
        ' <remarks>
        ' This sample demonstrates the following:
        ' 1. Creating an instance of the RunspaceInvoke class.
        ' 2. Using this instance to invoke a PowerShell command.
        ' 3. Using PSObject to extract properties from the objects
        '    returned by this command.
        ' </remarks>
        Sub Main()
            ' Create an instance of the RunspaceInvoke class.
            ' This takes care of all building all of the other
            ' data structures needed...
            Dim invoker As RunspaceInvoke = New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            For Each result As PSObject In invoker.Invoke("get-process")
                Console.WriteLine("{0,-20} {1}", _
                    result.Members("ProcessName").Value, _
                    result.Members("HandleCount").Value)
            Next
            System.Console.WriteLine("Hit any key to exit...")
            System.Console.ReadKey()
        End Sub
    End Module
End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace01.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace01.vb#L09-L53 "Runspace01.vb")] -->

## <a name="see-also"></a><span data-ttu-id="fdcf4-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="fdcf4-110">See Also</span></span>

[<span data-ttu-id="fdcf4-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fdcf4-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)