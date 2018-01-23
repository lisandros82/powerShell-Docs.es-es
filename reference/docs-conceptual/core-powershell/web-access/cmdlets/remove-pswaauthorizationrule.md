---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell, cmdlet
ms.date: 2016-12-12
title: remove pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 4d039e7e00f87bc7aebb89217251edbbb5c3f5be
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="f4dae-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f4dae-103">Remove-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="f4dae-104">SINOPSIS</span><span class="sxs-lookup"><span data-stu-id="f4dae-104">SYNOPSIS</span></span>

<span data-ttu-id="f4dae-105">Quita una regla de autorización especificada de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="f4dae-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4dae-106">SINTAXIS</span><span class="sxs-lookup"><span data-stu-id="f4dae-106">SYNTAX</span></span>

### <a name="id"></a><span data-ttu-id="f4dae-107">Id</span><span class="sxs-lookup"><span data-stu-id="f4dae-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="f4dae-108">Regla</span><span class="sxs-lookup"><span data-stu-id="f4dae-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="f4dae-109">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="f4dae-109">DESCRIPTION</span></span>

<span data-ttu-id="f4dae-110">Quita una regla de autorización especificada de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="f4dae-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="f4dae-111">PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="f4dae-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="f4dae-112">-Force</span><span class="sxs-lookup"><span data-stu-id="f4dae-112">-Force</span></span>

<span data-ttu-id="f4dae-113">Ejecuta el cmdlet sin pedir confirmación.</span><span class="sxs-lookup"><span data-stu-id="f4dae-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="f4dae-114">De forma predeterminada, el cmdlet pide confirmación antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f4dae-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="f4dae-115">Alias</span><span class="sxs-lookup"><span data-stu-id="f4dae-115">Aliases</span></span>                              | <span data-ttu-id="f4dae-116">ninguno</span><span class="sxs-lookup"><span data-stu-id="f4dae-116">none</span></span>                                 |
| <span data-ttu-id="f4dae-117">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="f4dae-117">Required?</span></span>                            | <span data-ttu-id="f4dae-118">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-118">false</span></span>                                |
| <span data-ttu-id="f4dae-119">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="f4dae-119">Position?</span></span>                            | <span data-ttu-id="f4dae-120">llamada</span><span class="sxs-lookup"><span data-stu-id="f4dae-120">named</span></span>                                |
| <span data-ttu-id="f4dae-121">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="f4dae-121">Default Value</span></span>                        | <span data-ttu-id="f4dae-122">ninguno</span><span class="sxs-lookup"><span data-stu-id="f4dae-122">none</span></span>                                 |
| <span data-ttu-id="f4dae-123">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="f4dae-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f4dae-124">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-124">false</span></span>                                |
| <span data-ttu-id="f4dae-125">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="f4dae-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f4dae-126">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="f4dae-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="f4dae-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="f4dae-128">Especifica los identificadores (ID) de una o varias reglas que se van a quitar.</span><span class="sxs-lookup"><span data-stu-id="f4dae-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="f4dae-129">Alias</span><span class="sxs-lookup"><span data-stu-id="f4dae-129">Aliases</span></span>                              | <span data-ttu-id="f4dae-130">ninguno</span><span class="sxs-lookup"><span data-stu-id="f4dae-130">none</span></span>                                 |
| <span data-ttu-id="f4dae-131">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="f4dae-131">Required?</span></span>                            | <span data-ttu-id="f4dae-132">true</span><span class="sxs-lookup"><span data-stu-id="f4dae-132">true</span></span>                                 |
| <span data-ttu-id="f4dae-133">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="f4dae-133">Position?</span></span>                            | <span data-ttu-id="f4dae-134">2</span><span class="sxs-lookup"><span data-stu-id="f4dae-134">2</span></span>                                    |
| <span data-ttu-id="f4dae-135">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="f4dae-135">Default Value</span></span>                        | <span data-ttu-id="f4dae-136">ninguno</span><span class="sxs-lookup"><span data-stu-id="f4dae-136">none</span></span>                                 |
| <span data-ttu-id="f4dae-137">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="f4dae-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f4dae-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="f4dae-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="f4dae-139">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="f4dae-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f4dae-140">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="f4dae-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="f4dae-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="f4dae-142">Especifica las reglas que se van a quitar.</span><span class="sxs-lookup"><span data-stu-id="f4dae-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="f4dae-143">Alias</span><span class="sxs-lookup"><span data-stu-id="f4dae-143">Aliases</span></span>                              | <span data-ttu-id="f4dae-144">ninguno</span><span class="sxs-lookup"><span data-stu-id="f4dae-144">none</span></span>                                 |
| <span data-ttu-id="f4dae-145">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="f4dae-145">Required?</span></span>                            | <span data-ttu-id="f4dae-146">true</span><span class="sxs-lookup"><span data-stu-id="f4dae-146">true</span></span>                                 |
| <span data-ttu-id="f4dae-147">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="f4dae-147">Position?</span></span>                            | <span data-ttu-id="f4dae-148">2</span><span class="sxs-lookup"><span data-stu-id="f4dae-148">2</span></span>                                    |
| <span data-ttu-id="f4dae-149">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="f4dae-149">Default Value</span></span>                        | <span data-ttu-id="f4dae-150">ninguno</span><span class="sxs-lookup"><span data-stu-id="f4dae-150">none</span></span>                                 |
| <span data-ttu-id="f4dae-151">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="f4dae-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f4dae-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="f4dae-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="f4dae-153">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="f4dae-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f4dae-154">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="f4dae-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f4dae-155">-Confirm</span></span>

