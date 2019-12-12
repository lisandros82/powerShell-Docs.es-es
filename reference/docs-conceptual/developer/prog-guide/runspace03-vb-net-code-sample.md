---
title: Ejemplo de código RunSpace03 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3611d66b-19da-4477-ac05-2e5e68312f51
caps.latest.revision: 6
ms.openlocfilehash: e744caf0201a6e2a7fbf86138d7b28e4f14d549f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417971"
---
# <a name="runspace03-vbnet-code-sample"></a><span data-ttu-id="a641d-102">Ejemplo de código Runspace03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="a641d-102">RunSpace03 (VB.NET) Code Sample</span></span>

<span data-ttu-id="a641d-103">Este es el código fuente de VB.NET para la aplicación de consola que se describe en "crear una aplicación de consola que ejecuta un script especificado".</span><span class="sxs-lookup"><span data-stu-id="a641d-103">Here is the VB.NET source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="a641d-104">En este ejemplo se usa la clase [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) para ejecutar un script que recupera información del proceso para la lista de nombres de proceso que se pasa al script.</span><span class="sxs-lookup"><span data-stu-id="a641d-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information for the list of process names passed into the script.</span></span> <span data-ttu-id="a641d-105">Muestra cómo pasar objetos de entrada a un script y cómo recuperar objetos de error, así como los objetos de salida.</span><span class="sxs-lookup"><span data-stu-id="a641d-105">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="a641d-106">Puede descargar el archivo de código fuente de VB.NET (runspace03. VB) para este ejemplo mediante el uso del kit de desarrollo de software de Windows para los componentes de tiempo de ejecución de Windows Vista y Microsoft .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="a641d-106">You can download the VB.NET source file (runspace03.vb) for this sample by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="a641d-107">Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="a641d-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="a641d-108">Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .</span><span class="sxs-lookup"><span data-stu-id="a641d-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a641d-109">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="a641d-109">Code Sample</span></span>

```vb
Imports System
Imports System.Collections
Imports System.Collections.Generic
Imports System.Collections.ObjectModel
Imports System.Text
Imports Microsoft.VisualBasic
Imports System.Management.Automation
Imports System.Management.Automation.Host
Imports System.Management.Automation.Runspaces

Namespace Microsoft.Samples.PowerShell.Runspaces

    Class Runspace03

        ''' <summary>
        ''' This sample uses the RunspaceInvoke class to execute
        ''' a script that retrieves process information for the
        ''' list of process names passed into the script.
        ''' It shows how to pass input objects to a script and
        ''' how to retrieve error objects as well as the output objects.
        ''' </summary>
        ''' <param name="args">Unused</param>
        ''' <remarks>
        ''' This sample demonstrates the following:
        ''' 1. Creating an instance of the RunspaceInvoke class.
        ''' 2. Using this instance to execute a string as a PowerShell script.
        ''' 3. Passing input objects to the script from the calling program.
        ''' 4. Using PSObject to extract and display properties from the objects
        '''    returned by this command.
        ''' 5. Retrieving and displaying error records that were generated
        '''    during the execution of that script.
        ''' </remarks>
        Shared Sub Main(ByVal args() As String)
            ' Define a list of processes to look for
            Dim processNames() As String = {"lsass", "nosuchprocess", _
                "services", "nosuchprocess2"}

            ' The script to run to get these processes. Input passed
            ' to the script will be available in the $input variable.
            Dim script As String = "$input | get-process -name {$_}"

            ' Create an instance of the RunspaceInvoke class.
            Dim invoker As New RunspaceInvoke()

            Console.WriteLine("Process              HandleCount")
            Console.WriteLine("--------------------------------")

            ' Now invoke the runspace and display the objects that are
            ' returned...
            Dim errors As System.Collections.IList = Nothing
            Dim result As PSObject
            For Each result In invoker.Invoke(script, processNames, errors)
                Console.WriteLine("{0,-20} {1}", _
                result.Members("ProcessName").Value, _
                result.Members("HandleCount").Value)
            Next result

            ' Now process any error records that were generated while
            ' running the script.
            Console.WriteLine(vbCrLf & _
                "The following non-terminating errors occurred:" & vbCrLf)
            If Not (errors Is Nothing) AndAlso errors.Count > 0 Then
                Dim err As PSObject
                For Each err In errors
                    System.Console.WriteLine("    error: {0}", err.ToString())
                Next err
            End If
            System.Console.WriteLine(vbCRLF & "Hit any key to exit...")
            System.Console.ReadKey()

        End Sub 'Main

    End Class 'Runspace03

End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace03.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace03.vb#L09-L83 "Runspace03.vb")] -->

## <a name="see-also"></a><span data-ttu-id="a641d-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="a641d-110">See Also</span></span>

[<span data-ttu-id="a641d-111">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a641d-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="a641d-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a641d-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
