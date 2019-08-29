---
title: Compatibilidad con caracteres comodín en los parámetros del cmdlet
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104444"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="c9a1f-102">Compatibilidad con caracteres comodín en los parámetros del cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9a1f-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="c9a1f-103">A menudo, tendrá que diseñar un cmdlet para que se ejecute en un grupo de recursos, en lugar de hacerlo en un solo recurso.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="c9a1f-104">Por ejemplo, un cmdlet puede necesitar Buscar todos los archivos de un almacén de datos que tengan el mismo nombre o extensión.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="c9a1f-105">Debe proporcionar compatibilidad con caracteres comodín al diseñar un cmdlet que se ejecutará en un grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="c9a1f-106">El uso de caracteres comodín a veces se conoce como *comodines*.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="c9a1f-107">Cmdlets de Windows PowerShell que usan caracteres comodín</span><span class="sxs-lookup"><span data-stu-id="c9a1f-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="c9a1f-108">Muchos cmdlets de Windows PowerShell admiten caracteres comodín para sus valores de parámetro.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="c9a1f-109">Por ejemplo, casi todos los cmdlets que `Name` tienen `Path` un parámetro o admiten caracteres comodín para estos parámetros.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="c9a1f-110">(Aunque la mayoría de los cmdlets `Path` que tienen un parámetro `LiteralPath` también tienen un parámetro que no admite caracteres comodín). El siguiente comando muestra cómo se usa un carácter comodín para devolver todos los cmdlets de la sesión actual cuyo nombre contiene el verbo GET.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="c9a1f-111">Caracteres comodín admitidos</span><span class="sxs-lookup"><span data-stu-id="c9a1f-111">Supported Wildcard Characters</span></span>

<span data-ttu-id="c9a1f-112">Windows PowerShell admite los siguientes caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-112">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="c9a1f-113">N</span><span class="sxs-lookup"><span data-stu-id="c9a1f-113">Wildcard</span></span> |                             <span data-ttu-id="c9a1f-114">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="c9a1f-114">Description</span></span>                             |  <span data-ttu-id="c9a1f-115">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c9a1f-115">Example</span></span>   |     <span data-ttu-id="c9a1f-116">Coincidencia</span><span class="sxs-lookup"><span data-stu-id="c9a1f-116">Matches</span></span>      | <span data-ttu-id="c9a1f-117">No coincide</span><span class="sxs-lookup"><span data-stu-id="c9a1f-117">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="c9a1f-118">Coincide con cero o más caracteres, empezando en la posición especificada</span><span class="sxs-lookup"><span data-stu-id="c9a1f-118">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="c9a1f-119">A, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="c9a1f-119">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="c9a1f-120">?</span><span class="sxs-lookup"><span data-stu-id="c9a1f-120">?</span></span>        | <span data-ttu-id="c9a1f-121">Coincide con cualquier carácter que se encuentra en la posición especificada</span><span class="sxs-lookup"><span data-stu-id="c9a1f-121">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="c9a1f-122">, En, en</span><span class="sxs-lookup"><span data-stu-id="c9a1f-122">An, in, on</span></span>       | <span data-ttu-id="c9a1f-123">ejecuta</span><span class="sxs-lookup"><span data-stu-id="c9a1f-123">ran</span></span>            |
| <span data-ttu-id="c9a1f-124">[ ]</span><span class="sxs-lookup"><span data-stu-id="c9a1f-124">[ ]</span></span>      | <span data-ttu-id="c9a1f-125">Coincide con un intervalo de caracteres</span><span class="sxs-lookup"><span data-stu-id="c9a1f-125">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="c9a1f-126">libro, Cook, mire</span><span class="sxs-lookup"><span data-stu-id="c9a1f-126">book, cook, look</span></span> | <span data-ttu-id="c9a1f-127">Nook, tardó</span><span class="sxs-lookup"><span data-stu-id="c9a1f-127">nook, took</span></span>     |
| <span data-ttu-id="c9a1f-128">[ ]</span><span class="sxs-lookup"><span data-stu-id="c9a1f-128">[ ]</span></span>      | <span data-ttu-id="c9a1f-129">Coincide con los caracteres especificados</span><span class="sxs-lookup"><span data-stu-id="c9a1f-129">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="c9a1f-130">libro, Nook</span><span class="sxs-lookup"><span data-stu-id="c9a1f-130">book, nook</span></span>       | <span data-ttu-id="c9a1f-131">Cook, mire</span><span class="sxs-lookup"><span data-stu-id="c9a1f-131">cook, look</span></span>     |

