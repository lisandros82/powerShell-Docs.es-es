---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: add pswaauthorizationrule
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 12f5cc30d4e3f9cfdd739cacbbab96134077e50a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2017
---
#  <a name="add-pswaauthorizationrule"></a><span data-ttu-id="c0aa4-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c0aa4-103">Add-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="c0aa4-104">SINOPSIS</span><span class="sxs-lookup"><span data-stu-id="c0aa4-104">SYNOPSIS</span></span>

<span data-ttu-id="c0aa4-105">Agrega una nueva regla de autorización al conjunto de reglas de autorización de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="c0aa4-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c0aa4-106">Syntax</span></span>

###  <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="c0aa4-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="c0aa4-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usergroupnamecomputername"></a><span data-ttu-id="c0aa4-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="c0aa4-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputergroupname"></a><span data-ttu-id="c0aa4-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="c0aa4-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputername"></a><span data-ttu-id="c0aa4-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="c0aa4-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="c0aa4-111">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="c0aa4-111">DESCRIPTION</span></span>

<span data-ttu-id="c0aa4-112">El cmdlet **Add-PswaAuthorizationRule** agrega una nueva regla de autorización al conjunto de reglas de autorización de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="c0aa4-113">Debe especificar los usuarios, los equipos y los puntos de conexión de Windows PowerShell para esta regla.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="c0aa4-114">Puede especificar los usuarios y los equipos ya sea por cuentas de usuario y nombres de equipo concretos o especificando grupos.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="c0aa4-115">Para un equipo que está unido a un dominio de Active Directory, el cmdlet usa el identificador de seguridad (SID) del equipo para crear la regla.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="c0aa4-116">Esto le permite usar un nombre corto, un nombre de dominio completo (FQDN) o una dirección IP para el campo **Nombre del equipo** en la página de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="c0aa4-117">En el caso de los equipos que no están unidos a un dominio de Active Directory, el cmdlet crea la regla con el nombre del equipo proporcionado por el administrador.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="c0aa4-118">Para conectarse correctamente a este equipo, el usuario final debe proporcionar el nombre del equipo tal y como aparece en la regla.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="c0aa4-119">Si hay varios equipos con el mismo nombre en la red, el nombre corto se puede resolver en más de un equipo,</span><span class="sxs-lookup"><span data-stu-id="c0aa4-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="c0aa4-120">lo cual puede generar ambigüedad a la hora de establecer una conexión.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="c0aa4-121">Por ejemplo, si existe una regla para el equipo del grupo de trabajo llamado "*Server1*" y se une a la red un equipo nuevo llamado *server1.contoso.com*, la validación con las reglas de autorización se efectúa correctamente y Windows PowerShell Web Access intenta establecer una conexión con el equipo llamado "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="c0aa4-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="c0aa4-122">No se garantiza que se establezca la conexión con el equipo del grupo de trabajo especificado; el intento de conexión podría efectuarse en el grupo de trabajo o en el equipo del dominio denominado "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="c0aa4-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="c0aa4-123">Para reducir la ambigüedad, se recomienda usar el FQDN del equipo de destino siempre que sea posible para crear una regla de autorización.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="c0aa4-124">Las reglas de autorización evalúan la credencial de inicio de sesión principal de los usuarios de Windows PowerShell Web Access, y no las credenciales alternativas (el segundo conjunto de credenciales de la sección **Configuración de conexión opcional** de la página de inicio de sesión).</span><span class="sxs-lookup"><span data-stu-id="c0aa4-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="c0aa4-125">Para ver un ejemplo, vea el ejemplo 6.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="c0aa4-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="c0aa4-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="c0aa4-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="c0aa4-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="c0aa4-128">Especifica el nombre de un grupo de equipos de Active Directory Domain Services (AD DS) o de grupos locales a los que concede acceso esta regla.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="c0aa4-129">Alias</span><span class="sxs-lookup"><span data-stu-id="c0aa4-129">Aliases</span></span>                              | <span data-ttu-id="c0aa4-130">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-130">none</span></span>                                 |
| <span data-ttu-id="c0aa4-131">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-131">Required?</span></span>                            | <span data-ttu-id="c0aa4-132">true</span><span class="sxs-lookup"><span data-stu-id="c0aa4-132">true</span></span>                                 |
| <span data-ttu-id="c0aa4-133">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-133">Position?</span></span>                            | <span data-ttu-id="c0aa4-134">llamada</span><span class="sxs-lookup"><span data-stu-id="c0aa4-134">named</span></span>                                |
| <span data-ttu-id="c0aa4-135">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c0aa4-135">Default Value</span></span>                        | <span data-ttu-id="c0aa4-136">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-136">none</span></span>                                 |
| <span data-ttu-id="c0aa4-137">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c0aa4-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c0aa4-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="c0aa4-139">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c0aa4-140">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="c0aa4-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="c0aa4-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="c0aa4-142">Especifica el nombre del equipo al que concede acceso esta regla.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-142">Specifies the computer name to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="c0aa4-143">Alias</span><span class="sxs-lookup"><span data-stu-id="c0aa4-143">Aliases</span></span>                              | <span data-ttu-id="c0aa4-144">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-144">none</span></span>                                 |
| <span data-ttu-id="c0aa4-145">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-145">Required?</span></span>                            | <span data-ttu-id="c0aa4-146">true</span><span class="sxs-lookup"><span data-stu-id="c0aa4-146">true</span></span>                                 |
| <span data-ttu-id="c0aa4-147">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-147">Position?</span></span>                            | <span data-ttu-id="c0aa4-148">llamada</span><span class="sxs-lookup"><span data-stu-id="c0aa4-148">named</span></span>                                |
| <span data-ttu-id="c0aa4-149">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c0aa4-149">Default Value</span></span>                        | <span data-ttu-id="c0aa4-150">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-150">none</span></span>                                 |
| <span data-ttu-id="c0aa4-151">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c0aa4-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c0aa4-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="c0aa4-153">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c0aa4-154">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="c0aa4-155">-ConfigurationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="c0aa4-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="c0aa4-156">Especifica el nombre de la configuración de sesión de Windows PowerShell (también conocida como "espacio de ejecución") a la que concede acceso esta regla.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="c0aa4-157">Alias</span><span class="sxs-lookup"><span data-stu-id="c0aa4-157">Aliases</span></span>                              | <span data-ttu-id="c0aa4-158">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-158">none</span></span>                                 |
| <span data-ttu-id="c0aa4-159">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-159">Required?</span></span>                            | <span data-ttu-id="c0aa4-160">true</span><span class="sxs-lookup"><span data-stu-id="c0aa4-160">true</span></span>                                 |
| <span data-ttu-id="c0aa4-161">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-161">Position?</span></span>                            | <span data-ttu-id="c0aa4-162">llamada</span><span class="sxs-lookup"><span data-stu-id="c0aa4-162">named</span></span>                                |
| <span data-ttu-id="c0aa4-163">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c0aa4-163">Default Value</span></span>                        | <span data-ttu-id="c0aa4-164">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-164">none</span></span>                                 |
| <span data-ttu-id="c0aa4-165">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c0aa4-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c0aa4-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="c0aa4-167">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c0aa4-168">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="c0aa4-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="c0aa4-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="c0aa4-170">Especifica un objeto **PSCredential** para una cuenta de usuario que quiera usar para cambiar las reglas de autorización de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="c0aa4-171">Si no agrega este parámetro, el cmdlet usará la cuenta del usuario que ha iniciado la sesión.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="c0aa4-172">Para obtener un objeto **PSCredential**, necesario para agregar reglas de autorización de forma remota, ejecute el cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).</span><span class="sxs-lookup"><span data-stu-id="c0aa4-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="c0aa4-173">Alias</span><span class="sxs-lookup"><span data-stu-id="c0aa4-173">Aliases</span></span>                              | <span data-ttu-id="c0aa4-174">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-174">none</span></span>                                 |
| <span data-ttu-id="c0aa4-175">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-175">Required?</span></span>                            | <span data-ttu-id="c0aa4-176">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-176">false</span></span>                                |
| <span data-ttu-id="c0aa4-177">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-177">Position?</span></span>                            | <span data-ttu-id="c0aa4-178">llamada</span><span class="sxs-lookup"><span data-stu-id="c0aa4-178">named</span></span>                                |
| <span data-ttu-id="c0aa4-179">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c0aa4-179">Default Value</span></span>                        | <span data-ttu-id="c0aa4-180">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-180">none</span></span>                                 |
| <span data-ttu-id="c0aa4-181">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c0aa4-182">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-182">false</span></span>                                |
| <span data-ttu-id="c0aa4-183">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c0aa4-184">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="c0aa4-185">-Force</span><span class="sxs-lookup"><span data-stu-id="c0aa4-185">-Force</span></span>

