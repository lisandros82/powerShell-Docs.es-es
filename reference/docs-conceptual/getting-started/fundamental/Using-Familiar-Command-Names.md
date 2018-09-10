---
ms.date: 08/27/2018
keywords: powershell, cmdlet
title: Usar nombres de comando conocidos
ms.assetid: 021e2424-c64e-4fa5-aa98-aa6405758d5d
ms.openlocfilehash: c5665f64fd832eb9c807f413a8e879f63db7f8c6
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353256"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="9414f-103">Usar nombres de comando conocidos</span><span class="sxs-lookup"><span data-stu-id="9414f-103">Using familiar command names</span></span>

<span data-ttu-id="9414f-104">PowerShell admite alias para referirse a comandos con nombres alternativos.</span><span class="sxs-lookup"><span data-stu-id="9414f-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="9414f-105">La creación de alias permite a los usuarios con experiencia en otros shells utilizar los nombres de comandos comunes que ya conocen en operaciones similares en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9414f-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="9414f-106">La creación de alias asocia un nombre nuevo con otro comando.</span><span class="sxs-lookup"><span data-stu-id="9414f-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="9414f-107">Por ejemplo, PowerShell tiene una función interna denominada `Clear-Host` que borra la ventana de salida.</span><span class="sxs-lookup"><span data-stu-id="9414f-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="9414f-108">Puede escribir el alias `cls` o `clear` en un símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="9414f-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="9414f-109">PowerShell interpreta estos alias y ejecuta la función `Clear-Host`.</span><span class="sxs-lookup"><span data-stu-id="9414f-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="9414f-110">Esta característica ayuda a los usuarios a aprender PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9414f-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="9414f-111">Primero, la mayoría de los usuarios de **cmd.exe** y Unix tienen un amplio repertorio de comandos que los usuarios ya conocen por su nombre.</span><span class="sxs-lookup"><span data-stu-id="9414f-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="9414f-112">Los equivalentes de PowerShell pueden no producir resultados idénticos.</span><span class="sxs-lookup"><span data-stu-id="9414f-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="9414f-113">Sin embargo, los resultados son lo suficientemente cercanos como para que los usuarios puedan trabajar sin conocer el nombre del comando PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9414f-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="9414f-114">El automatismo es otra fuente importante de frustración cuando se aprende un nuevo shell de comandos.</span><span class="sxs-lookup"><span data-stu-id="9414f-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="9414f-115">Si ha usado **cmd.exe** durante años, puede escribir de forma refleja el comando `cls` para borrar la pantalla.</span><span class="sxs-lookup"><span data-stu-id="9414f-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="9414f-116">Sin el alias de `Clear-Host`, recibirá un mensaje de error y no sabrá qué hacer para borrar la salida.</span><span class="sxs-lookup"><span data-stu-id="9414f-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="9414f-117">La siguiente lista muestra algunos de los comandos de **cmd.exe** y Unix comunes que puede usar en PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9414f-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="9414f-118">cat</span><span class="sxs-lookup"><span data-stu-id="9414f-118">cat</span></span>|<span data-ttu-id="9414f-119">dir</span><span class="sxs-lookup"><span data-stu-id="9414f-119">dir</span></span>|<span data-ttu-id="9414f-120">montar</span><span class="sxs-lookup"><span data-stu-id="9414f-120">mount</span></span>|<span data-ttu-id="9414f-121">rm</span><span class="sxs-lookup"><span data-stu-id="9414f-121">rm</span></span>|
|<span data-ttu-id="9414f-122">cd</span><span class="sxs-lookup"><span data-stu-id="9414f-122">cd</span></span>|<span data-ttu-id="9414f-123">echo</span><span class="sxs-lookup"><span data-stu-id="9414f-123">echo</span></span>|<span data-ttu-id="9414f-124">move</span><span class="sxs-lookup"><span data-stu-id="9414f-124">move</span></span>|<span data-ttu-id="9414f-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="9414f-125">rmdir</span></span>|
|<span data-ttu-id="9414f-126">chdir</span><span class="sxs-lookup"><span data-stu-id="9414f-126">chdir</span></span>|<span data-ttu-id="9414f-127">erase</span><span class="sxs-lookup"><span data-stu-id="9414f-127">erase</span></span>|<span data-ttu-id="9414f-128">popd</span><span class="sxs-lookup"><span data-stu-id="9414f-128">popd</span></span>|<span data-ttu-id="9414f-129">sleep</span><span class="sxs-lookup"><span data-stu-id="9414f-129">sleep</span></span>|
|<span data-ttu-id="9414f-130">clear</span><span class="sxs-lookup"><span data-stu-id="9414f-130">clear</span></span>|<span data-ttu-id="9414f-131">h</span><span class="sxs-lookup"><span data-stu-id="9414f-131">h</span></span>|<span data-ttu-id="9414f-132">ps</span><span class="sxs-lookup"><span data-stu-id="9414f-132">ps</span></span>|<span data-ttu-id="9414f-133">sort</span><span class="sxs-lookup"><span data-stu-id="9414f-133">sort</span></span>|
|<span data-ttu-id="9414f-134">cls</span><span class="sxs-lookup"><span data-stu-id="9414f-134">cls</span></span>|<span data-ttu-id="9414f-135">history</span><span class="sxs-lookup"><span data-stu-id="9414f-135">history</span></span>|<span data-ttu-id="9414f-136">pushd</span><span class="sxs-lookup"><span data-stu-id="9414f-136">pushd</span></span>|<span data-ttu-id="9414f-137">tee</span><span class="sxs-lookup"><span data-stu-id="9414f-137">tee</span></span>|
|<span data-ttu-id="9414f-138">copy</span><span class="sxs-lookup"><span data-stu-id="9414f-138">copy</span></span>|<span data-ttu-id="9414f-139">kill</span><span class="sxs-lookup"><span data-stu-id="9414f-139">kill</span></span>|<span data-ttu-id="9414f-140">pwd</span><span class="sxs-lookup"><span data-stu-id="9414f-140">pwd</span></span>|<span data-ttu-id="9414f-141">tipo</span><span class="sxs-lookup"><span data-stu-id="9414f-141">type</span></span>|
|<span data-ttu-id="9414f-142">del</span><span class="sxs-lookup"><span data-stu-id="9414f-142">del</span></span>|<span data-ttu-id="9414f-143">lp</span><span class="sxs-lookup"><span data-stu-id="9414f-143">lp</span></span>|<span data-ttu-id="9414f-144">r</span><span class="sxs-lookup"><span data-stu-id="9414f-144">r</span></span>|<span data-ttu-id="9414f-145">write</span><span class="sxs-lookup"><span data-stu-id="9414f-145">write</span></span>|
|<span data-ttu-id="9414f-146">diff</span><span class="sxs-lookup"><span data-stu-id="9414f-146">diff</span></span>|<span data-ttu-id="9414f-147">ls</span><span class="sxs-lookup"><span data-stu-id="9414f-147">ls</span></span>|<span data-ttu-id="9414f-148">ren</span><span class="sxs-lookup"><span data-stu-id="9414f-148">ren</span></span>||

