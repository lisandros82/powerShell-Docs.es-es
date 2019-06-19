---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Administración de servicios
ms.openlocfilehash: d9e17b2d91ae01d7d4d6d573348289fa68dc9c56
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030168"
---
# <a name="managing-services"></a><span data-ttu-id="95094-103">Administración de servicios</span><span class="sxs-lookup"><span data-stu-id="95094-103">Managing Services</span></span>

<span data-ttu-id="95094-104">Existen ocho cmdlets Service principales, diseñados para una amplia gama de tareas de servicio.</span><span class="sxs-lookup"><span data-stu-id="95094-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="95094-105">Solo veremos la enumeración y el cambio del estado de ejecución de los servicios, pero puede obtener una lista de cmdlets Service mediante `Get-Help \*-Service`. También puede encontrar información sobre cada cmdlet Service mediante `Get-Help <Cmdlet-Name>`, como `Get-Help New-Service`.</span><span class="sxs-lookup"><span data-stu-id="95094-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="95094-106">Obtener servicios</span><span class="sxs-lookup"><span data-stu-id="95094-106">Getting Services</span></span>

<span data-ttu-id="95094-107">Puede obtener los servicios en un equipo local o remoto mediante el cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="95094-107">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="95094-108">Del mismo modo que ocurre con `Get-Process`, si usa el comando `Get-Service` sin parámetros, se devolverán todos los servicios.</span><span class="sxs-lookup"><span data-stu-id="95094-108">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="95094-109">Puede filtrar por nombre, incluso con un asterisco como carácter comodín:</span><span class="sxs-lookup"><span data-stu-id="95094-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="95094-110">Dado que no siempre es evidente cuál es el nombre real del servicio, es posible que necesite buscar servicios por el nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="95094-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="95094-111">Puede hacerlo por el nombre específico, mediante caracteres comodín o con una lista de nombres para mostrar:</span><span class="sxs-lookup"><span data-stu-id="95094-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="95094-112">Puede usar el parámetro ComputerName del cmdlet Get-Service para obtener los servicios en equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="95094-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="95094-113">El parámetro ComputerName acepta varios valores y caracteres comodín, por lo que puede obtener los servicios en varios equipos con un solo comando.</span><span class="sxs-lookup"><span data-stu-id="95094-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="95094-114">Por ejemplo, el siguiente comando obtiene los servicios en el equipo remoto Server01.</span><span class="sxs-lookup"><span data-stu-id="95094-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="95094-115">Obtener servicios necesarios y dependientes</span><span class="sxs-lookup"><span data-stu-id="95094-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="95094-116">El cmdlet Get-Service tiene dos parámetros que son muy útiles para la administración de servicios.</span><span class="sxs-lookup"><span data-stu-id="95094-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="95094-117">El parámetro DependentServices obtiene servicios que dependen del servicio.</span><span class="sxs-lookup"><span data-stu-id="95094-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="95094-118">El parámetro RequiredServices obtiene servicios de los que depende este servicio.</span><span class="sxs-lookup"><span data-stu-id="95094-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="95094-119">Estos parámetros solo muestran los valores de las propiedades DependentServices y ServicesDependedOn (alias=RequiredServices) del objeto System.ServiceProcess.ServiceController que devuelve Get-Service, pero simplifican los comandos y hacen que resulte mucho más fácil obtener esta información.</span><span class="sxs-lookup"><span data-stu-id="95094-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="95094-120">El comando siguiente obtiene los servicios que el servicio LanmanWorkstation requiere.</span><span class="sxs-lookup"><span data-stu-id="95094-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="95094-121">El comando siguiente obtiene los servicios que requieren el servicio LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="95094-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="95094-122">También puede obtener todos los servicios que tengan dependencias.</span><span class="sxs-lookup"><span data-stu-id="95094-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="95094-123">El comando siguiente hace justamente eso y, después, usa el cmdlet Format-Table para mostrar las propiedades Status, Name, RequiredServices y DependentServices de los servicios en el equipo.</span><span class="sxs-lookup"><span data-stu-id="95094-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="95094-124">Detener, iniciar, suspender y reiniciar los servicios</span><span class="sxs-lookup"><span data-stu-id="95094-124">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="95094-125">Todos los cmdlets Service tienen el mismo formato general.</span><span class="sxs-lookup"><span data-stu-id="95094-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="95094-126">Los servicios pueden especificarse por el nombre común o el nombre para mostrar, y toman listas y caracteres comodín como valores.</span><span class="sxs-lookup"><span data-stu-id="95094-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="95094-127">Para detener el administrador de trabajos de impresión, use:</span><span class="sxs-lookup"><span data-stu-id="95094-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="95094-128">Para iniciar el administrador de trabajos de impresión una vez detenido, use:</span><span class="sxs-lookup"><span data-stu-id="95094-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="95094-129">Para suspender el administrador de trabajos de impresión, use:</span><span class="sxs-lookup"><span data-stu-id="95094-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="95094-130">El cmdlet `Restart-Service` funciona de la misma manera que los otros cmdlets Service, pero mostraremos algunos ejemplos más complejos.</span><span class="sxs-lookup"><span data-stu-id="95094-130">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="95094-131">En el uso más simple, debe especificar el nombre del servicio:</span><span class="sxs-lookup"><span data-stu-id="95094-131">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="95094-132">Observará que obtiene un mensaje de advertencia repetido sobre el inicio del administrador de trabajos de impresión.</span><span class="sxs-lookup"><span data-stu-id="95094-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="95094-133">Si realiza una operación de servicio que tarda bastante tiempo, Windows PowerShell le notificará que todavía está intentando realizar la tarea.</span><span class="sxs-lookup"><span data-stu-id="95094-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="95094-134">Si desea reiniciar varios servicios, puede obtener una lista de estos, filtrarlos y, después, ejecutar el reinicio:</span><span class="sxs-lookup"><span data-stu-id="95094-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="95094-135">Estos cmdlets Service no tienen un parámetro ComputerName, pero se pueden ejecutar en un equipo remoto mediante el cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="95094-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="95094-136">Por ejemplo, el siguiente comando reinicia el servicio de administrador de trabajos en cola en el equipo remoto Server01.</span><span class="sxs-lookup"><span data-stu-id="95094-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="95094-137">Establecer las propiedades del servicio</span><span class="sxs-lookup"><span data-stu-id="95094-137">Setting Service Properties</span></span>

