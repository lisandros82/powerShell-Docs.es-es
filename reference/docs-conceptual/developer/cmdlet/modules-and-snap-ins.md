---
title: Módulos y complementos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365374"
---
# <a name="modules-and-snap-ins"></a>Módulos y complementos

Los cmdlets se pueden agregar a una sesión mediante módulos (introducidos por Windows PowerShell 2,0) o complementos. Una vez que el cmdlet se agrega a la sesión, se puede ejecutar mediante programación en una aplicación host o de forma interactiva en la línea de comandos.

Se recomienda usar módulos como método de entrega para agregar cmdlets a una sesión por los siguientes motivos:

- Los módulos permiten agregar cmdlets cargando el ensamblado donde se define el cmdlet. No es necesario implementar una clase de complemento.

- Los módulos permiten agregar otros recursos, como variables, funciones, scripts, tipos y archivos de formato, etc.

- Los complementos solo se pueden usar para agregar cmdlets y proveedores a la sesión.

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
