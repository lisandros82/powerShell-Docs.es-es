---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: fe2b71dcfa870ba3f92484ae3fd3c45b3107a1bc
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523086"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="b99b1-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b99b1-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="b99b1-104">SINOPSIS</span><span class="sxs-lookup"><span data-stu-id="b99b1-104">SYNOPSIS</span></span>

<span data-ttu-id="b99b1-105">Agrega una nueva regla de autorización al conjunto de reglas de autorización de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="b99b1-105">Adds a new authorization rule to the Windows PowerShell Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="b99b1-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="b99b1-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="b99b1-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="b99b1-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="b99b1-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="b99b1-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="b99b1-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="b99b1-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="b99b1-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="b99b1-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="b99b1-111">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="b99b1-111">DESCRIPTION</span></span>

<span data-ttu-id="b99b1-112">El cmdlet **Add-PswaAuthorizationRule** agrega una nueva regla de autorización al conjunto de reglas de autorización de Windows PowerShell(r) Web Access.</span><span class="sxs-lookup"><span data-stu-id="b99b1-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell(r) Web Access authorization rule set.</span></span>

<span data-ttu-id="b99b1-113">Debe especificar los usuarios, los equipos y los puntos de conexión de Windows PowerShell para esta regla.</span><span class="sxs-lookup"><span data-stu-id="b99b1-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="b99b1-114">Puede especificar los usuarios y los equipos ya sea por cuentas de usuario y nombres de equipo concretos o especificando grupos.</span><span class="sxs-lookup"><span data-stu-id="b99b1-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="b99b1-115">Para un equipo que está unido a un dominio de Active Directory, el cmdlet usa el identificador de seguridad (SID) del equipo para crear la regla.</span><span class="sxs-lookup"><span data-stu-id="b99b1-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span> <span data-ttu-id="b99b1-116">Esto le permite usar un nombre corto, un nombre de dominio completo (FQDN) o una dirección IP para el campo **Nombre del equipo** en la página de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="b99b1-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="b99b1-117">En el caso de los equipos que no están unidos a un dominio de Active Directory, el cmdlet crea la regla con el nombre del equipo proporcionado por el administrador.</span><span class="sxs-lookup"><span data-stu-id="b99b1-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="b99b1-118">Para conectarse correctamente a este equipo, el usuario final debe proporcionar el nombre del equipo tal y como aparece en la regla.</span><span class="sxs-lookup"><span data-stu-id="b99b1-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="b99b1-119">Si hay varios equipos con el mismo nombre en la red, el nombre corto se puede resolver en más de un equipo,</span><span class="sxs-lookup"><span data-stu-id="b99b1-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="b99b1-120">lo cual puede generar ambigüedad a la hora de establecer una conexión.</span><span class="sxs-lookup"><span data-stu-id="b99b1-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="b99b1-121">Por ejemplo, si existe una regla para el equipo del grupo de trabajo llamado "*Server1*" y se une a la red un equipo nuevo llamado *server1.contoso.com*, la validación con las reglas de autorización se efectúa correctamente y Windows PowerShell Web Access intenta establecer una conexión con el equipo llamado "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="b99b1-121">For example, if a rule exists for the workgroup computer named "*Server1*" and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named "*Server1*".</span></span> <span data-ttu-id="b99b1-122">No se garantiza que se establezca la conexión con el equipo del grupo de trabajo especificado; el intento de conexión podría efectuarse en el grupo de trabajo o en el equipo del dominio denominado "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="b99b1-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="b99b1-123">Para reducir la ambigüedad, se recomienda usar el FQDN del equipo de destino siempre que sea posible para crear una regla de autorización.</span><span class="sxs-lookup"><span data-stu-id="b99b1-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="b99b1-124">Las reglas de autorización evalúan la credencial de inicio de sesión principal de los usuarios de Windows PowerShell Web Access, y no las credenciales alternativas (el segundo conjunto de credenciales de la sección **Configuración de conexión opcional** de la página de inicio de sesión).</span><span class="sxs-lookup"><span data-stu-id="b99b1-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="b99b1-125">Para ver un ejemplo, vea el ejemplo 6.</span><span class="sxs-lookup"><span data-stu-id="b99b1-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="b99b1-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b99b1-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="b99b1-127">-ComputerGroupName \<String\></span><span class="sxs-lookup"><span data-stu-id="b99b1-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="b99b1-128">Especifica el nombre de un grupo de equipos de Active Directory Domain Services (AD DS) o de grupos locales a los que concede acceso esta regla.</span><span class="sxs-lookup"><span data-stu-id="b99b1-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="b99b1-129">Alias</span><span class="sxs-lookup"><span data-stu-id="b99b1-129">Aliases</span></span>                     | <span data-ttu-id="b99b1-130">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-130">none</span></span>                  |
| <span data-ttu-id="b99b1-131">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b99b1-131">Required?</span></span>                   | <span data-ttu-id="b99b1-132">true</span><span class="sxs-lookup"><span data-stu-id="b99b1-132">true</span></span>                  |
| <span data-ttu-id="b99b1-133">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b99b1-133">Position?</span></span>                   | <span data-ttu-id="b99b1-134">llamada</span><span class="sxs-lookup"><span data-stu-id="b99b1-134">named</span></span>                 |
| <span data-ttu-id="b99b1-135">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b99b1-135">Default Value</span></span>               | <span data-ttu-id="b99b1-136">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-136">none</span></span>                  |
| <span data-ttu-id="b99b1-137">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b99b1-137">Accept Pipeline Input?</span></span>      | <span data-ttu-id="b99b1-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="b99b1-138">True (ByPropertyName)</span></span> |
| <span data-ttu-id="b99b1-139">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b99b1-139">Accept Wildcard Characters?</span></span> | <span data-ttu-id="b99b1-140">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-140">false</span></span>                 |

