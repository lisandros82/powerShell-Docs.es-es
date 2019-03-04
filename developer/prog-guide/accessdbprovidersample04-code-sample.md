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
# <a name="accessdbprovidersample04-code-sample"></a>Ejemplo de código AccessDbProviderSample04

El código siguiente muestra la implementación del proveedor de Windows PowerShell descrito en [creación de un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md). Este proveedor funciona en los almacenes de datos de varias capas. Para este tipo de almacén de datos, el nivel superior de la tienda contiene los elementos raíz y cada nivel posterior se conoce como un nodo de elementos secundarios. Al permitir al usuario que funcionan en los siguientes nodos secundarios, un usuario puede interactuar de forma jerárquica a través del almacén de datos.

## <a name="code-sample"></a>Ejemplo de código

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Véase también

[Windows PowerShell SDK](../windows-powershell-reference.md)