---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Realizar el segundo salto en la comunicación remota de PowerShell
ms.openlocfilehash: f4cfde39de8494050c31cfc3181271b968819695
ms.sourcegitcommit: a35450f420dc10a02379f6e6f08a28ad11fe5a6d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2019
ms.locfileid: "71692145"
---
# <a name="making-the-second-hop-in-powershell-remoting"></a><span data-ttu-id="9c405-103">Realizar el segundo salto en la comunicación remota de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c405-103">Making the second hop in PowerShell Remoting</span></span>

<span data-ttu-id="9c405-104">El "problema del segundo salto" se refiere a una situación similar a la siguiente:</span><span class="sxs-lookup"><span data-stu-id="9c405-104">The "second hop problem" refers to a situation like the following:</span></span>

1. <span data-ttu-id="9c405-105">Ha iniciado sesión en _ServidorA_.</span><span class="sxs-lookup"><span data-stu-id="9c405-105">You are logged in to _ServerA_.</span></span>
2. <span data-ttu-id="9c405-106">En _ServidorA_, inicia una sesión remota de PowerShell para conectarse a _ServidorB_.</span><span class="sxs-lookup"><span data-stu-id="9c405-106">From _ServerA_, you start a remote PowerShell session to connect to _ServerB_.</span></span>
3. <span data-ttu-id="9c405-107">Un comando que ejecuta en _ServidorB_ a través de la sesión de comunicación remota de PowerShell intenta obtener acceso a un recurso en _ServidorC_.</span><span class="sxs-lookup"><span data-stu-id="9c405-107">A command you run on _ServerB_ via your PowerShell Remoting session attempts to access a resource on _ServerC_.</span></span>
4. <span data-ttu-id="9c405-108">Se le deniega el acceso al recurso en _ServidorC_, porque no se pasan las credenciales que ha usado para crear la sesión de comunicación remota de PowerShell de _ServidorB_ a _ServidorC_.</span><span class="sxs-lookup"><span data-stu-id="9c405-108">Access to the resource on _ServerC_ is denied, because the credentials you used to create the PowerShell Remoting session are not passed from _ServerB_ to _ServerC_.</span></span>

<span data-ttu-id="9c405-109">Hay varias formas de abordar este problema.</span><span class="sxs-lookup"><span data-stu-id="9c405-109">There are several ways to address this problem.</span></span> <span data-ttu-id="9c405-110">En este tema, analizaremos algunas de las soluciones más populares del problema del segundo salto.</span><span class="sxs-lookup"><span data-stu-id="9c405-110">In this topic, we'll look at several of the most popular solutions to the second hop problem.</span></span>

## <a name="credssp"></a><span data-ttu-id="9c405-111">CredSSP</span><span class="sxs-lookup"><span data-stu-id="9c405-111">CredSSP</span></span>

