---
title: Creación de un flujo de trabajo mediante un Script de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853051"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="ef5e3-102">Creación de un flujo de trabajo mediante un script de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ef5e3-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="ef5e3-103">Puede crear un flujo de trabajo mediante la escritura de un script de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef5e3-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="ef5e3-104">Para crear un flujo de trabajo, use la palabra clave de flujo de trabajo seguida por un nombre para el flujo de trabajo antes del cuerpo de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="ef5e3-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="ef5e3-105">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="ef5e3-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="ef5e3-106">Encuentre el flujo de trabajo de la misma manera que lo haría con cualquier otro comando de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ef5e3-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="ef5e3-107">Implementación de secuencia y paralelas</span><span class="sxs-lookup"><span data-stu-id="ef5e3-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="ef5e3-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) admite la ejecución de actividades en paralelo.</span><span class="sxs-lookup"><span data-stu-id="ef5e3-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="ef5e3-109">Para implementar esta funcionalidad en un script de Windows PowerShell, use el `parallel` palabra clave delante de un bloque de script.</span><span class="sxs-lookup"><span data-stu-id="ef5e3-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="ef5e3-110">También puede usar el `foreach -parallel` construcción para recorrer en iteración una colección de objetos en paralelo.</span><span class="sxs-lookup"><span data-stu-id="ef5e3-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="ef5e3-111">Para ejecutar un grupo de actividades en orden secuencial dentro de un bloque paralelo, incluir ese grupo de actividades en un bloque de script y delante del bloque con la palabra clave de la secuencia.</span><span class="sxs-lookup"><span data-stu-id="ef5e3-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="ef5e3-112">Unir equipos a un dominio</span><span class="sxs-lookup"><span data-stu-id="ef5e3-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="ef5e3-113">El script siguiente crea un flujo de trabajo que comprueba el estado de dominio de un grupo de equipos especificado por el usuario, se une a un dominio si ya no están combinadas y, a continuación, comprueba el estado de nuevo.</span><span class="sxs-lookup"><span data-stu-id="ef5e3-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="ef5e3-114">Esta es una versión de la secuencia de comandos del flujo de trabajo XAML se explica en [crear un flujo de trabajo con actividades de Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="ef5e3-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
 }

```