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
ms.openlocfilehash: 1b480b68c7ce2064f42281d8c5d76156a39e0222
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2017
---
#  <a name="test-pswaauthorizationrule"></a><span data-ttu-id="ba98a-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ba98a-103">Test-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="ba98a-104">SINOPSIS</span><span class="sxs-lookup"><span data-stu-id="ba98a-104">SYNOPSIS</span></span>

<span data-ttu-id="ba98a-105">Comprueba si existe una regla para un usuario, un equipo o un punto de conexión determinados.</span><span class="sxs-lookup"><span data-stu-id="ba98a-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="ba98a-106">SINTAXIS</span><span class="sxs-lookup"><span data-stu-id="ba98a-106">SYNTAX</span></span>

###  <a name="computername"></a><span data-ttu-id="ba98a-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="ba98a-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

###  <a name="connectionuri"></a><span data-ttu-id="ba98a-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="ba98a-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="ba98a-109">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="ba98a-109">DESCRIPTION</span></span>

<span data-ttu-id="ba98a-110">El cmdlet **Test-PswaAuthorizationRule** comprueba si existe una regla para un usuario, un equipo o un punto de conexión determinado.</span><span class="sxs-lookup"><span data-stu-id="ba98a-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="ba98a-111">Este cmdlet también se puede usar para probar las reglas de autorización y para validar que se ha autorizado una solicitud de acceso de punto de conexión, equipo o usuario en concreto.</span><span class="sxs-lookup"><span data-stu-id="ba98a-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="ba98a-112">De forma predeterminada, este cmdlet evalúa todas las reglas del archivo de autorización,</span><span class="sxs-lookup"><span data-stu-id="ba98a-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="ba98a-113">aunque puede especificar que se evalúe un subconjunto de reglas.</span><span class="sxs-lookup"><span data-stu-id="ba98a-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="ba98a-114">Puede usar este cmdlet para solucionar errores de autenticación.</span><span class="sxs-lookup"><span data-stu-id="ba98a-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="ba98a-115">Los parámetros de este cmdlet corresponden a los campos de la página de inicio de sesión de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="ba98a-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="ba98a-116">PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="ba98a-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="ba98a-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="ba98a-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="ba98a-118">Especifica el nombre del equipo que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="ba98a-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="ba98a-119">Alias</span><span class="sxs-lookup"><span data-stu-id="ba98a-119">Aliases</span></span>                              | <span data-ttu-id="ba98a-120">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-120">none</span></span>                                 |
| <span data-ttu-id="ba98a-121">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="ba98a-121">Required?</span></span>                            | <span data-ttu-id="ba98a-122">true</span><span class="sxs-lookup"><span data-stu-id="ba98a-122">true</span></span>                                 |
| <span data-ttu-id="ba98a-123">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="ba98a-123">Position?</span></span>                            | <span data-ttu-id="ba98a-124">2</span><span class="sxs-lookup"><span data-stu-id="ba98a-124">2</span></span>                                    |
| <span data-ttu-id="ba98a-125">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="ba98a-125">Default Value</span></span>                        | <span data-ttu-id="ba98a-126">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-126">none</span></span>                                 |
| <span data-ttu-id="ba98a-127">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="ba98a-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ba98a-128">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-128">false</span></span>                                |
| <span data-ttu-id="ba98a-129">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="ba98a-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ba98a-130">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="ba98a-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="ba98a-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="ba98a-132">Especifica el nombre de la configuración de sesión de Windows PowerShell que se va a probar (también conocida como "punto de conexión" o "espacio de ejecución").</span><span class="sxs-lookup"><span data-stu-id="ba98a-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="ba98a-133">Alias</span><span class="sxs-lookup"><span data-stu-id="ba98a-133">Aliases</span></span>                              | <span data-ttu-id="ba98a-134">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-134">none</span></span>                                 |
| <span data-ttu-id="ba98a-135">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="ba98a-135">Required?</span></span>                            | <span data-ttu-id="ba98a-136">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-136">false</span></span>                                |
| <span data-ttu-id="ba98a-137">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="ba98a-137">Position?</span></span>                            | <span data-ttu-id="ba98a-138">3</span><span class="sxs-lookup"><span data-stu-id="ba98a-138">3</span></span>                                    |
| <span data-ttu-id="ba98a-139">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="ba98a-139">Default Value</span></span>                        | <span data-ttu-id="ba98a-140">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-140">none</span></span>                                 |
| <span data-ttu-id="ba98a-141">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="ba98a-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ba98a-142">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-142">false</span></span>                                |
| <span data-ttu-id="ba98a-143">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="ba98a-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ba98a-144">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="ba98a-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="ba98a-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="ba98a-146">Especifica el URI de conexión que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="ba98a-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="ba98a-147">Alias</span><span class="sxs-lookup"><span data-stu-id="ba98a-147">Aliases</span></span>                              | <span data-ttu-id="ba98a-148">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-148">none</span></span>                                 |
| <span data-ttu-id="ba98a-149">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="ba98a-149">Required?</span></span>                            | <span data-ttu-id="ba98a-150">true</span><span class="sxs-lookup"><span data-stu-id="ba98a-150">true</span></span>                                 |
| <span data-ttu-id="ba98a-151">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="ba98a-151">Position?</span></span>                            | <span data-ttu-id="ba98a-152">2</span><span class="sxs-lookup"><span data-stu-id="ba98a-152">2</span></span>                                    |
| <span data-ttu-id="ba98a-153">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="ba98a-153">Default Value</span></span>                        | <span data-ttu-id="ba98a-154">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-154">none</span></span>                                 |
| <span data-ttu-id="ba98a-155">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="ba98a-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ba98a-156">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-156">false</span></span>                                |
| <span data-ttu-id="ba98a-157">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="ba98a-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ba98a-158">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="ba98a-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="ba98a-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="ba98a-160">Especifica un objeto **PSCredential** para una cuenta de usuario que quiera usar para probar las reglas de autorización de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="ba98a-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="ba98a-161">Si no agrega este parámetro, el cmdlet usará la cuenta del usuario que ha iniciado la sesión.</span><span class="sxs-lookup"><span data-stu-id="ba98a-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="ba98a-162">Para obtener un objeto **PSCredential**, necesario para probar las reglas de autorización de forma remota, ejecute el cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).</span><span class="sxs-lookup"><span data-stu-id="ba98a-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="ba98a-163">Alias</span><span class="sxs-lookup"><span data-stu-id="ba98a-163">Aliases</span></span>                              | <span data-ttu-id="ba98a-164">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-164">none</span></span>                                 |
| <span data-ttu-id="ba98a-165">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="ba98a-165">Required?</span></span>                            | <span data-ttu-id="ba98a-166">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-166">false</span></span>                                |
| <span data-ttu-id="ba98a-167">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="ba98a-167">Position?</span></span>                            | <span data-ttu-id="ba98a-168">llamada</span><span class="sxs-lookup"><span data-stu-id="ba98a-168">named</span></span>                                |
| <span data-ttu-id="ba98a-169">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="ba98a-169">Default Value</span></span>                        | <span data-ttu-id="ba98a-170">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-170">none</span></span>                                 |
| <span data-ttu-id="ba98a-171">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="ba98a-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ba98a-172">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-172">false</span></span>                                |
| <span data-ttu-id="ba98a-173">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="ba98a-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ba98a-174">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="ba98a-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="ba98a-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="ba98a-176">Especifica un subconjunto de reglas que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="ba98a-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="ba98a-177">Si no se especifica este parámetro, este cmdlet hará una prueba en todas las reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="ba98a-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="ba98a-178">Alias</span><span class="sxs-lookup"><span data-stu-id="ba98a-178">Aliases</span></span>                              | <span data-ttu-id="ba98a-179">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-179">none</span></span>                                 |
| <span data-ttu-id="ba98a-180">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="ba98a-180">Required?</span></span>                            | <span data-ttu-id="ba98a-181">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-181">false</span></span>                                |
| <span data-ttu-id="ba98a-182">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="ba98a-182">Position?</span></span>                            | <span data-ttu-id="ba98a-183">llamada</span><span class="sxs-lookup"><span data-stu-id="ba98a-183">named</span></span>                                |
| <span data-ttu-id="ba98a-184">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="ba98a-184">Default Value</span></span>                        | <span data-ttu-id="ba98a-185">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-185">none</span></span>                                 |
| <span data-ttu-id="ba98a-186">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="ba98a-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ba98a-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="ba98a-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="ba98a-188">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="ba98a-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ba98a-189">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="ba98a-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="ba98a-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="ba98a-191">Especifica el nombre del usuario que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="ba98a-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="ba98a-192">Alias</span><span class="sxs-lookup"><span data-stu-id="ba98a-192">Aliases</span></span>                              | <span data-ttu-id="ba98a-193">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-193">none</span></span>                                 |
| <span data-ttu-id="ba98a-194">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="ba98a-194">Required?</span></span>                            | <span data-ttu-id="ba98a-195">true</span><span class="sxs-lookup"><span data-stu-id="ba98a-195">true</span></span>                                 |
| <span data-ttu-id="ba98a-196">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="ba98a-196">Position?</span></span>                            | <span data-ttu-id="ba98a-197">1</span><span class="sxs-lookup"><span data-stu-id="ba98a-197">1</span></span>                                    |
| <span data-ttu-id="ba98a-198">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="ba98a-198">Default Value</span></span>                        | <span data-ttu-id="ba98a-199">ninguno</span><span class="sxs-lookup"><span data-stu-id="ba98a-199">none</span></span>                                 |
| <span data-ttu-id="ba98a-200">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="ba98a-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ba98a-201">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-201">false</span></span>                                |
| <span data-ttu-id="ba98a-202">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="ba98a-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ba98a-203">falso</span><span class="sxs-lookup"><span data-stu-id="ba98a-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="ba98a-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="ba98a-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="ba98a-205">Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="ba98a-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="ba98a-206">Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ba98a-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="ba98a-207">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="ba98a-207">INPUTS</span></span>

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="ba98a-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="ba98a-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="ba98a-209">Este cmdlet acepta una matriz de objetos PswaAuthorizationRule como entrada.</span><span class="sxs-lookup"><span data-stu-id="ba98a-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