<span data-ttu-id="c9a1f-132">Al diseñar cmdlets que admiten caracteres comodín, permita combinaciones de caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-132">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="c9a1f-133">Por ejemplo, el siguiente comando usa el `Get-ChildItem` cmdlet para recuperar todos los archivos. txt que se encuentran en la carpeta c:\Techdocs y que comienzan con las letras "a" a "l".</span><span class="sxs-lookup"><span data-stu-id="c9a1f-133">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="c9a1f-134">El comando anterior usa el carácter comodín `[a-l]` de intervalo para especificar que el nombre de archivo debe empezar con los caracteres "a" a "l" `*` y usar el carácter comodín como marcador de posición para los caracteres entre la primera letra del nombre de archivo y la extensión **. txt** .</span><span class="sxs-lookup"><span data-stu-id="c9a1f-134">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="c9a1f-135">En el ejemplo siguiente se usa un patrón de caracteres comodín de intervalo que excluye la letra "d", pero se incluyen todas las demás Letras de la "a" a la "f".</span><span class="sxs-lookup"><span data-stu-id="c9a1f-135">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="c9a1f-136">Controlar caracteres literales en patrones de caracteres comodín</span><span class="sxs-lookup"><span data-stu-id="c9a1f-136">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="c9a1f-137">Si el patrón de carácter comodín que especifica contiene caracteres literales que no deben interpretarse como caracteres comodín, use el carácter`` ` ``de acento grave () como carácter de escape.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-137">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="c9a1f-138">Cuando especifique caracteres literales int en la API de PowerShell, use una sola marca de paso.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-138">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="c9a1f-139">Cuando especifique caracteres literales en el símbolo del sistema de PowerShell, use dos TICs.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-139">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="c9a1f-140">Por ejemplo, el siguiente patrón contiene dos corchetes que deben tomarse literalmente.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-140">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="c9a1f-141">Cuando se usa en la API de PowerShell, use:</span><span class="sxs-lookup"><span data-stu-id="c9a1f-141">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="c9a1f-142">"John Smith \`[\* ']"</span><span class="sxs-lookup"><span data-stu-id="c9a1f-142">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="c9a1f-143">Cuando se usa desde el símbolo del sistema de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c9a1f-143">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="c9a1f-144">"John Smith \` \`[\*\`']"</span><span class="sxs-lookup"><span data-stu-id="c9a1f-144">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="c9a1f-145">Este patrón coincide con "John Smith [marketing]" o "John Smith [desarrollo]".</span><span class="sxs-lookup"><span data-stu-id="c9a1f-145">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="c9a1f-146">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c9a1f-146">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="c9a1f-147">Resultados de cmdlet y caracteres comodín</span><span class="sxs-lookup"><span data-stu-id="c9a1f-147">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="c9a1f-148">Cuando los parámetros de cmdlet admiten caracteres comodín, la operación normalmente genera una salida de matriz.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-148">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="c9a1f-149">En ocasiones, no tiene sentido admitir una salida de matriz porque el usuario podría usar un solo elemento.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-149">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="c9a1f-150">Por ejemplo, el `Set-Location` cmdlet no admite la salida de matriz porque el usuario establece una sola ubicación.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-150">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="c9a1f-151">En esta instancia, el cmdlet sigue admitiendo caracteres comodín, pero fuerza la resolución en una sola ubicación.</span><span class="sxs-lookup"><span data-stu-id="c9a1f-151">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9a1f-152">Vea también</span><span class="sxs-lookup"><span data-stu-id="c9a1f-152">See Also</span></span>

[<span data-ttu-id="c9a1f-153">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c9a1f-153">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="c9a1f-154">Clase WildcardPattern</span><span class="sxs-lookup"><span data-stu-id="c9a1f-154">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