<span data-ttu-id="9414f-149">El cmdlet `Get-Alias` muestra el nombre real del comando PowerShell nativo asociado a un alias.</span><span class="sxs-lookup"><span data-stu-id="9414f-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="9414f-150">Interpretación de los alias estándar</span><span class="sxs-lookup"><span data-stu-id="9414f-150">Interpreting standard aliases</span></span>

<span data-ttu-id="9414f-151">Los alias que describimos anteriormente fueron diseñados para ser compatibles con los nombres de otros shells de comandos.</span><span class="sxs-lookup"><span data-stu-id="9414f-151">The aliases we described previous were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="9414f-152">La mayoría de los alias integrados en PowerShell están diseñados para ser breves.</span><span class="sxs-lookup"><span data-stu-id="9414f-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="9414f-153">Los nombres más cortos son más fáciles de escribir, pero son difíciles de leer si no sabe a qué se refieren.</span><span class="sxs-lookup"><span data-stu-id="9414f-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="9414f-154">Los alias de PowerShell intentan comprometer la claridad y la brevedad.</span><span class="sxs-lookup"><span data-stu-id="9414f-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="9414f-155">PowerShell utiliza un conjunto estándar de alias para sustantivos y verbos comunes.</span><span class="sxs-lookup"><span data-stu-id="9414f-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="9414f-156">Abreviaturas de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="9414f-156">Example abbreviations:</span></span>