### <a name="-computername-string"></a><span data-ttu-id="b99b1-141">-ComputerName \<String\></span><span class="sxs-lookup"><span data-stu-id="b99b1-141">-ComputerName \<String\></span></span>

<span data-ttu-id="b99b1-142">Especifica el nombre del equipo al que concede acceso esta regla.</span><span class="sxs-lookup"><span data-stu-id="b99b1-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="b99b1-143">Alias</span><span class="sxs-lookup"><span data-stu-id="b99b1-143">Aliases</span></span>                     | <span data-ttu-id="b99b1-144">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-144">none</span></span>                  |
| <span data-ttu-id="b99b1-145">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b99b1-145">Required?</span></span>                   | <span data-ttu-id="b99b1-146">true</span><span class="sxs-lookup"><span data-stu-id="b99b1-146">true</span></span>                  |
| <span data-ttu-id="b99b1-147">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b99b1-147">Position?</span></span>                   | <span data-ttu-id="b99b1-148">llamada</span><span class="sxs-lookup"><span data-stu-id="b99b1-148">named</span></span>                 |
| <span data-ttu-id="b99b1-149">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b99b1-149">Default Value</span></span>               | <span data-ttu-id="b99b1-150">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-150">none</span></span>                  |
| <span data-ttu-id="b99b1-151">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b99b1-151">Accept Pipeline Input?</span></span>      | <span data-ttu-id="b99b1-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="b99b1-152">True (ByPropertyName)</span></span> |
| <span data-ttu-id="b99b1-153">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b99b1-153">Accept Wildcard Characters?</span></span> | <span data-ttu-id="b99b1-154">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-154">false</span></span>                 |

### <a name="-configurationname-string"></a><span data-ttu-id="b99b1-155">-ConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="b99b1-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="b99b1-156">Especifica el nombre de la configuración de sesión de Windows PowerShell (también conocida como "espacio de ejecución") a la que concede acceso esta regla.</span><span class="sxs-lookup"><span data-stu-id="b99b1-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="b99b1-157">Alias</span><span class="sxs-lookup"><span data-stu-id="b99b1-157">Aliases</span></span>                     | <span data-ttu-id="b99b1-158">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-158">none</span></span>                  |
| <span data-ttu-id="b99b1-159">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b99b1-159">Required?</span></span>                   | <span data-ttu-id="b99b1-160">true</span><span class="sxs-lookup"><span data-stu-id="b99b1-160">true</span></span>                  |
| <span data-ttu-id="b99b1-161">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b99b1-161">Position?</span></span>                   | <span data-ttu-id="b99b1-162">llamada</span><span class="sxs-lookup"><span data-stu-id="b99b1-162">named</span></span>                 |
| <span data-ttu-id="b99b1-163">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b99b1-163">Default Value</span></span>               | <span data-ttu-id="b99b1-164">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-164">none</span></span>                  |
| <span data-ttu-id="b99b1-165">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b99b1-165">Accept Pipeline Input?</span></span>      | <span data-ttu-id="b99b1-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="b99b1-166">True (ByPropertyName)</span></span> |
| <span data-ttu-id="b99b1-167">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b99b1-167">Accept Wildcard Characters?</span></span> | <span data-ttu-id="b99b1-168">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-168">false</span></span>                 |

