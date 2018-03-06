---
ms.date: 2017-06-05
keywords: powershell, cmdlet
title: "Realizar el segundo salto en la comunicación remota de PowerShell"
ms.openlocfilehash: 726b4d1b7a41e9e344347543ecde26da6547bcf3
ms.sourcegitcommit: fff6c0522508eeb408cb055ba4c9337a2759b392
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="27cc5-103">Realizar el segundo salto en la comunicación remota de PowerShell</span><span class="sxs-lookup"><span data-stu-id="27cc5-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="27cc5-104">El "problema del segundo salto" se refiere a una situación similar a la siguiente:</span><span class="sxs-lookup"><span data-stu-id="27cc5-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="27cc5-105">Ha iniciado sesión en _ServidorA_.</span><span class="sxs-lookup"><span data-stu-id="27cc5-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="27cc5-106">En _ServidorA_, inicia una sesión remota de PowerShell para conectarse a _ServidorB_.</span><span class="sxs-lookup"><span data-stu-id="27cc5-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="27cc5-107">Un comando que ejecuta en _ServidorB_ a través de la sesión de comunicación remota de PowerShell intenta obtener acceso a un recurso en _ServidorC_.</span><span class="sxs-lookup"><span data-stu-id="27cc5-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="27cc5-108">Se le deniega el acceso al recurso en _ServidorC_, porque no se pasan las credenciales que ha usado para crear la sesión de comunicación remota de PowerShell de _ServidorB_ a _ServidorC_.</span><span class="sxs-lookup"><span data-stu-id="27cc5-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="27cc5-109">Hay varias formas de abordar este problema.</span><span class="sxs-lookup"><span data-stu-id="27cc5-109">There are several ways to address this problem.</span></span> <span data-ttu-id="27cc5-110">En este tema, analizaremos algunas de las soluciones más populares del problema del segundo salto.</span><span class="sxs-lookup"><span data-stu-id="27cc5-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="27cc5-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="27cc5-111">CredSSP</span></span>

