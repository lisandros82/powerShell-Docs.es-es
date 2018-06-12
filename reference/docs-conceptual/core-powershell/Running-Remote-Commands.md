---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Ejecutar comandos remotos
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: d21d1def1e25895f65b3578bf2892d56f14cc150
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482886"
---
# <a name="running-remote-commands"></a><span data-ttu-id="8df51-103">Ejecutar comandos remotos</span><span class="sxs-lookup"><span data-stu-id="8df51-103">Running Remote Commands</span></span>

<span data-ttu-id="8df51-104">Puede ejecutar comandos en un equipo o en cientos de ellos usando un solo comando de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8df51-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="8df51-105">Windows PowerShell admite la informática remota a través de varias tecnologías, como WS-Management, RPC y WMI.</span><span class="sxs-lookup"><span data-stu-id="8df51-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-in-powershell-core"></a><span data-ttu-id="8df51-106">Comunicación remota en PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8df51-106">Remoting in PowerShell Core</span></span>

<span data-ttu-id="8df51-107">PowerShell Core, la edición más reciente de PowerShell en Windows, macOS y Linux, es compatible con WMI, WS-Management y la comunicación remota mediante SSH.</span><span class="sxs-lookup"><span data-stu-id="8df51-107">PowerShell Core, the newer edition of PowerShell on Windows, macOS, and Linux, supports WMI, WS-Management, and SSH remoting.</span></span>
<span data-ttu-id="8df51-108">(Ya no se admite RPC).</span><span class="sxs-lookup"><span data-stu-id="8df51-108">(RPC is no longer supported.)</span></span>

<span data-ttu-id="8df51-109">Para más información sobre la configuración, vea:</span><span class="sxs-lookup"><span data-stu-id="8df51-109">For more information on setting this up, see:</span></span>