### <a name="-credential--pscredential"></a><span data-ttu-id="b99b1-169">-Credential  \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="b99b1-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="b99b1-170">Especifica un objeto **PSCredential** para una cuenta de usuario que quiera usar para cambiar las reglas de autorización de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="b99b1-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="b99b1-171">Si no agrega este parámetro, el cmdlet usará la cuenta del usuario que ha iniciado la sesión.</span><span class="sxs-lookup"><span data-stu-id="b99b1-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="b99b1-172">Para obtener un objeto **PSCredential**, necesario para agregar reglas de autorización de forma remota, ejecute el cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).</span><span class="sxs-lookup"><span data-stu-id="b99b1-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="b99b1-173">Alias</span><span class="sxs-lookup"><span data-stu-id="b99b1-173">Aliases</span></span>                     | <span data-ttu-id="b99b1-174">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-174">none</span></span>  |
| <span data-ttu-id="b99b1-175">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b99b1-175">Required?</span></span>                   | <span data-ttu-id="b99b1-176">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-176">false</span></span> |
| <span data-ttu-id="b99b1-177">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b99b1-177">Position?</span></span>                   | <span data-ttu-id="b99b1-178">llamada</span><span class="sxs-lookup"><span data-stu-id="b99b1-178">named</span></span> |
| <span data-ttu-id="b99b1-179">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b99b1-179">Default Value</span></span>               | <span data-ttu-id="b99b1-180">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-180">none</span></span>  |
| <span data-ttu-id="b99b1-181">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b99b1-181">Accept Pipeline Input?</span></span>      | <span data-ttu-id="b99b1-182">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-182">false</span></span> |
| <span data-ttu-id="b99b1-183">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b99b1-183">Accept Wildcard Characters?</span></span> | <span data-ttu-id="b99b1-184">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-184">false</span></span> |

### <a name="-force"></a><span data-ttu-id="b99b1-185">-Force</span><span class="sxs-lookup"><span data-stu-id="b99b1-185">-Force</span></span>

<span data-ttu-id="b99b1-186">Obliga al comando a ejecutarse sin solicitar la confirmación del usuario.</span><span class="sxs-lookup"><span data-stu-id="b99b1-186">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="b99b1-187">También pide confirmación al escribir un nombre de equipo corto o simple (por ejemplo, un nombre que no es un nombre de dominio o un nombre no completo).</span><span class="sxs-lookup"><span data-stu-id="b99b1-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="b99b1-188">La confirmación se solicita por motivos de seguridad, de modo que puede usar el nombre simple para agregar un equipo únicamente si dicho equipo se encuentra en un grupo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="b99b1-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="b99b1-189">Alias</span><span class="sxs-lookup"><span data-stu-id="b99b1-189">Aliases</span></span>                              | <span data-ttu-id="b99b1-190">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-190">none</span></span>                                 |
| <span data-ttu-id="b99b1-191">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b99b1-191">Required?</span></span>                            | <span data-ttu-id="b99b1-192">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-192">false</span></span>                                |
| <span data-ttu-id="b99b1-193">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b99b1-193">Position?</span></span>                            | <span data-ttu-id="b99b1-194">llamada</span><span class="sxs-lookup"><span data-stu-id="b99b1-194">named</span></span>                                |
| <span data-ttu-id="b99b1-195">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b99b1-195">Default Value</span></span>                        | <span data-ttu-id="b99b1-196">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-196">none</span></span>                                 |
| <span data-ttu-id="b99b1-197">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b99b1-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b99b1-198">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-198">false</span></span>                                |
| <span data-ttu-id="b99b1-199">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b99b1-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b99b1-200">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="b99b1-201">-RuleName \<String\></span><span class="sxs-lookup"><span data-stu-id="b99b1-201">-RuleName \<String\></span></span>

