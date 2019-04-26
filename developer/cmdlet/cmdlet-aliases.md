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
# <a name="cmdlet-aliases"></a><span data-ttu-id="8c480-102">Alias del cmdlet</span><span class="sxs-lookup"><span data-stu-id="8c480-102">Cmdlet Aliases</span></span>

<span data-ttu-id="8c480-103">Puede usar el alias de cmdlet para mejorar la experiencia de usuario de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c480-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="8c480-104">Puede agregar alias a los cmdlets usados con frecuencia para reducir escribir y para que resulte más fácil completar tareas rápidamente.</span><span class="sxs-lookup"><span data-stu-id="8c480-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="8c480-105">Puede incluir los alias integrados en los cmdlets o los usuarios pueden definir sus propios alias personalizados.</span><span class="sxs-lookup"><span data-stu-id="8c480-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="8c480-106">Por ejemplo, el [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet tiene integrada una `gcm` alias.</span><span class="sxs-lookup"><span data-stu-id="8c480-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="8c480-107">También puede utilizar alias para agregar nombres de comando de otros idiomas para que los usuarios no tiene que aprender nuevos comandos.</span><span class="sxs-lookup"><span data-stu-id="8c480-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="8c480-108">Directrices de alias</span><span class="sxs-lookup"><span data-stu-id="8c480-108">Alias Guidelines</span></span>

<span data-ttu-id="8c480-109">Cuando se creación el alias integrados en sus cmdlets, siga estas instrucciones:</span><span class="sxs-lookup"><span data-stu-id="8c480-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="8c480-110">Antes de asignar los alias, inicie Windows PowerShell y, a continuación, ejecute el [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet para ver los alias que ya se usan.</span><span class="sxs-lookup"><span data-stu-id="8c480-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="8c480-111">Incluir un prefijo de alias que hace referencia el verbo del nombre del cmdlet y un sufijo de alias que hace referencia el nombre del nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c480-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="8c480-112">Por ejemplo, el alias para el `Import-Module` cmdlet es "ipmo".</span><span class="sxs-lookup"><span data-stu-id="8c480-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="8c480-113">Para obtener una lista de todos los verbos y sus alias, vea [verbos de Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="8c480-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="8c480-114">Para los cmdlets que tengan el mismo verbo, incluyen el mismo prefijo de alias.</span><span class="sxs-lookup"><span data-stu-id="8c480-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="8c480-115">Por ejemplo, los alias para todos los cmdlets de Windows PowerShell que tienen el verbo "Get" en su nombre para usar el prefijo "g".</span><span class="sxs-lookup"><span data-stu-id="8c480-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="8c480-116">Para los cmdlets que tengan el mismo nombre, incluya el mismo sufijo de alias.</span><span class="sxs-lookup"><span data-stu-id="8c480-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="8c480-117">Por ejemplo, los alias para todos los cmdlets de Windows PowerShell que contienen el término "Sesión" en su nombre para usar el sufijo "sn".</span><span class="sxs-lookup"><span data-stu-id="8c480-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="8c480-118">Para los cmdlets que son equivalentes a los comandos en otros idiomas, use el nombre del comando.</span><span class="sxs-lookup"><span data-stu-id="8c480-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="8c480-119">En general, asegúrese de alias más breve posible.</span><span class="sxs-lookup"><span data-stu-id="8c480-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="8c480-120">Asegúrese de que el alias tiene al menos un carácter distinto para el verbo y un carácter distinto para el nombre.</span><span class="sxs-lookup"><span data-stu-id="8c480-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="8c480-121">Agregue más caracteres según sea necesario para que sea el alias único.</span><span class="sxs-lookup"><span data-stu-id="8c480-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c480-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="8c480-122">See Also</span></span>

[<span data-ttu-id="8c480-123">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8c480-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
