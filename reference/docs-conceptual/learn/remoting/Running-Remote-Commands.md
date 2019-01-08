---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Ejecutar comandos remotos
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: 2001b5509acde6ec4259bb1442944958a67aa66f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403250"
---
# <a name="running-remote-commands"></a><span data-ttu-id="e67ca-103">Ejecutar comandos remotos</span><span class="sxs-lookup"><span data-stu-id="e67ca-103">Running Remote Commands</span></span>

<span data-ttu-id="e67ca-104">Puede ejecutar comandos en un equipo o en cientos de ellos usando un solo comando de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e67ca-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="e67ca-105">Windows PowerShell admite la informática remota a través de varias tecnologías, como WS-Management, RPC y WMI.</span><span class="sxs-lookup"><span data-stu-id="e67ca-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="e67ca-106">PowerShell Core admite WMI, WS-Management y la comunicación remota mediante SSH.</span><span class="sxs-lookup"><span data-stu-id="e67ca-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="e67ca-107">Ya no se admite RPC.</span><span class="sxs-lookup"><span data-stu-id="e67ca-107">RPC is no longer supported.</span></span>

<span data-ttu-id="e67ca-108">Para más información sobre la comunicación remota de PowerShell Core, consulte los artículos siguientes:</span><span class="sxs-lookup"><span data-stu-id="e67ca-108">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="e67ca-109">[Comunicación remota mediante SSH en PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="e67ca-109">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="e67ca-110">[Comunicación remota mediante WSMan en PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="e67ca-110">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="e67ca-111">Comunicación remota de Windows PowerShell sin configuración</span><span class="sxs-lookup"><span data-stu-id="e67ca-111">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="e67ca-112">Muchos de los cmdlets de Windows PowerShell tienen un parámetro ComputerName que les permite recopilar datos y cambiar la configuración de uno o más equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="e67ca-112">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="e67ca-113">Estos cmdlets utilizan diversos protocolos de comunicación y funcionan en todos los sistemas operativos Windows sin ninguna configuración especial.</span><span class="sxs-lookup"><span data-stu-id="e67ca-113">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="e67ca-114">Estos cmdlets son:</span><span class="sxs-lookup"><span data-stu-id="e67ca-114">These cmdlets include:</span></span>

- [<span data-ttu-id="e67ca-115">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="e67ca-115">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="e67ca-116">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="e67ca-116">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="e67ca-117">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="e67ca-117">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="e67ca-118">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="e67ca-118">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="e67ca-119">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="e67ca-119">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="e67ca-120">Get-Process</span><span class="sxs-lookup"><span data-stu-id="e67ca-120">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="e67ca-121">Get-Service</span><span class="sxs-lookup"><span data-stu-id="e67ca-121">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="e67ca-122">Set-Service</span><span class="sxs-lookup"><span data-stu-id="e67ca-122">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="e67ca-123">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="e67ca-123">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="e67ca-124">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="e67ca-124">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="e67ca-125">Normalmente, los cmdlets que admiten la comunicación remota sin una configuración especial tienen un parámetro ComputerName y carecen de un parámetro Session.</span><span class="sxs-lookup"><span data-stu-id="e67ca-125">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="e67ca-126">Para encontrar estos cmdlets en la sesión, escriba:</span><span class="sxs-lookup"><span data-stu-id="e67ca-126">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="e67ca-127">Comunicación remota de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e67ca-127">Windows PowerShell Remoting</span></span>

<span data-ttu-id="e67ca-128">Mediante el protocolo WS-Management, la comunicación remota de Windows PowerShell permite ejecutar cualquier comando de Windows PowerShell en uno o varios equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="e67ca-128">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="e67ca-129">Puede establecer conexiones persistentes, iniciar sesiones interactivas y ejecutar scripts en equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="e67ca-129">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="e67ca-130">Para usar la comunicación remota de Windows PowerShell, el equipo remoto debe estar configurado para la administración remota.</span><span class="sxs-lookup"><span data-stu-id="e67ca-130">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="e67ca-131">Para más información y ver instrucciones, consulte [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements) (Acerca de los requisitos remotos).</span><span class="sxs-lookup"><span data-stu-id="e67ca-131">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="e67ca-132">Cuando haya configurado la comunicación remota de Windows PowerShell, tendrá a su disposición un gran número de estrategias de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="e67ca-132">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="e67ca-133">En este artículo se enumeran algunos de ellos.</span><span class="sxs-lookup"><span data-stu-id="e67ca-133">This article lists just a few of them.</span></span> <span data-ttu-id="e67ca-134">Para más información, consulte [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote) (Acerca del acceso remoto).</span><span class="sxs-lookup"><span data-stu-id="e67ca-134">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="e67ca-135">Iniciar una sesión interactiva</span><span class="sxs-lookup"><span data-stu-id="e67ca-135">Start an Interactive Session</span></span>

<span data-ttu-id="e67ca-136">Para iniciar una sesión interactiva con un único equipo remoto, use el cmdlet [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).</span><span class="sxs-lookup"><span data-stu-id="e67ca-136">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span>
<span data-ttu-id="e67ca-137">Por ejemplo, para iniciar una sesión interactiva con el equipo remoto Server01, escriba:</span><span class="sxs-lookup"><span data-stu-id="e67ca-137">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="e67ca-138">El símbolo del sistema cambia para mostrar el nombre del equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="e67ca-138">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="e67ca-139">Cualquier comando que escriba en el símbolo del sistema se ejecuta en el equipo remoto y los resultados se muestran en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="e67ca-139">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="e67ca-140">Para finalizar la sesión interactiva, escriba:</span><span class="sxs-lookup"><span data-stu-id="e67ca-140">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="e67ca-141">Para más información sobre los cmdlets Enter-PSSession y Exit-PSSession, consulte:</span><span class="sxs-lookup"><span data-stu-id="e67ca-141">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="e67ca-142">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="e67ca-142">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="e67ca-143">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="e67ca-143">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="e67ca-144">Ejecutar un comando remoto</span><span class="sxs-lookup"><span data-stu-id="e67ca-144">Run a Remote Command</span></span>

<span data-ttu-id="e67ca-145">Para ejecutar un comando en uno o varios equipos, use el cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command).</span><span class="sxs-lookup"><span data-stu-id="e67ca-145">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="e67ca-146">Por ejemplo, para ejecutar un comando [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) en los equipos remotos Server01 y Server02, escriba:</span><span class="sxs-lookup"><span data-stu-id="e67ca-146">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="e67ca-147">El resultado se muestra en su equipo.</span><span class="sxs-lookup"><span data-stu-id="e67ca-147">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="e67ca-148">Ejecutar un script</span><span class="sxs-lookup"><span data-stu-id="e67ca-148">Run a Script</span></span>

<span data-ttu-id="e67ca-149">Para ejecutar un script en uno o varios equipos remotos, use el parámetro FilePath del cmdlet `Invoke-Command`.</span><span class="sxs-lookup"><span data-stu-id="e67ca-149">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="e67ca-150">El script debe estar en el equipo local o accesible desde este.</span><span class="sxs-lookup"><span data-stu-id="e67ca-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="e67ca-151">Los resultados se devuelven en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="e67ca-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="e67ca-152">Por ejemplo, el siguiente comando ejecuta el script DiskCollect.ps1 en los equipos remotos Server01 y Server02.</span><span class="sxs-lookup"><span data-stu-id="e67ca-152">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="e67ca-153">Establecer una conexión persistente</span><span class="sxs-lookup"><span data-stu-id="e67ca-153">Establish a Persistent Connection</span></span>

<span data-ttu-id="e67ca-154">Utilice el cmdlet `New-PSSession` para crear una sesión persistente en un equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="e67ca-154">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="e67ca-155">En el ejemplo siguiente se crean sesiones remotas en Server01 y Server02.</span><span class="sxs-lookup"><span data-stu-id="e67ca-155">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="e67ca-156">Los objetos de la sesión se almacenan en la variable `$s`.</span><span class="sxs-lookup"><span data-stu-id="e67ca-156">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="e67ca-157">Ahora que las sesiones se han establecido, puede ejecutar cualquier comando en ellas.</span><span class="sxs-lookup"><span data-stu-id="e67ca-157">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="e67ca-158">Y, como las sesiones son persistentes, puede recopilar datos en un solo comando y usarlos en un otro comando.</span><span class="sxs-lookup"><span data-stu-id="e67ca-158">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="e67ca-159">Por ejemplo, el siguiente comando ejecuta un comando Get-Hotfix en las sesiones de la variable $s y guarda los resultados en la variable $h.</span><span class="sxs-lookup"><span data-stu-id="e67ca-159">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="e67ca-160">La variable $h se crea en cada una de las sesiones en $s, pero no existe en la sesión local.</span><span class="sxs-lookup"><span data-stu-id="e67ca-160">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="e67ca-161">Ahora puede usar los datos de la variable `$h` con otros comandos en la misma sesión.</span><span class="sxs-lookup"><span data-stu-id="e67ca-161">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="e67ca-162">Los resultados se muestran en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="e67ca-162">The results are displayed on the local computer.</span></span> <span data-ttu-id="e67ca-163">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e67ca-163">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="e67ca-164">Comunicación remota avanzada</span><span class="sxs-lookup"><span data-stu-id="e67ca-164">Advanced Remoting</span></span>

<span data-ttu-id="e67ca-165">La administración remota de Windows PowerShell empieza aquí.</span><span class="sxs-lookup"><span data-stu-id="e67ca-165">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="e67ca-166">Con los cmdlets que se instalan con Windows PowerShell puede, entre otras muchas cosas, establecer y configurar sesiones remotas desde extremos tanto locales como remotos, crear sesiones personalizadas y restringidas, dejar que los usuarios importen comandos desde una sesión remota que se ejecutan implícitamente en la sesión remota o configurar la seguridad de una sesión remota.</span><span class="sxs-lookup"><span data-stu-id="e67ca-166">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="e67ca-167">Windows PowerShell incluye un proveedor de WSMan.</span><span class="sxs-lookup"><span data-stu-id="e67ca-167">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="e67ca-168">El proveedor crea una unidad `WSMAN:` que le permite desplazarse por una jerarquía de valores de configuración en el equipo local y en los equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="e67ca-168">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="e67ca-169">Para más información sobre el proveedor de WSMan, consulte [Proveedor de WSMan](https://technet.microsoft.com/library/dd819476.aspx) y [About WS-Management Cmdlets (Acerca de los cmdlets de WS-Management)](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets). También puede escribir `Get-Help wsman` en la consola de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e67ca-169">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="e67ca-170">Para obtener más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="e67ca-170">For more information, see:</span></span>

- [<span data-ttu-id="e67ca-171">Acerca de las Preguntas más frecuentes sobre el acceso remoto</span><span class="sxs-lookup"><span data-stu-id="e67ca-171">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="e67ca-172">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e67ca-172">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="e67ca-173">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="e67ca-173">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="e67ca-174">Para obtener ayuda con los errores de comunicación remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="e67ca-174">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="e67ca-175">Véase también</span><span class="sxs-lookup"><span data-stu-id="e67ca-175">See Also</span></span>

- [<span data-ttu-id="e67ca-176">about_Remote</span><span class="sxs-lookup"><span data-stu-id="e67ca-176">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="e67ca-177">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="e67ca-177">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="e67ca-178">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="e67ca-178">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="e67ca-179">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="e67ca-179">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="e67ca-180">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="e67ca-180">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="e67ca-181">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="e67ca-181">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="e67ca-182">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e67ca-182">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="e67ca-183">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="e67ca-183">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="e67ca-184">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="e67ca-184">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="e67ca-185">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="e67ca-185">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="e67ca-186">Proveedor de WSMan</span><span class="sxs-lookup"><span data-stu-id="e67ca-186">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md