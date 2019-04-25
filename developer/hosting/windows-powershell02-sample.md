---
title: Ejemplo de Windows PowerShell02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92492a7e-257d-47d3-b119-89df3c5545e8
caps.latest.revision: 9
ms.openlocfilehash: 89ad17257ebac56105a93672317a149515e80d32
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082522"
---
# <a name="windows-powershell02-sample"></a><span data-ttu-id="4ac63-102">Ejemplo Windows PowerShell02</span><span class="sxs-lookup"><span data-stu-id="4ac63-102">Windows PowerShell02 Sample</span></span>

<span data-ttu-id="4ac63-103">Este ejemplo muestra cómo ejecutar comandos de forma asincrónica mediante el uso de los espacios de ejecución de un grupo de espacio de ejecución.</span><span class="sxs-lookup"><span data-stu-id="4ac63-103">This sample shows how to run commands asynchronously by using the runspaces of a runspace pool.</span></span> <span data-ttu-id="4ac63-104">El ejemplo genera una lista de comandos y, a continuación, ejecuta esos comandos mientras el motor de Windows PowerShell abre un espacio de ejecución de la agrupación cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="4ac63-104">The sample generates a list of commands, and then runs those commands while the Windows PowerShell engine opens a runspace from the pool when it is needed.</span></span>

## <a name="requirements"></a><span data-ttu-id="4ac63-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ac63-105">Requirements</span></span>

- <span data-ttu-id="4ac63-106">Este ejemplo requiere Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="4ac63-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="4ac63-107">Muestra</span><span class="sxs-lookup"><span data-stu-id="4ac63-107">Demonstrates</span></span>

<span data-ttu-id="4ac63-108">Este ejemplo muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ac63-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="4ac63-109">Creación de un objeto RunspacePool con un número mínimo y máximo de espacios de ejecución pueda estar abiertos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="4ac63-109">Creating a RunspacePool object with a minimum and maximum number of runspaces allowed to be open at the same time.</span></span>

- <span data-ttu-id="4ac63-110">Creación de una lista de comandos.</span><span class="sxs-lookup"><span data-stu-id="4ac63-110">Creating a list of commands.</span></span>

- <span data-ttu-id="4ac63-111">Ejecute los comandos de forma asincrónica.</span><span class="sxs-lookup"><span data-stu-id="4ac63-111">Running the commands asynchronously.</span></span>

- <span data-ttu-id="4ac63-112">Una llamada a la [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) método para ver cuántos espacios de ejecución son gratuitas.</span><span class="sxs-lookup"><span data-stu-id="4ac63-112">Calling the [System.Management.Automation.Runspaces.Runspacepool.Getavailablerunspaces\*](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool.GetAvailableRunspaces) method to see how many runspaces are free.</span></span>

- <span data-ttu-id="4ac63-113">Capturar la salida del comando con el [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) método.</span><span class="sxs-lookup"><span data-stu-id="4ac63-113">Capturing the command output with the [System.Management.Automation.Powershell.Endinvoke\*](/dotnet/api/System.Management.Automation.PowerShell.EndInvoke) method.</span></span>

## <a name="example"></a><span data-ttu-id="4ac63-114">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="4ac63-114">Example</span></span>

<span data-ttu-id="4ac63-115">Este ejemplo muestra cómo abrir los espacios de ejecución de un grupo de espacio de ejecución y cómo ejecutar de forma asincrónica comandos en esos espacios de ejecución.</span><span class="sxs-lookup"><span data-stu-id="4ac63-115">This sample shows how to open the runspaces of a runspace pool, and how to asynchronously run commands in those runspaces.</span></span>

[!code-csharp[PowerShell02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/PowerShell02/PowerShell02.cs#L11-L96 "PowerShell02.cs")]

## <a name="see-also"></a><span data-ttu-id="4ac63-116">Véase también</span><span class="sxs-lookup"><span data-stu-id="4ac63-116">See Also</span></span>

[<span data-ttu-id="4ac63-117">Escribir una aplicación de Host de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="4ac63-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)