---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: "plantilla de ejemplo de una escritura de problema o limitación conocida"
ms.openlocfilehash: b93393b2c84e76a301e6406d1388e82e95a2959c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
><span data-ttu-id="818a5-103">Nota: Especifique un título descriptivo propuesto y una breve descripción</span><span class="sxs-lookup"><span data-stu-id="818a5-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="818a5-104">Ejemplo: Errores de ExecutionPolicy errónea</span><span class="sxs-lookup"><span data-stu-id="818a5-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="818a5-105">En Windows 7, el uso de módulos de PowerShell y recursos de DSC puede provocar la notificación de errores sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="818a5-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="818a5-106">Solución</span><span class="sxs-lookup"><span data-stu-id="818a5-106">Resolution</span></span>

<span data-ttu-id="818a5-107">Para resolverlo, establezca **ExecutionPolicy** en **RemoteSigned**. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):</span><span class="sxs-lookup"><span data-stu-id="818a5-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

