---
ms.date: 08/14/2018
keywords: powershell, cmdlet
title: Ejecutar comandos remotos
ms.openlocfilehash: d6609deafd8dec4f34a8412439d87dacd20d46f1
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030318"
---
# <a name="running-remote-commands"></a>Ejecutar comandos remotos

Puede ejecutar comandos en un equipo o en cientos de ellos usando un solo comando de PowerShell. Windows PowerShell admite la informática remota a través de varias tecnologías, como WS-Management, RPC y WMI.

PowerShell Core admite WMI, WS-Management y la comunicación remota mediante SSH. Ya no se admite RPC.

Para más información sobre la comunicación remota de PowerShell Core, consulte los artículos siguientes:

- [Comunicación remota mediante SSH en PowerShell Core][ssh-remoting]
- [Comunicación remota mediante WSMan en PowerShell Core][wsman-remoting]

## <a name="windows-powershell-remoting-without-configuration"></a>Comunicación remota de Windows PowerShell sin configuración

Muchos de los cmdlets de Windows PowerShell tienen un parámetro ComputerName que les permite recopilar datos y cambiar la configuración de uno o más equipos remotos. Estos cmdlets utilizan diversos protocolos de comunicación y funcionan en todos los sistemas operativos Windows sin ninguna configuración especial.

Estos cmdlets son:

- [Restart-Computer](/powershell/module/microsoft.powershell.management/restart-computer)
- [Test-Connection](/powershell/module/microsoft.powershell.management/test-connection)
- [Clear-EventLog](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [Get-EventLog](/powershell/module/microsoft.powershell.management/get-eventlog)
- [Get-HotFix](/powershell/module/microsoft.powershell.management/get-hotfix)
- [Get-Process](/powershell/module/microsoft.powershell.management/get-process)
- [Get-Service](/powershell/module/microsoft.powershell.management/get-service)
- [Set-Service](/powershell/module/microsoft.powershell.management/set-service)
- [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [Get-WmiObject](/powershell/module/microsoft.powershell.management/get-wmiobject)

Normalmente, los cmdlets que admiten la comunicación remota sin una configuración especial tienen un parámetro ComputerName y carecen de un parámetro Session. Para encontrar estos cmdlets en la sesión, escriba:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Comunicación remota de Windows PowerShell

Mediante el protocolo WS-Management, la comunicación remota de Windows PowerShell permite ejecutar cualquier comando de Windows PowerShell en uno o varios equipos remotos. Puede establecer conexiones persistentes, iniciar sesiones interactivas y ejecutar scripts en equipos remotos.

Para usar la comunicación remota de Windows PowerShell, el equipo remoto debe estar configurado para la administración remota.
Para más información y ver instrucciones, consulte [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements) (Acerca de los requisitos remotos).

Cuando haya configurado la comunicación remota de Windows PowerShell, tendrá a su disposición un gran número de estrategias de comunicación remota.
En este artículo se enumeran algunos de ellos. Para más información, consulte [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote) (Acerca del acceso remoto).

### <a name="start-an-interactive-session"></a>Iniciar una sesión interactiva

Para iniciar una sesión interactiva con un único equipo remoto, use el cmdlet [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).
Por ejemplo, para iniciar una sesión interactiva con el equipo remoto Server01, escriba:

```powershell
Enter-PSSession Server01
```

El símbolo del sistema cambia para mostrar el nombre del equipo remoto. Cualquier comando que escriba en el símbolo del sistema se ejecuta en el equipo remoto y los resultados se muestran en el equipo local.

Para finalizar la sesión interactiva, escriba:

```powershell
Exit-PSSession
```

Para más información sobre los cmdlets Enter-PSSession y Exit-PSSession, consulte:

- [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession)
- [Exit-PSSession](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a>Ejecutar un comando remoto

Para ejecutar un comando en uno o varios equipos, use el cmdlet [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command). Por ejemplo, para ejecutar un comando [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) en los equipos remotos Server01 y Server02, escriba:

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

El resultado se muestra en su equipo.

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a>Ejecutar un script

Para ejecutar un script en uno o varios equipos remotos, use el parámetro FilePath del cmdlet `Invoke-Command`. El script debe estar en el equipo local o accesible desde este. Los resultados se devuelven en el equipo local.

Por ejemplo, el siguiente comando ejecuta el script DiskCollect.ps1 en los equipos remotos Server01 y Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a>Establecer una conexión persistente

Utilice el cmdlet `New-PSSession` para crear una sesión persistente en un equipo remoto. En el ejemplo siguiente se crean sesiones remotas en Server01 y Server02. Los objetos de la sesión se almacenan en la variable `$s`.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Ahora que las sesiones se han establecido, puede ejecutar cualquier comando en ellas. Y, como las sesiones son persistentes, puede recopilar datos en un solo comando y usarlos en un otro comando.

Por ejemplo, el siguiente comando ejecuta un comando Get-Hotfix en las sesiones de la variable $s y guarda los resultados en la variable $h. La variable $h se crea en cada una de las sesiones en $s, pero no existe en la sesión local.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Ahora puede usar los datos de la variable `$h` con otros comandos en la misma sesión. Los resultados se muestran en el equipo local. Por ejemplo:

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Comunicación remota avanzada

La administración remota de Windows PowerShell empieza aquí. Con los cmdlets que se instalan con Windows PowerShell puede, entre otras muchas cosas, establecer y configurar sesiones remotas desde extremos tanto locales como remotos, crear sesiones personalizadas y restringidas, dejar que los usuarios importen comandos desde una sesión remota que se ejecutan implícitamente en la sesión remota o configurar la seguridad de una sesión remota.

Windows PowerShell incluye un proveedor de WSMan. El proveedor crea una unidad `WSMAN:` que le permite desplazarse por una jerarquía de valores de configuración en el equipo local y en los equipos remotos.

Para más información sobre el proveedor de WSMan, consulte [Proveedor de WSMan](https://technet.microsoft.com/library/dd819476.aspx) y [About WS-Management Cmdlets (Acerca de los cmdlets de WS-Management)](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets). También puede escribir `Get-Help wsman` en la consola de Windows PowerShell.

Para obtener más información, consulte:

- [Acerca de las Preguntas más frecuentes sobre el acceso remoto](https://technet.microsoft.com/library/dd315359.aspx)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)

Para obtener ayuda con los errores de comunicación remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).

## <a name="see-also"></a>Véase también

- [about_Remote](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [about_Remote_FAQ](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [about_Remote_Requirements](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [about_Remote_Troubleshooting](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [about_PSSessions](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [about_WS-Management_Cmdlets](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Proveedor de WSMan](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