| <span data-ttu-id="9414f-157">Sustantivo o verbo</span><span class="sxs-lookup"><span data-stu-id="9414f-157">Noun or Verb</span></span> | <span data-ttu-id="9414f-158">Abreviatura</span><span class="sxs-lookup"><span data-stu-id="9414f-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="9414f-159">Get</span><span class="sxs-lookup"><span data-stu-id="9414f-159">Get</span></span>          | <span data-ttu-id="9414f-160">g</span><span class="sxs-lookup"><span data-stu-id="9414f-160">g</span></span>            |
| <span data-ttu-id="9414f-161">Establecer</span><span class="sxs-lookup"><span data-stu-id="9414f-161">Set</span></span>          | <span data-ttu-id="9414f-162">s</span><span class="sxs-lookup"><span data-stu-id="9414f-162">s</span></span>            |
| <span data-ttu-id="9414f-163">Elemento</span><span class="sxs-lookup"><span data-stu-id="9414f-163">Item</span></span>         | <span data-ttu-id="9414f-164">i</span><span class="sxs-lookup"><span data-stu-id="9414f-164">i</span></span>            |
| <span data-ttu-id="9414f-165">Ubicación</span><span class="sxs-lookup"><span data-stu-id="9414f-165">Location</span></span>     | <span data-ttu-id="9414f-166">l</span><span class="sxs-lookup"><span data-stu-id="9414f-166">l</span></span>            |
| <span data-ttu-id="9414f-167">Comando</span><span class="sxs-lookup"><span data-stu-id="9414f-167">Command</span></span>      | <span data-ttu-id="9414f-168">cm</span><span class="sxs-lookup"><span data-stu-id="9414f-168">cm</span></span>           |
| <span data-ttu-id="9414f-169">Alias</span><span class="sxs-lookup"><span data-stu-id="9414f-169">Alias</span></span>        | <span data-ttu-id="9414f-170">al</span><span class="sxs-lookup"><span data-stu-id="9414f-170">al</span></span>           |

<span data-ttu-id="9414f-171">Estos alias son comprensibles cuando se conocen los nombres abreviados.</span><span class="sxs-lookup"><span data-stu-id="9414f-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="9414f-172">Nombre del cmdlet</span><span class="sxs-lookup"><span data-stu-id="9414f-172">Cmdlet name</span></span>    | <span data-ttu-id="9414f-173">Alias</span><span class="sxs-lookup"><span data-stu-id="9414f-173">Alias</span></span> |
|----------------|-------|
| `Get-Item `    | <span data-ttu-id="9414f-174">gi</span><span class="sxs-lookup"><span data-stu-id="9414f-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="9414f-175">si</span><span class="sxs-lookup"><span data-stu-id="9414f-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="9414f-176">gl</span><span class="sxs-lookup"><span data-stu-id="9414f-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="9414f-177">sl</span><span class="sxs-lookup"><span data-stu-id="9414f-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="9414f-178">gcm</span><span class="sxs-lookup"><span data-stu-id="9414f-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="9414f-179">gal</span><span class="sxs-lookup"><span data-stu-id="9414f-179">gal</span></span>   |

<span data-ttu-id="9414f-180">Cuando ya esté familiarizado con la creación de alias de PowerShell, es fácil adivinar que el alias **sal** se refiere a `Set-Alias`.</span><span class="sxs-lookup"><span data-stu-id="9414f-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="9414f-181">Creación de nuevos alias</span><span class="sxs-lookup"><span data-stu-id="9414f-181">Creating new aliases</span></span>

<span data-ttu-id="9414f-182">Con el cmdlet `Set-Alias` puede crear sus propios alias.</span><span class="sxs-lookup"><span data-stu-id="9414f-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="9414f-183">Por ejemplo, las siguientes instrucciones crean los alias de cmdlet estándar que se describen anteriormente:</span><span class="sxs-lookup"><span data-stu-id="9414f-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="9414f-184">Internamente, PowerShell usa comandos similares durante el inicio, pero estos alias no se pueden cambiar.</span><span class="sxs-lookup"><span data-stu-id="9414f-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="9414f-185">Si intenta ejecutar realmente uno de estos comandos, obtiene un error que indica que no se puede modificar el alias.</span><span class="sxs-lookup"><span data-stu-id="9414f-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="9414f-186">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="9414f-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```