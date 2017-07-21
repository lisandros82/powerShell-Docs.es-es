---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Realizar tareas de redes
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 4d7a91595b9d9d637ce915be2c2be9c20879dd8b
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="db18c-103">Realizar tareas de redes</span><span class="sxs-lookup"><span data-stu-id="db18c-103">Performing Networking Tasks</span></span>
<span data-ttu-id="db18c-104">Dado que TCP/IP es el protocolo de red más usado, la mayoría de las tareas de administración de protocolo de red de bajo nivel implican TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="db18c-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="db18c-105">En esta sección, se usan Windows PowerShell y WMI para realizar estas tareas.</span><span class="sxs-lookup"><span data-stu-id="db18c-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

### <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="db18c-106">Enumerar las direcciones IP de un equipo</span><span class="sxs-lookup"><span data-stu-id="db18c-106">Listing IP Addresses for a Computer</span></span>
<span data-ttu-id="db18c-107">Para obtener todas las direcciones IP en uso en el equipo local, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="db18c-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="db18c-108">La salida de este comando difiere de la mayoría de las listas de propiedades porque los valores están entre llaves:</span><span class="sxs-lookup"><span data-stu-id="db18c-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

<a name="preipaddress"></a><pre>IPAddress
---------
<span data-ttu-id="db18c-109">{192.168.1.80} {192.168.148.1} {192.168.171.1} {0.0.0.0}</span><span class="sxs-lookup"><span data-stu-id="db18c-109">{192.168.1.80} {192.168.148.1} {192.168.171.1} {0.0.0.0}</span></span></pre>

<span data-ttu-id="db18c-110">Para entender por qué aparecen las llaves, use el cmdlet Get-Member para examinar la propiedad **IPAddress**:</span><span class="sxs-lookup"><span data-stu-id="db18c-110">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

<pre>PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Get-Member -Name IPAddress
TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapter
Configuration
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}</pre>

<span data-ttu-id="db18c-111">La propiedad IPAddress de cada adaptador de red es en realidad una matriz.</span><span class="sxs-lookup"><span data-stu-id="db18c-111">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="db18c-112">Las llaves de la definición indican que **IPAddress** no es un valor **System.String**, sino una matriz de valores **System.String**.</span><span class="sxs-lookup"><span data-stu-id="db18c-112">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

### <a name="listing-ip-configuration-data"></a><span data-ttu-id="db18c-113">Enumerar datos de configuración de IP</span><span class="sxs-lookup"><span data-stu-id="db18c-113">Listing IP Configuration Data</span></span>
<span data-ttu-id="db18c-114">Para mostrar datos detallados de configuración de IP de cada adaptador de red, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="db18c-114">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName .
```

<span data-ttu-id="db18c-115">La visualización predeterminada del objeto de configuración del adaptador de red es un conjunto muy reducido de datos disponibles.</span><span class="sxs-lookup"><span data-stu-id="db18c-115">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="db18c-116">Para la inspección en profundidad y la solución de problemas, use Select-Object o un cmdlet de formato, como Format-List, para especificar las propiedades que se mostrarán.</span><span class="sxs-lookup"><span data-stu-id="db18c-116">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="db18c-117">Si no está interesado en las propiedades IPX o WINS, probablemente el caso de una red TCP/IP moderna, puede usar el parámetro ExcludeProperty de Select-Object para ocultar las propiedades con nombres que comiencen por "WINS" o "IPX":</span><span class="sxs-lookup"><span data-stu-id="db18c-117">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="db18c-118">Este comando devuelve información detallada acerca de DHCP, DNS, el enrutamiento y otras propiedades de configuración de IP secundarias.</span><span class="sxs-lookup"><span data-stu-id="db18c-118">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

### <a name="pinging-computers"></a><span data-ttu-id="db18c-119">Hacer ping de equipos</span><span class="sxs-lookup"><span data-stu-id="db18c-119">Pinging Computers</span></span>
<span data-ttu-id="db18c-120">Puede hacer ping simplemente en un equipo mediante **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="db18c-120">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="db18c-121">El comando siguiente hace ping, pero devuelve una salida larga:</span><span class="sxs-lookup"><span data-stu-id="db18c-121">The following command performs the ping, but returns lengthy output:</span></span>

```
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="db18c-122">Un formato más útil de información resumida de la presentación de las propiedades Address, ResponseTime y StatusCode, como el que genera el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="db18c-122">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="db18c-123">El parámetro Autosize de Format-Table cambia el tamaño de las columnas de la tabla para que se muestren correctamente en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db18c-123">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
A status code of 0 indicates a successful ping.
```

<span data-ttu-id="db18c-124">Puede usar una matriz para hacer ping a varios equipos con un solo comando.</span><span class="sxs-lookup"><span data-stu-id="db18c-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="db18c-125">Dado que hay más de una dirección, use **ForEach_OBject** para hacer ping a cada dirección por separado:</span><span class="sxs-lookup"><span data-stu-id="db18c-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```
"127.0.0.1","localhost","research.microsoft.com" | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="db18c-126">Puede usar el mismo formato de comando para hacer ping a todos los equipos de una subred, como una red privada que use el número de red 192.168.1.0 y una máscara de subred de clase C estándar (255.255.255.0). Solo las direcciones del intervalo de 192.168.1.1 a 192.168.1.254 son direcciones locales legítimas (0 se reserva siempre al número de red y 255 es una dirección de difusión de subred).</span><span class="sxs-lookup"><span data-stu-id="db18c-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="db18c-127">Para representar una matriz de los números del 1 al 254 en Windows PowerShell, use la instrucción **1..254.**</span><span class="sxs-lookup"><span data-stu-id="db18c-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="db18c-128">Para hacer ping a una subred completa se puede generar la matriz y, a continuación, agregar los valores en una dirección parcial en la instrucción ping:</span><span class="sxs-lookup"><span data-stu-id="db18c-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="db18c-129">Tenga en cuenta que esta técnica para generar un intervalo de direcciones puede usarse también en otras ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="db18c-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="db18c-130">Puede generar un conjunto completo de direcciones de esta manera:</span><span class="sxs-lookup"><span data-stu-id="db18c-130">You can generate a complete set of addresses in this way:</span></span>