<span data-ttu-id="b99b1-202">Especifica el nombre descriptivo de esta regla.</span><span class="sxs-lookup"><span data-stu-id="b99b1-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="b99b1-203">Alias</span><span class="sxs-lookup"><span data-stu-id="b99b1-203">Aliases</span></span>                              | <span data-ttu-id="b99b1-204">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-204">none</span></span>                                 |
| <span data-ttu-id="b99b1-205">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b99b1-205">Required?</span></span>                            | <span data-ttu-id="b99b1-206">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-206">false</span></span>                                |
| <span data-ttu-id="b99b1-207">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b99b1-207">Position?</span></span>                            | <span data-ttu-id="b99b1-208">llamada</span><span class="sxs-lookup"><span data-stu-id="b99b1-208">named</span></span>                                |
| <span data-ttu-id="b99b1-209">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b99b1-209">Default Value</span></span>                        | <span data-ttu-id="b99b1-210">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-210">none</span></span>                                 |
| <span data-ttu-id="b99b1-211">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b99b1-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b99b1-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="b99b1-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="b99b1-213">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b99b1-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b99b1-214">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="b99b1-215">-UserGroupName \<String\[\]\></span><span class="sxs-lookup"><span data-stu-id="b99b1-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="b99b1-216">Especifica el nombre de uno o varios grupos de usuarios en AD DS o en grupos locales a los que concede acceso esta regla.</span><span class="sxs-lookup"><span data-stu-id="b99b1-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="b99b1-217">Alias</span><span class="sxs-lookup"><span data-stu-id="b99b1-217">Aliases</span></span>                              | <span data-ttu-id="b99b1-218">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-218">none</span></span>                                 |
| <span data-ttu-id="b99b1-219">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b99b1-219">Required?</span></span>                            | <span data-ttu-id="b99b1-220">true</span><span class="sxs-lookup"><span data-stu-id="b99b1-220">true</span></span>                                 |
| <span data-ttu-id="b99b1-221">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b99b1-221">Position?</span></span>                            | <span data-ttu-id="b99b1-222">llamada</span><span class="sxs-lookup"><span data-stu-id="b99b1-222">named</span></span>                                |
| <span data-ttu-id="b99b1-223">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b99b1-223">Default Value</span></span>                        | <span data-ttu-id="b99b1-224">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-224">none</span></span>                                 |
| <span data-ttu-id="b99b1-225">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b99b1-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b99b1-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="b99b1-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="b99b1-227">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b99b1-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b99b1-228">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="b99b1-229">-UserName \<String\[\]\></span><span class="sxs-lookup"><span data-stu-id="b99b1-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="b99b1-230">Especifica uno o varios usuarios a los que concede acceso esta regla.</span><span class="sxs-lookup"><span data-stu-id="b99b1-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="b99b1-231">El nombre de usuario puede ser una cuenta de usuario local del equipo de la puerta de enlace o un usuario de AD DS.</span><span class="sxs-lookup"><span data-stu-id="b99b1-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span> <span data-ttu-id="b99b1-232">El formato es `domain\user` o `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="b99b1-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="b99b1-233">Alias</span><span class="sxs-lookup"><span data-stu-id="b99b1-233">Aliases</span></span>                              | <span data-ttu-id="b99b1-234">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-234">none</span></span>                                 |
| <span data-ttu-id="b99b1-235">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="b99b1-235">Required?</span></span>                            | <span data-ttu-id="b99b1-236">true</span><span class="sxs-lookup"><span data-stu-id="b99b1-236">true</span></span>                                 |
| <span data-ttu-id="b99b1-237">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="b99b1-237">Position?</span></span>                            | <span data-ttu-id="b99b1-238">1</span><span class="sxs-lookup"><span data-stu-id="b99b1-238">1</span></span>                                    |
| <span data-ttu-id="b99b1-239">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="b99b1-239">Default Value</span></span>                        | <span data-ttu-id="b99b1-240">ninguno</span><span class="sxs-lookup"><span data-stu-id="b99b1-240">none</span></span>                                 |
| <span data-ttu-id="b99b1-241">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="b99b1-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="b99b1-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="b99b1-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="b99b1-243">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="b99b1-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="b99b1-244">falso</span><span class="sxs-lookup"><span data-stu-id="b99b1-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="b99b1-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="b99b1-245">\<CommonParameters\></span></span>

