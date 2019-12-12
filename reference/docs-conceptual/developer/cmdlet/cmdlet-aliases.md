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
# <a name="cmdlet-aliases"></a><span data-ttu-id="c6880-102">Alias del cmdlet</span><span class="sxs-lookup"><span data-stu-id="c6880-102">Cmdlet Aliases</span></span>

<span data-ttu-id="c6880-103">Puede utilizar alias de cmdlet para mejorar la experiencia de usuario del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c6880-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="c6880-104">Puede Agregar alias a los cmdlets de uso frecuente para reducir la escritura y facilitar la finalización de las tareas rápidamente.</span><span class="sxs-lookup"><span data-stu-id="c6880-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="c6880-105">Puede incluir alias integrados en los cmdlets o los usuarios pueden definir sus propios alias personalizados.</span><span class="sxs-lookup"><span data-stu-id="c6880-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="c6880-106">Por ejemplo, el cmdlet [get-command](/powershell/module/microsoft.powershell.core/get-command) tiene un alias de `gcm` integrado.</span><span class="sxs-lookup"><span data-stu-id="c6880-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="c6880-107">También puede usar alias para agregar nombres de comando desde otros idiomas para que los usuarios no tengan que aprender nuevos comandos.</span><span class="sxs-lookup"><span data-stu-id="c6880-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="c6880-108">Instrucciones de alias</span><span class="sxs-lookup"><span data-stu-id="c6880-108">Alias Guidelines</span></span>

<span data-ttu-id="c6880-109">Siga estas instrucciones cuando cree alias integrados para los cmdlets:</span><span class="sxs-lookup"><span data-stu-id="c6880-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="c6880-110">Antes de asignar alias, inicie Windows PowerShell y, a continuación, ejecute el cmdlet [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) para ver los alias que ya se usan.</span><span class="sxs-lookup"><span data-stu-id="c6880-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="c6880-111">Incluya un prefijo de alias que haga referencia al verbo del nombre del cmdlet y un sufijo de alias que haga referencia al nombre del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c6880-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="c6880-112">Por ejemplo, el alias del cmdlet `Import-Module` es "IPMO".</span><span class="sxs-lookup"><span data-stu-id="c6880-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="c6880-113">Para obtener una lista de todos los verbos y sus alias, vea [verbos de cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="c6880-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="c6880-114">Para los cmdlets que tienen el mismo verbo, incluya el mismo prefijo de alias.</span><span class="sxs-lookup"><span data-stu-id="c6880-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="c6880-115">Por ejemplo, los alias de todos los cmdlets de Windows PowerShell que tienen el verbo "Get" en su nombre usan el prefijo "g".</span><span class="sxs-lookup"><span data-stu-id="c6880-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="c6880-116">Para los cmdlets que tienen el mismo nombre, incluya el mismo sufijo de alias.</span><span class="sxs-lookup"><span data-stu-id="c6880-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="c6880-117">Por ejemplo, los alias de todos los cmdlets de Windows PowerShell que tienen el nombre "session" en su nombre usan el sufijo "SN".</span><span class="sxs-lookup"><span data-stu-id="c6880-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="c6880-118">Para los cmdlets que son equivalentes a los comandos en otros lenguajes, utilice el nombre del comando.</span><span class="sxs-lookup"><span data-stu-id="c6880-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="c6880-119">En general, cree alias lo más cortos posible.</span><span class="sxs-lookup"><span data-stu-id="c6880-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="c6880-120">Asegúrese de que el alias tiene al menos un carácter distinto para el verbo y un carácter distinto para el nombre.</span><span class="sxs-lookup"><span data-stu-id="c6880-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="c6880-121">Agregue más caracteres según sea necesario para que el alias sea único.</span><span class="sxs-lookup"><span data-stu-id="c6880-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6880-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="c6880-122">See Also</span></span>

[<span data-ttu-id="c6880-123">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6880-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
