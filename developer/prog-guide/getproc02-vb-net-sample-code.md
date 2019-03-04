---
title: GetProc02 código de ejemplo (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 5b5cefae1be3ccf6aec819df83363b7161955b0c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860191"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="16dc1-102">Código de ejemplo GetProc02 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="16dc1-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="16dc1-103">El código siguiente muestra la implementación de un `Get-Process` cmdlet que acepta la entrada de línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="16dc1-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="16dc1-104">Tenga en cuenta que esta implementación define un `Name` parámetro para permitir la entrada de línea de comandos y lo utiliza el [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como salida mecanismo para enviar el resultado de los objetos a la canalización.</span><span class="sxs-lookup"><span data-stu-id="16dc1-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="16dc1-105">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="16dc1-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="16dc1-106">Véase también</span><span class="sxs-lookup"><span data-stu-id="16dc1-106">See Also</span></span>

[<span data-ttu-id="16dc1-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="16dc1-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)