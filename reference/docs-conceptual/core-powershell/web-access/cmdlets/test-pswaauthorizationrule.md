---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Test-PswaAuthorizationRule
ms.openlocfilehash: 08248e65be229f9d0f4d606d6c0d039d86ced054
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190152"
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="9a2f8-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9a2f8-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="9a2f8-104">SINOPSIS</span><span class="sxs-lookup"><span data-stu-id="9a2f8-104">SYNOPSIS</span></span>

<span data-ttu-id="9a2f8-105">Comprueba si existe una regla para un usuario, un equipo o un punto de conexión determinados.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a2f8-106">SINTAXIS</span><span class="sxs-lookup"><span data-stu-id="9a2f8-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="9a2f8-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="9a2f8-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="9a2f8-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="9a2f8-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="9a2f8-109">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="9a2f8-109">DESCRIPTION</span></span>

<span data-ttu-id="9a2f8-110">El cmdlet **Test-PswaAuthorizationRule** comprueba si existe una regla para un usuario, un equipo o un punto de conexión determinado.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="9a2f8-111">Este cmdlet también se puede usar para probar las reglas de autorización y para validar que se ha autorizado una solicitud de acceso de punto de conexión, equipo o usuario en concreto.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="9a2f8-112">De forma predeterminada, este cmdlet evalúa todas las reglas del archivo de autorización,</span><span class="sxs-lookup"><span data-stu-id="9a2f8-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="9a2f8-113">aunque puede especificar que se evalúe un subconjunto de reglas.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="9a2f8-114">Puede usar este cmdlet para solucionar errores de autenticación.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="9a2f8-115">Los parámetros de este cmdlet corresponden a los campos de la página de inicio de sesión de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="9a2f8-116">PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="9a2f8-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="9a2f8-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9a2f8-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="9a2f8-118">Especifica el nombre del equipo que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-118">Specifies the name of the computer to test.</span></span>

|||
|-|-|
| <span data-ttu-id="9a2f8-119">Alias</span><span class="sxs-lookup"><span data-stu-id="9a2f8-119">Aliases</span></span>                              | <span data-ttu-id="9a2f8-120">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-120">none</span></span>                                 |
| <span data-ttu-id="9a2f8-121">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-121">Required?</span></span>                            | <span data-ttu-id="9a2f8-122">true</span><span class="sxs-lookup"><span data-stu-id="9a2f8-122">true</span></span>                                 |
| <span data-ttu-id="9a2f8-123">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-123">Position?</span></span>                            | <span data-ttu-id="9a2f8-124">2</span><span class="sxs-lookup"><span data-stu-id="9a2f8-124">2</span></span>                                    |
| <span data-ttu-id="9a2f8-125">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="9a2f8-125">Default Value</span></span>                        | <span data-ttu-id="9a2f8-126">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-126">none</span></span>                                 |
| <span data-ttu-id="9a2f8-127">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a2f8-128">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-128">false</span></span>                                |
| <span data-ttu-id="9a2f8-129">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a2f8-130">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="9a2f8-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9a2f8-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="9a2f8-132">Especifica el nombre de la configuración de sesión de Windows PowerShell que se va a probar (también conocida como "punto de conexión" o "espacio de ejecución").</span><span class="sxs-lookup"><span data-stu-id="9a2f8-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||
|-|-|
| <span data-ttu-id="9a2f8-133">Alias</span><span class="sxs-lookup"><span data-stu-id="9a2f8-133">Aliases</span></span>                              | <span data-ttu-id="9a2f8-134">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-134">none</span></span>                                 |
| <span data-ttu-id="9a2f8-135">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-135">Required?</span></span>                            | <span data-ttu-id="9a2f8-136">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-136">false</span></span>                                |
| <span data-ttu-id="9a2f8-137">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-137">Position?</span></span>                            | <span data-ttu-id="9a2f8-138">3</span><span class="sxs-lookup"><span data-stu-id="9a2f8-138">3</span></span>                                    |
| <span data-ttu-id="9a2f8-139">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="9a2f8-139">Default Value</span></span>                        | <span data-ttu-id="9a2f8-140">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-140">none</span></span>                                 |
| <span data-ttu-id="9a2f8-141">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a2f8-142">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-142">false</span></span>                                |
| <span data-ttu-id="9a2f8-143">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a2f8-144">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="9a2f8-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="9a2f8-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="9a2f8-146">Especifica el URI de conexión que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-146">Specifies the connection URI to test.</span></span>

