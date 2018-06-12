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
# <a name="running-remote-commands"></a>Ejecutar comandos remotos

Puede ejecutar comandos en un equipo o en cientos de ellos usando un solo comando de Windows PowerShell. Windows PowerShell admite la informática remota a través de varias tecnologías, como WS-Management, RPC y WMI.

## <a name="remoting-in-powershell-core"></a>Comunicación remota en PowerShell Core

PowerShell Core, la edición más reciente de PowerShell en Windows, macOS y Linux, es compatible con WMI, WS-Management y la comunicación remota mediante SSH.
(Ya no se admite RPC).

Para más información sobre la configuración, vea:

* [Comunicación remota mediante SSH en PowerShell Core][ssh-remoting]
* [Comunicación remota mediante WSMan en PowerShell Core][wsman-remoting]

## <a name="remoting-without-configuration"></a>Comunicación remota sin configuración

Muchos de los cmdlets de Windows PowerShell tienen un parámetro ComputerName que les permite recopilar datos y cambiar la configuración de uno o más equipos remotos. Usan distintas tecnologías de comunicación y muchos de ellos funcionan con todos los sistemas operativos de Windows que Windows PowerShell admite sin necesidad de ninguna configuración especial.

Estos cmdlets son:

* [Restart-Computer](https://go.microsoft.com/fwlink/?LinkId=821625)
* [Test-Connection](https://go.microsoft.com/fwlink/?LinkId=821646)
* [Clear-EventLog](https://go.microsoft.com/fwlink/?LinkId=821568)
* [Get-EventLog](https://go.microsoft.com/fwlink/?LinkId=821585)
* [Get-HotFix](https://go.microsoft.com/fwlink/?LinkId=821586)
* [Get-Process](https://go.microsoft.com/fwlink/?linkid=821590)
* [Get-Service](https://go.microsoft.com/fwlink/?LinkId=821593)
* [Set-Service](https://go.microsoft.com/fwlink/?LinkId=821633)
* [Get-WinEvent](https://go.microsoft.com/fwlink/?linkid=821529)
* [Get-WmiObject](https://go.microsoft.com/fwlink/?LinkId=821595)

Normalmente, los cmdlets que admiten la comunicación remota sin una configuración especial tienen un parámetro ComputerName y carecen de un parámetro Session. Para encontrar estos cmdlets en la sesión, escriba:

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a>Comunicación remota de Windows PowerShell

La comunicación remota de Windows PowerShell, que usa el protocolo WS-Management, permite ejecutar cualquier comando de Windows PowerShell en uno o varios equipos remotos. Así, permite establecer conexiones persistentes, iniciar sesiones interactivas de 1:1 y ejecutar scripts en varios equipos.

Para usar la comunicación remota de Windows PowerShell, el equipo remoto debe estar configurado para la administración remota. Para más información y ver instrucciones, consulte [About Remote Requirements](https://technet.microsoft.com/library/dd315349.aspx) (Acerca de los requisitos remotos).

Después de configurar la comunicación remota de Windows PowerShell, tendrá a su disposición un gran número de estrategias de comunicación remota. En lo que resta de este documento se mencionan solo algunas de ellas. Para más información, vea [About Remote](https://technet.microsoft.com/library/dd347744.aspx) (Acerca del acceso remoto) y [About Remote FAQ](https://technet.microsoft.com/library/dd347744.aspx) (Preguntas más frecuentes sobre el acceso remoto).

### <a name="start-an-interactive-session"></a>Iniciar una sesión interactiva

Para iniciar una sesión interactiva con un único equipo remoto, use el cmdlet [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477).
Por ejemplo, para iniciar una sesión interactiva con el equipo remoto Server01, escriba:

```powershell
Enter-PSSession Server01
```

El símbolo del sistema cambia para mostrar el nombre del equipo al que está conectado. Desde ese momento, cualquier comando que escriba en el símbolo del sistema se ejecutará en el equipo remoto y los resultados se mostrarán en el equipo local.

Para finalizar la sesión interactiva, escriba:

```powershell
Exit-PSSession
```

Para más información sobre los cmdlets Enter-PSSession y Exit-PSSession, vea [Enter-PSSession](https://go.microsoft.com/fwlink/?LinkId=821477) y [Exit-PSSession](https://go.microsoft.com/fwlink/?LinkID=821478).

### <a name="run-a-remote-command"></a>Ejecutar un comando remoto

Para ejecutar cualquier comando en uno o varios equipos remotos, use el cmdlet [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).
Por ejemplo, para ejecutar un comando [Get-UICulture](https://go.microsoft.com/fwlink/?LinkId=821806) en los equipos remotos Server01 y Server02, escriba:

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

Para más información sobre el cmdlet Invoke-Command, vea [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="run-a-script"></a>Ejecutar un script

Para ejecutar un script en uno o varios equipos remotos, use el parámetro FilePath del cmdlet Invoke-Command. El script debe estar en el equipo local o accesible desde este. Los resultados se devuelven en el equipo local.

Por ejemplo, el siguiente comando ejecuta el script DiskCollect.ps1 en los equipos remotos Server01 y Server02.

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

Para más información sobre el cmdlet Invoke-Command, vea [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493).

### <a name="establish-a-persistent-connection"></a>Establecer una conexión persistente

Para ejecutar una serie de comandos relacionados que comparten datos, crear una sesión en el equipo remoto y, a continuación, use el cmdlet Invoke-Command para ejecutar comandos en la sesión que cree. Para crear una sesión remota, use el cmdlet New-PSSession.

Por ejemplo, el comando siguiente crea una sesión remota en el equipo Server01 y otra sesión remota en el equipo Server02. Guarda los objetos de la sesión en la variable $s.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

Ahora que las sesiones se han establecido, puede ejecutar cualquier comando en ellas. Y, como las sesiones son persistentes, puede recopilar datos en un solo comando y usarlos en un comando posterior.

Por ejemplo, el siguiente comando ejecuta un comando Get-Hotfix en las sesiones de la variable $s y guarda los resultados en la variable $h. La variable $h se crea en cada una de las sesiones en $s, pero no existe en la sesión local.

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

Ahora puede usar los datos de la variable $h en los siguientes comandos, como en el siguiente. Los resultados se muestran en el equipo local.

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a>Comunicación remota avanzada

La administración remota de Windows PowerShell empieza aquí. Con los cmdlets que se instalan con Windows PowerShell puede, entre otras muchas cosas, establecer y configurar sesiones remotas desde extremos tanto locales como remotos, crear sesiones personalizadas y restringidas, dejar que los usuarios importen comandos desde una sesión remota que se ejecutan implícitamente en la sesión remota o configurar la seguridad de una sesión remota.

Para facilitar la configuración remota, Windows PowerShell incluye un proveedor WSMan. La unidad WSMAN: que este proveedor crea permite desplazarse por una jerarquía de valores de configuración en el equipo local y en los equipos remotos.
Para obtener más información sobre el proveedor WSMan, vea el tema sobre el [proveedor WSMan](https://technet.microsoft.com/library/dd819476.aspx) y el tema [About WS-Management Cmdlets](https://technet.microsoft.com/library/dd819481.aspx) (Acerca de los cmdlets de WS-Management). También puede escribir "Get-Help wsman" en la consola de Windows PowerShell.

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
- [Invoke-Command](https://go.microsoft.com/fwlink/?LinkId=821493)
- [Import-PSSession](https://go.microsoft.com/fwlink/?LinkId=821821)
- [New-PSSession](https://go.microsoft.com/fwlink/?LinkId=821498)
- [Register-PSSessionConfiguration](https://go.microsoft.com/fwlink/?LinkId=821508)
- [Proveedor de WSMan](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md