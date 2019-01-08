---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Recopilar información acerca de los equipos
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: 99125ef701705c20d4e955c79eaa3469ce4d58fb
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402361"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="70d72-103">Recopilar información acerca de los equipos</span><span class="sxs-lookup"><span data-stu-id="70d72-103">Collecting Information About Computers</span></span>

<span data-ttu-id="70d72-104">Los cmdlets del módulo **CimCmdlets** son los más importantes para tareas de administración generales del sistema.</span><span class="sxs-lookup"><span data-stu-id="70d72-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span>
<span data-ttu-id="70d72-105">Todas las opciones de configuración críticas del subsistema se exponen a través de WMI.</span><span class="sxs-lookup"><span data-stu-id="70d72-105">All critical subsystem settings are exposed through WMI.</span></span>
<span data-ttu-id="70d72-106">Además, WMI trata los datos como objetos que están en colecciones de uno o más elementos.</span><span class="sxs-lookup"><span data-stu-id="70d72-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span>
<span data-ttu-id="70d72-107">Dado que Windows PowerShell también funciona con objetos y tiene una canalización que permite tratar uno o varios objetos de la misma manera, el acceso genérico a WMI le permite realizar algunas tareas avanzadas con muy poco esfuerzo.</span><span class="sxs-lookup"><span data-stu-id="70d72-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="70d72-108">Los ejemplos siguientes muestran cómo recopilar información específica mediante `Get-CimInstance` en un equipo arbitrario.</span><span class="sxs-lookup"><span data-stu-id="70d72-108">The following examples demonstrate how to collect specific information by using `Get-CimInstance` against an arbitrary computer.</span></span>
<span data-ttu-id="70d72-109">Especificamos el parámetro **ComputerName** con el valor de punto (**.**), que representa el equipo local.</span><span class="sxs-lookup"><span data-stu-id="70d72-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span>
<span data-ttu-id="70d72-110">Puede especificar una dirección IP o un nombre asociado a cualquier equipo que pueda alcanzar a través de WMI.</span><span class="sxs-lookup"><span data-stu-id="70d72-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span>
<span data-ttu-id="70d72-111">Para recuperar información sobre el equipo local, puede omitir el parámetro **ComputerName**.</span><span class="sxs-lookup"><span data-stu-id="70d72-111">To retrieve information about the local computer, you could omit the **ComputerName** parameter.</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="70d72-112">Enumerar la configuración del escritorio</span><span class="sxs-lookup"><span data-stu-id="70d72-112">Listing Desktop Settings</span></span>

