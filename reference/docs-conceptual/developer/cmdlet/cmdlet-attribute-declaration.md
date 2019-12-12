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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363544"
---
# <a name="cmdlet-attribute-declaration"></a>Declaración de atributo del cmdlet

El atributo de cmdlet identifica una clase de marco de Microsoft .NET como un cmdlet y especifica el verbo y el sustantivo que se usan para invocar el cmdlet.

## <a name="syntax"></a>Sintaxis

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parámetros

se requiere `VerbName` ([System. String](/dotnet/api/System.String)). Especifica el verbo del cmdlet. Este verbo especifica la acción realizada por el cmdlet. Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbo de cmdlet](./approved-verbs-for-windows-powershell-commands.md) y directrices de [desarrollo necesarias](./required-development-guidelines.md).

se requiere `NounName` ([System. String](/dotnet/api/System.String)). Especifica el nombre del cmdlet. Este nombre especifica el recurso sobre el que actúa el cmdlet. Para obtener más información sobre los nombres de cmdlet, consulte [declaración de cmdlets](./cmdlet-class-declaration.md) y [directrices de desarrollo muy alentadas](./strongly-encouraged-development-guidelines.md).

parámetro con nombre opcional `SupportsShouldProcess` ([System. Boolean](/dotnet/api/System.Boolean)). `True` indica que el cmdlet admite llamadas al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , que proporciona al cmdlet una manera de preguntar al usuario antes de que se realice una acción que cambia el sistema. `False`, el valor predeterminado, indica que el cmdlet no admite llamadas al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Para obtener más información acerca de las solicitudes de confirmación, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System. Management. Automation. Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) opcional parámetro con nombre. Especifica cuándo se debe confirmar la acción del cmdlet mediante una llamada al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solo se llamará cuando el valor ConfirmImpact del cmdlet (de forma predeterminada, Medium) sea igual o mayor que el valor de la variable `$ConfirmPreference`. Este parámetro debe especificarse solo cuando se especifica el parámetro `SupportsShouldProcess`.

parámetro con nombre opcional `DefaultParameterSetName` ([System. String](/dotnet/api/System.String)). Especifica el conjunto de parámetros predeterminado que el tiempo de ejecución de Windows PowerShell intenta usar cuando no puede determinar el conjunto de parámetros que se va a usar. Tenga en cuenta que esta situación se puede eliminar si hace que el parámetro único de cada parámetro establezca un parámetro obligatorio.

Hay un caso en el que Windows PowerShell no puede usar el conjunto de parámetros predeterminado aunque se especifique un nombre de conjunto de parámetros predeterminado. El tiempo de ejecución de Windows PowerShell no puede distinguir entre conjuntos de parámetros basados únicamente en el tipo de objeto. Por ejemplo, si tiene un conjunto de parámetros que toma una cadena como ruta de acceso del archivo y otro conjunto que toma un objeto **FileInfo** directamente, Windows PowerShell no puede determinar qué conjunto de parámetros debe usar en función de los valores que se pasan al cmdlet, ni tampoco usa el conjunto de parámetros predeterminado. En este caso, aunque especifique un nombre de conjunto de parámetros predeterminado, Windows PowerShell genera un mensaje de error de conjunto de parámetros ambiguos.

parámetro con nombre opcional `SupportsTransactions` ([System. Boolean](/dotnet/api/System.Boolean)). `True` indica que el cmdlet puede usarse dentro de una transacción. Cuando se especifica `True`, el tiempo de ejecución de Windows PowerShell agrega el parámetro `UseTransaction` a la lista de parámetros del cmdlet. `False`, el valor predeterminado, indica que el cmdlet no se puede usar en una transacción.

## <a name="remarks"></a>Observaciones

- Juntos, el verbo y el nombre se usan para identificar el cmdlet registrado e invocar el cmdlet en un script.

- Cuando el cmdlet se invoca desde la consola de Windows PowerShell, el comando es similar al siguiente comando:

**VerbName-NounName**

- Todos los cmdlets que cambian recursos fuera de Windows PowerShell deben incluir la palabra clave `SupportsShouldProcess` cuando se declara el atributo cmdlet, lo que permite que el cmdlet llame al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) antes de que el cmdlet realice su acción. Si la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) devuelve `false`, no se debe realizar la acción. Para obtener más información sobre las solicitudes de confirmación generadas por la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

Los parámetros de cmdlet `Confirm` y `WhatIf` solo están disponibles para los cmdlets que admiten llamadas a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .

## <a name="example"></a>Ejemplo

La siguiente definición de clase usa el atributo cmdlet para identificar la clase .NET Framework para un cmdlet **Get-proc** que recupera información sobre los procesos que se ejecutan en el equipo local.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Para obtener más información sobre el cmdlet **Get-proc** , vea el [tutorial de GetProc](./getproc-tutorial.md).

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
