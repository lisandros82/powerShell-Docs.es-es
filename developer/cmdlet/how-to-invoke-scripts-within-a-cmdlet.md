---
title: Cómo invocar Scripts dentro de un Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 4b4d5645785b751eb1390e196f5b9437b4a1e13b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855841"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="34ba3-102">Cómo invocar scripts dentro de un cmdlet</span><span class="sxs-lookup"><span data-stu-id="34ba3-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="34ba3-103">En este ejemplo se muestra cómo invocar un script que se proporciona a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="34ba3-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="34ba3-104">El script se ejecuta el cmdlet y sus resultados se devuelven al cmdlet como una colección de [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objetos.</span><span class="sxs-lookup"><span data-stu-id="34ba3-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="34ba3-105">Para invocar un bloque de script</span><span class="sxs-lookup"><span data-stu-id="34ba3-105">To invoke a script block</span></span>

1. <span data-ttu-id="34ba3-106">El comando comprueba que se proporcionó un bloque de script al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="34ba3-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="34ba3-107">Si se ha proporcionado un bloque de script, el comando invoca el bloque de script con sus parámetros necesarios.</span><span class="sxs-lookup"><span data-stu-id="34ba3-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. <span data-ttu-id="34ba3-108">A continuación, el script recorre en iteración la colección devuelta de [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objetos y realizar las operaciones necesarias.</span><span class="sxs-lookup"><span data-stu-id="34ba3-108">Then, the script iterates through the returned collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a><span data-ttu-id="34ba3-109">Véase también</span><span class="sxs-lookup"><span data-stu-id="34ba3-109">See Also</span></span>

[<span data-ttu-id="34ba3-110">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="34ba3-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)