`$ips = 1..254 | ForEach-Object -Process {"192.168.1." + $_}`

### <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="db18c-131">Recuperar las propiedades del adaptador de red</span><span class="sxs-lookup"><span data-stu-id="db18c-131">Retrieving Network Adapter Properties</span></span>
<span data-ttu-id="db18c-132">Anteriormente en esta guía de usuario, mencionamos que podía recuperar las propiedades de configuración general mediante **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="db18c-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="db18c-133">Aunque no sea estrictamente información de TCP/IP, la información del adaptador de red, como las direcciones MAC y los tipos de adaptador, puede ser útil para comprender lo que ocurre con un equipo.</span><span class="sxs-lookup"><span data-stu-id="db18c-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="db18c-134">Para obtener un resumen de esta información, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="db18c-134">To get a summary of this information, use the following command:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="db18c-135">Asignación del dominio DNS de un adaptador de red</span><span class="sxs-lookup"><span data-stu-id="db18c-135">Assigning the DNS Domain for a Network Adapter</span></span>
<span data-ttu-id="db18c-136">Para asignar el dominio DNS para la resolución de nombres automática, use el método **Win32_NetworkAdapterConfiguration SetDNSDomain**.</span><span class="sxs-lookup"><span data-stu-id="db18c-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="db18c-137">Dado que el dominio DNS se asigna para cada configuración de adaptador de red de manera independiente, debe usar una instrucción **ForEach-Object** para asignar el dominio a cada adaptador:</span><span class="sxs-lookup"><span data-stu-id="db18c-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain("fabrikam.com") }
```

<span data-ttu-id="db18c-138">La instrucción de filtrado "IPEnabled\=true" es necesaria, ya que, incluso en una red que use solo TCP/IP, varias de las configuraciones de adaptador de red de un equipo no son adaptadores TCP/IP reales; son elementos de software generales que admiten RAS, PPTP, QoS y otros servicios para todos los adaptadores y, por tanto, no tienen una dirección propia.</span><span class="sxs-lookup"><span data-stu-id="db18c-138">The filtering statement "IPEnabled=true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="db18c-139">Puede filtrar el comando mediante el cmdlet **Where-Object**, en lugar de usar el filtro **Get-WmiObject**.</span><span class="sxs-lookup"><span data-stu-id="db18c-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain("fabrikam.com")}
```

