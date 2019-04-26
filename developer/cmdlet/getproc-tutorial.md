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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068103"
---
# <a name="getproc-tutorial"></a><span data-ttu-id="36345-102">Tutorial de GetProc</span><span class="sxs-lookup"><span data-stu-id="36345-102">GetProc Tutorial</span></span>

<span data-ttu-id="36345-103">Esta sección proporciona un tutorial para crear un cmdlet Get-Proc que es muy similar a la [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet proporcionado por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36345-103">This section provides a tutorial for creating a Get-Proc cmdlet that is very similar to the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="36345-104">Este tutorial proporciona fragmentos de código que ilustran cómo se implementan los cmdlets y obtener una explicación del código.</span><span class="sxs-lookup"><span data-stu-id="36345-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="36345-105">Temas de este Tutorial</span><span class="sxs-lookup"><span data-stu-id="36345-105">Topics in this Tutorial</span></span>

<span data-ttu-id="36345-106">Los temas de este tutorial están diseñados para que se leen secuencialmente, con cada tema Creación en lo que se ha explicado en el tema anterior.</span><span class="sxs-lookup"><span data-stu-id="36345-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="36345-107">[Creación de un Cmdlet sin parámetros](./creating-a-cmdlet-without-parameters.md) en esta sección se describe cómo crear un cmdlet que recupera información desde el equipo local sin el uso de parámetros y, a continuación, escribe la información en la canalización.</span><span class="sxs-lookup"><span data-stu-id="36345-107">[Creating a Cmdlet without Parameters](./creating-a-cmdlet-without-parameters.md) This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="36345-108">[Adición de parámetros de esa entrada de línea de comandos del proceso](./adding-parameters-that-process-command-line-input.md) en esta sección se describe cómo agregar un parámetro al cmdlet Get-Proc para que el cmdlet pueda procesar entradas basadas en objetos explícitos que se pasa al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="36345-108">[Adding Parameters that Process Command-Line Input](./adding-parameters-that-process-command-line-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process input based on explicit objects passed to the cmdlet.</span></span> <span data-ttu-id="36345-109">La implementación que se describe aquí recupera los procesos según su nombre y, a continuación, escribe la información en la canalización.</span><span class="sxs-lookup"><span data-stu-id="36345-109">The implementation described here retrieves processes based on their name, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="36345-110">[Agregar parámetros de entrada de la canalización de ese proceso](./adding-parameters-that-process-pipeline-input.md) en esta sección se describe cómo agregar un parámetro al cmdlet Get-Proc para que el cmdlet pueda procesar los objetos que se pasen a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="36345-110">[Adding Parameters that Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md) This section describes how to add a parameter to the Get-Proc cmdlet so that the cmdlet can process objects passed to it through the pipeline.</span></span> <span data-ttu-id="36345-111">El cmdlet de implementación que se describe aquí recupera los procesos basados en objetos que se pasan al cmdlet y, a continuación, escribe la información en la canalización.</span><span class="sxs-lookup"><span data-stu-id="36345-111">The implementation cmdlet described here retrieves processes based on objects passed to the cmdlet, and then writes the information to the pipeline.</span></span>

<span data-ttu-id="36345-112">[Agregar informes de errores de no terminación para su Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) en esta sección se describe cómo agregar informes a un cmdlet de errores de no terminación.</span><span class="sxs-lookup"><span data-stu-id="36345-112">[Adding Nonterminating Error Reporting to Your Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) This section describes how to add nonterminating error reporting to a cmdlet.</span></span> <span data-ttu-id="36345-113">La implementación que se describen aquí detecta errores de no terminación que se producen al procesar la entrada y escribe un registro de errores en la secuencia de error.</span><span class="sxs-lookup"><span data-stu-id="36345-113">The implementation described here detects nonterminating errors that occur when processing input, and writes an error record to the error stream.</span></span>

## <a name="see-also"></a><span data-ttu-id="36345-114">Véase también</span><span class="sxs-lookup"><span data-stu-id="36345-114">See Also</span></span>

[<span data-ttu-id="36345-115">Creación de un Cmdlet sin parámetros</span><span class="sxs-lookup"><span data-stu-id="36345-115">Creating a Cmdlet without Parameters</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="36345-116">Adición de parámetros que procesa la entrada de línea de comandos</span><span class="sxs-lookup"><span data-stu-id="36345-116">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="36345-117">Agregar parámetros de entrada de la canalización de proceso</span><span class="sxs-lookup"><span data-stu-id="36345-117">Adding Parameters that Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="36345-118">Agregar informes al Cmdlet de errores de no terminación</span><span class="sxs-lookup"><span data-stu-id="36345-118">Adding Nonterminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="36345-119">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="36345-119">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