<span data-ttu-id="70d72-113">Comenzaremos con un comando que recopila información acerca de los escritorios en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="70d72-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName .
```

<span data-ttu-id="70d72-114">Devuelve información de todos los equipos de escritorio, independientemente de si están en uso.</span><span class="sxs-lookup"><span data-stu-id="70d72-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="70d72-115">La información devuelta por algunas clases WMI puede ser muy detallada y, a menudo, incluir metadatos acerca de la clase WMI.</span><span class="sxs-lookup"><span data-stu-id="70d72-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>
<span data-ttu-id="70d72-116">Dado que la mayoría de las propiedades de estos metadatos tienen nombres que comienzan por **Cim**, puede filtrarlas mediante `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="70d72-116">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span>
<span data-ttu-id="70d72-117">Especifique el parámetro **-ExcludeProperty** con "Cim\*" como valor.</span><span class="sxs-lookup"><span data-stu-id="70d72-117">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span>
<span data-ttu-id="70d72-118">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="70d72-118">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="70d72-119">Para filtrar los metadatos, use un operador de canalización (|) para enviar los resultados del comando `Get-CimInstance` a `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="70d72-119">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="70d72-120">Enumerar información del BIOS</span><span class="sxs-lookup"><span data-stu-id="70d72-120">Listing BIOS Information</span></span>

<span data-ttu-id="70d72-121">La clase **Win32_BIOS** de WMI devuelve información bastante compacta y completa sobre el BIOS del sistema en el equipo local:</span><span class="sxs-lookup"><span data-stu-id="70d72-121">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="70d72-122">Enumerar información del procesador</span><span class="sxs-lookup"><span data-stu-id="70d72-122">Listing Processor Information</span></span>

<span data-ttu-id="70d72-123">Puede recuperar información general del procesador mediante la clase **Win32_Processor** de WMI, aunque probablemente desee filtrar la información:</span><span class="sxs-lookup"><span data-stu-id="70d72-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor -ComputerName . | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="70d72-124">Para obtener una cadena descriptiva genérica de la familia del procesador, puede devolver la propiedad **SystemType**:</span><span class="sxs-lookup"><span data-stu-id="70d72-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="70d72-125">Enumerar el modelo y el fabricante del equipo</span><span class="sxs-lookup"><span data-stu-id="70d72-125">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="70d72-126">La información del modelo del equipo también está disponible en **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="70d72-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span>
<span data-ttu-id="70d72-127">La salida estándar mostrada no necesita ningún filtrado para proporcionar datos de OEM:</span><span class="sxs-lookup"><span data-stu-id="70d72-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="70d72-128">La salida de comandos como este, que devuelven información directamente de determinado hardware, es tan buena como los datos que posee.</span><span class="sxs-lookup"><span data-stu-id="70d72-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span>
<span data-ttu-id="70d72-129">Los fabricantes del hardware no configuran correctamente algunos datos, por lo que podrían no estar disponibles.</span><span class="sxs-lookup"><span data-stu-id="70d72-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="70d72-130">Enumerar las revisiones instaladas</span><span class="sxs-lookup"><span data-stu-id="70d72-130">Listing Installed Hotfixes</span></span>

<span data-ttu-id="70d72-131">Puede enumerar todas las revisiones instaladas mediante **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="70d72-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="70d72-132">Esta clase devuelve una lista de revisiones que se ve así:</span><span class="sxs-lookup"><span data-stu-id="70d72-132">This class returns a list of hotfixes that looks like this:</span></span>

```output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="70d72-133">Para obtener una salida más concisa, puede excluir algunas propiedades.</span><span class="sxs-lookup"><span data-stu-id="70d72-133">For more succinct output, you may want to exclude some properties.</span></span>
<span data-ttu-id="70d72-134">Aunque puede usar el parámetro **Property** de `Get-CimInstance` para elegir solo **HotFixID**, al hacerlo se devolverá más información, porque se muestran todos los metadatos de manera predeterminada:</span><span class="sxs-lookup"><span data-stu-id="70d72-134">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixID
```

```output
PSShowComputerName    : True
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4048951
InstalledBy           :
ServicePackInEffect   :
PSComputerName        : .
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

<span data-ttu-id="70d72-135">Se devuelven los datos adicionales, ya que el parámetro Property de `Get-CimInstance` restringe las propiedades devueltas de instancias de la clase WMI, no el objeto que se devuelve a Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="70d72-135">The additional data is returned, because the Property parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span>
<span data-ttu-id="70d72-136">Para reducir la salida, use `Select-Object`:</span><span class="sxs-lookup"><span data-stu-id="70d72-136">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -ComputerName . -Property HotFixId | Select-Object -Property HotFixId
```

```output
HotFixId
--------
KB4048951
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="70d72-137">Enumerar la información de versión del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="70d72-137">Listing Operating System Version Information</span></span>

<span data-ttu-id="70d72-138">Las propiedades de la clase **Win32_OperatingSystem** incluyen información acerca de la versión y del Service Pack.</span><span class="sxs-lookup"><span data-stu-id="70d72-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span>
<span data-ttu-id="70d72-139">Solo puede seleccionar explícitamente estas propiedades para obtener un resumen de la información de versión de **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="70d72-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="70d72-140">También puede usar caracteres comodín con el parámetro **Property** de `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="70d72-140">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span>
<span data-ttu-id="70d72-141">Dado que todas las propiedades que comienzan por **Build** o **ServicePack** son importantes para usar aquí, podemos reducirlo al formato siguiente:</span><span class="sxs-lookup"><span data-stu-id="70d72-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*
```

```output
BuildNumber             : 16299
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="70d72-142">Enumerar el propietario y los usuarios locales</span><span class="sxs-lookup"><span data-stu-id="70d72-142">Listing Local Users and Owner</span></span>

