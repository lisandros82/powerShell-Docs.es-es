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
# <a name="accessdbprovidersample04-code-sample"></a>Ejemplo de código AccessDbProviderSample04

En el código siguiente se muestra la implementación del proveedor de Windows PowerShell que se describe en [crear un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md). Este proveedor funciona en almacenes de datos de varias capas. Para este tipo de almacén de datos, el nivel superior del almacén contiene los elementos raíz y cada nivel subsiguiente se denomina nodo de los elementos secundarios. Al permitir que el usuario trabaje en estos nodos secundarios, un usuario puede interactuar jerárquicamente a través del almacén de datos.

## <a name="code-sample"></a>Código de ejemplo

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Véase también

[Windows PowerShell SDK](../windows-powershell-reference.md)
