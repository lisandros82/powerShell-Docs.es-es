---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: plantilla de ejemplo de una escritura de problema o limitación conocida
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055554"
---
 ><span data-ttu-id="28f15-103">Nota: Especifique un título descriptivo propuesto y una breve descripción</span><span class="sxs-lookup"><span data-stu-id="28f15-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="28f15-104">Ejemplo: errores de ExecutionPolicy errónea</span><span class="sxs-lookup"><span data-stu-id="28f15-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="28f15-105">En Windows 7, el uso de módulos de PowerShell y recursos de DSC puede provocar la notificación de errores sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="28f15-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="28f15-106">Solución</span><span class="sxs-lookup"><span data-stu-id="28f15-106">Resolution</span></span>

<span data-ttu-id="28f15-107">Para resolverlo, establezca **ExecutionPolicy** en **RemoteSigned**. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):</span><span class="sxs-lookup"><span data-stu-id="28f15-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
