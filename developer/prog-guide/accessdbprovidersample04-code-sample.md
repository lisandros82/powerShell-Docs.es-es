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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081961"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="56c70-102">Ejemplo de código AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="56c70-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="56c70-103">El código siguiente muestra la implementación del proveedor de Windows PowerShell descrito en [creación de un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="56c70-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="56c70-104">Este proveedor funciona en los almacenes de datos de varias capas.</span><span class="sxs-lookup"><span data-stu-id="56c70-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="56c70-105">Para este tipo de almacén de datos, el nivel superior de la tienda contiene los elementos raíz y cada nivel posterior se conoce como un nodo de elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="56c70-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="56c70-106">Al permitir al usuario que funcionan en los siguientes nodos secundarios, un usuario puede interactuar de forma jerárquica a través del almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="56c70-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="56c70-107">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="56c70-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="56c70-108">Véase también</span><span class="sxs-lookup"><span data-stu-id="56c70-108">See Also</span></span>

[<span data-ttu-id="56c70-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="56c70-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)