### <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="db18c-140">Realizar tareas de configuración de DHCP</span><span class="sxs-lookup"><span data-stu-id="db18c-140">Performing DHCP Configuration Tasks</span></span>
<span data-ttu-id="db18c-141">La modificación de detalles de DHCP implica trabajar con un conjunto de adaptadores de red, igual que en la configuración de DNS.</span><span class="sxs-lookup"><span data-stu-id="db18c-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="db18c-142">Existen varias acciones distintas que se pueden realizar mediante WMI. Veremos las más comunes.</span><span class="sxs-lookup"><span data-stu-id="db18c-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

#### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="db18c-143">Determinar los adaptadores con DHCP habilitado</span><span class="sxs-lookup"><span data-stu-id="db18c-143">Determining DHCP-Enabled Adapters</span></span>
<span data-ttu-id="db18c-144">Para buscar los adaptadores con DHCP habilitado en un equipo, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="db18c-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName .
```

<span data-ttu-id="db18c-145">Para excluir los adaptadores con problemas de configuración de IP, puede recuperar solo los adaptadores con IP habilitada:</span><span class="sxs-lookup"><span data-stu-id="db18c-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="db18c-146">Recuperar propiedades de DHCP</span><span class="sxs-lookup"><span data-stu-id="db18c-146">Retrieving DHCP Properties</span></span>
<span data-ttu-id="db18c-147">Dado que las propiedades relacionadas con DHCP de un adaptador suelen empezar por "DHCP", puede usar el parámetro Property de Format-Table para mostrar solo esas propiedades:</span><span class="sxs-lookup"><span data-stu-id="db18c-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="db18c-148">Habilitar DHCP en cada adaptador</span><span class="sxs-lookup"><span data-stu-id="db18c-148">Enabling DHCP on Each Adapter</span></span>
<span data-ttu-id="db18c-149">Para habilitar DHCP en todos los adaptadores, use el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="db18c-149">To enable DHCP on all adapters, use the following command:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="db18c-150">Puede usar la instrucción **Filter** "IPEnabled\=true y DHCPEnabled\=false" para evitar tener que habilitar DHCP si ya está habilitado, aunque la omisión de este paso no provocará errores.</span><span class="sxs-lookup"><span data-stu-id="db18c-150">You can use the **Filter** statement "IPEnabled=true and DHCPEnabled=false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="db18c-151">Liberar y renovar las concesiones DHCP en adaptadores específicos</span><span class="sxs-lookup"><span data-stu-id="db18c-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>
<span data-ttu-id="db18c-152">La clase **Win32_NetworkAdapterConfiguration** tiene los métodos **ReleaseDHCPLease** y **RenewDHCPLease**.</span><span class="sxs-lookup"><span data-stu-id="db18c-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="db18c-153">Ambos se usan de la misma manera.</span><span class="sxs-lookup"><span data-stu-id="db18c-153">Both are used in the same way.</span></span> <span data-ttu-id="db18c-154">En general, use estos métodos si solo necesita liberar o renovar direcciones de un adaptador en una subred específica.</span><span class="sxs-lookup"><span data-stu-id="db18c-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="db18c-155">La manera más fácil de filtrar adaptadores en una subred es elegir solo las configuraciones de adaptador que usen la puerta de enlace para esa subred.</span><span class="sxs-lookup"><span data-stu-id="db18c-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="db18c-156">Por ejemplo, el comando siguiente libera todas las concesiones DHCP de los adaptadores en el equipo local que obtienen concesiones DHCP de 192.168.1.254:</span><span class="sxs-lookup"><span data-stu-id="db18c-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="db18c-157">El único cambio en la renovación de una concesión DHCP es que se usa el método **RenewDHCPLease** en lugar del método **ReleaseDHCPLease**:</span><span class="sxs-lookup"><span data-stu-id="db18c-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="db18c-158">Al usar estos métodos en un equipo remoto, tenga en cuenta que puede perder el acceso al sistema remoto si está conectados a este a través del adaptador con la concesión liberada o renovada.</span><span class="sxs-lookup"><span data-stu-id="db18c-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="db18c-159">Liberar y renovar las concesiones DHCP en todos los adaptadores</span><span class="sxs-lookup"><span data-stu-id="db18c-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>
<span data-ttu-id="db18c-160">Puede realizar liberaciones o renovaciones de direcciones DHCP en todos los adaptadores mediante los métodos **ReleaseDHCPLeaseAll** y **RenewDHCPLeaseAll** de la clase **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="db18c-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="db18c-161">Sin embargo, el comando se debe aplicar a la clase WMI, en lugar de a un adaptador determinado, porque liberar y renovar concesiones globalmente se realiza en la clase, no en un adaptador específico.</span><span class="sxs-lookup"><span data-stu-id="db18c-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="db18c-162">Puede obtener una referencia a una clase WMI, en lugar de instancias de clase. Para ello, enumere todas las clases WMI y, a continuación, seleccione solo la clase deseada por nombre.</span><span class="sxs-lookup"><span data-stu-id="db18c-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="db18c-163">Por ejemplo, el siguiente comando devuelve la clase Win32_NetworkAdapterConfiguration:</span><span class="sxs-lookup"><span data-stu-id="db18c-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"}
```

