---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Obtener objetos de WMI (Get-CimInstance)
ms.openlocfilehash: 4ff47844fd367a49f554c7c05c491bdddf28eabc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/04/2020
ms.locfileid: "77002655"
---
# <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="54b98-103">Obtener objetos de WMI (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="54b98-103">Getting WMI Objects (Get-CimInstance)</span></span>

## <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="54b98-104">Obtener objetos de WMI (Get-CimInstance)</span><span class="sxs-lookup"><span data-stu-id="54b98-104">Getting WMI Objects (Get-CimInstance)</span></span>

<span data-ttu-id="54b98-105">Windows Management Instrumentation (WMI) es una tecnología principal para la administración del sistema de Windows porque expone una amplia gama de información de manera uniforme.</span><span class="sxs-lookup"><span data-stu-id="54b98-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="54b98-106">Debido a la medida en que WMI lo hace posible, el cmdlet de PowerShell para acceder a objetos WMI, `Get-CimInstance` es uno de los más útiles para realizar el trabajo real.</span><span class="sxs-lookup"><span data-stu-id="54b98-106">Because of how much WMI makes possible, the PowerShell cmdlet for accessing WMI objects, `Get-CimInstance`, is one of the most useful for doing real work.</span></span> <span data-ttu-id="54b98-107">Vamos a explicar cómo usar CimCmdlets para acceder a objetos WMI y, después, cómo usar objetos WMI para realizar acciones específicas.</span><span class="sxs-lookup"><span data-stu-id="54b98-107">We are going to discuss how to use the CimCmdlets to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="54b98-108">Enumerar clases WMI</span><span class="sxs-lookup"><span data-stu-id="54b98-108">Listing WMI Classes</span></span>

<span data-ttu-id="54b98-109">El primer problema que la mayoría de los usuarios de WMI experimentan es intentar averiguar qué se puede hacer con WMI.</span><span class="sxs-lookup"><span data-stu-id="54b98-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="54b98-110">Las clases WMI describen los recursos que se pueden administrar.</span><span class="sxs-lookup"><span data-stu-id="54b98-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="54b98-111">Existen cientos de clases WMI, algunas de los cuales contienen decenas de propiedades.</span><span class="sxs-lookup"><span data-stu-id="54b98-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="54b98-112">`Get-CimClass` hace que WMI se pueda detectar para abordar este problema.</span><span class="sxs-lookup"><span data-stu-id="54b98-112">`Get-CimClass` addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="54b98-113">Para obtener una lista de las clases WMI disponibles en el equipo local, escriba:</span><span class="sxs-lookup"><span data-stu-id="54b98-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 |
  Where-Object CimClassName -like Win32* |
    Select-Object CimClassName