##  <a name="outputs"></a><span data-ttu-id="ba98a-210">SALIDAS</span><span class="sxs-lookup"><span data-stu-id="ba98a-210">OUTPUTS</span></span>

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="ba98a-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="ba98a-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="ba98a-212">Este cmdlet genera una matriz de objetos PswaAuthorizationRule como salida.</span><span class="sxs-lookup"><span data-stu-id="ba98a-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="ba98a-213">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="ba98a-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="ba98a-214">EJEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="ba98a-214">EXAMPLE 1</span></span>

<span data-ttu-id="ba98a-215">Este ejemplo prueba todas las reglas de autorización para que se muestren todas las reglas que permiten que el usuario *contoso\\mhanson* se conecte al equipo *srv2* y use una configuración de sesión de Windows PowerShell denominada *test*.</span><span class="sxs-lookup"><span data-stu-id="ba98a-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="ba98a-216">EJEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="ba98a-216">EXAMPLE 2</span></span>

<span data-ttu-id="ba98a-217">Este ejemplo prueba todas las reglas de autorización para comprobar qué reglas de autorización se aplican al usuario *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="ba98a-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

##  <a name="related-topics"></a><span data-ttu-id="ba98a-218">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="ba98a-218">Related topics</span></span>

-  [<span data-ttu-id="ba98a-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ba98a-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="ba98a-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ba98a-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
-  [<span data-ttu-id="ba98a-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="ba98a-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
-  [<span data-ttu-id="ba98a-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ba98a-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
