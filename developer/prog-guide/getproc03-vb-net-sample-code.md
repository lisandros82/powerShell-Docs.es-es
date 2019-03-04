---
title: GetProc03 código de ejemplo (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: da85155c43471150a7b35ac37c1dce0790277084
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854641"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="c8d15-102">Código de ejemplo GetProc03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="c8d15-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="c8d15-103">El código siguiente muestra la implementación de un `Get-Process` cmdlet que puede aceptar canaliza la entrada.</span><span class="sxs-lookup"><span data-stu-id="c8d15-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="c8d15-104">Esta implementación define un `Name` parámetro que acepta la entrada de la canalización, recupera información de proceso del equipo local en función de los nombres proporcionados y, a continuación, usa el [System.Management.Automation.Cmdlet.Writeobject% 28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como el mecanismo de salida para enviar objetos a la canalización.</span><span class="sxs-lookup"><span data-stu-id="c8d15-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c8d15-105">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="c8d15-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->