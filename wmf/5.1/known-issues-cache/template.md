---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: plantilla de ejemplo de una escritura de problema o limitación conocida
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="41af6-103">Nota: Especifique un título descriptivo propuesto y una breve descripción</span><span class="sxs-lookup"><span data-stu-id="41af6-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="41af6-104">Ejemplo: Errores de ExecutionPolicy errónea</span><span class="sxs-lookup"><span data-stu-id="41af6-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="41af6-105">En Windows 7, el uso de módulos de PowerShell y recursos de DSC puede provocar la notificación de errores sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="41af6-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="41af6-106">Solución</span><span class="sxs-lookup"><span data-stu-id="41af6-106">Resolution</span></span>

<span data-ttu-id="41af6-107">Para resolverlo, establezca **ExecutionPolicy** en **RemoteSigned**. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):</span><span class="sxs-lookup"><span data-stu-id="41af6-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```