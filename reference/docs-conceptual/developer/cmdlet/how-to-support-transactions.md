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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365544"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="5fa0b-102">Cómo admitir transacciones</span><span class="sxs-lookup"><span data-stu-id="5fa0b-102">How to Support Transactions</span></span>

<span data-ttu-id="5fa0b-103">En este ejemplo se muestran los elementos de código básicos que agregan compatibilidad para las transacciones a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fa0b-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fa0b-104">Para obtener más información acerca de cómo Windows PowerShell controla las transacciones, consulte [About Transactions][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="5fa0b-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="5fa0b-105">Para admitir transacciones</span><span class="sxs-lookup"><span data-stu-id="5fa0b-105">To support transactions</span></span>

1. <span data-ttu-id="5fa0b-106">Al declarar el atributo del cmdlet, especifique que el cmdlet admita las transacciones.</span><span class="sxs-lookup"><span data-stu-id="5fa0b-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="5fa0b-107">Cuando el cmdlet admite transacciones, Windows PowerShell agrega el parámetro `UseTransaction` al cmdlet cuando se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="5fa0b-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="5fa0b-108">Dentro de uno de los métodos de procesamiento de entrada, agregue un bloque `if` para determinar si una transacción está disponible.</span><span class="sxs-lookup"><span data-stu-id="5fa0b-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="5fa0b-109">Si la instrucción `if` se resuelve en `true`, se pueden realizar las acciones dentro de esta instrucción en el contexto de la transacción actual.</span><span class="sxs-lookup"><span data-stu-id="5fa0b-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="5fa0b-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="5fa0b-110">See Also</span></span>

[<span data-ttu-id="5fa0b-111">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fa0b-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