<span data-ttu-id="27cc5-112">Puede usar el [proveedor de compatibilidad para seguridad de credenciales (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="27cc5-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="27cc5-113">CredSSP copia en caché las credenciales en el servidor remoto (_ServidorB_), por lo que, al usarlo, le hace vulnerable a los ataques de robos de credenciales.</span><span class="sxs-lookup"><span data-stu-id="27cc5-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="27cc5-114">Si el equipo remoto se ve comprometido, el atacante tiene acceso a las credenciales del usuario.</span><span class="sxs-lookup"><span data-stu-id="27cc5-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="27cc5-115">CredSSP está deshabilitado de forma predeterminada tanto en el equipo del cliente como del servidor.</span><span class="sxs-lookup"><span data-stu-id="27cc5-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="27cc5-116">Debe habilitar CredSSP solo en los entornos de mayor confianza.</span><span class="sxs-lookup"><span data-stu-id="27cc5-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="27cc5-117">Por ejemplo, un administrador de dominio que se conecta a un controlador de dominio porque el controlador de dominio es de plena confianza.</span><span class="sxs-lookup"><span data-stu-id="27cc5-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="27cc5-118">Para obtener más información sobre problemas de seguridad cuando se usa CredSSP para la comunicación remota de PowerShell, vea [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp) (Sabotaje accidental: tenga cuidado con CredSSP).</span><span class="sxs-lookup"><span data-stu-id="27cc5-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="27cc5-119">Para obtener más información acerca de los ataques de robo de credenciales, consulte [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036) (Mitigación de ataques Pass-the-Hash (PtH) y otros robos de credenciales).</span><span class="sxs-lookup"><span data-stu-id="27cc5-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="27cc5-120">Para obtener un ejemplo sobre cómo habilitar y usar CredSSP para la comunicación remota de PowerShell, consulte [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/) (Usar CredSSP para solucionar el problema del segundo salto).</span><span class="sxs-lookup"><span data-stu-id="27cc5-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="27cc5-121">Pros</span><span class="sxs-lookup"><span data-stu-id="27cc5-121">Pros</span></span>

- <span data-ttu-id="27cc5-122">Funciona en todos los servidores con Windows Server 2008 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="27cc5-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="27cc5-123">Contras</span><span class="sxs-lookup"><span data-stu-id="27cc5-123">Cons</span></span>

- <span data-ttu-id="27cc5-124">Tiene vulnerabilidades de seguridad.</span><span class="sxs-lookup"><span data-stu-id="27cc5-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="27cc5-125">Requiere la configuración de roles de cliente y servidor.</span><span class="sxs-lookup"><span data-stu-id="27cc5-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="27cc5-126">Delegación Kerberos (sin restricciones)</span><span class="sxs-lookup"><span data-stu-id="27cc5-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="27cc5-127">También puede usar la delegación Kerberos sin restricciones para realizar el segundo salto.</span><span class="sxs-lookup"><span data-stu-id="27cc5-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="27cc5-128">En cambio, este método no proporciona control sobre dónde se usan las credenciales delegadas.</span><span class="sxs-lookup"><span data-stu-id="27cc5-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="27cc5-129">**Nota:** No se pueden delegar las cuentas de Active Directory que tienen la propiedad **La cuenta es importante y no se puede delegar** establecida.</span><span class="sxs-lookup"><span data-stu-id="27cc5-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="27cc5-130">Para obtener más información, consulte [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Enfoque de seguridad: analizar "La cuenta es importante y no se puede delegar" para cuentas con privilegios) y [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Configuración y herramientas de la autenticación Kerberos).</span><span class="sxs-lookup"><span data-stu-id="27cc5-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="27cc5-131">Pros</span><span class="sxs-lookup"><span data-stu-id="27cc5-131">Pros</span></span>

- <span data-ttu-id="27cc5-132">No requiere código especial.</span><span class="sxs-lookup"><span data-stu-id="27cc5-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="27cc5-133">Contras</span><span class="sxs-lookup"><span data-stu-id="27cc5-133">Cons</span></span>

- <span data-ttu-id="27cc5-134">No se admite el segundo salto para WinRM.</span><span class="sxs-lookup"><span data-stu-id="27cc5-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="27cc5-135">No proporciona ningún control sobre dónde se usan las credenciales, lo que crea una vulnerabilidad de seguridad.</span><span class="sxs-lookup"><span data-stu-id="27cc5-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="27cc5-136">Delegación limitada de Kerberos</span><span class="sxs-lookup"><span data-stu-id="27cc5-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="27cc5-137">Puede usar la delegación limitada heredada (no basada en recursos) para realizar el segundo salto.</span><span class="sxs-lookup"><span data-stu-id="27cc5-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> 

><span data-ttu-id="27cc5-138">**Nota:** No se pueden delegar las cuentas de Active Directory que tienen la propiedad **La cuenta es importante y no se puede delegar** establecida.</span><span class="sxs-lookup"><span data-stu-id="27cc5-138">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="27cc5-139">Para obtener más información, consulte [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Enfoque de seguridad: analizar "La cuenta es importante y no se puede delegar" para cuentas con privilegios) y [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Configuración y herramientas de la autenticación Kerberos).</span><span class="sxs-lookup"><span data-stu-id="27cc5-139">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="27cc5-140">Pros</span><span class="sxs-lookup"><span data-stu-id="27cc5-140">Pros</span></span>

- <span data-ttu-id="27cc5-141">No requiere código especial</span><span class="sxs-lookup"><span data-stu-id="27cc5-141">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="27cc5-142">Contras</span><span class="sxs-lookup"><span data-stu-id="27cc5-142">Cons</span></span>

- <span data-ttu-id="27cc5-143">No se admite el segundo salto para WinRM.</span><span class="sxs-lookup"><span data-stu-id="27cc5-143">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="27cc5-144">Se debe configurar en el objeto de Active Directory del servidor remoto (_ServidorB_).</span><span class="sxs-lookup"><span data-stu-id="27cc5-144">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="27cc5-145">Limitado a un dominio.</span><span class="sxs-lookup"><span data-stu-id="27cc5-145">Limited to one domain.</span></span> <span data-ttu-id="27cc5-146">No puede cruzar dominios ni bosques.</span><span class="sxs-lookup"><span data-stu-id="27cc5-146">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="27cc5-147">Requiere derechos para actualizar objetos y nombres de entidad de seguridad de servicio (SPN).</span><span class="sxs-lookup"><span data-stu-id="27cc5-147">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="27cc5-148">Delegación limitada de Kerberos basada en recursos</span><span class="sxs-lookup"><span data-stu-id="27cc5-148">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="27cc5-149">Con la delegación limitada de Kerberos basada en recursos (introducida en Windows Server 2012), configura la delegación de credenciales en el objeto de servidor en que residen los recursos.</span><span class="sxs-lookup"><span data-stu-id="27cc5-149">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="27cc5-150">En el escenario del segundo salto descrito anteriormente, puede configurar el _ServidorC_ para especificar desde dónde va a aceptar credenciales delegadas.</span><span class="sxs-lookup"><span data-stu-id="27cc5-150">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="27cc5-151">**Nota:** No se pueden delegar las cuentas de Active Directory que tienen la propiedad **La cuenta es importante y no se puede delegar** establecida.</span><span class="sxs-lookup"><span data-stu-id="27cc5-151">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="27cc5-152">Para obtener más información, consulte [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Enfoque de seguridad: analizar "La cuenta es importante y no se puede delegar" para cuentas con privilegios) y [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Configuración y herramientas de la autenticación Kerberos).</span><span class="sxs-lookup"><span data-stu-id="27cc5-152">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="27cc5-153">Pros</span><span class="sxs-lookup"><span data-stu-id="27cc5-153">Pros</span></span>

- <span data-ttu-id="27cc5-154">Las credenciales no se almacenan.</span><span class="sxs-lookup"><span data-stu-id="27cc5-154">Credentials are not stored.</span></span>
- <span data-ttu-id="27cc5-155">Relativamente fácil de configurar mediante cmdlets de PowerShell, no se requiere ninguna codificación especial.</span><span class="sxs-lookup"><span data-stu-id="27cc5-155">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="27cc5-156">No se requiere ningún acceso especial de dominio.</span><span class="sxs-lookup"><span data-stu-id="27cc5-156">No special domain access is required.</span></span>
- <span data-ttu-id="27cc5-157">Funciona en dominios y bosques.</span><span class="sxs-lookup"><span data-stu-id="27cc5-157">Works across domains and forests.</span></span>
- <span data-ttu-id="27cc5-158">Código de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27cc5-158">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="27cc5-159">Contras</span><span class="sxs-lookup"><span data-stu-id="27cc5-159">Cons</span></span>

- <span data-ttu-id="27cc5-160">Necesita Windows Server 2012 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="27cc5-160">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="27cc5-161">No se admite el segundo salto para WinRM.</span><span class="sxs-lookup"><span data-stu-id="27cc5-161">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="27cc5-162">Requiere derechos para actualizar objetos y nombres de entidad de seguridad de servicio (SPN).</span><span class="sxs-lookup"><span data-stu-id="27cc5-162">Requires rights to update objects and Service Principal Names (SPNs).</span></span> 

### <a name="example"></a><span data-ttu-id="27cc5-163">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27cc5-163">Example</span></span>

<span data-ttu-id="27cc5-164">Veamos un ejemplo de PowerShell que configura la delegación restringida basada en recursos en el _ServidorC_ para admitir credenciales delegadas de un _ServidorB_.</span><span class="sxs-lookup"><span data-stu-id="27cc5-164">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="27cc5-165">En este ejemplo, se supone que todos los servidores ejecutan Windows Server 2012 o una versión posterior y que hay al menos un controlador de dominio de Windows Server 2012 en cada dominio a los que pertenecen los servidores.</span><span class="sxs-lookup"><span data-stu-id="27cc5-165">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="27cc5-166">Antes de que pueda configurar la delegación restringida, debe agregar la característica `RSAT-AD-PowerShell` para instalar el módulo de PowerShell de Active Directory y después importar ese módulo en la sesión:</span><span class="sxs-lookup"><span data-stu-id="27cc5-166">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="27cc5-167">Varios cmdlets disponibles tienen ahora un parámetro **PrincipalsAllowedToDelegateToAccount**:</span><span class="sxs-lookup"><span data-stu-id="27cc5-167">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

```powershell
PS C:\> Get-Command -ParameterName PrincipalsAllowedToDelegateToAccount

CommandType Name                 ModuleName     
----------- ----                 ----------     
Cmdlet      New-ADComputer       ActiveDirectory
Cmdlet      New-ADServiceAccount ActiveDirectory
Cmdlet      New-ADUser           ActiveDirectory
Cmdlet      Set-ADComputer       ActiveDirectory
Cmdlet      Set-ADServiceAccount ActiveDirectory
Cmdlet      Set-ADUser           ActiveDirectory
```

<span data-ttu-id="27cc5-168">El parámetro **PrincipalsAllowedToDelegateToAccount** establece el atributo de objeto de Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, que contiene una lista de control de acceso (ACL) que especifica qué cuentas tienen permiso para delegar credenciales a la cuenta asociada (en nuestro ejemplo, será la cuenta del equipo de _Servidor_).</span><span class="sxs-lookup"><span data-stu-id="27cc5-168">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="27cc5-169">Ahora vamos a configurar las variables que usaremos para representar los servidores:</span><span class="sxs-lookup"><span data-stu-id="27cc5-169">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse            
$ServerA = $env:COMPUTERNAME            
$ServerB = Get-ADComputer -Identity ServerB            
$ServerC = Get-ADComputer -Identity ServerC            
```

<span data-ttu-id="27cc5-170">WinRM (y, por tanto, la comunicación remota de PowerShell) se ejecuta como la cuenta de equipo de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="27cc5-170">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="27cc5-171">Puede ver esto si atiende a la propiedad **StartName** del servicio `winrm`:</span><span class="sxs-lookup"><span data-stu-id="27cc5-171">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="27cc5-172">Para que _ServidorC_ permita la delegación desde una sesión de comunicación remota de PowerShell en _ServidorB_, le concederemos acceso al establecer el parámetro **PrincipalsAllowedToDelegateToAccount** en _ServidorC_ al objeto de equipo de _ServidorB_:</span><span class="sxs-lookup"><span data-stu-id="27cc5-172">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB            
            
# Check the value of the attribute directly            
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity            
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access            
            
# Check the value of the attribute indirectly            
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="27cc5-173">El [Centro de distribución de claves (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) de Kerberos copia en caché los intentos de acceso denegados (caché negativa) durante 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="27cc5-173">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="27cc5-174">Si _ServidorB_ ha intentado previamente obtener acceso a _ServidorC_, deberá borrar la caché de _ServidorB_ al invocar el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="27cc5-174">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {            
    klist purge -li 0x3e7            
}
```

<span data-ttu-id="27cc5-175">También puede reiniciar el equipo o esperar al menos 15 minutos para borrar la caché.</span><span class="sxs-lookup"><span data-stu-id="27cc5-175">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="27cc5-176">Después de borrar la caché, puede ejecutar correctamente código desde el _ServidorA_ a través del _ServidorB_ hasta el _ServidorC_:</span><span class="sxs-lookup"><span data-stu-id="27cc5-176">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

```powershell
# Capture a credential            
$cred = Get-Credential Contoso\Alice            
            
# Test kerberos double hop            
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {            
    Test-Path \\$($using:ServerC.Name)\C$            
    Get-Process lsass -ComputerName $($using:ServerC.Name)            
    Get-EventLog -LogName System -Newest 3 -ComputerName $($using:ServerC.Name)            
}
```

<span data-ttu-id="27cc5-177">En este ejemplo, la variable `$using` se usa para hacer visible la variable `$ServerC` en el _ServidorB_.</span><span class="sxs-lookup"><span data-stu-id="27cc5-177">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="27cc5-178">Para obtener más información sobre la variable `$using`, consulte [about_Remote_Variables](https://technet.microsoft.com/en-us/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="27cc5-178">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/en-us/library/jj149005.aspx).</span></span>

<span data-ttu-id="27cc5-179">Para permitir que varios servidores deleguen credenciales en el _ServidorC_, establezca el valor del parámetro **PrincipalsAllowedToDelegateToAccount** en el _ServidorC_ a una matriz:</span><span class="sxs-lookup"><span data-stu-id="27cc5-179">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

```powershell
# Set up variables for each server            
$ServerB1 = Get-ADComputer -Identity ServerB1            
$ServerB2 = Get-ADComputer -Identity ServerB2            
$ServerB3 = Get-ADComputer -Identity ServerB3            
$ServerC  = Get-ADComputer -Identity ServerC            
            
# Grant resource-based Kerberos constrained delegation            
Set-ADComputer -Identity $ServerC `
    -PrincipalsAllowedToDelegateToAccount @($ServerB1,$ServerB2,$ServerB3)
```

<span data-ttu-id="27cc5-180">Si quiere realizar el segundo salto entre dominios, agregue el nombre de dominio completo (FQDN) del controlador del dominio al que pertenece el _ServidorB_:</span><span class="sxs-lookup"><span data-stu-id="27cc5-180">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain            
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com            
$ServerC = Get-ADComputer -Identity ServerC            
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="27cc5-181">Para quitar la capacidad de delegar credenciales en el ServidorC, establezca el valor del parámetro **PrincipalsAllowedToDelegateToAccount** en el _ServidorC_ en `$null`:</span><span class="sxs-lookup"><span data-stu-id="27cc5-181">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="27cc5-182">Información sobre la delegación limitada de Kerberos basada en recursos</span><span class="sxs-lookup"><span data-stu-id="27cc5-182">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="27cc5-183">Novedades de la autenticación Kerberos</span><span class="sxs-lookup"><span data-stu-id="27cc5-183">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- <span data-ttu-id="27cc5-184">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1) (Cómo simplifica Windows Server 2012 el proceso de delegación limitada de Kerberos, parte 1)</span><span class="sxs-lookup"><span data-stu-id="27cc5-184">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)</span></span>
- <span data-ttu-id="27cc5-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2) (Cómo simplifica Windows Server 2012 el proceso de delegación limitada de Kerberos, parte 2)</span><span class="sxs-lookup"><span data-stu-id="27cc5-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](http://windowsitpro.com/security/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)</span></span>
- <span data-ttu-id="27cc5-186">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](http://aka.ms/kcdpaper) (Comprender la delegación limitada de Kerberos para implementaciones de proxy de aplicación de Active Directory con la autenticación integrada de Windows)</span><span class="sxs-lookup"><span data-stu-id="27cc5-186">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](http://aka.ms/kcdpaper)</span></span>
- <span data-ttu-id="27cc5-187">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/en-us/library/hh554126.aspx) ([MS-ADA2]: atributos de esquema de Active Directory, atributo M2.210 msDS-AllowedToActOnBehalfOfOtherIdentity)</span><span class="sxs-lookup"><span data-stu-id="27cc5-187">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/en-us/library/hh554126.aspx)</span></span>
- <span data-ttu-id="27cc5-188">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/en-us/library/cc246079.aspx) ([MS-SFU]: Extensiones de protocolo de Kerberos: protocolo de delegación limitada y de servicio para el usuario 1.3.2 S4U2proxy)</span><span class="sxs-lookup"><span data-stu-id="27cc5-188">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/en-us/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="27cc5-189">Delegación limitada de Kerberos basada en recursos</span><span class="sxs-lookup"><span data-stu-id="27cc5-189">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- <span data-ttu-id="27cc5-190">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/) (Administración remota sin delegación limitada con PrincipalsAllowedToDelegateToAccount)</span><span class="sxs-lookup"><span data-stu-id="27cc5-190">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="27cc5-191">PSSessionConfiguration con RunAs</span><span class="sxs-lookup"><span data-stu-id="27cc5-191">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="27cc5-192">Puede crear una configuración de sesión en el _ServidorB_ y establecer su parámetro **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="27cc5-192">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="27cc5-193">Para obtener información sobre el uso de PSSessionConfiguration y RunAs para resolver el problema del segundo salto, consulte [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/) (Otra solución a la comunicación remota de PowerShell de varios saltos).</span><span class="sxs-lookup"><span data-stu-id="27cc5-193">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="27cc5-194">Pros</span><span class="sxs-lookup"><span data-stu-id="27cc5-194">Pros</span></span>

- <span data-ttu-id="27cc5-195">Funciona con cualquier servidor con WMF 3.0 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="27cc5-195">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="27cc5-196">Contras</span><span class="sxs-lookup"><span data-stu-id="27cc5-196">Cons</span></span>

- <span data-ttu-id="27cc5-197">Requiere la configuración de **PSSessionConfiguration** y **RunAs** en cada servidor intermedio (_ServidorB_).</span><span class="sxs-lookup"><span data-stu-id="27cc5-197">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="27cc5-198">Requiere el mantenimiento de la contraseña cuando se usa una cuenta de **ejecución** de dominio</span><span class="sxs-lookup"><span data-stu-id="27cc5-198">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="27cc5-199">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="27cc5-199">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="27cc5-200">JEA le permite restringir qué comandos puede ejecutar un administrador durante una sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="27cc5-200">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="27cc5-201">Se puede usar para resolver el problema del segundo salto.</span><span class="sxs-lookup"><span data-stu-id="27cc5-201">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="27cc5-202">Para obtener información sobre JEA, consulte [Just Enough Administration](https://docs.microsoft.com/en-us/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="27cc5-202">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/en-us/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="27cc5-203">Pros</span><span class="sxs-lookup"><span data-stu-id="27cc5-203">Pros</span></span>

- <span data-ttu-id="27cc5-204">No hay mantenimiento de contraseña al usar una cuenta virtual.</span><span class="sxs-lookup"><span data-stu-id="27cc5-204">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="27cc5-205">Contras</span><span class="sxs-lookup"><span data-stu-id="27cc5-205">Cons</span></span>

- <span data-ttu-id="27cc5-206">Requiere WMF 5.0 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="27cc5-206">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="27cc5-207">Es necesario configurar cada servidor intermedio (_ServidorB_).</span><span class="sxs-lookup"><span data-stu-id="27cc5-207">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="27cc5-208">Pasar credenciales dentro de un bloque de script de Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="27cc5-208">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="27cc5-209">Se pueden pasar credenciales dentro del parámetro **ScriptBlock** de una llamada al cmdlet [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="27cc5-209">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="27cc5-210">Pros</span><span class="sxs-lookup"><span data-stu-id="27cc5-210">Pros</span></span>

- <span data-ttu-id="27cc5-211">No requiere configuración especial del servidor.</span><span class="sxs-lookup"><span data-stu-id="27cc5-211">Does not require special server configuration.</span></span>
- <span data-ttu-id="27cc5-212">Funciona en cualquier servidor que ejecute WMF 2.0 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="27cc5-212">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="27cc5-213">Contras</span><span class="sxs-lookup"><span data-stu-id="27cc5-213">Cons</span></span>

- <span data-ttu-id="27cc5-214">Se requiere una técnica de código complicada.</span><span class="sxs-lookup"><span data-stu-id="27cc5-214">Requires an awkward code technique.</span></span>
- <span data-ttu-id="27cc5-215">Si ejecuta WMF 2.0, requiere una sintaxis diferente para pasar argumentos a una sesión remota.</span><span class="sxs-lookup"><span data-stu-id="27cc5-215">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="27cc5-216">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="27cc5-216">Example</span></span>

<span data-ttu-id="27cc5-217">En el ejemplo siguiente, se muestra cómo pasar las credenciales en un bloque de script **Invoke-Command**:</span><span class="sxs-lookup"><span data-stu-id="27cc5-217">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds            
# Note $Using:Cred in nested request            
$cred = Get-Credential Contoso\Administrator            
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {            
    hostname            
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}            
}
```

## <a name="see-also"></a><span data-ttu-id="27cc5-218">Vea también</span><span class="sxs-lookup"><span data-stu-id="27cc5-218">See also</span></span>

[<span data-ttu-id="27cc5-219">Consideraciones de seguridad de comunicación remota de PowerShell</span><span class="sxs-lookup"><span data-stu-id="27cc5-219">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)








 