* <span data-ttu-id="8df51-110">[Comunicación remota mediante SSH en PowerShell Core][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="8df51-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
* <span data-ttu-id="8df51-111">[Comunicación remota mediante WSMan en PowerShell Core][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="8df51-111">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="8df51-112">Comunicación remota sin configuración</span><span class="sxs-lookup"><span data-stu-id="8df51-112">Remoting Without Configuration</span></span>

<span data-ttu-id="8df51-113">Muchos de los cmdlets de Windows PowerShell tienen un parámetro ComputerName que les permite recopilar datos y cambiar la configuración de uno o más equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="8df51-113">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="8df51-114">Usan distintas tecnologías de comunicación y muchos de ellos funcionan con todos los sistemas operativos de Windows que Windows PowerShell admite sin necesidad de ninguna configuración especial.</span><span class="sxs-lookup"><span data-stu-id="8df51-114">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="8df51-115">Estos cmdlets son:</span><span class="sxs-lookup"><span data-stu-id="8df51-115">These cmdlets include:</span></span>

* [<span data-ttu-id="8df51-116">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="8df51-116">Restart-Computer</span></span>](https://go.microsoft.com/fwlink/?LinkId=821625)
* [<span data-ttu-id="8df51-117">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="8df51-117">Test-Connection</span></span>](https://go.microsoft.com/fwlink/?LinkId=821646)
* [<span data-ttu-id="8df51-118">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="8df51-118">Clear-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821568)
* [<span data-ttu-id="8df51-119">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="8df51-119">Get-EventLog</span></span>](https://go.microsoft.com/fwlink/?LinkId=821585)
* [<span data-ttu-id="8df51-120">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="8df51-120">Get-HotFix</span></span>](https://go.microsoft.com/fwlink/?LinkId=821586)
* [<span data-ttu-id="8df51-121">Get-Process</span><span class="sxs-lookup"><span data-stu-id="8df51-121">Get-Process</span></span>](https://go.microsoft.com/fwlink/?linkid=821590)
* [<span data-ttu-id="8df51-122">Get-Service</span><span class="sxs-lookup"><span data-stu-id="8df51-122">Get-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821593)
* [<span data-ttu-id="8df51-123">Set-Service</span><span class="sxs-lookup"><span data-stu-id="8df51-123">Set-Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=821633)
* [<span data-ttu-id="8df51-124">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="8df51-124">Get-WinEvent</span></span>](https://go.microsoft.com/fwlink/?linkid=821529)
* [<span data-ttu-id="8df51-125">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="8df51-125">Get-WmiObject</span></span>](https://go.microsoft.com/fwlink/?LinkId=821595)

<span data-ttu-id="8df51-126">Normalmente, los cmdlets que admiten la comunicación remota sin una configuración especial tienen un parámetro ComputerName y carecen de un parámetro Session.</span><span class="sxs-lookup"><span data-stu-id="8df51-126">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="8df51-127">Para encontrar estos cmdlets en la sesión, escriba:</span><span class="sxs-lookup"><span data-stu-id="8df51-127">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="8df51-128">Comunicación remota de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8df51-128">Windows PowerShell Remoting</span></span>

<span data-ttu-id="8df51-129">La comunicación remota de Windows PowerShell, que usa el protocolo WS-Management, permite ejecutar cualquier comando de Windows PowerShell en uno o varios equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="8df51-129">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="8df51-130">Así, permite establecer conexiones persistentes, iniciar sesiones interactivas de 1:1 y ejecutar scripts en varios equipos.</span><span class="sxs-lookup"><span data-stu-id="8df51-130">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="8df51-131">Para usar la comunicación remota de Windows PowerShell, el equipo remoto debe estar configurado para la administración remota.</span><span class="sxs-lookup"><span data-stu-id="8df51-131">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="8df51-132">Para más información y ver instrucciones, consulte [About Remote Requirements](https://technet.microsoft.com/library/dd315349.aspx) (Acerca de los requisitos remotos).</span><span class="sxs-lookup"><span data-stu-id="8df51-132">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/library/dd315349.aspx).</span></span>

<span data-ttu-id="8df51-133">Después de configurar la comunicación remota de Windows PowerShell, tendrá a su disposición un gran número de estrategias de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="8df51-133">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="8df51-134">En lo que resta de este documento se mencionan solo algunas de ellas.</span><span class="sxs-lookup"><span data-stu-id="8df51-134">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="8df51-135">Para más información, vea [About Remote](https://technet.microsoft.com/library/dd347744.aspx) (Acerca del acceso remoto) y [About Remote FAQ](https://technet.microsoft.com/library/dd347744.aspx) (Preguntas más frecuentes sobre el acceso remoto).</span><span class="sxs-lookup"><span data-stu-id="8df51-135">For more information, see [About Remote](https://technet.microsoft.com/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="8df51-136">Iniciar una sesión interactiva</span><span class="sxs-lookup"><span data-stu-id="8df51-136">Start an Interactive Session</span></span>

<span data-ttu-id="8df51-137">Para iniciar una sesión interactiva con un único equipo remoto, use el cmdlet [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477).</span><span class="sxs-lookup"><span data-stu-id="8df51-137">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) cmdlet.</span></span>
<span data-ttu-id="8df51-138">Por ejemplo, para iniciar una sesión interactiva con el equipo remoto Server01, escriba:</span><span class="sxs-lookup"><span data-stu-id="8df51-138">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="8df51-139">El símbolo del sistema cambia para mostrar el nombre del equipo al que está conectado.</span><span class="sxs-lookup"><span data-stu-id="8df51-139">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="8df51-140">Desde ese momento, cualquier comando que escriba en el símbolo del sistema se ejecutará en el equipo remoto y los resultados se mostrarán en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="8df51-140">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="8df51-141">Para finalizar la sesión interactiva, escriba:</span><span class="sxs-lookup"><span data-stu-id="8df51-141">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="8df51-142">Para más información sobre los cmdlets Enter-PSSession y Exit-PSSession, vea [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) y [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span><span class="sxs-lookup"><span data-stu-id="8df51-142">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) and [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="8df51-143">Ejecutar un comando remoto</span><span class="sxs-lookup"><span data-stu-id="8df51-143">Run a Remote Command</span></span>

<span data-ttu-id="8df51-144">Para ejecutar cualquier comando en uno o varios equipos remotos, use el cmdlet [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="8df51-144">To run any command on one or many remote computers, use the [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493) cmdlet.</span></span>
<span data-ttu-id="8df51-145">Por ejemplo, para ejecutar un comando [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) en los equipos remotos Server01 y Server02, escriba:</span><span class="sxs-lookup"><span data-stu-id="8df51-145">For example, to run a [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="8df51-146">El resultado se muestra en su equipo.</span><span class="sxs-lookup"><span data-stu-id="8df51-146">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

<span data-ttu-id="8df51-147">Para más información sobre el cmdlet Invoke-Command, vea [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="8df51-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="8df51-148">Ejecutar un script</span><span class="sxs-lookup"><span data-stu-id="8df51-148">Run a Script</span></span>

<span data-ttu-id="8df51-149">Para ejecutar un script en uno o varios equipos remotos, use el parámetro FilePath del cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="8df51-149">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="8df51-150">El script debe estar en el equipo local o accesible desde este.</span><span class="sxs-lookup"><span data-stu-id="8df51-150">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="8df51-151">Los resultados se devuelven en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="8df51-151">The results are returned to your local computer.</span></span>

<span data-ttu-id="8df51-152">Por ejemplo, el siguiente comando ejecuta el script DiskCollect.ps1 en los equipos remotos Server01 y Server02.</span><span class="sxs-lookup"><span data-stu-id="8df51-152">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="8df51-153">Para más información sobre el cmdlet Invoke-Command, vea [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span><span class="sxs-lookup"><span data-stu-id="8df51-153">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="8df51-154">Establecer una conexión persistente</span><span class="sxs-lookup"><span data-stu-id="8df51-154">Establish a Persistent Connection</span></span>

<span data-ttu-id="8df51-155">Para ejecutar una serie de comandos relacionados que comparten datos, crear una sesión en el equipo remoto y, a continuación, use el cmdlet Invoke-Command para ejecutar comandos en la sesión que cree.</span><span class="sxs-lookup"><span data-stu-id="8df51-155">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="8df51-156">Para crear una sesión remota, use el cmdlet New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="8df51-156">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="8df51-157">Por ejemplo, el comando siguiente crea una sesión remota en el equipo Server01 y otra sesión remota en el equipo Server02.</span><span class="sxs-lookup"><span data-stu-id="8df51-157">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="8df51-158">Guarda los objetos de la sesión en la variable $s.</span><span class="sxs-lookup"><span data-stu-id="8df51-158">It saves the session objects in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="8df51-159">Ahora que las sesiones se han establecido, puede ejecutar cualquier comando en ellas.</span><span class="sxs-lookup"><span data-stu-id="8df51-159">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="8df51-160">Y, como las sesiones son persistentes, puede recopilar datos en un solo comando y usarlos en un comando posterior.</span><span class="sxs-lookup"><span data-stu-id="8df51-160">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="8df51-161">Por ejemplo, el siguiente comando ejecuta un comando Get-Hotfix en las sesiones de la variable $s y guarda los resultados en la variable $h.</span><span class="sxs-lookup"><span data-stu-id="8df51-161">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="8df51-162">La variable $h se crea en cada una de las sesiones en $s, pero no existe en la sesión local.</span><span class="sxs-lookup"><span data-stu-id="8df51-162">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="8df51-163">Ahora puede usar los datos de la variable $h en los siguientes comandos, como en el siguiente.</span><span class="sxs-lookup"><span data-stu-id="8df51-163">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="8df51-164">Los resultados se muestran en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="8df51-164">The results are displayed on the local computer.</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="8df51-165">Comunicación remota avanzada</span><span class="sxs-lookup"><span data-stu-id="8df51-165">Advanced Remoting</span></span>

<span data-ttu-id="8df51-166">La administración remota de Windows PowerShell empieza aquí.</span><span class="sxs-lookup"><span data-stu-id="8df51-166">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="8df51-167">Con los cmdlets que se instalan con Windows PowerShell puede, entre otras muchas cosas, establecer y configurar sesiones remotas desde extremos tanto locales como remotos, crear sesiones personalizadas y restringidas, dejar que los usuarios importen comandos desde una sesión remota que se ejecutan implícitamente en la sesión remota o configurar la seguridad de una sesión remota.</span><span class="sxs-lookup"><span data-stu-id="8df51-167">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="8df51-168">Para facilitar la configuración remota, Windows PowerShell incluye un proveedor WSMan.</span><span class="sxs-lookup"><span data-stu-id="8df51-168">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="8df51-169">La unidad WSMAN: que este proveedor crea permite desplazarse por una jerarquía de valores de configuración en el equipo local y en los equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="8df51-169">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="8df51-170">Para obtener más información sobre el proveedor WSMan, vea el tema sobre el [proveedor WSMan](https://technet.microsoft.com/library/dd819476.aspx) y el tema [About WS-Management Cmdlets](https://technet.microsoft.com/library/dd819481.aspx) (Acerca de los cmdlets de WS-Management). También puede escribir "Get-Help wsman" en la consola de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8df51-170">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](https://technet.microsoft.com/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="8df51-171">Para obtener más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="8df51-171">For more information, see:</span></span>

- [<span data-ttu-id="8df51-172">Acerca de las Preguntas más frecuentes sobre el acceso remoto</span><span class="sxs-lookup"><span data-stu-id="8df51-172">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="8df51-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8df51-173">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="8df51-174">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="8df51-174">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="8df51-175">Para obtener ayuda con los errores de comunicación remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="8df51-175">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="8df51-176">Véase también</span><span class="sxs-lookup"><span data-stu-id="8df51-176">See Also</span></span>

- [<span data-ttu-id="8df51-177">about_Remote</span><span class="sxs-lookup"><span data-stu-id="8df51-177">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="8df51-178">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="8df51-178">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="8df51-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="8df51-179">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="8df51-180">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="8df51-180">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="8df51-181">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="8df51-181">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="8df51-182">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="8df51-182">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="8df51-183">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="8df51-183">Invoke-Command</span></span>](https://go.microsoft.com/fwlink/?LinkId=821493)
- [<span data-ttu-id="8df51-184">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="8df51-184">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="8df51-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="8df51-185">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="8df51-186">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8df51-186">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="8df51-187">Proveedor de WSMan</span><span class="sxs-lookup"><span data-stu-id="8df51-187">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md