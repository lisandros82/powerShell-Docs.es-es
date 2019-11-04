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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363544"
---
# <a name="cmdlet-attribute-declaration"></a><span data-ttu-id="0083d-102">Declaración de atributo del cmdlet</span><span class="sxs-lookup"><span data-stu-id="0083d-102">Cmdlet Attribute Declaration</span></span>

<span data-ttu-id="0083d-103">El atributo de cmdlet identifica una clase de marco de Microsoft .NET como un cmdlet y especifica el verbo y el sustantivo que se usan para invocar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0083d-103">The Cmdlet attribute identifies a Microsoft .NET Framework class as a cmdlet and specifies the verb and noun used to invoke the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="0083d-104">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="0083d-104">Syntax</span></span>

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="0083d-105">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0083d-105">Parameters</span></span>

<span data-ttu-id="0083d-106">`VerbName` ([System. String](/dotnet/api/System.String)) requerido.</span><span class="sxs-lookup"><span data-stu-id="0083d-106">`VerbName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="0083d-107">Especifica el verbo del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0083d-107">Specifies the cmdlet verb.</span></span> <span data-ttu-id="0083d-108">Este verbo especifica la acción realizada por el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0083d-108">This verb specifies the action taken by the cmdlet.</span></span> <span data-ttu-id="0083d-109">Para obtener más información sobre los verbos de cmdlet aprobados, consulte [nombres de verbo de cmdlet](./approved-verbs-for-windows-powershell-commands.md) y directrices de [desarrollo necesarias](./required-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="0083d-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md) and [Required Development Guidelines](./required-development-guidelines.md).</span></span>

<span data-ttu-id="0083d-110">`NounName` ([System. String](/dotnet/api/System.String)) requerido.</span><span class="sxs-lookup"><span data-stu-id="0083d-110">`NounName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="0083d-111">Especifica el nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0083d-111">Specifies the cmdlet noun.</span></span> <span data-ttu-id="0083d-112">Este nombre especifica el recurso sobre el que actúa el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0083d-112">This noun specifies the resource that the cmdlet acts upon.</span></span> <span data-ttu-id="0083d-113">Para obtener más información sobre los nombres de cmdlet, consulte [declaración de cmdlets](./cmdlet-class-declaration.md) y [directrices de desarrollo muy alentadas](./strongly-encouraged-development-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="0083d-113">For more information about cmdlet nouns, see [Cmdlet Declaration](./cmdlet-class-declaration.md) and [Strongly Encouraged Development Guidelines](./strongly-encouraged-development-guidelines.md).</span></span>

<span data-ttu-id="0083d-114">parámetro con nombre opcional `SupportsShouldProcess` ([System. Boolean](/dotnet/api/System.Boolean)).</span><span class="sxs-lookup"><span data-stu-id="0083d-114">`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="0083d-115">`True` indica que el cmdlet admite llamadas al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , que proporciona al cmdlet una manera de preguntar al usuario antes de que se realice una acción que cambia el sistema.</span><span class="sxs-lookup"><span data-stu-id="0083d-115">`True` indicates that the cmdlet supports calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, which provides the cmdlet with a way to prompt the user before an action that changes the system is performed.</span></span> <span data-ttu-id="0083d-116">`False`, el valor predeterminado, indica que el cmdlet no admite llamadas al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .</span><span class="sxs-lookup"><span data-stu-id="0083d-116">`False`, the default value, indicates that the cmdlet does not support calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="0083d-117">Para obtener más información acerca de las solicitudes de confirmación, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="0083d-117">For more information about confirmation requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="0083d-118">`ConfirmImpact` ([System. Management. Automation. Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) opcional parámetro con nombre.</span><span class="sxs-lookup"><span data-stu-id="0083d-118">`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) Optional named parameter.</span></span> <span data-ttu-id="0083d-119">Especifica cuándo se debe confirmar la acción del cmdlet mediante una llamada al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .</span><span class="sxs-lookup"><span data-stu-id="0083d-119">Specifies when the action of the cmdlet should be confirmed by a call to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="0083d-120">[System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) solo se llamará cuando el valor ConfirmImpact del cmdlet (de forma predeterminada, Medium) sea igual o mayor que el valor de la variable `$ConfirmPreference`.</span><span class="sxs-lookup"><span data-stu-id="0083d-120">[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) will only be called when the ConfirmImpact value of the cmdlet (by default, Medium) is equal to or greater than the value of the `$ConfirmPreference` variable.</span></span> <span data-ttu-id="0083d-121">Este parámetro debe especificarse solo cuando se especifica el parámetro `SupportsShouldProcess`.</span><span class="sxs-lookup"><span data-stu-id="0083d-121">This parameter should be specified only when the `SupportsShouldProcess` parameter is specified.</span></span>

