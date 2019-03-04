---
title: RunSpace04 (VB.NET) ejemplo de código | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f0dea3c-4354-4d7d-9823-5e6234c9a89e
caps.latest.revision: 6
ms.openlocfilehash: 348d34dc0132705fa4a50fb6fe1fd43f510ae210
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853621"
---
# <a name="runspace04--vbnet-code-sample"></a><span data-ttu-id="6d101-102">Ejemplo de código Runspace04 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="6d101-102">RunSpace04  (VB.NET) Code Sample</span></span>

<span data-ttu-id="6d101-103">Este es el código fuente VB.NET del ejemplo Runspace04.</span><span class="sxs-lookup"><span data-stu-id="6d101-103">Here is the VB.NET source code for the Runspace04 sample.</span></span> <span data-ttu-id="6d101-104">Este ejemplo se utiliza el [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) clase para ejecutar un script que genera un error de terminación.</span><span class="sxs-lookup"><span data-stu-id="6d101-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="6d101-105">La aplicación host es responsable de detectar el error e interpretar el registro de error.</span><span class="sxs-lookup"><span data-stu-id="6d101-105">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="6d101-106">Puede descargar el archivo de código fuente VB.NET (runspace02.vb) para este ejemplo con el Kit del desarrollo de Software de Windows para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="6d101-106">You can download the VB.NET source file (runspace02.vb) for this sample by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6d101-107">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6d101-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="6d101-108">Puede descargar el archivo de código fuente VB.NET (runspace02.vb) para este ejemplo con el Kit del desarrollo de Software de Windows para Windows Vista y Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="6d101-108">You can download the VB.NET source file (runspace02.vb) for this sample by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="6d101-109">Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="6d101-109">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="6d101-110">Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="6d101-110">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6d101-111">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="6d101-111">Code Sample</span></span>

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

    Class Runspace04

        ''' <summary>
        ''' This sample uses the RunspaceInvoke class to execute
        ''' a script. This script will generate a terminating
        ''' exception that the caller should catch and process.
        ''' </summary>
        ''' <param name="args">Unused</param>
        ''' <remarks>
        ''' This sample demonstrates the following:
        ''' 1. Creating an instance of the RunspaceInvoke class.
        ''' 2. Using this instance to execute a string as a PowerShell script.
        ''' 3. Passing input objects to the script from the calling program.
        ''' 4. Using PSObject to extract and display properties from the objects
        '''    returned by this command.
        ''' 5. Retrieving and displaying error records that may be generated
        '''    during the execution of that script.
        ''' 6. Catching and displaying terminating exceptions generated
        '''    by the script being run.
        ''' </remarks>
        Shared Sub Main(ByVal args() As String)
            ' Define a list of patterns to use in matching
            ' Note that the fourth pattern is not a valid regular
            ' expression so it will cause a terminating exception to
            ' be thrown when used in select-string.
            Dim patterns() As String = {"aa", "bc", "ab*c", "*", "abc"}

            ' The script to run to use the patterns. Input passed
            ' to the script will be available in the $input variable.
            Dim script As String = "$input | where {" & _
                " select-string $_ -inputobject 'abc' }"

            ' Create an instance of the RunspaceInvoke class.
            Dim invoker As New RunspaceInvoke()

            ' Invoke the runspace. Because of the bad regular expression,
            ' no objects will be returned. Instead, an exception will be
            ' thrown.
            Try
                Dim errors As System.Collections.IList = Nothing
                Dim result As PSObject
                For Each result In invoker.Invoke(script, patterns, errors)
                    Console.WriteLine("'{0}'", result.ToString())
                Next result

                ' Now process any error records that were generated
                ' while running the script.
                Console.WriteLine(vbCrLf & _
                    "The following non-terminating errors occurred:" & vbCrLf)
                If Not (errors Is Nothing) AndAlso errors.Count > 0 Then
                    Dim err As PSObject
                    For Each err In errors
                        System.Console.WriteLine("    error: {0}", err.ToString())
                    Next err
                End If
            Catch runtimeException As RuntimeException
                ' Trap any exception generated by the script. These exceptions
                ' will all be derived from RuntimeException.
                System.Console.WriteLine("Runtime exception: {0}: {1}" & _
                   vbCrLf + "{2}", _
                   runtimeException.ErrorRecord.InvocationInfo.InvocationName, _
                   runtimeException.Message, _
                   runtimeException.ErrorRecord.InvocationInfo.PositionMessage)
            End Try

            System.Console.WriteLine(vbCrLf + "Hit any key to exit...")
            System.Console.ReadKey()

        End Sub 'Main
    End Class 'Runspace04

End Namespace
```

<!-- TODO!!!: [!code-csharp[Runspace04.vb](../../powershell-sdk-samples/SDK-2.0/vb/Runspace01/Runspace04.vb#L09-L92 "Runspace04.vb")] -->

## <a name="see-also"></a><span data-ttu-id="6d101-112">Véase también</span><span class="sxs-lookup"><span data-stu-id="6d101-112">See Also</span></span>

[<span data-ttu-id="6d101-113">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d101-113">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="6d101-114">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6d101-114">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)