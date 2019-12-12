---
title: Alias de cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369984"
---
# <a name="cmdlet-aliases"></a>Alias del cmdlet

Puede utilizar alias de cmdlet para mejorar la experiencia de usuario del cmdlet. Puede Agregar alias a los cmdlets de uso frecuente para reducir la escritura y facilitar la finalización de las tareas rápidamente. Puede incluir alias integrados en los cmdlets o los usuarios pueden definir sus propios alias personalizados.

Por ejemplo, el cmdlet [get-command](/powershell/module/microsoft.powershell.core/get-command) tiene un alias de `gcm` integrado. También puede usar alias para agregar nombres de comando desde otros idiomas para que los usuarios no tengan que aprender nuevos comandos.

## <a name="alias-guidelines"></a>Instrucciones de alias

Siga estas instrucciones cuando cree alias integrados para los cmdlets:

- Antes de asignar alias, inicie Windows PowerShell y, a continuación, ejecute el cmdlet [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) para ver los alias que ya se usan.

- Incluya un prefijo de alias que haga referencia al verbo del nombre del cmdlet y un sufijo de alias que haga referencia al nombre del cmdlet. Por ejemplo, el alias del cmdlet `Import-Module` es "IPMO". Para obtener una lista de todos los verbos y sus alias, vea [verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).

- Para los cmdlets que tienen el mismo verbo, incluya el mismo prefijo de alias. Por ejemplo, los alias de todos los cmdlets de Windows PowerShell que tienen el verbo "Get" en su nombre usan el prefijo "g".

- Para los cmdlets que tienen el mismo nombre, incluya el mismo sufijo de alias. Por ejemplo, los alias de todos los cmdlets de Windows PowerShell que tienen el nombre "session" en su nombre usan el sufijo "SN".

- Para los cmdlets que son equivalentes a los comandos en otros lenguajes, utilice el nombre del comando.

- En general, cree alias lo más cortos posible. Asegúrese de que el alias tiene al menos un carácter distinto para el verbo y un carácter distinto para el nombre. Agregue más caracteres según sea necesario para que el alias sea único.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
