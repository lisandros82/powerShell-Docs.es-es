---
title: Cómo invocar scripts dentro de un cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364414"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Cómo invocar scripts dentro de un cmdlet

En este ejemplo se muestra cómo invocar un script que se proporciona a un cmdlet. El cmdlet ejecuta el script y sus resultados se devuelven al cmdlet como una colección de objetos [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) .

## <a name="to-invoke-a-script-block"></a>Para invocar un bloque de script

1. El comando comprueba que se ha proporcionado un bloque de script al cmdlet. Si se proporciona un bloque de script, el comando invoca el bloque de script con sus parámetros necesarios.

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

2. A continuación, el script recorre en iteración la colección devuelta de objetos [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) y realiza las operaciones necesarias.

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

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
