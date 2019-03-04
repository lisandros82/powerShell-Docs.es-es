---
title: Cómo admitir transacciones | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857121"
---
# <a name="how-to-support-transactions"></a>Cómo admitir transacciones

Este ejemplo muestra los elementos de código básico que agregan compatibilidad con transacciones a un cmdlet.

> [!IMPORTANT]
> Para obtener más información acerca de cómo Windows PowerShell controla las transacciones, vea [sobre transacciones][about_Transactions].

## <a name="to-support-transactions"></a>Para admitir las transacciones

1. Al declarar el atributo de Cmdlet, especificar que el cmdlet admite transacciones.
   Cuando el cmdlet admite transacciones, Windows PowerShell agrega la `UseTransaction` parámetro al cmdlet cuando se ejecuta.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Dentro de uno de los métodos de procesamiento de entrada, agregue un `if` bloque para determinar si una transacción está disponible.
   Si el `if` instrucción se resuelve en `true`, se pueden realizar las acciones dentro de esta instrucción dentro del contexto de la transacción actual.

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