<span data-ttu-id="0083d-122">parámetro con nombre opcional `DefaultParameterSetName` ([System. String](/dotnet/api/System.String)).</span><span class="sxs-lookup"><span data-stu-id="0083d-122">`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="0083d-123">Especifica el conjunto de parámetros predeterminado que el tiempo de ejecución de Windows PowerShell intenta usar cuando no puede determinar el conjunto de parámetros que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="0083d-123">Specifies the default parameter set that the Windows PowerShell runtime attempts to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="0083d-124">Tenga en cuenta que esta situación se puede eliminar si hace que el parámetro único de cada parámetro establezca un parámetro obligatorio.</span><span class="sxs-lookup"><span data-stu-id="0083d-124">Notice that this situation can be eliminated by making the unique parameter of each parameter set a mandatory parameter.</span></span>

<span data-ttu-id="0083d-125">Hay un caso en el que Windows PowerShell no puede usar el conjunto de parámetros predeterminado aunque se especifique un nombre de conjunto de parámetros predeterminado.</span><span class="sxs-lookup"><span data-stu-id="0083d-125">There is one case where Windows PowerShell cannot use the default parameter set even if a default parameter set name is specified.</span></span> <span data-ttu-id="0083d-126">El tiempo de ejecución de Windows PowerShell no puede distinguir entre conjuntos de parámetros basados únicamente en el tipo de objeto.</span><span class="sxs-lookup"><span data-stu-id="0083d-126">The Windows PowerShell runtime cannot distinguish between parameter sets based solely on object type.</span></span> <span data-ttu-id="0083d-127">Por ejemplo, si tiene un conjunto de parámetros que toma una cadena como ruta de acceso del archivo y otro conjunto que toma un objeto **FileInfo** directamente, Windows PowerShell no puede determinar qué conjunto de parámetros debe usar en función de los valores que se pasan al cmdlet, ni tampoco usa el cmdlet conjunto de parámetros predeterminado.</span><span class="sxs-lookup"><span data-stu-id="0083d-127">For example, if you have one parameter set that takes a string as the file path, and another set that takes a **FileInfo** object directly, Windows PowerShell cannot determine which parameter set to use based on the values passed to the cmdlet, nor does it use the default parameter set.</span></span> <span data-ttu-id="0083d-128">En este caso, aunque especifique un nombre de conjunto de parámetros predeterminado, Windows PowerShell genera un mensaje de error de conjunto de parámetros ambiguos.</span><span class="sxs-lookup"><span data-stu-id="0083d-128">In this case, even if you specify a default parameter set name, Windows PowerShell throws an ambiguous parameter set error message.</span></span>

<span data-ttu-id="0083d-129">parámetro con nombre opcional `SupportsTransactions` ([System. Boolean](/dotnet/api/System.Boolean)).</span><span class="sxs-lookup"><span data-stu-id="0083d-129">`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="0083d-130">`True` indica que el cmdlet puede usarse dentro de una transacción.</span><span class="sxs-lookup"><span data-stu-id="0083d-130">`True` indicates that the cmdlet can be used within a transaction.</span></span> <span data-ttu-id="0083d-131">Cuando se especifica `True`, el tiempo de ejecución de Windows PowerShell agrega el parámetro `UseTransaction` a la lista de parámetros del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0083d-131">When `True` is specified, the Windows PowerShell runtime adds the `UseTransaction` parameter to the parameter list of the cmdlet.</span></span> <span data-ttu-id="0083d-132">`False`, el valor predeterminado, indica que el cmdlet no se puede usar en una transacción.</span><span class="sxs-lookup"><span data-stu-id="0083d-132">`False`, the default value, indicates that the cmdlet cannot be used within a transaction.</span></span>

