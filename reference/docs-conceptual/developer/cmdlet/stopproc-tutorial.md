---
title: Tutorial de StopProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369414"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="9d152-102">Tutorial de StopProc</span><span class="sxs-lookup"><span data-stu-id="9d152-102">StopProc Tutorial</span></span>

<span data-ttu-id="9d152-103">En esta sección se proporciona un tutorial para crear el cmdlet Stop-proc, que es muy similar al cmdlet [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) proporcionado por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9d152-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="9d152-104">En este tutorial se proporcionan fragmentos de código que muestran cómo se implementan los cmdlets y una explicación del código.</span><span class="sxs-lookup"><span data-stu-id="9d152-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="9d152-105">Temas de este tutorial</span><span class="sxs-lookup"><span data-stu-id="9d152-105">Topics in this Tutorial</span></span>

<span data-ttu-id="9d152-106">Los temas de este tutorial están diseñados para leerse secuencialmente, donde cada tema se basa en lo que se analizó en el tema anterior.</span><span class="sxs-lookup"><span data-stu-id="9d152-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="9d152-107">[Creación de un cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md) En esta sección se describe cómo crear un cmdlet que admita modificaciones del sistema, como la detención de un proceso que se ejecuta en el equipo.</span><span class="sxs-lookup"><span data-stu-id="9d152-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="9d152-108">[Agregar mensajes de usuario al cmdlet](./adding-user-messages-to-your-cmdlet.md) En esta sección se describe cómo agregar la capacidad de escribir mensajes de usuario, mensajes de depuración, mensajes de advertencia e información de progreso en el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9d152-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="9d152-109">[Agregar alias, expansión de caracteres comodín y ayuda para los parámetros de cmdlet](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) En esta sección se describe cómo crear un cmdlet que admita alias de parámetros, ayuda y expansión de caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="9d152-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="9d152-110">[Agregar conjuntos de parámetros a cmdlets](./adding-parameter-sets-to-a-cmdlet.md) En esta sección se describe cómo agregar conjuntos de parámetros a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9d152-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="9d152-111">Los conjuntos de parámetros permiten que el cmdlet funcione de forma diferente en función de los parámetros especificados por el usuario.</span><span class="sxs-lookup"><span data-stu-id="9d152-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d152-112">Véase también</span><span class="sxs-lookup"><span data-stu-id="9d152-112">See Also</span></span>

[<span data-ttu-id="9d152-113">Creación de un cmdlet que modifica el sistema</span><span class="sxs-lookup"><span data-stu-id="9d152-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="9d152-114">Agregar mensajes de usuario al cmdlet</span><span class="sxs-lookup"><span data-stu-id="9d152-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="9d152-115">Agregar alias, expansión de caracteres comodín y ayuda para los parámetros de cmdlet</span><span class="sxs-lookup"><span data-stu-id="9d152-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="9d152-116">Agregar conjuntos de parámetros a cmdlets</span><span class="sxs-lookup"><span data-stu-id="9d152-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="9d152-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9d152-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