<span data-ttu-id="db18c-164">Puede tratar todo el comando como la clase y, después, invocar en este el método **ReleaseDHCPAdapterLease**.</span><span class="sxs-lookup"><span data-stu-id="db18c-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="db18c-165">En el siguiente comando, los paréntesis que rodean los elementos de la canalización **Get-WmiObject** y **Where-Object** indican a Windows PowerShell que los evalúe primero:</span><span class="sxs-lookup"><span data-stu-id="db18c-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="db18c-166">Puede usar el mismo formato de comando para invocar el método **RenewDHCPLeaseAll**:</span><span class="sxs-lookup"><span data-stu-id="db18c-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a><span data-ttu-id="db18c-167">Crear un recurso compartido de red</span><span class="sxs-lookup"><span data-stu-id="db18c-167">Creating a Network Share</span></span>
<span data-ttu-id="db18c-168">Para crear un recurso compartido de red, use el método **Win32_Share Create**:</span><span class="sxs-lookup"><span data-stu-id="db18c-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Win32_Share"}).Create("C:\temp","TempShare",0,25,"test share of the temp folder")
```

<span data-ttu-id="db18c-169">También puede crear el recurso compartido mediante **net share** en Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="db18c-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a><span data-ttu-id="db18c-170">Quitar un recurso compartido de red</span><span class="sxs-lookup"><span data-stu-id="db18c-170">Removing a Network Share</span></span>
<span data-ttu-id="db18c-171">Puede quitar un recurso compartido de red con **Win32_Share**, pero el proceso es ligeramente diferente del de creación de un recurso compartido, porque debe recuperar el recurso compartido específico que quiere quitar, en lugar de la clase **Win32_Share**.</span><span class="sxs-lookup"><span data-stu-id="db18c-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="db18c-172">La instrucción siguiente elimina el recurso compartido "TempShare":</span><span class="sxs-lookup"><span data-stu-id="db18c-172">The following statement deletes the share "TempShare":</span></span>

```
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="db18c-173">**Net share** también funciona:</span><span class="sxs-lookup"><span data-stu-id="db18c-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete
tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="db18c-174">Conectar una unidad de red accesible de Windows</span><span class="sxs-lookup"><span data-stu-id="db18c-174">Connecting a Windows Accessible Network Drive</span></span>
<span data-ttu-id="db18c-175">El cmdlet **New-PSDrive** crea una unidad de Windows PowerShell, pero las unidades creadas de esta manera solo están disponibles para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db18c-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="db18c-176">Para crear una nueva unidad en red, puede usar el objeto COM **WScript.Network**.</span><span class="sxs-lookup"><span data-stu-id="db18c-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="db18c-177">El siguiente comando asigna el recurso compartido \\\\FPS01\\users a la unidad local B:</span><span class="sxs-lookup"><span data-stu-id="db18c-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```
(New-Object -ComObject WScript.Network).MapNetworkDrive("B:", "\\FPS01\users")
```

<span data-ttu-id="db18c-178">El comando **net use** también funciona:</span><span class="sxs-lookup"><span data-stu-id="db18c-178">The **net use** command works as well:</span></span>

```
net use B: \\FPS01\users
```

<span data-ttu-id="db18c-179">Las unidades asignadas con **WScript.Network** o net use están disponibles inmediatamente para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db18c-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>

