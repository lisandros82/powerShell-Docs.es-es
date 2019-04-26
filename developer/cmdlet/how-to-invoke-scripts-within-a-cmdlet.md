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
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067882"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Cómo invocar scripts dentro de un cmdlet

En este ejemplo se muestra cómo invocar un script que se proporciona a un cmdlet. El script se ejecuta el cmdlet y sus resultados se devuelven al cmdlet como una colección de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objetos.

## <a name="to-invoke-a-script-block"></a>Para invocar un bloque de script

1. El comando comprueba que se proporcionó un bloque de script al cmdlet. Si se ha proporcionado un bloque de script, el comando invoca el bloque de script con sus parámetros necesarios.

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

2. A continuación, el script recorre en iteración la colección devuelta de [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objetos y realizar las operaciones necesarias.

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
