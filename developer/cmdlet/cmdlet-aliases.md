---
title: Alias de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068732"
---
# <a name="cmdlet-aliases"></a>Alias del cmdlet

Puede usar el alias de cmdlet para mejorar la experiencia de usuario de cmdlet. Puede agregar alias a los cmdlets usados con frecuencia para reducir escribir y para que resulte más fácil completar tareas rápidamente. Puede incluir los alias integrados en los cmdlets o los usuarios pueden definir sus propios alias personalizados.

Por ejemplo, el [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet tiene integrada una `gcm` alias. También puede utilizar alias para agregar nombres de comando de otros idiomas para que los usuarios no tiene que aprender nuevos comandos.

## <a name="alias-guidelines"></a>Directrices de alias

Cuando se creación el alias integrados en sus cmdlets, siga estas instrucciones:

- Antes de asignar los alias, inicie Windows PowerShell y, a continuación, ejecute el [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet para ver los alias que ya se usan.

- Incluir un prefijo de alias que hace referencia el verbo del nombre del cmdlet y un sufijo de alias que hace referencia el nombre del nombre del cmdlet. Por ejemplo, el alias para el `Import-Module` cmdlet es "ipmo". Para obtener una lista de todos los verbos y sus alias, vea [verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).

- Para los cmdlets que tengan el mismo verbo, incluyen el mismo prefijo de alias. Por ejemplo, los alias para todos los cmdlets de Windows PowerShell que tienen el verbo "Get" en su nombre para usar el prefijo "g".

- Para los cmdlets que tengan el mismo nombre, incluya el mismo sufijo de alias. Por ejemplo, los alias para todos los cmdlets de Windows PowerShell que contienen el término "Sesión" en su nombre para usar el sufijo "sn".

- Para los cmdlets que son equivalentes a los comandos en otros idiomas, use el nombre del comando.

- En general, asegúrese de alias más breve posible. Asegúrese de que el alias tiene al menos un carácter distinto para el verbo y un carácter distinto para el nombre. Agregue más caracteres según sea necesario para que sea el alias único.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
