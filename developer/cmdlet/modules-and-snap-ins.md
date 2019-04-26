---
title: Los módulos y complementos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067627"
---
# <a name="modules-and-snap-ins"></a>Módulos y complementos

Los cmdlets se pueden agregar a una sesión mediante complementos o módulos (introducidos en Windows PowerShell 2.0). Una vez que el cmdlet se agrega a la sesión que se puede ejecutar mediante programación mediante una aplicación host o de forma interactiva en la línea de comandos.

Se recomienda que use módulos como método de entrega para agregar cmdlets a una sesión por las razones siguientes:

- Los módulos permiten agregar cmdlets al cargar el ensamblado donde se define el cmdlet. No hay ninguna necesidad de implementar una clase de complemento.

- Los módulos permiten agregar otros recursos, como variables, funciones, scripts, tipos y formato archivos y mucho más.

- Complementos pueden usarse únicamente para agregar los cmdlets y proveedores a la sesión.

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
