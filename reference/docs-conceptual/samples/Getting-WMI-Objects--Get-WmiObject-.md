---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Obtener objetos de WMI Get-WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: 522822ac3ea6f08b20fa5af6c9accb48b01035d3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058257"
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="b4681-103">Obtener objetos de WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="b4681-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="b4681-104">Obtener objetos de WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="b4681-104">Getting WMI Objects (Get-WmiObject)</span></span>

<span data-ttu-id="b4681-105">Windows Management Instrumentation (WMI) es una tecnología principal para la administración del sistema de Windows porque expone una amplia gama de información de manera uniforme.</span><span class="sxs-lookup"><span data-stu-id="b4681-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="b4681-106">Debido a la medida en que WMI lo hace posible, el cmdlet de Windows PowerShell para acceder a objetos WMI, **Get-WmiObject**, es uno de los más útiles para realizar el trabajo real.</span><span class="sxs-lookup"><span data-stu-id="b4681-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="b4681-107">Vamos a explicar cómo usar Get-WmiObject para acceder a objetos WMI y, después, cómo usar objetos WMI para realizar acciones específicas.</span><span class="sxs-lookup"><span data-stu-id="b4681-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="b4681-108">Enumerar clases WMI</span><span class="sxs-lookup"><span data-stu-id="b4681-108">Listing WMI Classes</span></span>

<span data-ttu-id="b4681-109">El primer problema que la mayoría de los usuarios de WMI experimentan es intentar averiguar qué se puede hacer con WMI.</span><span class="sxs-lookup"><span data-stu-id="b4681-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="b4681-110">Las clases WMI describen los recursos que se pueden administrar.</span><span class="sxs-lookup"><span data-stu-id="b4681-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="b4681-111">Existen cientos de clases WMI, algunas de los cuales contienen decenas de propiedades.</span><span class="sxs-lookup"><span data-stu-id="b4681-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="b4681-112">**Get-WmiObject** hace que WMI se pueda detectar para abordar este problema.</span><span class="sxs-lookup"><span data-stu-id="b4681-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="b4681-113">Para obtener una lista de las clases WMI disponibles en el equipo local, escriba:</span><span class="sxs-lookup"><span data-stu-id="b4681-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="b4681-114">Puede recuperar la misma información de un equipo remoto mediante el parámetro ComputerName. Para ello, especifique un nombre de equipo o una dirección IP:</span><span class="sxs-lookup"><span data-stu-id="b4681-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="b4681-115">La lista de clases que devuelven los equipos remotos puede variar según el sistema operativo específico que el equipo está ejecutando y las extensiones WMI determinadas agregadas por las aplicaciones instaladas.</span><span class="sxs-lookup"><span data-stu-id="b4681-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="b4681-116">Al usar Get-WmiObject para conectarse a un equipo remoto, el equipo remoto debe ejecutar WMI y, en la configuración predeterminada, la cuenta que está usando debe estar en el grupo de administradores local en el equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="b4681-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="b4681-117">El sistema remoto no necesita tener Windows PowerShell instalado.</span><span class="sxs-lookup"><span data-stu-id="b4681-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="b4681-118">Esto permite administrar los sistemas operativos que no ejecutan Windows PowerShell, pero tienen WMI disponible.</span><span class="sxs-lookup"><span data-stu-id="b4681-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="b4681-119">También puede incluir el parámetro ComputerName al conectarse al sistema local.</span><span class="sxs-lookup"><span data-stu-id="b4681-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="b4681-120">Puede usar el nombre del equipo local, su dirección IP (o la dirección de bucle invertido 127.0.0.1) o el estilo de WMI '.' como nombre del equipo.</span><span class="sxs-lookup"><span data-stu-id="b4681-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="b4681-121">Si está ejecutando Windows PowerShell en un equipo denominado Admin01 con la dirección IP 192.168.1.90, los siguientes comandos devolverán la lista de clases WMI de ese equipo:</span><span class="sxs-lookup"><span data-stu-id="b4681-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="b4681-122">Get-WmiObject usa el espacio de nombres root/cimv2 de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="b4681-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="b4681-123">Si desea especificar otro espacio de nombres de WMI, use el parámetro **Namespace** y especifique la ruta de acceso del espacio de nombres correspondiente:</span><span class="sxs-lookup"><span data-stu-id="b4681-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="b4681-124">Visualizar detalles de clases WMI</span><span class="sxs-lookup"><span data-stu-id="b4681-124">Displaying WMI Class Details</span></span>

<span data-ttu-id="b4681-125">Si conoce el nombre de una clase WMI, puede usarlo para obtener información inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="b4681-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="b4681-126">Por ejemplo, una de las clases WMI que se usa habitualmente para recuperar información sobre un equipo es **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="b4681-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="b4681-127">Aunque vamos a presentar todos los parámetros, el comando se puede expresar de forma más concisa.</span><span class="sxs-lookup"><span data-stu-id="b4681-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="b4681-128">El parámetro **ComputerName** no es necesario cuando se conecta al sistema local.</span><span class="sxs-lookup"><span data-stu-id="b4681-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="b4681-129">Los presentamos para demostrar el caso más general y recordarle el parámetro.</span><span class="sxs-lookup"><span data-stu-id="b4681-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="b4681-130">**Namespace** se establece de manera predeterminada en root/cimv2 y también se puede omitir.</span><span class="sxs-lookup"><span data-stu-id="b4681-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="b4681-131">Por último, la mayoría de los cmdlets permite omitir el nombre de los parámetros comunes.</span><span class="sxs-lookup"><span data-stu-id="b4681-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="b4681-132">Con Get-WmiObject, si no se especifica ningún nombre para el primer parámetro, Windows PowerShell lo trata como el parámetro **Class**.</span><span class="sxs-lookup"><span data-stu-id="b4681-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="b4681-133">Esto significa que el último comando se podría haber emitido escribiendo:</span><span class="sxs-lookup"><span data-stu-id="b4681-133">This means the last command could have been issued by typing:</span></span>

```powershell
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="b4681-134">La clase **Win32_OperatingSystem** tiene muchas más propiedades de las que se muestran aquí.</span><span class="sxs-lookup"><span data-stu-id="b4681-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="b4681-135">Puede usar Get-Member para ver todas las propiedades.</span><span class="sxs-lookup"><span data-stu-id="b4681-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="b4681-136">Las propiedades de una clase WMI están disponibles automáticamente como otras propiedades de objeto:</span><span class="sxs-lookup"><span data-stu-id="b4681-136">The properties of a WMI class are automatically available like other object properties:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="b4681-137">Visualizar propiedades no predeterminadas con cmdlets de formato</span><span class="sxs-lookup"><span data-stu-id="b4681-137">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="b4681-138">Si quiere ver la información incluida en la clase **Win32_OperatingSystem** que no aparece de forma predeterminada, puede mostrarla mediante los cmdlets **Format**.</span><span class="sxs-lookup"><span data-stu-id="b4681-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="b4681-139">Por ejemplo, si desea mostrar los datos de memoria disponible, escriba:</span><span class="sxs-lookup"><span data-stu-id="b4681-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="b4681-140">Los caracteres comodín funcionan con nombres de propiedad de **Format-Table**, por lo que el elemento final de la canalización se puede reducir a `Format-Table -Property Total,Free`.</span><span class="sxs-lookup"><span data-stu-id="b4681-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to `Format-Table -Property Total,Free`</span></span>

<span data-ttu-id="b4681-141">Los datos de la memoria podrían ser más legibles si se formatean como una lista escribiendo:</span><span class="sxs-lookup"><span data-stu-id="b4681-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
