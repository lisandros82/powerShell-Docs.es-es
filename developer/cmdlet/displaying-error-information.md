---
title: Mostrar información de Error | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858281"
---
# <a name="displaying-error-information"></a><span data-ttu-id="d5781-102">Muestra de información del error</span><span class="sxs-lookup"><span data-stu-id="d5781-102">Displaying Error Information</span></span>

<span data-ttu-id="d5781-103">En este tema se describe las maneras en que los usuarios pueden mostrar información de error.</span><span class="sxs-lookup"><span data-stu-id="d5781-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="d5781-104">Cuando el cmdlet encuentra un error, la presentación de la información de error será, de forma predeterminada, similar a la siguiente salida de error.</span><span class="sxs-lookup"><span data-stu-id="d5781-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="d5781-105">Sin embargo, los usuarios pueden ver los errores por categoría estableciendo el `$ErrorView` variable `"CategoryView"`.</span><span class="sxs-lookup"><span data-stu-id="d5781-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="d5781-106">Vista por categorías muestra información específica desde el registro de error en lugar de una descripción textual del error.</span><span class="sxs-lookup"><span data-stu-id="d5781-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="d5781-107">Esta vista puede ser útil si tiene una larga lista de errores de análisis.</span><span class="sxs-lookup"><span data-stu-id="d5781-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="d5781-108">En la vista por categorías, el mensaje de error anterior se muestra como se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="d5781-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="d5781-109">Para obtener más información acerca de las categorías de error, consulte [registros de Error de Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="d5781-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5781-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="d5781-110">See Also</span></span>

[<span data-ttu-id="d5781-111">Registros de errores de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="d5781-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="d5781-112">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5781-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