<span data-ttu-id="70d72-143">La información local del usuario general (número de usuarios con licencia, número actual de usuarios y nombre del propietario) puede encontrarse con una selección de propiedades de la clase **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="70d72-143">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class' properties.</span></span>
<span data-ttu-id="70d72-144">Puede seleccionar explícitamente las propiedades para que tengan el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="70d72-144">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="70d72-145">Una versión más concisa con caracteres comodín es:</span><span class="sxs-lookup"><span data-stu-id="70d72-145">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="70d72-146">Obtener el espacio disponible en disco</span><span class="sxs-lookup"><span data-stu-id="70d72-146">Getting Available Disk Space</span></span>

<span data-ttu-id="70d72-147">Para ver el espacio en disco y el espacio libre de las unidades locales, puede usar la clase Win32_LogicalDisk de WMI.</span><span class="sxs-lookup"><span data-stu-id="70d72-147">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="70d72-148">Solo necesita ver las instancias con un valor de DriveType de 3 (valor que WMI usa para los discos duros fijos).</span><span class="sxs-lookup"><span data-stu-id="70d72-148">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .

Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum

Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

### <a name="getting-logon-session-information"></a><span data-ttu-id="70d72-149">Obtener información de la sesión de inicio</span><span class="sxs-lookup"><span data-stu-id="70d72-149">Getting Logon Session Information</span></span>

<span data-ttu-id="70d72-150">Puede obtener información general sobre las sesiones de inicio asociadas a los usuarios a través de la clase **Win32_LogonSession** de WMI:</span><span class="sxs-lookup"><span data-stu-id="70d72-150">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="70d72-151">Ayudar al usuario a iniciar sesión en un equipo</span><span class="sxs-lookup"><span data-stu-id="70d72-151">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="70d72-152">Para ver el usuario que inició sesión en un equipo concreto use Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="70d72-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span>
<span data-ttu-id="70d72-153">Este comando devuelve solo el usuario que inició sesión en el escritorio del sistema:</span><span class="sxs-lookup"><span data-stu-id="70d72-153">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="70d72-154">Obtener la hora local de un equipo</span><span class="sxs-lookup"><span data-stu-id="70d72-154">Getting Local Time from a Computer</span></span>

<span data-ttu-id="70d72-155">Puede recuperar la hora local actual de un equipo específico mediante la clase **Win32_LocalTime** de WMI.</span><span class="sxs-lookup"><span data-stu-id="70d72-155">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LocalTime -ComputerName .

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2017
PSComputerName : .
```

### <a name="displaying-service-status"></a><span data-ttu-id="70d72-156">Visualizar el estado del servicio</span><span class="sxs-lookup"><span data-stu-id="70d72-156">Displaying Service Status</span></span>

<span data-ttu-id="70d72-157">Para ver el estado de todos los servicios de un equipo concreto, puede usar el cmdlet `Get-Service`localmente.</span><span class="sxs-lookup"><span data-stu-id="70d72-157">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span>
<span data-ttu-id="70d72-158">Para los sistemas remotos, puede usar la clase **Win32_Service** de WMI.</span><span class="sxs-lookup"><span data-stu-id="70d72-158">For remote systems, you can use the **Win32_Service** WMI class.</span></span>
<span data-ttu-id="70d72-159">Si también usa `Select-Object` para filtrar los resultados con **Status**, **Name** y **DisplayName**, el formato de salida será prácticamente idéntico al de `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="70d72-159">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="70d72-160">Para permitir la visualización completa de los nombres de los servicios ocasionales con nombres muy largos, puede usar `Format-Table` con los parámetros **AutoSize** y **Wrap** a fin de optimizar el ancho de columna y permitir que los nombres largos se ajusten en lugar de truncarse:</span><span class="sxs-lookup"><span data-stu-id="70d72-160">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
