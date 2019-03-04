---
title: Ejemplo de código AccessDbProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853611"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="f77ca-102">Ejemplo de código AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="f77ca-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="f77ca-103">El código siguiente muestra la implementación del proveedor de Windows PowerShell descrito en [creación de un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="f77ca-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="f77ca-104">Este proveedor funciona en los almacenes de datos de varias capas.</span><span class="sxs-lookup"><span data-stu-id="f77ca-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="f77ca-105">Para este tipo de almacén de datos, el nivel superior de la tienda contiene los elementos raíz y cada nivel posterior se conoce como un nodo de elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="f77ca-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="f77ca-106">Al permitir al usuario que funcionan en los siguientes nodos secundarios, un usuario puede interactuar de forma jerárquica a través del almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="f77ca-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f77ca-107">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="f77ca-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="f77ca-108">Véase también</span><span class="sxs-lookup"><span data-stu-id="f77ca-108">See Also</span></span>

[<span data-ttu-id="f77ca-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f77ca-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)