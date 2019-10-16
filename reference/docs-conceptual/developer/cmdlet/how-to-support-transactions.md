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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365544"
---
# <a name="how-to-support-transactions"></a>Cómo admitir transacciones

En este ejemplo se muestran los elementos de código básicos que agregan compatibilidad para las transacciones a un cmdlet.

> [!IMPORTANT]
> Para obtener más información acerca de cómo Windows PowerShell controla las transacciones, consulte [About Transactions][about_Transactions].

## <a name="to-support-transactions"></a>Para admitir transacciones

1. Al declarar el atributo del cmdlet, especifique que el cmdlet admita las transacciones.
   Cuando el cmdlet admite transacciones, Windows PowerShell agrega el parámetro `UseTransaction` al cmdlet cuando se ejecuta.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Dentro de uno de los métodos de procesamiento de entrada, agregue un bloque `if` para determinar si una transacción está disponible.
   Si la instrucción `if` se resuelve en `true`, las acciones dentro de esta instrucción se pueden realizar dentro del contexto de la transacción actual.

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