```

```Output
CimClassName
------------
Win32_DeviceChangeEvent
Win32_SystemConfigurationChangeEvent
Win32_VolumeChangeEvent
Win32_SystemTrace
Win32_ProcessTrace
Win32_ProcessStartTrace
Win32_ProcessStopTrace
Win32_ThreadTrace
Win32_ThreadStartTrace
Win32_ThreadStopTrace
...
```

<span data-ttu-id="54b98-114">Puede recuperar la misma información de un equipo remoto mediante el parámetro **ComputerName**. Para ello, especifique un nombre de equipo o una dirección IP:</span><span class="sxs-lookup"><span data-stu-id="54b98-114">You can retrieve the same information from a remote computer by using the **ComputerName** parameter, specifying a computer name or IP address:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

<span data-ttu-id="54b98-115">La lista de clases que devuelven los equipos remotos puede variar según el sistema operativo específico que el equipo está ejecutando y las extensiones WMI determinadas agregadas por las aplicaciones instaladas.</span><span class="sxs-lookup"><span data-stu-id="54b98-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="54b98-116">Al usar cmdlets de CIM para conectarse a un equipo remoto, este debe ejecutar WMI y la cuenta que está usando debe estar en el grupo de administradores local en el equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="54b98-116">When using CIM cmdlets to connect to a remote computer, the remote computer must be running WMI and the account you are using must be in the local administrators group on the remote computer.</span></span>
> <span data-ttu-id="54b98-117">El sistema remoto no necesita tener PowerShell instalado.</span><span class="sxs-lookup"><span data-stu-id="54b98-117">The remote system does not need to have PowerShell installed.</span></span> <span data-ttu-id="54b98-118">Esto permite administrar los sistemas operativos que no ejecutan PowerShell, pero tienen WMI disponible.</span><span class="sxs-lookup"><span data-stu-id="54b98-118">This allows you to administer operating systems that are not running PowerShell, but do have WMI available.</span></span>

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="54b98-119">Visualizar detalles de clases WMI</span><span class="sxs-lookup"><span data-stu-id="54b98-119">Displaying WMI Class Details</span></span>

<span data-ttu-id="54b98-120">Si conoce el nombre de una clase WMI, puede usarlo para obtener información inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="54b98-120">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="54b98-121">Por ejemplo, una de las clases WMI que se usa habitualmente para recuperar información sobre un equipo es **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="54b98-121">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

<span data-ttu-id="54b98-122">Aunque vamos a presentar todos los parámetros, el comando se puede expresar de forma más concisa.</span><span class="sxs-lookup"><span data-stu-id="54b98-122">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span>
<span data-ttu-id="54b98-123">El parámetro **ComputerName** no es necesario cuando se conecta al sistema local.</span><span class="sxs-lookup"><span data-stu-id="54b98-123">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="54b98-124">Los presentamos para demostrar el caso más general y recordarle el parámetro.</span><span class="sxs-lookup"><span data-stu-id="54b98-124">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="54b98-125">**Namespace** se establece de manera predeterminada en `root/CIMV2` y también se puede omitir.</span><span class="sxs-lookup"><span data-stu-id="54b98-125">The **Namespace** defaults to `root/CIMV2`, and can be omitted as well.</span></span> <span data-ttu-id="54b98-126">Por último, la mayoría de los cmdlets permite omitir el nombre de los parámetros comunes.</span><span class="sxs-lookup"><span data-stu-id="54b98-126">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="54b98-127">Con `Get-CimInstance`, si no se especifica ningún nombre para el primer parámetro, PowerShell lo trata como el parámetro **Class**.</span><span class="sxs-lookup"><span data-stu-id="54b98-127">With `Get-CimInstance`, if no name is specified for the first parameter, PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="54b98-128">Esto significa que el último comando se podría haber emitido escribiendo:</span><span class="sxs-lookup"><span data-stu-id="54b98-128">This means the last command could have been issued by typing:</span></span>

```powershell
Get-CimInstance Win32_OperatingSystem
```

<span data-ttu-id="54b98-129">La clase **Win32_OperatingSystem** tiene muchas más propiedades de las que se muestran aquí.</span><span class="sxs-lookup"><span data-stu-id="54b98-129">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="54b98-130">Puede usar Get-Member para ver todas las propiedades.</span><span class="sxs-lookup"><span data-stu-id="54b98-130">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="54b98-131">Las propiedades de una clase WMI están disponibles automáticamente como otras propiedades de objeto:</span><span class="sxs-lookup"><span data-stu-id="54b98-131">The properties of a WMI class are automatically available like other object properties:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Get-Member -MemberType Property
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_OperatingSystem
Name                                      MemberType Definition
----                                      ---------- ----------
BootDevice                                Property   string BootDevice {get;}
BuildNumber                               Property   string BuildNumber {get;}
BuildType                                 Property   string BuildType {get;}
Caption                                   Property   string Caption {get;}
CodeSet                                   Property   string CodeSet {get;}
CountryCode                               Property   string CountryCode {get;}
CreationClassName                         Property   string CreationClassName {get;}
CSCreationClassName                       Property   string CSCreationClassName {get;}
CSDVersion                                Property   string CSDVersion {get;}
CSName                                    Property   string CSName {get;}
CurrentTimeZone                           Property   short CurrentTimeZone {get;}
DataExecutionPrevention_32BitApplications Property   bool DataExecutionPrevention_32BitApplications {get;}
DataExecutionPrevention_Available         Property   bool DataExecutionPrevention_Available {get;}
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="54b98-132">Visualizar propiedades no predeterminadas con cmdlets de formato</span><span class="sxs-lookup"><span data-stu-id="54b98-132">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="54b98-133">Si quiere ver la información incluida en la clase **Win32_OperatingSystem** que no aparece de forma predeterminada, puede mostrarla mediante los cmdlets **Format**.</span><span class="sxs-lookup"><span data-stu-id="54b98-133">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="54b98-134">Por ejemplo, si desea mostrar los datos de memoria disponible, escriba:</span><span class="sxs-lookup"><span data-stu-id="54b98-134">For example, if you want to display available memory data, type:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem |
  Format-Table -Property TotalVirtualMemorySize, TotalVisibleMemorySize,
    FreePhysicalMemory, FreeVirtualMemory, FreeSpaceInPagingFiles
```

```Output
TotalVirtualMemorySize TotalVisibleMemorySize FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------------- ------------------ ----------------- ----------------------
              33449088               16671872            6451868          18424496               16285032
```

> [!NOTE]
> <span data-ttu-id="54b98-135">Los caracteres comodín funcionan con nombres de propiedad de `Format-Table`, por lo que el elemento final de la canalización se puede reducir a `Format-Table -Property Total*Memory*, Free*`.</span><span class="sxs-lookup"><span data-stu-id="54b98-135">Wildcards work with property names in `Format-Table`, so the final pipeline element can be reduced to `Format-Table -Property Total*Memory*, Free*`</span></span>

<span data-ttu-id="54b98-136">Los datos de la memoria podrían ser más legibles si se formatean como una lista escribiendo:</span><span class="sxs-lookup"><span data-stu-id="54b98-136">The memory data might be more readable if you format it as a list by typing:</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Format-List Total*Memory*, Free*
```

```Output
TotalVirtualMemorySize : 33449088
TotalVisibleMemorySize : 16671872
FreePhysicalMemory     : 6524456
FreeSpaceInPagingFiles : 16285808
FreeVirtualMemory      : 18393668
Name                   : Microsoft Windows 10 Pro|C:\WINDOWS|\Device\Harddisk0\Partition2
```