|||
|-|-|
| <span data-ttu-id="9a2f8-147">Alias</span><span class="sxs-lookup"><span data-stu-id="9a2f8-147">Aliases</span></span>                              | <span data-ttu-id="9a2f8-148">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-148">none</span></span>                                 |
| <span data-ttu-id="9a2f8-149">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-149">Required?</span></span>                            | <span data-ttu-id="9a2f8-150">true</span><span class="sxs-lookup"><span data-stu-id="9a2f8-150">true</span></span>                                 |
| <span data-ttu-id="9a2f8-151">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-151">Position?</span></span>                            | <span data-ttu-id="9a2f8-152">2</span><span class="sxs-lookup"><span data-stu-id="9a2f8-152">2</span></span>                                    |
| <span data-ttu-id="9a2f8-153">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="9a2f8-153">Default Value</span></span>                        | <span data-ttu-id="9a2f8-154">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-154">none</span></span>                                 |
| <span data-ttu-id="9a2f8-155">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a2f8-156">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-156">false</span></span>                                |
| <span data-ttu-id="9a2f8-157">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a2f8-158">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="9a2f8-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="9a2f8-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="9a2f8-160">Especifica un objeto **PSCredential** para una cuenta de usuario que quiera usar para probar las reglas de autorización de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="9a2f8-161">Si no agrega este parámetro, el cmdlet usará la cuenta del usuario que ha iniciado la sesión.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="9a2f8-162">Para obtener un objeto **PSCredential**, necesario para probar las reglas de autorización de forma remota, ejecute el cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).</span><span class="sxs-lookup"><span data-stu-id="9a2f8-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="9a2f8-163">Alias</span><span class="sxs-lookup"><span data-stu-id="9a2f8-163">Aliases</span></span>                              | <span data-ttu-id="9a2f8-164">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-164">none</span></span>                                 |
| <span data-ttu-id="9a2f8-165">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-165">Required?</span></span>                            | <span data-ttu-id="9a2f8-166">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-166">false</span></span>                                |
| <span data-ttu-id="9a2f8-167">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-167">Position?</span></span>                            | <span data-ttu-id="9a2f8-168">llamada</span><span class="sxs-lookup"><span data-stu-id="9a2f8-168">named</span></span>                                |
| <span data-ttu-id="9a2f8-169">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="9a2f8-169">Default Value</span></span>                        | <span data-ttu-id="9a2f8-170">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-170">none</span></span>                                 |
| <span data-ttu-id="9a2f8-171">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a2f8-172">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-172">false</span></span>                                |
| <span data-ttu-id="9a2f8-173">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a2f8-174">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="9a2f8-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="9a2f8-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="9a2f8-176">Especifica un subconjunto de reglas que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="9a2f8-177">Si no se especifica este parámetro, este cmdlet hará una prueba en todas las reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="9a2f8-178">Alias</span><span class="sxs-lookup"><span data-stu-id="9a2f8-178">Aliases</span></span>                              | <span data-ttu-id="9a2f8-179">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-179">none</span></span>                                 |
| <span data-ttu-id="9a2f8-180">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-180">Required?</span></span>                            | <span data-ttu-id="9a2f8-181">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-181">false</span></span>                                |
| <span data-ttu-id="9a2f8-182">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-182">Position?</span></span>                            | <span data-ttu-id="9a2f8-183">llamada</span><span class="sxs-lookup"><span data-stu-id="9a2f8-183">named</span></span>                                |
| <span data-ttu-id="9a2f8-184">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="9a2f8-184">Default Value</span></span>                        | <span data-ttu-id="9a2f8-185">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-185">none</span></span>                                 |
| <span data-ttu-id="9a2f8-186">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a2f8-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="9a2f8-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="9a2f8-188">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a2f8-189">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="9a2f8-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="9a2f8-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="9a2f8-191">Especifica el nombre del usuario que se va a probar.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-191">Specifies the name of the user to test.</span></span>

|||
|-|-|
| <span data-ttu-id="9a2f8-192">Alias</span><span class="sxs-lookup"><span data-stu-id="9a2f8-192">Aliases</span></span>                              | <span data-ttu-id="9a2f8-193">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-193">none</span></span>                                 |
| <span data-ttu-id="9a2f8-194">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-194">Required?</span></span>                            | <span data-ttu-id="9a2f8-195">true</span><span class="sxs-lookup"><span data-stu-id="9a2f8-195">true</span></span>                                 |
| <span data-ttu-id="9a2f8-196">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-196">Position?</span></span>                            | <span data-ttu-id="9a2f8-197">1</span><span class="sxs-lookup"><span data-stu-id="9a2f8-197">1</span></span>                                    |
| <span data-ttu-id="9a2f8-198">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="9a2f8-198">Default Value</span></span>                        | <span data-ttu-id="9a2f8-199">ninguno</span><span class="sxs-lookup"><span data-stu-id="9a2f8-199">none</span></span>                                 |
| <span data-ttu-id="9a2f8-200">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="9a2f8-201">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-201">false</span></span>                                |
| <span data-ttu-id="9a2f8-202">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="9a2f8-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="9a2f8-203">falso</span><span class="sxs-lookup"><span data-stu-id="9a2f8-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="9a2f8-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="9a2f8-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="9a2f8-205">Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="9a2f8-206">Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9a2f8-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="9a2f8-207">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="9a2f8-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="9a2f8-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="9a2f8-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="9a2f8-209">Este cmdlet acepta una matriz de objetos PswaAuthorizationRule como entrada.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="9a2f8-210">SALIDAS</span><span class="sxs-lookup"><span data-stu-id="9a2f8-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="9a2f8-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="9a2f8-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="9a2f8-212">Este cmdlet genera una matriz de objetos PswaAuthorizationRule como salida.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="9a2f8-213">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="9a2f8-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="9a2f8-214">EJEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="9a2f8-214">EXAMPLE 1</span></span>

<span data-ttu-id="9a2f8-215">Este ejemplo prueba todas las reglas de autorización para que se muestren todas las reglas que permiten que el usuario *contoso\\mhanson* se conecte al equipo *srv2* y use una configuración de sesión de Windows PowerShell denominada *test*.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="9a2f8-216">EJEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="9a2f8-216">EXAMPLE 2</span></span>

<span data-ttu-id="9a2f8-217">Este ejemplo prueba todas las reglas de autorización para comprobar qué reglas de autorización se aplican al usuario *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="9a2f8-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="9a2f8-218">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="9a2f8-218">Related topics</span></span>

- [<span data-ttu-id="9a2f8-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9a2f8-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="9a2f8-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9a2f8-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="9a2f8-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="9a2f8-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="9a2f8-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="9a2f8-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)