<span data-ttu-id="95094-138">El cmdlet `Set-Service` cambia las propiedades de un servicio en un equipo local o remoto.</span><span class="sxs-lookup"><span data-stu-id="95094-138">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="95094-139">Dado que el estado del servicio es una propiedad, puede usar este cmdlet para iniciar, detener y suspender un servicio.</span><span class="sxs-lookup"><span data-stu-id="95094-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="95094-140">El cmdlet Set-Service también tiene un parámetro StartupType que permite cambiar el tipo de inicio del servicio.</span><span class="sxs-lookup"><span data-stu-id="95094-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="95094-141">Para usar `Set-Service` en Windows Vista y en versiones posteriores de Windows, abra Windows PowerShell con la opción "Ejecutar como administrador".</span><span class="sxs-lookup"><span data-stu-id="95094-141">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="95094-142">Para obtener más información, consulte [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="95094-142">For more information, see [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>

## <a name="see-also"></a><span data-ttu-id="95094-143">Véase también</span><span class="sxs-lookup"><span data-stu-id="95094-143">See Also</span></span>

- <span data-ttu-id="95094-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span><span class="sxs-lookup"><span data-stu-id="95094-144">[Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)</span></span>
- <span data-ttu-id="95094-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span><span class="sxs-lookup"><span data-stu-id="95094-145">[Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)</span></span>
- <span data-ttu-id="95094-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span><span class="sxs-lookup"><span data-stu-id="95094-146">[Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)</span></span>
- <span data-ttu-id="95094-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span><span class="sxs-lookup"><span data-stu-id="95094-147">[Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)</span></span>