<span data-ttu-id="c0aa4-186">Obliga al comando a ejecutarse sin solicitar la confirmación del usuario. \\</span><span class="sxs-lookup"><span data-stu-id="c0aa4-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="c0aa4-187">También pide confirmación al escribir un nombre de equipo corto o simple (por ejemplo, un nombre que no es un nombre de dominio o un nombre no completo).</span><span class="sxs-lookup"><span data-stu-id="c0aa4-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="c0aa4-188">La confirmación se solicita por motivos de seguridad, de modo que puede usar el nombre simple para agregar un equipo únicamente si dicho equipo se encuentra en un grupo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||  
|-|-|
| <span data-ttu-id="c0aa4-189">Alias</span><span class="sxs-lookup"><span data-stu-id="c0aa4-189">Aliases</span></span>                              | <span data-ttu-id="c0aa4-190">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-190">none</span></span>                                 |
| <span data-ttu-id="c0aa4-191">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-191">Required?</span></span>                            | <span data-ttu-id="c0aa4-192">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-192">false</span></span>                                |
| <span data-ttu-id="c0aa4-193">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-193">Position?</span></span>                            | <span data-ttu-id="c0aa4-194">llamada</span><span class="sxs-lookup"><span data-stu-id="c0aa4-194">named</span></span>                                |
| <span data-ttu-id="c0aa4-195">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c0aa4-195">Default Value</span></span>                        | <span data-ttu-id="c0aa4-196">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-196">none</span></span>                                 |
| <span data-ttu-id="c0aa4-197">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c0aa4-198">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-198">false</span></span>                                |
| <span data-ttu-id="c0aa4-199">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c0aa4-200">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="c0aa4-201">-RuleName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="c0aa4-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="c0aa4-202">Especifica el nombre descriptivo de esta regla.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-202">Specifies the friendly name for this rule.</span></span>

