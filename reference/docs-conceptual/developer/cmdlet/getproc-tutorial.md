---
title: Tutorial de GetProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364444"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="48b2f-102">Tutorial de GetProc</span><span class="sxs-lookup"><span data-stu-id="48b2f-102">GetProc Tutorial</span></span>

<span data-ttu-id="48b2f-103">En esta sección se proporciona un tutorial para crear un cmdlet Get-proc que es muy similar al cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) proporcionado por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48b2f-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="48b2f-104">En este tutorial se proporcionan fragmentos de código que muestran cómo se implementan los cmdlets y una explicación del código.</span><span class="sxs-lookup"><span data-stu-id="48b2f-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="48b2f-105">Temas de este tutorial</span><span class="sxs-lookup"><span data-stu-id="48b2f-105">Topics in this Tutorial</span></span>

<span data-ttu-id="48b2f-106">Los temas de este tutorial están diseñados para leerse secuencialmente, donde cada tema se basa en lo que se analizó en el tema anterior.</span><span class="sxs-lookup"><span data-stu-id="48b2f-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="48b2f-107">[Crear un cmdlet sin parámetros](./creating-a-cmdlet-without-parameters.md) En esta sección se describe cómo crear un cmdlet que recupera información del equipo local sin el uso de parámetros y, a continuación, escribe la información en la canalización.</span><span class="sxs-lookup"><span data-stu-id="48b2f-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="48b2f-108">[Agregar parámetros que procesan la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md) En esta sección se describe cómo agregar un parámetro al cmdlet Get-proc para que el cmdlet pueda procesar la entrada en función de los objetos explícitos pasados al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="48b2f-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="48b2f-109">La implementación que se describe aquí recupera procesos en función de su nombre y, a continuación, escribe la información en la canalización.</span><span class="sxs-lookup"><span data-stu-id="48b2f-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="48b2f-110">[Agregar parámetros que procesan la entrada de canalización](./adding-parameters-that-process-pipeline-input.md) En esta sección se describe cómo agregar un parámetro al cmdlet Get-proc para que el cmdlet pueda procesar los objetos que se le pasan a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="48b2f-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="48b2f-111">El cmdlet de implementación que se describe aquí recupera los procesos basados en los objetos que se pasan al cmdlet y, a continuación, escribe la información en la canalización.</span><span class="sxs-lookup"><span data-stu-id="48b2f-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="48b2f-112">[Agregar informes de errores de no terminación al cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) En esta sección se describe cómo agregar informes de errores de no terminación a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="48b2f-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="48b2f-113">La implementación que se describe aquí detecta los errores de no terminación que se producen al procesar la entrada y escribe un registro de error en la secuencia de error.</span><span class="sxs-lookup"><span data-stu-id="48b2f-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="48b2f-114">Véase también</span><span class="sxs-lookup"><span data-stu-id="48b2f-114">See Also</span></span>

[<span data-ttu-id="48b2f-115">Crear un cmdlet sin parámetros</span><span class="sxs-lookup"><span data-stu-id="48b2f-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="48b2f-116">Agregar parámetros que procesan la entrada de la línea de comandos</span><span class="sxs-lookup"><span data-stu-id="48b2f-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="48b2f-117">Agregar parámetros que procesan la entrada de canalización</span><span class="sxs-lookup"><span data-stu-id="48b2f-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="48b2f-118">Agregar informes de errores de no terminación al cmdlet</span><span class="sxs-lookup"><span data-stu-id="48b2f-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="48b2f-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="48b2f-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
