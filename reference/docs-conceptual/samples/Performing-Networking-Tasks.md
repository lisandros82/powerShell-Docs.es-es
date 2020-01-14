---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Realizar tareas de redes
ms.openlocfilehash: e0aa3b8ef3d911ab0fe851f6621d70e1265c5bd4
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737209"
---
# <a name="performing-networking-tasks"></a>Realizar tareas de redes

Dado que TCP/IP es el protocolo de red más usado, la mayoría de las tareas de administración de protocolo de red de bajo nivel implican TCP/IP. En esta sección, se usan PowerShell y WMI para realizar estas tareas.

## <a name="listing-ip-addresses-for-a-computer"></a>Enumerar las direcciones IP de un equipo

Para obtener todas las direcciones IP en uso en el equipo local, use el siguiente comando:

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExpandProperty IPAddress
```

La salida de este comando difiere de la mayoría de las listas de propiedades porque los valores están entre llaves:

```Output
10.0.0.1
fe80::60ea:29a7:a233:7cb7
2601:600:a27f:a470:f532:6451:5630:ec8b
2601:600:a27f:a470:e167:477d:6c5c:342d
2601:600:a27f:a470:b021:7f0d:eab9:6299
2601:600:a27f:a470:a40e:ebce:1a8c:a2f3
2601:600:a27f:a470:613c:12a2:e0e0:bd89
2601:600:a27f:a470:444f:17ec:b463:7edd
2601:600:a27f:a470:10fd:7063:28e9:c9f3
2601:600:a27f:a470:60ea:29a7:a233:7cb7
2601:600:a27f:a470::2ec1
```

Para entender por qué aparecen las llaves, use el cmdlet `Get-Member` para examinar la propiedad **IPAddress**:

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Get-Member -Name IPAddress
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_NetworkAdapterConfiguration
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   string[] IPAddress {get;}
```

La propiedad IPAddress de cada adaptador de red es en realidad una matriz. Las llaves de la definición indican que **IPAddress** no es un valor **System.String**, sino una matriz de valores **System.String**.

## <a name="listing-ip-configuration-data"></a>Enumerar datos de configuración de IP

Para mostrar datos detallados de configuración de IP de cada adaptador de red, use el siguiente comando:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true
```

La visualización predeterminada del objeto de configuración del adaptador de red es un conjunto muy reducido de datos disponibles. Para la inspección en profundidad y la solución de problemas, use `Select-Object` o un cmdlet de formato, como `Format-List`, para especificar las propiedades que se mostrarán.

En redes TCP/IP modernas, probablemente no le interesan las propiedades IPX o WINS. Puede usar el parámetro **ExcludeProperty** de `Select-Object` para ocultar las propiedades con nombres que comienzan por "WINS" o "IPX".

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExcludeProperty IPX*,WINS*
```

Este comando devuelve información detallada acerca de DHCP, DNS, el enrutamiento y otras propiedades de configuración de IP secundarias.

## <a name="pinging-computers"></a>Hacer ping de equipos

Puede hacer ping simplemente en un equipo mediante **Win32_PingStatus**. El comando siguiente hace ping, pero devuelve una salida larga:

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'"
```

Un formato más útil de información resumida de la presentación de las propiedades Address, ResponseTime y StatusCode, como el que genera el siguiente comando. El parámetro **Autosize** de `Format-Table` cambia el tamaño de las columnas de la tabla para que se muestren correctamente en PowerShell.

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'" |
  Format-Table -Property Address,ResponseTime,StatusCode -Autosize
```

```Output
Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

Un StatusCode de 0 indica un ping correcto.

Puede usar una matriz para hacer ping a varios equipos con un solo comando. Dado que hay más de una dirección, use `ForEach-Object` para hacer ping a cada dirección por separado:

```powershell
'127.0.0.1','localhost','research.microsoft.com' |
  ForEach-Object -Process {
    Get-CimInstance -Class Win32_PingStatus -Filter ("Address='$_'") |
      Select-Object -Property Address,ResponseTime,StatusCode
  }
```

Puede usar el mismo formato de comando para hacer ping a todos los equipos de una subred, como una red privada que use el número de red 192.168.1.0 y una máscara de subred de clase C estándar (255.255.255.0). Solo las direcciones del intervalo de 192.168.1.1 a 192.168.1.254 son direcciones locales legítimas (0 se reserva siempre al número de red y 255 es una dirección de difusión de subred).

Para representar una matriz de los números del 1 al 254 en PowerShell, use la instrucción **1..254**.
Para hacer ping a una subred completa se puede generar la matriz y, a continuación, agregar los valores en una dirección parcial en la instrucción ping:

```powershell
1..254| ForEach-Object -Process {
  Get-CimInstance -Class Win32_PingStatus -Filter ("Address='192.168.1.$_ '") } |
    Select-Object -Property Address,ResponseTime,StatusCode
```

Tenga en cuenta que esta técnica para generar un intervalo de direcciones puede usarse también en otras ubicaciones. Puede generar un conjunto completo de direcciones de esta manera:

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a>Recuperar las propiedades del adaptador de red

Anteriormente, mencionamos que podía recuperar las propiedades de configuración general mediante la clase **Win32_NetworkAdapterConfiguration**. Aunque no sea estrictamente información de TCP/IP, la información del adaptador de red, como las direcciones MAC y los tipos de adaptador, puede ser útil para comprender lo que ocurre con un equipo. Para obtener un resumen de esta información, use el siguiente comando:

```powershell
Get-CimInstance -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Asignación del dominio DNS de un adaptador de red

