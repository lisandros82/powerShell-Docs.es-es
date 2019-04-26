---
title: Compatibilidad con caracteres comodín en los parámetros de Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067406"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="593d5-102">Compatibilidad con caracteres comodín en los parámetros del cmdlet</span><span class="sxs-lookup"><span data-stu-id="593d5-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="593d5-103">A menudo, tendrá que diseñar un cmdlet para ejecutar en un grupo de recursos en lugar de en un único recurso.</span><span class="sxs-lookup"><span data-stu-id="593d5-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="593d5-104">Por ejemplo, un cmdlet posible que deba buscar todos los archivos en un almacén de datos que tienen el mismo nombre o la extensión.</span><span class="sxs-lookup"><span data-stu-id="593d5-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="593d5-105">Debe proporcionar compatibilidad con caracteres comodín cuando se diseña un cmdlet que se va a ejecutar en un grupo de recursos.</span><span class="sxs-lookup"><span data-stu-id="593d5-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="593d5-106">Uso de caracteres comodín se denomina a veces *comodines*.</span><span class="sxs-lookup"><span data-stu-id="593d5-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="593d5-107">Cmdlets de PowerShell de Windows que usan caracteres comodín</span><span class="sxs-lookup"><span data-stu-id="593d5-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="593d5-108">Muchos de los cmdlets de Windows PowerShell admiten caracteres comodín para sus valores de parámetro.</span><span class="sxs-lookup"><span data-stu-id="593d5-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="593d5-109">Por ejemplo, casi todos los cmdlets que tiene un `Name` o `Path` parámetro admite caracteres comodín para estos parámetros.</span><span class="sxs-lookup"><span data-stu-id="593d5-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="593d5-110">(Aunque la mayoría de los cmdlets que tengan un `Path` parámetro también tienen un `LiteralPath` parámetro que no admite caracteres comodín.) El comando siguiente muestra cómo se usa un carácter comodín para devolver todos los cmdlets de la sesión actual cuyos nombres contienen el verbo Get.</span><span class="sxs-lookup"><span data-stu-id="593d5-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 <span data-ttu-id="593d5-111">**PS > get-command get -\***</span><span class="sxs-lookup"><span data-stu-id="593d5-111">**PS>get-command get-\***</span></span>

## <a name="supported-wildcard-characters"></a><span data-ttu-id="593d5-112">Caracteres comodín admitidos</span><span class="sxs-lookup"><span data-stu-id="593d5-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="593d5-113">Windows PowerShell es compatible con los siguientes caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="593d5-113">Windows PowerShell supports the following wildcard characters.</span></span>

|<span data-ttu-id="593d5-114">carácter comodín</span><span class="sxs-lookup"><span data-stu-id="593d5-114">Wildcard character</span></span>|<span data-ttu-id="593d5-115">Descripción</span><span class="sxs-lookup"><span data-stu-id="593d5-115">Description</span></span>|<span data-ttu-id="593d5-116">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="593d5-116">Example</span></span>|<span data-ttu-id="593d5-117">Coincidencia</span><span class="sxs-lookup"><span data-stu-id="593d5-117">Matches</span></span>|<span data-ttu-id="593d5-118">No coincide con</span><span class="sxs-lookup"><span data-stu-id="593d5-118">Does not match</span></span>|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|<span data-ttu-id="593d5-119">Coincide con cero o más caracteres, empezando en la posición especificada</span><span class="sxs-lookup"><span data-stu-id="593d5-119">Matches zero or more characters, starting at the specified position</span></span>|<span data-ttu-id="593d5-120">a\*</span><span class="sxs-lookup"><span data-stu-id="593d5-120">a\*</span></span>|<span data-ttu-id="593d5-121">Una, ag, Apple</span><span class="sxs-lookup"><span data-stu-id="593d5-121">A, ag, Apple</span></span>||
|<span data-ttu-id="593d5-122">?</span><span class="sxs-lookup"><span data-stu-id="593d5-122">?</span></span>|<span data-ttu-id="593d5-123">Cualquiercarácter coincide con la posición especificada</span><span class="sxs-lookup"><span data-stu-id="593d5-123">Matches anycharacter at the specified position</span></span>|<span data-ttu-id="593d5-124">?n</span><span class="sxs-lookup"><span data-stu-id="593d5-124">?n</span></span>|<span data-ttu-id="593d5-125">Una, en, en</span><span class="sxs-lookup"><span data-stu-id="593d5-125">An, in, on</span></span>|<span data-ttu-id="593d5-126">se ejecutó</span><span class="sxs-lookup"><span data-stu-id="593d5-126">ran</span></span>|
|<span data-ttu-id="593d5-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="593d5-127">[ ]</span></span>|<span data-ttu-id="593d5-128">Coincide con un intervalo de caracteres</span><span class="sxs-lookup"><span data-stu-id="593d5-128">Matches a range of characters</span></span>|<span data-ttu-id="593d5-129">[a-l] ook</span><span class="sxs-lookup"><span data-stu-id="593d5-129">[a-l]ook</span></span>|<span data-ttu-id="593d5-130">libro, cook, apariencia</span><span class="sxs-lookup"><span data-stu-id="593d5-130">book, cook, look</span></span>|<span data-ttu-id="593d5-131">tardó</span><span class="sxs-lookup"><span data-stu-id="593d5-131">took</span></span>|
|<span data-ttu-id="593d5-132">[ ]</span><span class="sxs-lookup"><span data-stu-id="593d5-132">[ ]</span></span>|<span data-ttu-id="593d5-133">Coincide con los caracteres especificados</span><span class="sxs-lookup"><span data-stu-id="593d5-133">Matches the specified characters</span></span>|<span data-ttu-id="593d5-134">[bc]ook</span><span class="sxs-lookup"><span data-stu-id="593d5-134">[bc]ook</span></span>|<span data-ttu-id="593d5-135">libro, cook</span><span class="sxs-lookup"><span data-stu-id="593d5-135">book, cook</span></span>|<span data-ttu-id="593d5-136">look</span><span class="sxs-lookup"><span data-stu-id="593d5-136">look</span></span>|