<span data-ttu-id="f4dae-156">Solicita confirmación antes de ejecutar el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4dae-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="f4dae-157">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="f4dae-157">Required?</span></span>                            | <span data-ttu-id="f4dae-158">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-158">false</span></span>                                |
| <span data-ttu-id="f4dae-159">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="f4dae-159">Position?</span></span>                            | <span data-ttu-id="f4dae-160">llamada</span><span class="sxs-lookup"><span data-stu-id="f4dae-160">named</span></span>                                |
| <span data-ttu-id="f4dae-161">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="f4dae-161">Default Value</span></span>                        | <span data-ttu-id="f4dae-162">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-162">false</span></span>                                |
| <span data-ttu-id="f4dae-163">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="f4dae-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f4dae-164">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-164">false</span></span>                                |
| <span data-ttu-id="f4dae-165">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="f4dae-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f4dae-166">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="f4dae-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f4dae-167">-WhatIf</span></span>

<span data-ttu-id="f4dae-168">Muestra lo que sucedería si se ejecutara el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f4dae-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f4dae-169">El cmdlet no se ejecuta.</span><span class="sxs-lookup"><span data-stu-id="f4dae-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="f4dae-170">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="f4dae-170">Required?</span></span>                            | <span data-ttu-id="f4dae-171">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-171">false</span></span>                                |
| <span data-ttu-id="f4dae-172">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="f4dae-172">Position?</span></span>                            | <span data-ttu-id="f4dae-173">llamada</span><span class="sxs-lookup"><span data-stu-id="f4dae-173">named</span></span>                                |
| <span data-ttu-id="f4dae-174">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="f4dae-174">Default Value</span></span>                        | <span data-ttu-id="f4dae-175">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-175">false</span></span>                                |
| <span data-ttu-id="f4dae-176">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="f4dae-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="f4dae-177">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-177">false</span></span>                                |
| <span data-ttu-id="f4dae-178">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="f4dae-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="f4dae-179">falso</span><span class="sxs-lookup"><span data-stu-id="f4dae-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="f4dae-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="f4dae-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="f4dae-181">Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="f4dae-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="f4dae-182">Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f4dae-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="f4dae-183">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="f4dae-183">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="f4dae-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="f4dae-184">int\[\]</span></span>

<span data-ttu-id="f4dae-185">Este cmdlet acepta una matriz de enteros o una matriz de objetos PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="f4dae-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

### <a name="pswaauthorizationrule"></a><span data-ttu-id="f4dae-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="f4dae-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="f4dae-187">Este cmdlet acepta una matriz de enteros o una matriz de objetos PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="f4dae-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="f4dae-188">SALIDAS</span><span class="sxs-lookup"><span data-stu-id="f4dae-188">OUTPUTS</span></span>

<span data-ttu-id="f4dae-189">Este cmdlet no genera ninguna salida.</span><span class="sxs-lookup"><span data-stu-id="f4dae-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="f4dae-190">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="f4dae-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="f4dae-191">EJEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="f4dae-191">EXAMPLE 1</span></span>

<span data-ttu-id="f4dae-192">Este ejemplo quita la regla de autorización con el identificador de *2*.</span><span class="sxs-lookup"><span data-stu-id="f4dae-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="f4dae-193">EJEMPLO 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="f4dae-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="f4dae-194">Este ejemplo quita todas las reglas de autorización y también requiere la confirmación del usuario.</span><span class="sxs-lookup"><span data-stu-id="f4dae-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

## <a name="related-topics"></a><span data-ttu-id="f4dae-195">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="f4dae-195">Related topics</span></span>

- [<span data-ttu-id="f4dae-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f4dae-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="f4dae-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f4dae-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="f4dae-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="f4dae-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="f4dae-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="f4dae-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