## <a name="remarks"></a><span data-ttu-id="0083d-133">Observaciones</span><span class="sxs-lookup"><span data-stu-id="0083d-133">Remarks</span></span>

- <span data-ttu-id="0083d-134">Juntos, el verbo y el nombre se usan para identificar el cmdlet registrado e invocar el cmdlet en un script.</span><span class="sxs-lookup"><span data-stu-id="0083d-134">Together, the verb and noun are used to identify your registered cmdlet and to invoke your cmdlet within a script.</span></span>

- <span data-ttu-id="0083d-135">Cuando el cmdlet se invoca desde la consola de Windows PowerShell, el comando es similar al siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="0083d-135">When the cmdlet is invoked from the Windows PowerShell console, the command resembles the following command:</span></span>

<span data-ttu-id="0083d-136">**VerbName-NounName**</span><span class="sxs-lookup"><span data-stu-id="0083d-136">**VerbName-NounName**</span></span>

- <span data-ttu-id="0083d-137">Todos los cmdlets que cambian recursos fuera de Windows PowerShell deben incluir la palabra clave `SupportsShouldProcess` cuando se declara el atributo cmdlet, lo que permite que el cmdlet llame al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) antes de la realiza su acción.</span><span class="sxs-lookup"><span data-stu-id="0083d-137">All cmdlets that change resources outside of Windows PowerShell should include the `SupportsShouldProcess` keyword when the Cmdlet attribute is declared, which allows the cmdlet to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method before the cmdlet performs its action.</span></span> <span data-ttu-id="0083d-138">Si la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) devuelve `false`, no se debe realizar la acción.</span><span class="sxs-lookup"><span data-stu-id="0083d-138">If the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call returns `false`, the action should not be taken.</span></span> <span data-ttu-id="0083d-139">Para obtener más información sobre las solicitudes de confirmación generadas por la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="0083d-139">For more information about the confirmation requests generated by the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="0083d-140">Los parámetros de cmdlet `Confirm` y `WhatIf` solo están disponibles para los cmdlets que admiten llamadas a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .</span><span class="sxs-lookup"><span data-stu-id="0083d-140">The `Confirm` and `WhatIf` cmdlet parameters are available only for cmdlets that support [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) calls.</span></span>

## <a name="example"></a><span data-ttu-id="0083d-141">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="0083d-141">Example</span></span>

<span data-ttu-id="0083d-142">La siguiente definición de clase usa el atributo cmdlet para identificar la clase .NET Framework para un cmdlet **Get-proc** que recupera información sobre los procesos que se ejecutan en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="0083d-142">The following class definition uses the Cmdlet attribute to identify the .NET Framework class for a **Get-Proc** cmdlet that retrieves information about the processes running on the local computer.</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="0083d-143">Para obtener más información sobre el cmdlet **Get-proc** , vea el [tutorial de GetProc](./getproc-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="0083d-143">For more information about the **Get-Proc** cmdlet, see [GetProc Tutorial](./getproc-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0083d-144">Véase también</span><span class="sxs-lookup"><span data-stu-id="0083d-144">See Also</span></span>

[<span data-ttu-id="0083d-145">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0083d-145">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)