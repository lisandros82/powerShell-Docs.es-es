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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067865"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="ec99a-102">Cómo admitir transacciones</span><span class="sxs-lookup"><span data-stu-id="ec99a-102">How to Support Transactions</span></span>

<span data-ttu-id="ec99a-103">Este ejemplo muestra los elementos de código básico que agregan compatibilidad con transacciones a un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ec99a-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec99a-104">Para obtener más información acerca de cómo Windows PowerShell controla las transacciones, vea [sobre transacciones][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="ec99a-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="ec99a-105">Para admitir las transacciones</span><span class="sxs-lookup"><span data-stu-id="ec99a-105">To support transactions</span></span>

1. <span data-ttu-id="ec99a-106">Al declarar el atributo de Cmdlet, especificar que el cmdlet admite transacciones.</span><span class="sxs-lookup"><span data-stu-id="ec99a-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="ec99a-107">Cuando el cmdlet admite transacciones, Windows PowerShell agrega la `UseTransaction` parámetro al cmdlet cuando se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="ec99a-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="ec99a-108">Dentro de uno de los métodos de procesamiento de entrada, agregue un `if` bloque para determinar si una transacción está disponible.</span><span class="sxs-lookup"><span data-stu-id="ec99a-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="ec99a-109">Si el `if` instrucción se resuelve en `true`, se pueden realizar las acciones dentro de esta instrucción dentro del contexto de la transacción actual.</span><span class="sxs-lookup"><span data-stu-id="ec99a-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="ec99a-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="ec99a-110">See Also</span></span>

[<span data-ttu-id="ec99a-111">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec99a-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
