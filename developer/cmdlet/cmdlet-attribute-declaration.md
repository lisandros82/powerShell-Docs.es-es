---
title: Declaración de atributo de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068630"
---
# <a name="cmdlet-attribute-declaration"></a>Declaración de atributo del cmdlet

El atributo de Cmdlet identifica una clase de Microsoft .NET Framework como un cmdlet y especifica el verbo y sustantivo que se usa para invocar el cmdlet.

## <a name="syntax"></a>Sintaxis

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parámetros

`VerbName` ([System.String](/dotnet/api/System.String)) necesarios. Especifica el verbo del cmdlet. Este verbo especifica la acción realizada por el cmdlet. Para obtener más información acerca de los verbos de cmdlet aprobadas, consulte [los nombres de verbo del Cmdlet](./approved-verbs-for-windows-powershell-commands.md) y [las instrucciones de desarrollo necesario](./required-development-guidelines.md).

`NounName` ([System.String](/dotnet/api/System.String)) necesarios. Especifica el nombre de cmdlet. Este nombre especifica el recurso que actúa el cmdlet. Para obtener más información sobre los nombres de cmdlet, consulte [Cmdlet declaración](./cmdlet-class-declaration.md) y [aconseja encarecidamente instrucciones de desarrollo](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional. `True` indica que el cmdlet admite llamadas a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, que proporciona un mecanismo para preguntar al usuario antes de realiza una acción que cambia el sistema el cmdlet. `False`, el valor predeterminado, indica que el cmdlet no admite llamadas a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. Para obtener más información acerca de las solicitudes de confirmación, vea [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) con el nombre de parámetro opcional. Especifica cuándo se debe confirmar la acción del cmdlet mediante una llamada a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solo se llamará cuando el valor de ConfirmImpact del cmdlet (de forma predeterminada, Media) es igual o mayor que el valor de la `$ConfirmPreference` variable. Este parámetro debe especificarse solo cuando el `SupportsShouldProcess` se especifica el parámetro.

`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) con el nombre de parámetro opcional. Especifica que el parámetro predeterminado establecido que el tiempo de ejecución de Windows PowerShell intenta usar cuando no se puede determinar qué conjunto de parámetros para usar. Tenga en cuenta que esta situación se puede eliminar mediante la realización de establecer un parámetro obligatorio el parámetro unique de cada parámetro.

Hay un caso donde Windows PowerShell no se puede usar el parámetro predeterminado configurado incluso si se especifica un nombre de conjunto de parámetro predeterminado. El tiempo de ejecución de Windows PowerShell no puede distinguir entre los conjuntos de parámetros basándose únicamente en el tipo de objeto. Por ejemplo, si tiene un conjunto de parámetros que toma una cadena como la ruta de acceso de archivo y otro conjunto que toma un **FileInfo** objeto directamente, Windows PowerShell no puede determinar qué parámetro configurado para usar en función de los valores pasados a la el cmdlet, ni usa el conjunto de parámetros de forma predeterminada. En este caso, incluso si se especifica que un parámetro predeterminado establece el nombre, Windows PowerShell genera un mensaje de error de conjunto de parámetro ambiguo.

`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) con el nombre de parámetro opcional. `True` indica que el cmdlet puede usarse dentro de una transacción. Cuando `True` se especifica, el tiempo de ejecución de Windows PowerShell agrega la `UseTransaction` parámetro a la lista de parámetros del cmdlet. `False`, el valor predeterminado, indica que no se puede usar el cmdlet dentro de una transacción.

## <a name="remarks"></a>Observaciones

- Juntos, el verbo y sustantivo se usan para identificar su cmdlet registrado e invocar el cmdlet dentro de una secuencia de comandos.

- Cuando se invoca el cmdlet desde la consola de Windows PowerShell, el comando es similar a lo siguiente:

**VerbName-NounName**

- Todos los cmdlets que cambian los recursos fuera de Windows PowerShell debe incluir el `SupportsShouldProcess` palabra clave cuando se declara el atributo de Cmdlet, que permite al cmdlet llamar el [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método antes de que el cmdlet realice su acción. Si el [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) llamada devuelve `false`, no se debe realizar la acción. Para obtener más información acerca de las solicitudes de confirmación generados por el [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) llamar, vea [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

El `Confirm` y `WhatIf` parámetros del cmdlet solo están disponibles para los cmdlets que admiten [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) llamadas.

## <a name="example"></a>Ejemplo

La definición de clase siguiente utiliza el atributo de Cmdlet para identificar la clase de .NET Framework para un **Get-Proc** cmdlet que recupera información acerca de los procesos que se ejecutan en el equipo local.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Para obtener más información sobre la **Get-Proc** cmdlet, consulte [GetProc Tutorial](./getproc-tutorial.md).

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