<span data-ttu-id="9c405-112">Puede usar el [proveedor de compatibilidad para seguridad de credenciales (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) para la autenticación.</span><span class="sxs-lookup"><span data-stu-id="9c405-112">You can use the [Credential Security Support Provider (CredSSP)](https://msdn.microsoft.com/library/windows/desktop/bb931352.aspx) for authentication.</span></span> <span data-ttu-id="9c405-113">CredSSP copia en caché las credenciales en el servidor remoto (_ServidorB_), por lo que, al usarlo, le hace vulnerable a los ataques de robos de credenciales.</span><span class="sxs-lookup"><span data-stu-id="9c405-113">CredSSP caches credentials on the remote server (_ServerB_), so using it opens you up to credential theft attacks.</span></span> <span data-ttu-id="9c405-114">Si el equipo remoto se ve comprometido, el atacante tiene acceso a las credenciales del usuario.</span><span class="sxs-lookup"><span data-stu-id="9c405-114">If the remote computer is compromised, the attacker has access to the user's credentials.</span></span> <span data-ttu-id="9c405-115">CredSSP está deshabilitado de forma predeterminada tanto en el equipo del cliente como del servidor.</span><span class="sxs-lookup"><span data-stu-id="9c405-115">CredSSP is disabled by default on both client and server computers.</span></span> <span data-ttu-id="9c405-116">Debe habilitar CredSSP solo en los entornos de mayor confianza.</span><span class="sxs-lookup"><span data-stu-id="9c405-116">You should enable CredSSP only in the most trusted environments.</span></span> <span data-ttu-id="9c405-117">Por ejemplo, un administrador de dominio que se conecta a un controlador de dominio porque el controlador de dominio es de plena confianza.</span><span class="sxs-lookup"><span data-stu-id="9c405-117">For example, a domain administrator connecting to a domain controller because the domain controller is highly trusted.</span></span>

<span data-ttu-id="9c405-118">Para obtener más información sobre problemas de seguridad cuando se usa CredSSP para la comunicación remota de PowerShell, vea [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp) (Sabotaje accidental: tenga cuidado con CredSSP).</span><span class="sxs-lookup"><span data-stu-id="9c405-118">For more information about security concerns when using CredSSP for PowerShell Remoting, see [Accidental Sabotage: Beware of CredSSP](https://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp).</span></span>

<span data-ttu-id="9c405-119">Para obtener más información acerca de los ataques de robo de credenciales, consulte [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036) (Mitigación de ataques Pass-the-Hash (PtH) y otros robos de credenciales).</span><span class="sxs-lookup"><span data-stu-id="9c405-119">For more information about credential theft attacks, see [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036).</span></span>

<span data-ttu-id="9c405-120">Para obtener un ejemplo sobre cómo habilitar y usar CredSSP para la comunicación remota de PowerShell, consulte [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/) (Usar CredSSP para solucionar el problema del segundo salto).</span><span class="sxs-lookup"><span data-stu-id="9c405-120">For an example of how to enable and use CredSSP for PowerShell remoting, see [Using CredSSP to solve the second-hop problem](https://blogs.technet.microsoft.com/heyscriptingguy/2012/11/14/enable-powershell-second-hop-functionality-with-credssp/).</span></span>

### <a name="pros"></a><span data-ttu-id="9c405-121">Pros</span><span class="sxs-lookup"><span data-stu-id="9c405-121">Pros</span></span>

- <span data-ttu-id="9c405-122">Funciona en todos los servidores con Windows Server 2008 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="9c405-122">It works for all servers with Windows Server 2008 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="9c405-123">Contras</span><span class="sxs-lookup"><span data-stu-id="9c405-123">Cons</span></span>

- <span data-ttu-id="9c405-124">Tiene vulnerabilidades de seguridad.</span><span class="sxs-lookup"><span data-stu-id="9c405-124">Has security vulnerabilities.</span></span>
- <span data-ttu-id="9c405-125">Requiere la configuración de roles de cliente y servidor.</span><span class="sxs-lookup"><span data-stu-id="9c405-125">Requires configuration of both client and server roles.</span></span>

## <a name="kerberos-delegation-unconstrained"></a><span data-ttu-id="9c405-126">Delegación Kerberos (sin restricciones)</span><span class="sxs-lookup"><span data-stu-id="9c405-126">Kerberos delegation (unconstrained)</span></span>

<span data-ttu-id="9c405-127">También puede usar la delegación Kerberos sin restricciones para realizar el segundo salto.</span><span class="sxs-lookup"><span data-stu-id="9c405-127">You can also used Kerberos unconstrained delegation to make the second hop.</span></span> <span data-ttu-id="9c405-128">En cambio, este método no proporciona control sobre dónde se usan las credenciales delegadas.</span><span class="sxs-lookup"><span data-stu-id="9c405-128">However, this method provides no control of where delegated credentials are used.</span></span>

><span data-ttu-id="9c405-129">**Nota:** No se pueden delegar las cuentas de Active Directory que tengan la propiedad **La cuenta es importante y no se puede delegar** establecida.</span><span class="sxs-lookup"><span data-stu-id="9c405-129">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="9c405-130">Para obtener más información, consulte [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Enfoque de seguridad: analizar "La cuenta es importante y no se puede delegar" para cuentas con privilegios) y [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Configuración y herramientas de la autenticación Kerberos).</span><span class="sxs-lookup"><span data-stu-id="9c405-130">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="9c405-131">Pros</span><span class="sxs-lookup"><span data-stu-id="9c405-131">Pros</span></span>

- <span data-ttu-id="9c405-132">No requiere código especial.</span><span class="sxs-lookup"><span data-stu-id="9c405-132">Requires no special coding.</span></span>

### <a name="cons"></a><span data-ttu-id="9c405-133">Contras</span><span class="sxs-lookup"><span data-stu-id="9c405-133">Cons</span></span>

- <span data-ttu-id="9c405-134">No se admite el segundo salto para WinRM.</span><span class="sxs-lookup"><span data-stu-id="9c405-134">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="9c405-135">No proporciona ningún control sobre dónde se usan las credenciales, lo que crea una vulnerabilidad de seguridad.</span><span class="sxs-lookup"><span data-stu-id="9c405-135">Provides no control over where credentials are used, creating a security vulnerability.</span></span>

## <a name="kerberos-constrained-delegation"></a><span data-ttu-id="9c405-136">Delegación limitada de Kerberos</span><span class="sxs-lookup"><span data-stu-id="9c405-136">Kerberos constrained delegation</span></span>

<span data-ttu-id="9c405-137">Puede usar la delegación limitada heredada (no basada en recursos) para realizar el segundo salto.</span><span class="sxs-lookup"><span data-stu-id="9c405-137">You can use legacy constrained delegation (not resource-based) to make the second hop.</span></span> <span data-ttu-id="9c405-138">Configure la delegación restringida de Kerberos con la opción "Usar cualquier protocolo de autenticación" para permitir la transición del protocolo.</span><span class="sxs-lookup"><span data-stu-id="9c405-138">Configure Kerberos constrained delegation with the option "Use any authentication protocol" to allow protocol transition.</span></span>

> [!NOTE]
> <span data-ttu-id="9c405-139">No se pueden delegar las cuentas de Active Directory que tengan la propiedad **La cuenta es importante y no se puede delegar** establecida.</span><span class="sxs-lookup"><span data-stu-id="9c405-139">Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="9c405-140">Para obtener más información, consulte [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Enfoque de seguridad: analizar "La cuenta es importante y no se puede delegar" para cuentas con privilegios) y [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Configuración y herramientas de la autenticación Kerberos).</span><span class="sxs-lookup"><span data-stu-id="9c405-140">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="9c405-141">Pros</span><span class="sxs-lookup"><span data-stu-id="9c405-141">Pros</span></span>

- <span data-ttu-id="9c405-142">No requiere código especial</span><span class="sxs-lookup"><span data-stu-id="9c405-142">Requires no special coding</span></span>

### <a name="cons"></a><span data-ttu-id="9c405-143">Contras</span><span class="sxs-lookup"><span data-stu-id="9c405-143">Cons</span></span>

- <span data-ttu-id="9c405-144">No se admite el segundo salto para WinRM.</span><span class="sxs-lookup"><span data-stu-id="9c405-144">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="9c405-145">Se debe configurar en el objeto de Active Directory del servidor remoto (_ServidorB_).</span><span class="sxs-lookup"><span data-stu-id="9c405-145">Must be configured on the Active Directory object of the remote server (_ServerB_).</span></span>
- <span data-ttu-id="9c405-146">Limitado a un dominio.</span><span class="sxs-lookup"><span data-stu-id="9c405-146">Limited to one domain.</span></span> <span data-ttu-id="9c405-147">No puede cruzar dominios ni bosques.</span><span class="sxs-lookup"><span data-stu-id="9c405-147">Cannot cross domains or forests.</span></span>
- <span data-ttu-id="9c405-148">Requiere derechos para actualizar objetos y nombres de entidad de seguridad de servicio (SPN).</span><span class="sxs-lookup"><span data-stu-id="9c405-148">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

## <a name="resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="9c405-149">Delegación limitada de Kerberos basada en recursos</span><span class="sxs-lookup"><span data-stu-id="9c405-149">Resource-based Kerberos constrained delegation</span></span>

<span data-ttu-id="9c405-150">Con la delegación limitada de Kerberos basada en recursos (introducida en Windows Server 2012), configura la delegación de credenciales en el objeto de servidor en que residen los recursos.</span><span class="sxs-lookup"><span data-stu-id="9c405-150">Using resource-based Kerberos constrained delegation (introduced in Windows Server 2012), you configure credential delegation on the server object where resources reside.</span></span>
<span data-ttu-id="9c405-151">En el escenario del segundo salto descrito anteriormente, puede configurar el _ServidorC_ para especificar desde dónde va a aceptar credenciales delegadas.</span><span class="sxs-lookup"><span data-stu-id="9c405-151">In the second hop scenario described above, you configure _ServerC_ to specify from where it will accept delegated credentials.</span></span>

><span data-ttu-id="9c405-152">**Nota:** No se pueden delegar las cuentas de Active Directory que tengan la propiedad **La cuenta es importante y no se puede delegar** establecida.</span><span class="sxs-lookup"><span data-stu-id="9c405-152">**Note:** Active Directory accounts that have the **Account is sensitive and cannot be delegated** property set cannot be delegated.</span></span> <span data-ttu-id="9c405-153">Para obtener más información, consulte [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) (Enfoque de seguridad: analizar "La cuenta es importante y no se puede delegar" para cuentas con privilegios) y [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx) (Configuración y herramientas de la autenticación Kerberos).</span><span class="sxs-lookup"><span data-stu-id="9c405-153">For more information, see [Security Focus: Analysing 'Account is sensitive and cannot be delegated' for Privileged Accounts](https://blogs.technet.microsoft.com/poshchap/2015/05/01/security-focus-analysing-account-is-sensitive-and-cannot-be-delegated-for-privileged-accounts/) and [Kerberos Authentication Tools and Settings](https://technet.microsoft.com/library/cc738673(v=ws.10).aspx)</span></span>

### <a name="pros"></a><span data-ttu-id="9c405-154">Pros</span><span class="sxs-lookup"><span data-stu-id="9c405-154">Pros</span></span>

- <span data-ttu-id="9c405-155">Las credenciales no se almacenan.</span><span class="sxs-lookup"><span data-stu-id="9c405-155">Credentials are not stored.</span></span>
- <span data-ttu-id="9c405-156">Relativamente fácil de configurar mediante cmdlets de PowerShell, no se requiere ninguna codificación especial.</span><span class="sxs-lookup"><span data-stu-id="9c405-156">Relatively easy to configure by using PowerShell cmdlets--no special coding required.</span></span>
- <span data-ttu-id="9c405-157">No se requiere ningún acceso especial de dominio.</span><span class="sxs-lookup"><span data-stu-id="9c405-157">No special domain access is required.</span></span>
- <span data-ttu-id="9c405-158">Funciona en dominios y bosques.</span><span class="sxs-lookup"><span data-stu-id="9c405-158">Works across domains and forests.</span></span>
- <span data-ttu-id="9c405-159">Código de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c405-159">PowerShell code.</span></span>

### <a name="cons"></a><span data-ttu-id="9c405-160">Contras</span><span class="sxs-lookup"><span data-stu-id="9c405-160">Cons</span></span>

- <span data-ttu-id="9c405-161">Necesita Windows Server 2012 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="9c405-161">Requires Windows Server 2012 or later.</span></span>
- <span data-ttu-id="9c405-162">No se admite el segundo salto para WinRM.</span><span class="sxs-lookup"><span data-stu-id="9c405-162">Does not support the second hop for WinRM.</span></span>
- <span data-ttu-id="9c405-163">Requiere derechos para actualizar objetos y nombres de entidad de seguridad de servicio (SPN).</span><span class="sxs-lookup"><span data-stu-id="9c405-163">Requires rights to update objects and Service Principal Names (SPNs).</span></span>

### <a name="example"></a><span data-ttu-id="9c405-164">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9c405-164">Example</span></span>

<span data-ttu-id="9c405-165">Veamos un ejemplo de PowerShell que configura la delegación restringida basada en recursos en el _ServidorC_ para admitir credenciales delegadas de un _ServidorB_.</span><span class="sxs-lookup"><span data-stu-id="9c405-165">Let's look at a PowerShell example that configures resource based constrained delegation on _ServerC_ to allow delegated credentials from a _ServerB_.</span></span>
<span data-ttu-id="9c405-166">En este ejemplo, se supone que todos los servidores ejecutan Windows Server 2012 o una versión posterior y que hay al menos un controlador de dominio de Windows Server 2012 en cada dominio a los que pertenecen los servidores.</span><span class="sxs-lookup"><span data-stu-id="9c405-166">This example assumes that all servers are running Windows Server 2012 or later, and that there is at least one Windows Server 2012 domain controller each domain to which any of the servers belong.</span></span>

<span data-ttu-id="9c405-167">Antes de que pueda configurar la delegación restringida, debe agregar la característica `RSAT-AD-PowerShell` para instalar el módulo de PowerShell de Active Directory y después importar ese módulo en la sesión:</span><span class="sxs-lookup"><span data-stu-id="9c405-167">Before you can configure constrained delegation, you must add the `RSAT-AD-PowerShell` feature to install the Active Directory PowerShell module, and then import that module into your session:</span></span>

```powershell
PS C:\> Add-WindowsFeature RSAT-AD-PowerShell

PS C:\> Import-Module ActiveDirectory
```
<span data-ttu-id="9c405-168">Varios cmdlets disponibles tienen ahora un parámetro **PrincipalsAllowedToDelegateToAccount**:</span><span class="sxs-lookup"><span data-stu-id="9c405-168">Several available cmdlets now have a **PrincipalsAllowedToDelegateToAccount** parameter:</span></span>

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

<span data-ttu-id="9c405-169">El parámetro **PrincipalsAllowedToDelegateToAccount** establece el atributo de objeto de Active Directory **msDS-AllowedToActOnBehalfOfOtherIdentity**, que contiene una lista de control de acceso (ACL) que especifica qué cuentas tienen permiso para delegar credenciales a la cuenta asociada (en nuestro ejemplo, será la cuenta del equipo de _Servidor_).</span><span class="sxs-lookup"><span data-stu-id="9c405-169">The **PrincipalsAllowedToDelegateToAccount** parameter sets the Active Directory object attribute **msDS-AllowedToActOnBehalfOfOtherIdentity**, which contains an access control list (ACL) that specifies which accounts have permission to delegate credentials to the associated account (in our example, it will be the machine account for _Server_).</span></span>

<span data-ttu-id="9c405-170">Ahora vamos a configurar las variables que usaremos para representar los servidores:</span><span class="sxs-lookup"><span data-stu-id="9c405-170">Now let's set up the variables we'll use to represent the servers:</span></span>

```powershell
# Set up variables for reuse
$ServerA = $env:COMPUTERNAME
$ServerB = Get-ADComputer -Identity ServerB
$ServerC = Get-ADComputer -Identity ServerC
```

<span data-ttu-id="9c405-171">WinRM (y, por tanto, la comunicación remota de PowerShell) se ejecuta como la cuenta de equipo de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="9c405-171">WinRM (and therefore PowerShell remoting) runs as the computer account by default.</span></span> <span data-ttu-id="9c405-172">Puede ver esto si atiende a la propiedad **StartName** del servicio `winrm`:</span><span class="sxs-lookup"><span data-stu-id="9c405-172">You can see this by looking at the **StartName** property of the `winrm` service:</span></span>

```powershell
PS C:\> Get-WmiObject win32_service -filter 'name="winrm"' | Format-List StartName

StartName : NT AUTHORITY\NetworkService
```

<span data-ttu-id="9c405-173">Para que _ServidorC_ permita la delegación desde una sesión de comunicación remota de PowerShell en _ServidorB_, le concederemos acceso al establecer el parámetro **PrincipalsAllowedToDelegateToAccount** en _ServidorC_ al objeto de equipo de _ServidorB_:</span><span class="sxs-lookup"><span data-stu-id="9c405-173">For _ServerC_ to allow delegation from a PowerShell remoting session on _ServerB_, we will grant access by setting the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to the computer object of _ServerB_:</span></span>

```powershell
# Grant resource-based Kerberos constrained delegation
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB

# Check the value of the attribute directly
$x = Get-ADComputer -Identity $ServerC -Properties msDS-AllowedToActOnBehalfOfOtherIdentity
$x.'msDS-AllowedToActOnBehalfOfOtherIdentity'.Access

# Check the value of the attribute indirectly
Get-ADComputer -Identity $ServerC -Properties PrincipalsAllowedToDelegateToAccount
```

<span data-ttu-id="9c405-174">El [Centro de distribución de claves (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) de Kerberos copia en caché los intentos de acceso denegados (caché negativa) durante 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="9c405-174">The Kerberos [Key Distribution Center (KDC)](https://msdn.microsoft.com/library/windows/desktop/aa378170(v=vs.85).aspx) caches denied access attempts (negative cache) for 15 minutes.</span></span> <span data-ttu-id="9c405-175">Si _ServidorB_ ha intentado previamente obtener acceso a _ServidorC_, deberá borrar la caché de _ServidorB_ al invocar el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="9c405-175">If _ServerB_ has previously attempted to access _ServerC_, you will need to clear the cache on _ServerB_ by invoking the following command:</span></span>

```powershell
Invoke-Command -ComputerName $ServerB.Name -Credential $cred -ScriptBlock {
    klist purge -li 0x3e7
}
```

<span data-ttu-id="9c405-176">También puede reiniciar el equipo o esperar al menos 15 minutos para borrar la caché.</span><span class="sxs-lookup"><span data-stu-id="9c405-176">You could also restart the computer, or wait at least 15 minutes to clear the cache.</span></span>

<span data-ttu-id="9c405-177">Después de borrar la caché, puede ejecutar correctamente código desde el _ServidorA_ a través del _ServidorB_ hasta el _ServidorC_:</span><span class="sxs-lookup"><span data-stu-id="9c405-177">After clearing the cache, you can successfully run code from _ServerA_ through _ServerB_ to _ServerC_:</span></span>

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

<span data-ttu-id="9c405-178">En este ejemplo, la variable `$using` se usa para hacer visible la variable `$ServerC` en el _ServidorB_.</span><span class="sxs-lookup"><span data-stu-id="9c405-178">In this example, the `$using` variable is used to make the `$ServerC` variable visible to _ServerB_.</span></span> <span data-ttu-id="9c405-179">Para obtener más información sobre la variable `$using`, consulte [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span><span class="sxs-lookup"><span data-stu-id="9c405-179">For more information about the `$using` variable, see [about_Remote_Variables](https://technet.microsoft.com/library/jj149005.aspx).</span></span>

<span data-ttu-id="9c405-180">Para permitir que varios servidores deleguen credenciales en el _ServidorC_, establezca el valor del parámetro **PrincipalsAllowedToDelegateToAccount** en el _ServidorC_ a una matriz:</span><span class="sxs-lookup"><span data-stu-id="9c405-180">To allow multiple servers to delegate credentials to _ServerC_, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to an array:</span></span>

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

<span data-ttu-id="9c405-181">Si quiere realizar el segundo salto entre dominios, agregue el nombre de dominio completo (FQDN) del controlador del dominio al que pertenece el _ServidorB_:</span><span class="sxs-lookup"><span data-stu-id="9c405-181">If you want to make the second hop across domains, add fully-qualified domain name (FQDN) of the domain controller of the domain to which _ServerB_ belongs:</span></span>

```powershell
# For ServerC in Contoso domain and ServerB in other domain
$ServerB = Get-ADComputer -Identity ServerB -Server dc1.alpineskihouse.com
$ServerC = Get-ADComputer -Identity ServerC
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $ServerB
```

<span data-ttu-id="9c405-182">Para quitar la capacidad de delegar credenciales en el ServidorC, establezca el valor del parámetro **PrincipalsAllowedToDelegateToAccount** en el _ServidorC_ en `$null`:</span><span class="sxs-lookup"><span data-stu-id="9c405-182">To remove the ability to delegate credentials to ServerC, set the value of the **PrincipalsAllowedToDelegateToAccount** parameter on _ServerC_ to `$null`:</span></span>

```powershell
Set-ADComputer -Identity $ServerC -PrincipalsAllowedToDelegateToAccount $null
```

### <a name="information-on-resource-based-kerberos-constrained-delegation"></a><span data-ttu-id="9c405-183">Información sobre la delegación limitada de Kerberos basada en recursos</span><span class="sxs-lookup"><span data-stu-id="9c405-183">Information on resource-based Kerberos constrained delegation</span></span>

- [<span data-ttu-id="9c405-184">Novedades de la autenticación Kerberos</span><span class="sxs-lookup"><span data-stu-id="9c405-184">What's New in Kerberos Authentication</span></span>](https://technet.microsoft.com/library/hh831747.aspx)
- <span data-ttu-id="9c405-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1) (Cómo simplifica Windows Server 2012 el proceso de delegación limitada de Kerberos, parte 1)</span><span class="sxs-lookup"><span data-stu-id="9c405-185">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 1](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-1)</span></span>
- <span data-ttu-id="9c405-186">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2) (Cómo simplifica Windows Server 2012 el proceso de delegación limitada de Kerberos, parte 2)</span><span class="sxs-lookup"><span data-stu-id="9c405-186">[How Windows Server 2012 Eases the Pain of Kerberos Constrained Delegation, Part 2](https://www.itprotoday.com/windows-server/how-windows-server-2012-eases-pain-kerberos-constrained-delegation-part-2)</span></span>
- <span data-ttu-id="9c405-187">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](https://aka.ms/kcdpaper) (Comprender la delegación limitada de Kerberos para implementaciones de proxy de aplicación de Active Directory con la autenticación integrada de Windows)</span><span class="sxs-lookup"><span data-stu-id="9c405-187">[Understanding Kerberos Constrained Delegation for Azure Active Directory Application Proxy Deployments with Integrated Windows Authentication](https://aka.ms/kcdpaper)</span></span>
- <span data-ttu-id="9c405-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx) ([MS-ADA2]: atributos de esquema de Active Directory, atributo M2.210 msDS-AllowedToActOnBehalfOfOtherIdentity)</span><span class="sxs-lookup"><span data-stu-id="9c405-188">[[MS-ADA2]: Active Directory Schema Attributes M2.210 Attribute msDS-AllowedToActOnBehalfOfOtherIdentity](https://msdn.microsoft.com/library/hh554126.aspx)</span></span>
- <span data-ttu-id="9c405-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx) ([MS-SFU]: Extensiones del protocolo de Kerberos: servicio para el usuario y protocolo de delegación restringida 1.3.2 S4U2proxy)</span><span class="sxs-lookup"><span data-stu-id="9c405-189">[[MS-SFU]: Kerberos Protocol Extensions: Service for User and Constrained Delegation Protocol 1.3.2 S4U2proxy](https://msdn.microsoft.com/library/cc246079.aspx)</span></span>
- [<span data-ttu-id="9c405-190">Delegación limitada de Kerberos basada en recursos</span><span class="sxs-lookup"><span data-stu-id="9c405-190">Resource Based Kerberos Constrained Delegation</span></span>](https://blog.kloud.com.au/2013/07/11/kerberos-constrained-delegation/)
- <span data-ttu-id="9c405-191">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/) (Administración remota sin delegación limitada con PrincipalsAllowedToDelegateToAccount)</span><span class="sxs-lookup"><span data-stu-id="9c405-191">[Remote Administration Without Constrained Delegation Using PrincipalsAllowedToDelegateToAccount](https://blogs.msdn.microsoft.com/taylorb/2012/11/06/remote-administration-without-constrained-delegation-using-principalsallowedtodelegatetoaccount/)</span></span>

## <a name="pssessionconfiguration-using-runas"></a><span data-ttu-id="9c405-192">PSSessionConfiguration con RunAs</span><span class="sxs-lookup"><span data-stu-id="9c405-192">PSSessionConfiguration using RunAs</span></span>

<span data-ttu-id="9c405-193">Puede crear una configuración de sesión en el _ServidorB_ y establecer su parámetro **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="9c405-193">You can create a session configuration on _ServerB_ and set its **RunAsCredential** parameter.</span></span>

<span data-ttu-id="9c405-194">Para obtener información sobre el uso de PSSessionConfiguration y RunAs para resolver el problema del segundo salto, consulte [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/) (Otra solución a la comunicación remota de PowerShell de varios saltos).</span><span class="sxs-lookup"><span data-stu-id="9c405-194">For information about using PSSessionConfiguration and RunAs to solve the second hop problem, see [Another solution to multi-hop PowerShell remoting](https://blogs.msdn.microsoft.com/sergey_babkins_blog/2015/03/18/another-solution-to-multi-hop-powershell-remoting/).</span></span>

### <a name="pros"></a><span data-ttu-id="9c405-195">Pros</span><span class="sxs-lookup"><span data-stu-id="9c405-195">Pros</span></span>

- <span data-ttu-id="9c405-196">Funciona con cualquier servidor con WMF 3.0 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="9c405-196">Works with any server with WMF 3.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="9c405-197">Contras</span><span class="sxs-lookup"><span data-stu-id="9c405-197">Cons</span></span>

- <span data-ttu-id="9c405-198">Requiere la configuración de **PSSessionConfiguration** y **RunAs** en cada servidor intermedio (_ServidorB_).</span><span class="sxs-lookup"><span data-stu-id="9c405-198">Requires configuration of **PSSessionConfiguration** and **RunAs** on every intermediate server (_ServerB_).</span></span>
- <span data-ttu-id="9c405-199">Requiere el mantenimiento de la contraseña cuando se usa una cuenta de **ejecución** de dominio</span><span class="sxs-lookup"><span data-stu-id="9c405-199">Requires password maintenance when using a domain **RunAs** account</span></span>

## <a name="just-enough-administration-jea"></a><span data-ttu-id="9c405-200">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="9c405-200">Just Enough Administration (JEA)</span></span>

<span data-ttu-id="9c405-201">JEA le permite restringir qué comandos puede ejecutar un administrador durante una sesión de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c405-201">JEA allows you to restrict what commands an administrator can run during a PowerShell session.</span></span> <span data-ttu-id="9c405-202">Se puede usar para resolver el problema del segundo salto.</span><span class="sxs-lookup"><span data-stu-id="9c405-202">It can be used to solve the second hop problem.</span></span>

<span data-ttu-id="9c405-203">Para obtener información sobre JEA, consulte [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span><span class="sxs-lookup"><span data-stu-id="9c405-203">For information about JEA, see [Just Enough Administration](https://docs.microsoft.com/powershell/jea/overview).</span></span>

### <a name="pros"></a><span data-ttu-id="9c405-204">Pros</span><span class="sxs-lookup"><span data-stu-id="9c405-204">Pros</span></span>

- <span data-ttu-id="9c405-205">No hay mantenimiento de contraseña al usar una cuenta virtual.</span><span class="sxs-lookup"><span data-stu-id="9c405-205">No password maintenance when using a virtual account.</span></span>

### <a name="cons"></a><span data-ttu-id="9c405-206">Contras</span><span class="sxs-lookup"><span data-stu-id="9c405-206">Cons</span></span>

- <span data-ttu-id="9c405-207">Requiere WMF 5.0 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="9c405-207">Requires WMF 5.0 or later.</span></span>
- <span data-ttu-id="9c405-208">Es necesario configurar cada servidor intermedio (_ServidorB_).</span><span class="sxs-lookup"><span data-stu-id="9c405-208">Requires configuration on every intermediate server (_ServerB_).</span></span>

## <a name="pass-credentials-inside-an-invoke-command-script-block"></a><span data-ttu-id="9c405-209">Pasar credenciales dentro de un bloque de script de Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="9c405-209">Pass credentials inside an Invoke-Command script block</span></span>

<span data-ttu-id="9c405-210">Se pueden pasar credenciales dentro del parámetro **ScriptBlock** de una llamada al cmdlet [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="9c405-210">You can pass credentials inside the **ScriptBlock** parameter of a call to the [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) cmdlet.</span></span>

### <a name="pros"></a><span data-ttu-id="9c405-211">Pros</span><span class="sxs-lookup"><span data-stu-id="9c405-211">Pros</span></span>

- <span data-ttu-id="9c405-212">No requiere configuración especial del servidor.</span><span class="sxs-lookup"><span data-stu-id="9c405-212">Does not require special server configuration.</span></span>
- <span data-ttu-id="9c405-213">Funciona en cualquier servidor que ejecute WMF 2.0 o versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="9c405-213">Works on any server running WMF 2.0 or later.</span></span>

### <a name="cons"></a><span data-ttu-id="9c405-214">Contras</span><span class="sxs-lookup"><span data-stu-id="9c405-214">Cons</span></span>

- <span data-ttu-id="9c405-215">Se requiere una técnica de código complicada.</span><span class="sxs-lookup"><span data-stu-id="9c405-215">Requires an awkward code technique.</span></span>
- <span data-ttu-id="9c405-216">Si ejecuta WMF 2.0, requiere una sintaxis diferente para pasar argumentos a una sesión remota.</span><span class="sxs-lookup"><span data-stu-id="9c405-216">If running WMF 2.0, requires different syntax for passing arguments to a remote session.</span></span>

### <a name="example"></a><span data-ttu-id="9c405-217">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="9c405-217">Example</span></span>

<span data-ttu-id="9c405-218">En el ejemplo siguiente, se muestra cómo pasar las credenciales en un bloque de script **Invoke-Command**:</span><span class="sxs-lookup"><span data-stu-id="9c405-218">The following example shows how to pass credentials in an **Invoke-Command** script block:</span></span>

```powershell
# This works without delegation, passing fresh creds
# Note $Using:Cred in nested request
$cred = Get-Credential Contoso\Administrator
Invoke-Command -ComputerName ServerB -Credential $cred -ScriptBlock {
    hostname
    Invoke-Command -ComputerName ServerC -Credential $Using:cred -ScriptBlock {hostname}
}
```

## <a name="see-also"></a><span data-ttu-id="9c405-219">Vea también</span><span class="sxs-lookup"><span data-stu-id="9c405-219">See also</span></span>

[<span data-ttu-id="9c405-220">Consideraciones de seguridad de comunicación remota de PowerShell</span><span class="sxs-lookup"><span data-stu-id="9c405-220">PowerShell Remoting Security Considerations</span></span>](WinRMSecurity.md)
