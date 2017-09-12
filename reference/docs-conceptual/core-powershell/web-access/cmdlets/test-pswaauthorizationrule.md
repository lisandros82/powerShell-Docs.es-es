---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: test pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 900547301c815ba6fe3a9507f975503fec864e4e
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="3b540-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3b540-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="3b540-104">SINOPSIS</span><span class="sxs-lookup"><span data-stu-id="3b540-104">SYNOPSIS</span></span>

<span data-ttu-id="3b540-105">Comprueba si existe una regla para un usuario, un equipo o un punto de conexión determinados.</span><span class="sxs-lookup"><span data-stu-id="3b540-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="3b540-106">SINTAXIS</span><span class="sxs-lookup"><span data-stu-id="3b540-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="3b540-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="3b540-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="3b540-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="3b540-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="3b540-109">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="3b540-109">DESCRIPTION</span></span>

<span data-ttu-id="3b540-110">El cmdlet **Test-PswaAuthorizationRule** comprueba si existe una regla para un usuario, un equipo o un punto de conexión determinado.</span><span class="sxs-lookup"><span data-stu-id="3b540-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="3b540-111">Este cmdlet también se puede usar para probar las reglas de autorización y para validar que se ha autorizado una solicitud de acceso de punto de conexión, equipo o usuario en concreto.</span><span class="sxs-lookup"><span data-stu-id="3b540-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="3b540-112">De forma predeterminada, este cmdlet evalúa todas las reglas del archivo de autorización,</span><span class="sxs-lookup"><span data-stu-id="3b540-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="3b540-113">aunque puede especificar que se evalúe un subconjunto de reglas.</span><span class="sxs-lookup"><span data-stu-id="3b540-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="3b540-114">Puede usar este cmdlet para solucionar errores de autenticación.</span><span class="sxs-lookup"><span data-stu-id="3b540-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="3b540-115">Los parámetros de este cmdlet corresponden a los campos de la página de inicio de sesión de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="3b540-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="3b540-116">PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="3b540-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="3b540-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3b540-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="3b540-118">Especifica el nombre del equipo que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="3b540-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="3b540-119">Alias</span><span class="sxs-lookup"><span data-stu-id="3b540-119">Aliases</span></span>                              | <span data-ttu-id="3b540-120">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-120">none</span></span>                                 |
| <span data-ttu-id="3b540-121">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="3b540-121">Required?</span></span>                            | <span data-ttu-id="3b540-122">true</span><span class="sxs-lookup"><span data-stu-id="3b540-122">true</span></span>                                 |
| <span data-ttu-id="3b540-123">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="3b540-123">Position?</span></span>                            | <span data-ttu-id="3b540-124">2</span><span class="sxs-lookup"><span data-stu-id="3b540-124">2</span></span>                                    |
| <span data-ttu-id="3b540-125">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="3b540-125">Default Value</span></span>                        | <span data-ttu-id="3b540-126">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-126">none</span></span>                                 |
| <span data-ttu-id="3b540-127">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="3b540-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3b540-128">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-128">false</span></span>                                |
| <span data-ttu-id="3b540-129">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="3b540-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3b540-130">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="3b540-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3b540-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="3b540-132">Especifica el nombre de la configuración de sesión de Windows PowerShell que se va a probar (también conocida como "punto de conexión" o "espacio de ejecución").</span><span class="sxs-lookup"><span data-stu-id="3b540-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="3b540-133">Alias</span><span class="sxs-lookup"><span data-stu-id="3b540-133">Aliases</span></span>                              | <span data-ttu-id="3b540-134">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-134">none</span></span>                                 |
| <span data-ttu-id="3b540-135">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="3b540-135">Required?</span></span>                            | <span data-ttu-id="3b540-136">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-136">false</span></span>                                |
| <span data-ttu-id="3b540-137">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="3b540-137">Position?</span></span>                            | <span data-ttu-id="3b540-138">3</span><span class="sxs-lookup"><span data-stu-id="3b540-138">3</span></span>                                    |
| <span data-ttu-id="3b540-139">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="3b540-139">Default Value</span></span>                        | <span data-ttu-id="3b540-140">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-140">none</span></span>                                 |
| <span data-ttu-id="3b540-141">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="3b540-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3b540-142">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-142">false</span></span>                                |
| <span data-ttu-id="3b540-143">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="3b540-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3b540-144">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="3b540-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="3b540-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="3b540-146">Especifica el URI de conexión que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="3b540-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="3b540-147">Alias</span><span class="sxs-lookup"><span data-stu-id="3b540-147">Aliases</span></span>                              | <span data-ttu-id="3b540-148">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-148">none</span></span>                                 |
| <span data-ttu-id="3b540-149">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="3b540-149">Required?</span></span>                            | <span data-ttu-id="3b540-150">true</span><span class="sxs-lookup"><span data-stu-id="3b540-150">true</span></span>                                 |
| <span data-ttu-id="3b540-151">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="3b540-151">Position?</span></span>                            | <span data-ttu-id="3b540-152">2</span><span class="sxs-lookup"><span data-stu-id="3b540-152">2</span></span>                                    |
| <span data-ttu-id="3b540-153">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="3b540-153">Default Value</span></span>                        | <span data-ttu-id="3b540-154">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-154">none</span></span>                                 |
| <span data-ttu-id="3b540-155">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="3b540-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3b540-156">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-156">false</span></span>                                |
| <span data-ttu-id="3b540-157">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="3b540-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3b540-158">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="3b540-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="3b540-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="3b540-160">Especifica un objeto **PSCredential** para una cuenta de usuario que quiera usar para probar las reglas de autorización de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="3b540-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="3b540-161">Si no agrega este parámetro, el cmdlet usará la cuenta del usuario que ha iniciado la sesión.</span><span class="sxs-lookup"><span data-stu-id="3b540-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="3b540-162">Para obtener un objeto **PSCredential**, necesario para probar las reglas de autorización de forma remota, ejecute el cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).</span><span class="sxs-lookup"><span data-stu-id="3b540-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="3b540-163">Alias</span><span class="sxs-lookup"><span data-stu-id="3b540-163">Aliases</span></span>                              | <span data-ttu-id="3b540-164">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-164">none</span></span>                                 |
| <span data-ttu-id="3b540-165">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="3b540-165">Required?</span></span>                            | <span data-ttu-id="3b540-166">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-166">false</span></span>                                |
| <span data-ttu-id="3b540-167">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="3b540-167">Position?</span></span>                            | <span data-ttu-id="3b540-168">llamada</span><span class="sxs-lookup"><span data-stu-id="3b540-168">named</span></span>                                |
| <span data-ttu-id="3b540-169">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="3b540-169">Default Value</span></span>                        | <span data-ttu-id="3b540-170">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-170">none</span></span>                                 |
| <span data-ttu-id="3b540-171">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="3b540-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3b540-172">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-172">false</span></span>                                |
| <span data-ttu-id="3b540-173">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="3b540-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3b540-174">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="3b540-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="3b540-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="3b540-176">Especifica un subconjunto de reglas que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="3b540-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="3b540-177">Si no se especifica este parámetro, este cmdlet hará una prueba en todas las reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="3b540-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="3b540-178">Alias</span><span class="sxs-lookup"><span data-stu-id="3b540-178">Aliases</span></span>                              | <span data-ttu-id="3b540-179">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-179">none</span></span>                                 |
| <span data-ttu-id="3b540-180">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="3b540-180">Required?</span></span>                            | <span data-ttu-id="3b540-181">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-181">false</span></span>                                |
| <span data-ttu-id="3b540-182">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="3b540-182">Position?</span></span>                            | <span data-ttu-id="3b540-183">llamada</span><span class="sxs-lookup"><span data-stu-id="3b540-183">named</span></span>                                |
| <span data-ttu-id="3b540-184">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="3b540-184">Default Value</span></span>                        | <span data-ttu-id="3b540-185">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-185">none</span></span>                                 |
| <span data-ttu-id="3b540-186">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="3b540-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3b540-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="3b540-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="3b540-188">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="3b540-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3b540-189">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="3b540-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="3b540-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="3b540-191">Especifica el nombre del usuario que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="3b540-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="3b540-192">Alias</span><span class="sxs-lookup"><span data-stu-id="3b540-192">Aliases</span></span>                              | <span data-ttu-id="3b540-193">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-193">none</span></span>                                 |
| <span data-ttu-id="3b540-194">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="3b540-194">Required?</span></span>                            | <span data-ttu-id="3b540-195">true</span><span class="sxs-lookup"><span data-stu-id="3b540-195">true</span></span>                                 |
| <span data-ttu-id="3b540-196">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="3b540-196">Position?</span></span>                            | <span data-ttu-id="3b540-197">1</span><span class="sxs-lookup"><span data-stu-id="3b540-197">1</span></span>                                    |
| <span data-ttu-id="3b540-198">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="3b540-198">Default Value</span></span>                        | <span data-ttu-id="3b540-199">ninguno</span><span class="sxs-lookup"><span data-stu-id="3b540-199">none</span></span>                                 |
| <span data-ttu-id="3b540-200">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="3b540-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="3b540-201">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-201">false</span></span>                                |
| <span data-ttu-id="3b540-202">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="3b540-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="3b540-203">falso</span><span class="sxs-lookup"><span data-stu-id="3b540-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="3b540-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="3b540-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="3b540-205">Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="3b540-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="3b540-206">Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3b540-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="3b540-207">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="3b540-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="3b540-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="3b540-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="3b540-209">Este cmdlet acepta una matriz de objetos PswaAuthorizationRule como entrada.</span><span class="sxs-lookup"><span data-stu-id="3b540-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="3b540-210">SALIDAS</span><span class="sxs-lookup"><span data-stu-id="3b540-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="3b540-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="3b540-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="3b540-212">Este cmdlet genera una matriz de objetos PswaAuthorizationRule como salida.</span><span class="sxs-lookup"><span data-stu-id="3b540-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="3b540-213">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="3b540-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="3b540-214">EJEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="3b540-214">EXAMPLE 1</span></span>

<span data-ttu-id="3b540-215">Este ejemplo prueba todas las reglas de autorización para que se muestren todas las reglas que permiten que el usuario *contoso\\mhanson* se conecte al equipo *srv2* y use una configuración de sesión de Windows PowerShell denominada *test*.</span><span class="sxs-lookup"><span data-stu-id="3b540-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="3b540-216">EJEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="3b540-216">EXAMPLE 2</span></span>

<span data-ttu-id="3b540-217">Este ejemplo prueba todas las reglas de autorización para comprobar qué reglas de autorización se aplican al usuario *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="3b540-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="3b540-218">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="3b540-218">Related topics</span></span>

- [<span data-ttu-id="3b540-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3b540-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="3b540-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3b540-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="3b540-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="3b540-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="3b540-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="3b540-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
