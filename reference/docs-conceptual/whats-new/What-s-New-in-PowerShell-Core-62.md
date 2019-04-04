---
title: Novedades de PowerShell Core 6.2
description: Nuevas características y cambios publicados en PowerShell Core 6.2
ms.date: 03/28/2019
ms.openlocfilehash: 2224d23a244175059a705c07001e8ad8d6ab3aa0
ms.sourcegitcommit: 8dd4394cf867005a8b9ef0bb74b744c964fbc332
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2019
ms.locfileid: "58750060"
---
# <a name="whats-new-in-powershell-core-62"></a>Novedades de PowerShell Core 6.2

Esta es una selección de algunas de las principales características nuevas y los cambios que se han incorporado en PowerShell Core 6.2.

También hay **toneladas** de "cosas aburridas" que hacen que PowerShell sea más rápido y más estable (además de montones y montones de correcciones de errores).
Si quiere ver una lista completa de los cambios, eche un vistazo a nuestro [registro de cambios en GitHub](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md).

Y aunque destacamos algunos nombres al final, queremos dar las gracias a [todos los colaboradores de la comunidad](https://github.com/PowerShell/PowerShell/graphs/contributors) que han hecho posible esta versión.

## <a name="engine-updates-and-fixes"></a>Actualizaciones y correcciones del motor

- Incorporación de mensajes de advertencia de cmdlet de habilitación o deshabilitación remota de PowerShell ([#9203][])
- Corrección de la regresión de deserialización remota `FormatTable` ([#9116][])
- Actualización de las API `async` basadas en tareas agregadas a PowerShell para devolver directamente un objeto de tarea ([#9079][])
- Incorporación de 5 cargas de trabajo `InvokeAsync` y `StopAsync` al tipo `PowerShell` ([#8056][]) (Muchas gracias, @KirkMunro)

## <a name="general-cmdlet-updates-and-fixes"></a>Actualizaciones y correcciones generales de cmdlet

- Habilitación de cmdlets `SecureString` para entornos que no son de Windows mediante el almacenamiento del texto sin formato ([#9199][])
- Incorporación de mensaje obsoleto en `Send-MailMessage` ([#9178][])
- Corrección de `Restart-Computer` para trabajar en `localhost` cuando WinRM no está presente ([#9160][])
- Generación de error de terminación `Start-Job` cuando se hospeda PowerShell ([#9128][])
- Actualización de la versión para `PowerShell.Native` y pruebas de hospedaje ([#8983][])

## <a name="breaking-changes"></a>Cambios importantes

Corrección del comportamiento -NoEnumerate en Write-Output para coherencia con Windows PowerShell ([#9069][]) (Muchas gracias, @vexx32)

<!-- Link references -->
[#8056]: https://github.com/PowerShell/PowerShell/pull/8056
[#8983]: https://github.com/PowerShell/PowerShell/pull/8983
[#9069]: https://github.com/PowerShell/PowerShell/pull/9069
[#9079]: https://github.com/PowerShell/PowerShell/pull/9079
[#9116]: https://github.com/PowerShell/PowerShell/pull/9116
[#9128]: https://github.com/PowerShell/PowerShell/pull/9128
[#9160]: https://github.com/PowerShell/PowerShell/pull/9160
[#9178]: https://github.com/PowerShell/PowerShell/pull/9178
[#9199]: https://github.com/PowerShell/PowerShell/pull/9199
[#9203]: https://github.com/PowerShell/PowerShell/pull/9203
