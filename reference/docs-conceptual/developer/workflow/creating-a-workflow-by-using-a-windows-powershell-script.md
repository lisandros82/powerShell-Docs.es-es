---
title: Crear un flujo de trabajo mediante un script de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366034"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a><span data-ttu-id="c553f-102">Creación de un flujo de trabajo mediante un script de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c553f-102">Creating a Workflow by Using a Windows PowerShell Script</span></span>

<span data-ttu-id="c553f-103">Puede crear un flujo de trabajo escribiendo un script de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c553f-103">You can create a workflow by writing a Windows PowerShell script.</span></span> <span data-ttu-id="c553f-104">Para crear un flujo de trabajo, utilice la palabra clave Workflow seguida de un nombre para el flujo de trabajo antes del cuerpo del script.</span><span class="sxs-lookup"><span data-stu-id="c553f-104">To create a workflow, use the workflow keyword followed by a name for the workflow before the body of the script.</span></span> <span data-ttu-id="c553f-105">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c553f-105">For example:</span></span>

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

<span data-ttu-id="c553f-106">El flujo de trabajo se encuentra de la misma manera que con cualquier otro comando de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c553f-106">You find the workflow in the same way you would any other Windows PowerShell command.</span></span>

## <a name="implementing-parallel-and-sequence"></a><span data-ttu-id="c553f-107">Implementar Parallel y Sequence</span><span class="sxs-lookup"><span data-stu-id="c553f-107">Implementing Parallel and Sequence</span></span>

<span data-ttu-id="c553f-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) admite la ejecución de actividades en paralelo.</span><span class="sxs-lookup"><span data-stu-id="c553f-108">[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) supports execution of activities in parallel.</span></span> <span data-ttu-id="c553f-109">Para implementar esta funcionalidad en un script de Windows PowerShell, use la palabra clave `parallel` delante de un bloque de script.</span><span class="sxs-lookup"><span data-stu-id="c553f-109">To implement this capability in a Windows PowerShell script, use the `parallel` keyword in front of a script block.</span></span> <span data-ttu-id="c553f-110">También puede utilizar la construcción `foreach -parallel` para recorrer en iteración una colección de objetos en paralelo.</span><span class="sxs-lookup"><span data-stu-id="c553f-110">You can also use the `foreach -parallel` construction to iterate through a collection of objects in parallel.</span></span> <span data-ttu-id="c553f-111">Para ejecutar un grupo de actividades en orden secuencial dentro de un bloque paralelo, incluya ese grupo de actividades en un bloque de script y preceda el bloque con la palabra clave Sequence.</span><span class="sxs-lookup"><span data-stu-id="c553f-111">To execute a group of activities in sequential order within a parallel block, enclose that group of activities in a script block and precede the block with the sequence keyword.</span></span>

## <a name="joining-computers-to-a-domain"></a><span data-ttu-id="c553f-112">Unir equipos a un dominio</span><span class="sxs-lookup"><span data-stu-id="c553f-112">Joining Computers to a Domain</span></span>

<span data-ttu-id="c553f-113">El siguiente script crea un flujo de trabajo que comprueba el estado de dominio de un grupo de equipos especificados por el usuario, los une a un dominio si aún no están Unidos y, a continuación, vuelve a comprobar el estado.</span><span class="sxs-lookup"><span data-stu-id="c553f-113">The following script creates a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span> <span data-ttu-id="c553f-114">Se trata de una versión de script del flujo de trabajo de XAML que se explica en [creación de un flujo de trabajo con actividades de Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md).</span><span class="sxs-lookup"><span data-stu-id="c553f-114">This is a script version of the XAML workflow explained in [Creating a Workflow with Windows PowerShell Activities](./creating-a-workflow-with-windows-powershell-activities.md).</span></span>

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