|||  
|-|-|
| <span data-ttu-id="c0aa4-203">Alias</span><span class="sxs-lookup"><span data-stu-id="c0aa4-203">Aliases</span></span>                              | <span data-ttu-id="c0aa4-204">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-204">none</span></span>                                 |
| <span data-ttu-id="c0aa4-205">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-205">Required?</span></span>                            | <span data-ttu-id="c0aa4-206">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-206">false</span></span>                                |
| <span data-ttu-id="c0aa4-207">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-207">Position?</span></span>                            | <span data-ttu-id="c0aa4-208">llamada</span><span class="sxs-lookup"><span data-stu-id="c0aa4-208">named</span></span>                                |
| <span data-ttu-id="c0aa4-209">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c0aa4-209">Default Value</span></span>                        | <span data-ttu-id="c0aa4-210">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-210">none</span></span>                                 |
| <span data-ttu-id="c0aa4-211">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c0aa4-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c0aa4-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="c0aa4-213">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c0aa4-214">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="c0aa4-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="c0aa4-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="c0aa4-216">Especifica el nombre de uno o varios grupos de usuarios en AD DS o en grupos locales a los que concede acceso esta regla.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="c0aa4-217">Alias</span><span class="sxs-lookup"><span data-stu-id="c0aa4-217">Aliases</span></span>                              | <span data-ttu-id="c0aa4-218">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-218">none</span></span>                                 |
| <span data-ttu-id="c0aa4-219">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-219">Required?</span></span>                            | <span data-ttu-id="c0aa4-220">true</span><span class="sxs-lookup"><span data-stu-id="c0aa4-220">true</span></span>                                 |
| <span data-ttu-id="c0aa4-221">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-221">Position?</span></span>                            | <span data-ttu-id="c0aa4-222">llamada</span><span class="sxs-lookup"><span data-stu-id="c0aa4-222">named</span></span>                                |
| <span data-ttu-id="c0aa4-223">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c0aa4-223">Default Value</span></span>                        | <span data-ttu-id="c0aa4-224">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-224">none</span></span>                                 |
| <span data-ttu-id="c0aa4-225">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c0aa4-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c0aa4-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="c0aa4-227">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c0aa4-228">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="c0aa4-229">-UserName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="c0aa4-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="c0aa4-230">Especifica uno o varios usuarios a los que concede acceso esta regla.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="c0aa4-231">El nombre de usuario puede ser una cuenta de usuario local del equipo de la puerta de enlace o un usuario de AD DS.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="c0aa4-232">El formato es `domain\user` o `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-232">The format is `domain\user` or `computer\user`.</span></span>

|||  
|-|-|
| <span data-ttu-id="c0aa4-233">Alias</span><span class="sxs-lookup"><span data-stu-id="c0aa4-233">Aliases</span></span>                              | <span data-ttu-id="c0aa4-234">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-234">none</span></span>                                 |
| <span data-ttu-id="c0aa4-235">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-235">Required?</span></span>                            | <span data-ttu-id="c0aa4-236">true</span><span class="sxs-lookup"><span data-stu-id="c0aa4-236">true</span></span>                                 |
| <span data-ttu-id="c0aa4-237">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-237">Position?</span></span>                            | <span data-ttu-id="c0aa4-238">1</span><span class="sxs-lookup"><span data-stu-id="c0aa4-238">1</span></span>                                    |
| <span data-ttu-id="c0aa4-239">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c0aa4-239">Default Value</span></span>                        | <span data-ttu-id="c0aa4-240">ninguno</span><span class="sxs-lookup"><span data-stu-id="c0aa4-240">none</span></span>                                 |
| <span data-ttu-id="c0aa4-241">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c0aa4-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c0aa4-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="c0aa4-243">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="c0aa4-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c0aa4-244">falso</span><span class="sxs-lookup"><span data-stu-id="c0aa4-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="c0aa4-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="c0aa4-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="c0aa4-246">Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="c0aa4-247">Para más información, vea [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="c0aa4-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="c0aa4-248">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="c0aa4-248">INPUTS</span></span>

###  <a name="string"></a><span data-ttu-id="c0aa4-249">Cadena</span><span class="sxs-lookup"><span data-stu-id="c0aa4-249">String</span></span>

<span data-ttu-id="c0aa4-250">Este cmdlet acepta como entrada una cadena o una matriz de cadenas.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-250">This cmdlet accepts a string or an array of strings as input.</span></span>

###  <a name="string"></a><span data-ttu-id="c0aa4-251">String\[\]</span><span class="sxs-lookup"><span data-stu-id="c0aa4-251">String\[\]</span></span>

<span data-ttu-id="c0aa4-252">Este cmdlet acepta como entrada una cadena o una matriz de cadenas.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-252">This cmdlet accepts a string or an array of strings as input.</span></span>

##  <a name="outputs"></a><span data-ttu-id="c0aa4-253">Salidas</span><span class="sxs-lookup"><span data-stu-id="c0aa4-253">Outputs</span></span>

###   <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="c0aa4-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c0aa4-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="c0aa4-255">Este cmdlet devuelve el objeto de la regla de autorización.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="c0aa4-256">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="c0aa4-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="c0aa4-257">EJEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="c0aa4-257">EXAMPLE 1</span></span>

<span data-ttu-id="c0aa4-258">Este ejemplo concede acceso a la configuración de sesión *PSWAEndpoint*, a un espacio de ejecución restringido, en *srv2* para los usuarios del grupo *SMAdmins*. \\</span><span class="sxs-lookup"><span data-stu-id="c0aa4-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="c0aa4-259">**Nota**: El nombre del equipo debe ser un nombre de dominio completo (FQDN).</span><span class="sxs-lookup"><span data-stu-id="c0aa4-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="c0aa4-260">Los administradores definen una configuración de sesión o espacio de ejecución restringido, que es un intervalo limitado de cmdlets y tareas que los usuarios finales pueden ejecutar.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="c0aa4-261">Definir un espacio de ejecución restringido puede impedir que los usuarios puedan obtener acceso a otros equipos que no se encuentran en el espacio de ejecución de Windows PowerShell® permitido, lo que garantiza una conexión más segura.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="c0aa4-262">Para más información sobre las configuraciones de sesión, vea [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) o [Instalación y uso de Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="c0aa4-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="c0aa4-263">EJEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="c0aa4-263">EXAMPLE 2</span></span>

<span data-ttu-id="c0aa4-264">Este ejemplo concede acceso a la configuración de sesión predeterminada de Windows PowerShell, `Microsoft.PowerShell`, en *srv2* para los usuarios de los usuarios denominados contoso\\user1, contoso\\user2 y contoso\\user3.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="c0aa4-265">Este cmdlet crea tres reglas (una por persona).</span><span class="sxs-lookup"><span data-stu-id="c0aa4-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="c0aa4-266">EJEMPLO 3</span><span class="sxs-lookup"><span data-stu-id="c0aa4-266">EXAMPLE 3</span></span>

<span data-ttu-id="c0aa4-267">En este ejemplo se muestra cómo se especifican valores de nombre de usuario a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="c0aa4-268">EJEMPLO 4</span><span class="sxs-lookup"><span data-stu-id="c0aa4-268">EXAMPLE 4</span></span>

<span data-ttu-id="c0aa4-269">En este ejemplo se muestra cómo todos los parámetros toman valores de la canalización por nombre de propiedad.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

\
###   <a name="section-subheading"></a><span data-ttu-id="c0aa4-270">{#section .subHeading}</span><span class="sxs-lookup"><span data-stu-id="c0aa4-270">{#section .subHeading}</span></span>

<div class="subSection">

<div id="code-snippet-5" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="c0aa4-271">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0aa4-271">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="c0aa4-272">Copiar</span><span class="sxs-lookup"><span data-stu-id="c0aa4-272">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f'); "Copiar al Portapapeles.")

</div>

</div>

<div id="CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o = New-Object -TypeName PSObject | Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

</div>

</div>

</div>

</div>

</div>

###   <a name="section-1-subheading"></a><span data-ttu-id="c0aa4-273">{#section-1 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="c0aa4-273">{#section-1 .subHeading}</span></span>

<div class="subSection">

<div id="code-snippet-6" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="c0aa4-274">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0aa4-274">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="c0aa4-275">Copiar</span><span class="sxs-lookup"><span data-stu-id="c0aa4-275">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb'); "Copiar al Portapapeles.")

</div>

</div>

<div id="CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

</div>

### <a name="example-5-example-5-subheading"></a><span data-ttu-id="c0aa4-276">EJEMPLO 5 {#example-5 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="c0aa4-276">EXAMPLE 5 {#example-5 .subHeading}</span></span>

<div class="subSection">

<span data-ttu-id="c0aa4-277">Este ejemplo agrega una regla para permitir que el usuario local llamado *PswaServer\\ChrisLocal* obtenga acceso al servidor llamado *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-277">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="c0aa4-278">En este ejemplo se muestra un escenario en el que la puerta de enlace está en un grupo de trabajo y el equipo de destino está en un dominio.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-278">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="c0aa4-279">La regla de autorización se aplica a los usuarios locales de la puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-279">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="c0aa4-280">En la página de inicio de sesión de Windows PowerShell Web Access, para autenticarse correctamente, el usuario debe proporcionar un segundo conjunto de credenciales en el área **Configuración de conexión opcional**.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-280">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="c0aa4-281">El servidor de puerta de enlace usa el conjunto de credenciales adicional para autenticar al usuario en el equipo de destino, un servidor llamado *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-281">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

\
<div id="code-snippet-7" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="c0aa4-282">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0aa4-282">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="c0aa4-283">Copiar</span><span class="sxs-lookup"><span data-stu-id="c0aa4-283">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3'); "Copiar al Portapapeles.")

</div>

</div>

<div id="CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

### <a name="example-6-example-6-subheading"></a><span data-ttu-id="c0aa4-284">EJEMPLO 6 {#example-6 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="c0aa4-284">EXAMPLE 6 {#example-6 .subHeading}</span></span>

<div class="subSection">

<span data-ttu-id="c0aa4-285">Este ejemplo permite que todos los usuarios obtengan acceso a todos los puntos de conexión de todos los equipos.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-285">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="c0aa4-286">Esto equivale a desactivar las reglas de autorización. \\</span><span class="sxs-lookup"><span data-stu-id="c0aa4-286">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="c0aa4-287">**Nota**: No se recomienda usar el carácter comodín `*` para las implementaciones de seguridad. Solo debe tenerse en cuenta para los entornos de prueba o bien en las implementaciones en las que la seguridad puede ser algo laxa.</span><span class="sxs-lookup"><span data-stu-id="c0aa4-287">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

\
<div id="code-snippet-8" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="c0aa4-288">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0aa4-288">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="c0aa4-289">Copiar</span><span class="sxs-lookup"><span data-stu-id="c0aa4-289">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076'); "Copiar al Portapapeles.")

</div>

</div>

<div id="CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *

</div>

</div>

</div>

</div>

</div>

</div>

<a name="related-topics"></a><span data-ttu-id="c0aa4-290">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="c0aa4-290">Related topics</span></span> 
--------------


<span data-ttu-id="c0aa4-291">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="c0aa4-291">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="c0aa4-292">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="c0aa4-292">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="c0aa4-293">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="c0aa4-293">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="c0aa4-294">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="c0aa4-294">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="c0aa4-295">[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)\\</span><span class="sxs-lookup"><span data-stu-id="c0aa4-295">[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)\\</span></span>
\
<span data-ttu-id="c0aa4-296">[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)\\</span><span class="sxs-lookup"><span data-stu-id="c0aa4-296">[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)\\</span></span>
\
[<span data-ttu-id="c0aa4-297">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="c0aa4-297">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)