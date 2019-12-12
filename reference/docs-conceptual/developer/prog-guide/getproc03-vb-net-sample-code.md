---
title: Código de ejemplo de GetProc03 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360314"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="fc7e4-102">Código de ejemplo GetProc03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="fc7e4-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="fc7e4-103">En el código siguiente se muestra la implementación de un cmdlet `Get-Process` que puede aceptar la entrada canalizada.</span><span class="sxs-lookup"><span data-stu-id="fc7e4-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="fc7e4-104">Esta implementación define un parámetro `Name` que acepta la entrada de canalización, recupera información del proceso del equipo local basándose en los nombres proporcionados y, a continuación, usa el método [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) como mecanismo de salida para enviar objetos a la canalización.</span><span class="sxs-lookup"><span data-stu-id="fc7e4-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fc7e4-105">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="fc7e4-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
