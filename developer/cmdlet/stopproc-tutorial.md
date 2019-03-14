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
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794406"
---
# <a name="stopproc-tutorial"></a><span data-ttu-id="37772-102">Tutorial de StopProc</span><span class="sxs-lookup"><span data-stu-id="37772-102">StopProc Tutorial</span></span>

<span data-ttu-id="37772-103">Esta sección proporciona un tutorial para crear el cmdlet Stop-Proc, que es muy similar a la [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet proporcionado por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="37772-103">This section provides a tutorial for creating the Stop-Proc cmdlet, which is very similar to the [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet provided by Windows PowerShell.</span></span> <span data-ttu-id="37772-104">Este tutorial proporciona fragmentos de código que ilustran cómo se implementan los cmdlets y obtener una explicación del código.</span><span class="sxs-lookup"><span data-stu-id="37772-104">This tutorial provides fragments of code that illustrate how cmdlets are implemented, and an explanation of the code.</span></span>

## <a name="topics-in-this-tutorial"></a><span data-ttu-id="37772-105">Temas de este Tutorial</span><span class="sxs-lookup"><span data-stu-id="37772-105">Topics in this Tutorial</span></span>

<span data-ttu-id="37772-106">Los temas de este tutorial están diseñados para que se leen secuencialmente, con cada tema Creación en lo que se ha explicado en el tema anterior.</span><span class="sxs-lookup"><span data-stu-id="37772-106">The topics in this tutorial are designed to be read sequentially, with each topic building on what was discussed in the previous topic.</span></span>

<span data-ttu-id="37772-107">[Creación de un Cmdlet que modifica el sistema](./creating-a-cmdlet-that-modifies-the-system.md) en esta sección se describe cómo crear un cmdlet que es compatible con las modificaciones del sistema, como detener un proceso que se ejecuta en el equipo.</span><span class="sxs-lookup"><span data-stu-id="37772-107">[Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md) This section describes how to create a cmdlet that supports system modifications, such as stopping a process running on the computer.</span></span>

<span data-ttu-id="37772-108">[Agregar mensajes de usuario a su Cmdlet](./adding-user-messages-to-your-cmdlet.md) en esta sección se describe cómo agregar la capacidad para escribir información de progreso, mensajes de depuración, los mensajes de advertencia y mensajes de usuario al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="37772-108">[Adding User Messages to Your Cmdlet](./adding-user-messages-to-your-cmdlet.md) This section describes how to add the ability to write user messages, debug messages, warning messages, and progress information to your cmdlet.</span></span>

<span data-ttu-id="37772-109">[Agregar alias, expansión de caracteres comodín y ayudar a los parámetros de Cmdlet](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) en esta sección se describe cómo crear un cmdlet que admite la expansión de caracteres comodín, ayuda y alias de parámetro.</span><span class="sxs-lookup"><span data-stu-id="37772-109">[Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) This section describes how to create a cmdlet that supports parameter aliases, Help, and wildcard expansion.</span></span>

<span data-ttu-id="37772-110">[Agregar conjuntos de parámetros en los Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) en esta sección se describe cómo agregar el parámetro se establece en un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="37772-110">[Adding Parameter Sets to Cmdlets](./adding-parameter-sets-to-a-cmdlet.md) This section describes how to add parameter sets to a cmdlet.</span></span> <span data-ttu-id="37772-111">Conjuntos de parámetros que el cmdlet pueda funcionar forma diferente basándose en los parámetros que se especifican por el usuario.</span><span class="sxs-lookup"><span data-stu-id="37772-111">Parameter sets allow the cmdlet to operate differently based on what parameters are specified by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="37772-112">Véase también</span><span class="sxs-lookup"><span data-stu-id="37772-112">See Also</span></span>

[<span data-ttu-id="37772-113">Creación de un Cmdlet que modifica el sistema</span><span class="sxs-lookup"><span data-stu-id="37772-113">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="37772-114">Agregar mensajes de usuario al Cmdlet</span><span class="sxs-lookup"><span data-stu-id="37772-114">Adding User Messages to Your Cmdlet</span></span>](./adding-user-messages-to-your-cmdlet.md)

[<span data-ttu-id="37772-115">Agregar alias, expansión de caracteres comodín y ayudar a los parámetros de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="37772-115">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[<span data-ttu-id="37772-116">Agregar parámetro conjuntos a los Cmdlets</span><span class="sxs-lookup"><span data-stu-id="37772-116">Adding Parameter Sets to Cmdlets</span></span>](./adding-parameter-sets-to-a-cmdlet.md)

[<span data-ttu-id="37772-117">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="37772-117">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
