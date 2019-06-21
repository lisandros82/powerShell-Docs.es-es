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
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301572"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="bfacc-102">Código de ejemplo GetProc03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="bfacc-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="bfacc-103">El código siguiente muestra la implementación de un `Get-Process` cmdlet que puede aceptar canaliza la entrada.</span><span class="sxs-lookup"><span data-stu-id="bfacc-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="bfacc-104">Esta implementación define un `Name` parámetro que acepta la entrada de la canalización, recupera información de proceso del equipo local en función de los nombres proporcionados y, a continuación, usa el [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)método como el mecanismo de salida para enviar objetos a la canalización.</span><span class="sxs-lookup"><span data-stu-id="bfacc-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="bfacc-105">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="bfacc-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
