---
title: Ejemplo de PowerShell02 de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: db7ff3a2dbd92f562379d206db494ab92ef08736
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367304"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="48510-102">Ejemplo Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="48510-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="48510-103">En este ejemplo se muestra cómo ejecutar comandos de forma asincrónica mediante los espacios de ejecución de un grupo de espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="48510-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="48510-104">En el ejemplo se genera una lista de comandos y, a continuación, se ejecutan esos comandos mientras el motor de Windows PowerShell abre un espacio de ejecución desde el grupo cuando es necesario.</span><span class="sxs-lookup"><span data-stu-id="48510-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="48510-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48510-105">Requirements</span></span>

- <span data-ttu-id="48510-106">Este ejemplo requiere Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="48510-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="48510-107">Demuestra</span><span class="sxs-lookup"><span data-stu-id="48510-107">Demonstrates</span></span>

<span data-ttu-id="48510-108">Este ejemplo muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="48510-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="48510-109">Crear un objeto RunspacePool con un número mínimo y máximo de espacios de tiempo permitidos que estén abiertos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="48510-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="48510-110">Crear una lista de comandos.</span><span class="sxs-lookup"><span data-stu-id="48510-110">Creating a list of commands.</span></span>

- <span data-ttu-id="48510-111">Ejecutar los comandos de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="48510-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="48510-112">Llamada al método [System. Management. Automation. espacios de Runspacepool. Getavailablerunspaces \*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) para ver cuántos espacios de administración son gratis.</span><span class="sxs-lookup"><span data-stu-id="48510-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="48510-113">Capturar la salida del comando con el método [System. Management. Automation. PowerShell. EndInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) .</span><span class="sxs-lookup"><span data-stu-id="48510-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="48510-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="48510-114">Example</span></span>

<span data-ttu-id="48510-115">En este ejemplo se muestra cómo abrir los espacios de ejecución de un grupo de espacio de ejecución y cómo ejecutar comandos de forma asincrónica en esos espacios de ejecución.</span><span class="sxs-lookup"><span data-stu-id="48510-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="48510-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="48510-116">See Also</span></span>

[<span data-ttu-id="48510-117">Escritura de una aplicación host de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="48510-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