<span data-ttu-id="593d5-137">Al diseñar los cmdlets que admiten caracteres comodín, se permite para combinaciones de caracteres comodín.</span><span class="sxs-lookup"><span data-stu-id="593d5-137">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="593d5-138">Por ejemplo, el siguiente comando usa el `Get-ChildItem` para recuperar todos los archivos .txt que se encuentran en la carpeta c:\Techdocs y que comienzan con las letras "a" a "l".</span><span class="sxs-lookup"><span data-stu-id="593d5-138">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

<span data-ttu-id="593d5-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="593d5-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span></span>

<span data-ttu-id="593d5-140">El comando anterior usa el carácter comodín de intervalo **[a-l]** para especificar el nombre de archivo debe empezar con los caracteres "a" a "l".</span><span class="sxs-lookup"><span data-stu-id="593d5-140">The previous command uses the range wildcard **[a-l]** to specify that the file name should begin with the characters "a" through "l."</span></span> <span data-ttu-id="593d5-141">El comando usa el \* carácter comodín como marcador de posición para cualquier carácter entre la primera letra del nombre de archivo y la extensión. txt.</span><span class="sxs-lookup"><span data-stu-id="593d5-141">The command then uses the \* wildcard character as a placeholder for any characters between the first letter of the file name and the .txt extension.</span></span>

<span data-ttu-id="593d5-142">En el ejemplo siguiente se usa un modelo de carácter comodín de intervalo que excluye la letra "d", pero incluye todas las letras de la "a" a "f".</span><span class="sxs-lookup"><span data-stu-id="593d5-142">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

<span data-ttu-id="593d5-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span><span class="sxs-lookup"><span data-stu-id="593d5-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span></span>

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="593d5-144">Caracteres literales de carácter comodín patrones de control</span><span class="sxs-lookup"><span data-stu-id="593d5-144">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="593d5-145">Si el patrón de carácter comodín que especifique contiene caracteres literales, use el carácter de acento grave (') como carácter de escape.</span><span class="sxs-lookup"><span data-stu-id="593d5-145">If the wildcard pattern you specify contains literal characters, use the backtick character (\`) as an escape character.</span></span> <span data-ttu-id="593d5-146">Al especificar caracteres literales mediante programación, utilice un acento grave único.</span><span class="sxs-lookup"><span data-stu-id="593d5-146">When you specify literal characters programmatically, use a single backtick.</span></span> <span data-ttu-id="593d5-147">Al especificar los caracteres literales en el símbolo del sistema, use dos graves.</span><span class="sxs-lookup"><span data-stu-id="593d5-147">When you specify literal characters at the command prompt, use two backticks.</span></span> <span data-ttu-id="593d5-148">Por ejemplo, el siguiente patrón contiene dos corchetes que se deben tener literalmente.</span><span class="sxs-lookup"><span data-stu-id="593d5-148">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="593d5-149">"John Smith \`[\*']" (especificado mediante programación)</span><span class="sxs-lookup"><span data-stu-id="593d5-149">"John Smith \`[\*\`]" (specified programmatically)</span></span>

<span data-ttu-id="593d5-150">"John Smith \` \`[\*\`']" (especificado en el símbolo del sistema)</span><span class="sxs-lookup"><span data-stu-id="593d5-150">"John Smith \`\`[\*\`\`]"  (specified at the command prompt)</span></span>

<span data-ttu-id="593d5-151">Este patrón coincide con "John Smith [Marketing]" o "John Smith [desarrollo de]".</span><span class="sxs-lookup"><span data-stu-id="593d5-151">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span>

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="593d5-152">Salida del cmdlet y caracteres comodín</span><span class="sxs-lookup"><span data-stu-id="593d5-152">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="593d5-153">Cuando los parámetros de cmdlet admiten caracteres comodín, una operación de cmdlet normalmente genera una salida de la matriz.</span><span class="sxs-lookup"><span data-stu-id="593d5-153">When cmdlet parameters support wildcard characters, a cmdlet operation usually generates an array output.</span></span> <span data-ttu-id="593d5-154">En ocasiones, no tiene sentido para admitir una matriz de salida porque el usuario podría usar sólo un elemento a la vez.</span><span class="sxs-lookup"><span data-stu-id="593d5-154">Occasionally, it makes no sense to support an array output because the user might use only a single item at a time.</span></span> <span data-ttu-id="593d5-155">Por ejemplo, el `Set-Location` cmdlet es compatible con una matriz de salida porque el usuario establece una única ubicación.</span><span class="sxs-lookup"><span data-stu-id="593d5-155">For example, the `Set-Location` cmdlet does support an array output because the user sets only a single location.</span></span> <span data-ttu-id="593d5-156">En este caso, el cmdlet todavía admite caracteres comodín, pero fuerza la resolución a una única ubicación.</span><span class="sxs-lookup"><span data-stu-id="593d5-156">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="593d5-157">Véase también</span><span class="sxs-lookup"><span data-stu-id="593d5-157">See Also</span></span>

[<span data-ttu-id="593d5-158">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="593d5-158">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="593d5-159">Clase WildcardPattern</span><span class="sxs-lookup"><span data-stu-id="593d5-159">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