Para asignar el dominio DNS para la resolución de nombres automática, use el método **SetDNSDomain** de **Win32_NetworkAdapterConfiguration**. Dado que el dominio DNS se asigna para cada configuración de adaptador de red de manera independiente, debe usar una instrucción `ForEach-Object` para asignar el dominio a cada adaptador:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process { $_.SetDNSDomain('fabrikam.com') }
```

Se necesita la instrucción de filtrado `IPEnabled=$true`, ya que, incluso en una red que solo usa TCP/IP, varias de las configuraciones de adaptador de red de un equipo no corresponden a adaptadores TCP/IP reales; son elementos de software generales que admiten RAS, PPTP, QoS y otros servicios para todos los adaptadores y, por tanto, no tienen una dirección propia.

Puede filtrar el comando mediante el cmdlet `Where-Object`, en lugar de usar el filtro `Get-CimInstance`.

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration |
  Where-Object {$_.IPEnabled} |
    ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a>Realizar tareas de configuración de DHCP

La modificación de detalles de DHCP implica trabajar con un conjunto de adaptadores de red, igual que en la configuración de DNS. Existen varias acciones distintas que se pueden realizar mediante WMI. Veremos las más comunes.

### <a name="determining-dhcp-enabled-adapters"></a>Determinar los adaptadores con DHCP habilitado

Para buscar los adaptadores con DHCP habilitado en un equipo, use el siguiente comando:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true"
```

Para excluir los adaptadores con problemas de configuración de IP, puede recuperar solo los adaptadores con IP habilitada:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true"
```

### <a name="retrieving-dhcp-properties"></a>Recuperar propiedades de DHCP

Dado que las propiedades relacionadas con DHCP de un adaptador suelen empezar por `DHCP`, puede usar el parámetro Property de `Format-Table` para mostrar solo esas propiedades:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" |
  Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a>Habilitar DHCP en cada adaptador

Para habilitar DHCP en todos los adaptadores, use el siguiente comando:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process {$_.EnableDHCP()}
```

Puede usar la instrucción **Filter** `IPEnabled=$true and DHCPEnabled=$false` para evitar tener que habilitar DHCP si ya está habilitado, aunque la omisión de este paso no provocará errores.

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Liberar y renovar las concesiones DHCP en adaptadores específicos

La clase **Win32_NetworkAdapterConfiguration** tiene los métodos **ReleaseDHCPLease** y **RenewDHCPLease**. Ambos se usan de la misma manera. En general, use estos métodos si solo necesita liberar o renovar direcciones de un adaptador en una subred específica. La manera más fácil de filtrar adaptadores en una subred es elegir solo las configuraciones de adaptador que usen la puerta de enlace para esa subred. Por ejemplo, el comando siguiente libera todas las concesiones DHCP de los adaptadores en el equipo local que obtienen concesiones DHCP de 192.168.1.254:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

El único cambio en la renovación de una concesión DHCP es que se usa el método **RenewDHCPLease** en lugar del método **ReleaseDHCPLease**:

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Al usar estos métodos en un equipo remoto, tenga en cuenta que puede perder el acceso al sistema remoto si está conectados a este a través del adaptador con la concesión liberada o renovada.

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Liberar y renovar las concesiones DHCP en todos los adaptadores

Puede realizar liberaciones o renovaciones de direcciones DHCP en todos los adaptadores mediante los métodos **ReleaseDHCPLeaseAll** y **RenewDHCPLeaseAll** de la clase **Win32_NetworkAdapterConfiguration**.
Sin embargo, el comando se debe aplicar a la clase WMI, en lugar de a un adaptador determinado, porque liberar y renovar concesiones globalmente se realiza en la clase, no en un adaptador específico.

Puede obtener una referencia a una clase WMI, en lugar de instancias de clase. Para ello, enumere todas las clases WMI y, a continuación, seleccione solo la clase deseada por nombre. Por ejemplo, el comando siguiente devuelve la clase **Win32_NetworkAdapterConfiguration**:

```powershell
Get-CimInstance -List | Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

Puede tratar todo el comando como la clase y, después, invocar en este el método **ReleaseDHCPAdapterLease**. En el siguiente comando, los paréntesis que rodean los elementos de la canalización `Get-CimInstance` y `Where-Object` indican a PowerShell que los evalúe primero:

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).ReleaseDHCPLeaseAll()
```

Puede usar el mismo formato de comando para invocar el método **RenewDHCPLeaseAll**:

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a>Crear un recurso compartido de red

Para crear un recurso compartido de red, use el método **Create** de **Win32_Share**:

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_Share'}).Create(
    'C:\temp','TempShare',0,25,'test share of the temp folder'
  )
```

También puede crear el recurso compartido mediante el uso de `net share` en PowerShell en Windows:

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a>Quitar un recurso compartido de red

Puede quitar un recurso compartido de red con **Win32_Share**, pero el proceso es ligeramente diferente del de creación de un recurso compartido, porque debe recuperar el recurso compartido específico que quiere quitar, en lugar de la clase **Win32_Share**. La instrucción siguiente elimina el recurso compartido **TempShare**:

```powershell
(Get-CimInstance -Class Win32_Share -Filter "Name='TempShare'").Delete()
```

En Windows, `net share` funciona también:

```powershell
net share tempshare /delete
```

```Output
tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a>Conectar una unidad de red accesible de Windows

El cmdlet `New-PSDrive` crea una unidad de PowerShell, pero las unidades creadas de esta manera solo están disponibles para PowerShell. Para crear una nueva unidad en red, puede usar el objeto COM **WScript.Network**. El siguiente comando asigna el recurso compartido `\\FPS01\users` a la unidad local `B:`:

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

En Windows, el comando `net use` funciona también:

```powershell
net use B: \\FPS01\users
```

Las unidades asignadas con **WScript.Network** o `net use` están disponibles inmediatamente para PowerShell.