<span data-ttu-id="b99b1-246">Este cmdlet admite los parámetros comunes:</span><span class="sxs-lookup"><span data-stu-id="b99b1-246">This cmdlet supports the common parameters:</span></span>

<span data-ttu-id="b99b1-247">-Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="b99b1-247">-Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="b99b1-248">Para más información, vea [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="b99b1-248">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="b99b1-249">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="b99b1-249">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="b99b1-250">Cadena</span><span class="sxs-lookup"><span data-stu-id="b99b1-250">String</span></span>

<span data-ttu-id="b99b1-251">Este cmdlet acepta como entrada una cadena o una matriz de cadenas.</span><span class="sxs-lookup"><span data-stu-id="b99b1-251">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="b99b1-252">String\[\]</span><span class="sxs-lookup"><span data-stu-id="b99b1-252">String\[\]</span></span>

<span data-ttu-id="b99b1-253">Este cmdlet acepta como entrada una cadena o una matriz de cadenas.</span><span class="sxs-lookup"><span data-stu-id="b99b1-253">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="b99b1-254">Salidas</span><span class="sxs-lookup"><span data-stu-id="b99b1-254">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="b99b1-255">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="b99b1-255">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="b99b1-256">Este cmdlet devuelve el objeto de la regla de autorización.</span><span class="sxs-lookup"><span data-stu-id="b99b1-256">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="b99b1-257">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="b99b1-257">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="b99b1-258">EJEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="b99b1-258">EXAMPLE 1</span></span>

<span data-ttu-id="b99b1-259">Este ejemplo concede acceso a la configuración de la sesión _PSWAEndpoint_, un espacio de ejecución restringido, en _srv2_ para los usuarios del grupo _SMAdmins_.</span><span class="sxs-lookup"><span data-stu-id="b99b1-259">This example grants access to the session configuration _PSWAEndpoint_, a restricted runspace, on _srv2_ for users in the _SMAdmins_ group.</span></span>

> [!NOTE]
> <span data-ttu-id="b99b1-260">El nombre del equipo debe ser un nombre de dominio completo (FQDN).</span><span class="sxs-lookup"><span data-stu-id="b99b1-260">The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="b99b1-261">Los administradores definen una configuración de sesión o espacio de ejecución restringido, que es un intervalo limitado de cmdlets y tareas que los usuarios finales pueden ejecutar.</span><span class="sxs-lookup"><span data-stu-id="b99b1-261">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="b99b1-262">Definir un espacio de ejecución restringido puede impedir que los usuarios puedan obtener acceso a otros equipos que no se encuentran en el espacio de ejecución de Windows PowerShell(r) permitido, lo que garantiza una conexión más segura.</span><span class="sxs-lookup"><span data-stu-id="b99b1-262">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell(r) runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="b99b1-263">Para más información sobre las configuraciones de sesión, consulte [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) o [Instalación y uso de Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="b99b1-263">For more information on session configurations, see [about_Session_Configurations](/powershell/module/microsoft.powershell.core/about/about_session_configurations) or [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```powershell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="b99b1-264">EJEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="b99b1-264">EXAMPLE 2</span></span>

<span data-ttu-id="b99b1-265">Este ejemplo concede acceso a la configuración de sesión predeterminada de Windows PowerShell, `Microsoft.PowerShell`, en *srv2* para los usuarios de los usuarios denominados `contoso\user1`, `contoso\user2` y `contoso\user3`.r3.</span><span class="sxs-lookup"><span data-stu-id="b99b1-265">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="b99b1-266">Este cmdlet crea tres reglas (una por persona).</span><span class="sxs-lookup"><span data-stu-id="b99b1-266">This cmdlet creates three rules (1 per person).</span></span>

```powershell
Add-PswaAuthorizationRule -UserName contoso\user1, contoso\user2, contoso\user3 -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="b99b1-267">EJEMPLO 3</span><span class="sxs-lookup"><span data-stu-id="b99b1-267">EXAMPLE 3</span></span>

<span data-ttu-id="b99b1-268">En este ejemplo se muestra cómo se especifican valores de nombre de usuario a través de la canalización.</span><span class="sxs-lookup"><span data-stu-id="b99b1-268">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule -ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="b99b1-269">EJEMPLO 4</span><span class="sxs-lookup"><span data-stu-id="b99b1-269">EXAMPLE 4</span></span>

<span data-ttu-id="b99b1-270">En este ejemplo se muestra cómo todos los parámetros toman valores de la canalización por nombre de propiedad.</span><span class="sxs-lookup"><span data-stu-id="b99b1-270">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````powershell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" -PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="b99b1-271">EJEMPLO 5</span><span class="sxs-lookup"><span data-stu-id="b99b1-271">EXAMPLE 5</span></span>

<span data-ttu-id="b99b1-272">Este ejemplo agrega una regla para permitir que el usuario local llamado `PswaServer\ChrisLocal` obtenga acceso al servidor llamado **srv1.contoso.com**.</span><span class="sxs-lookup"><span data-stu-id="b99b1-272">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="b99b1-273">En este ejemplo se muestra un escenario en el que la puerta de enlace está en un grupo de trabajo y el equipo de destino está en un dominio.</span><span class="sxs-lookup"><span data-stu-id="b99b1-273">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="b99b1-274">La regla de autorización se aplica a los usuarios locales de la puerta de enlace.</span><span class="sxs-lookup"><span data-stu-id="b99b1-274">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="b99b1-275">En la página de inicio de sesión de Windows PowerShell Web Access, para autenticarse correctamente, el usuario debe proporcionar un segundo conjunto de credenciales en el área **Configuración de conexión opcional**.</span><span class="sxs-lookup"><span data-stu-id="b99b1-275">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="b99b1-276">El servidor de puerta de enlace usa el conjunto de credenciales adicional para autenticar al usuario en el equipo de destino, un servidor llamado *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="b99b1-276">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule -UserName PswaServer\ChrisLocal -ComputerName srv1.contoso.com -ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="b99b1-277">EJEMPLO 6</span><span class="sxs-lookup"><span data-stu-id="b99b1-277">EXAMPLE 6</span></span>

<span data-ttu-id="b99b1-278">Este ejemplo permite que todos los usuarios obtengan acceso a todos los puntos de conexión de todos los equipos.</span><span class="sxs-lookup"><span data-stu-id="b99b1-278">This example allows all users access to all endpoints on all computers.</span></span> <span data-ttu-id="b99b1-279">Esto equivale a desactivar las reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="b99b1-279">This essentially turns off authorization rules.</span></span>

> [!NOTE]
> <span data-ttu-id="b99b1-280">No se recomienda usar el carácter comodín `*` para las implementaciones de seguridad. Solo debe aplicarse en los entornos de prueba, o bien en las implementaciones en las que la seguridad pueda ser algo laxa.</span><span class="sxs-lookup"><span data-stu-id="b99b1-280">Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````powershell
Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="b99b1-281">Véase también</span><span class="sxs-lookup"><span data-stu-id="b99b1-281">See Also</span></span>

<span data-ttu-id="b99b1-282">[Get-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="b99b1-282">[Get-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="b99b1-283">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="b99b1-283">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="b99b1-284">[Test-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="b99b1-284">[Test-PswaAuthorizationRule](https://technet.microsoft.com/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="b99b1-285">[Install-PswaWebApplication](https://technet.microsoft.com/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="b99b1-285">[Install-PswaWebApplication](https://technet.microsoft.com/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="b99b1-286">Add-Member</span><span class="sxs-lookup"><span data-stu-id="b99b1-286">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="b99b1-287">New-Object</span><span class="sxs-lookup"><span data-stu-id="b99b1-287">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="b99b1-288">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="b99b1-288">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)
