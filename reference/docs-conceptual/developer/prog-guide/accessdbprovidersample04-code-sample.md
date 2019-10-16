---
title: Código de ejemplo de AccessDbProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: ff43286bc90c1a4d2270be0ee03ca5910867cec2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366974"
---
# <a name="accessdbprovidersample04-code-sample"></a><span data-ttu-id="a283f-102">Ejemplo de código AccessDbProviderSample04</span><span class="sxs-lookup"><span data-stu-id="a283f-102">AccessDbProviderSample04 Code Sample</span></span>

<span data-ttu-id="a283f-103">En el código siguiente se muestra la implementación del proveedor de Windows PowerShell que se describe en [crear un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a283f-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span> <span data-ttu-id="a283f-104">Este proveedor funciona en almacenes de datos de varias capas.</span><span class="sxs-lookup"><span data-stu-id="a283f-104">This provider works on multi-layer data stores.</span></span> <span data-ttu-id="a283f-105">Para este tipo de almacén de datos, el nivel superior del almacén contiene los elementos raíz y cada nivel subsiguiente se denomina nodo de los elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="a283f-105">For this type of data store, the top level of the store contains the root items and each subsequent level is referred to as a node of child items.</span></span> <span data-ttu-id="a283f-106">Al permitir que el usuario trabaje en estos nodos secundarios, un usuario puede interactuar jerárquicamente a través del almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="a283f-106">By allowing the user to work on these child nodes, a user can interact hierarchically through the data store.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a283f-107">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="a283f-107">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="a283f-108">Véase también</span><span class="sxs-lookup"><span data-stu-id="a283f-108">See Also</span></span>

[<span data-ttu-id="a283f-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a283f-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
