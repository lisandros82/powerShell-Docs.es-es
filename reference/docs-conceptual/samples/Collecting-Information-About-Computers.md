---
ms.date: 12/23/2019
keywords: powershell, cmdlet
title: Recopilar información acerca de los equipos
ms.openlocfilehash: 9407ff15b3c3ca6b3adab60d4d01d957c599e79e
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737243"
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="8598a-103">Recopilar información acerca de los equipos</span><span class="sxs-lookup"><span data-stu-id="8598a-103">Collecting Information About Computers</span></span>

<span data-ttu-id="8598a-104">Los cmdlets del módulo **CimCmdlets** son los más importantes para tareas de administración generales del sistema.</span><span class="sxs-lookup"><span data-stu-id="8598a-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span> <span data-ttu-id="8598a-105">Todas las opciones de configuración críticas del subsistema se exponen a través de WMI.</span><span class="sxs-lookup"><span data-stu-id="8598a-105">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="8598a-106">Además, WMI trata los datos como objetos que están en colecciones de uno o más elementos.</span><span class="sxs-lookup"><span data-stu-id="8598a-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="8598a-107">Dado que Windows PowerShell también funciona con objetos y tiene una canalización que permite tratar uno o varios objetos de la misma manera, el acceso genérico a WMI le permite realizar algunas tareas avanzadas con muy poco esfuerzo.</span><span class="sxs-lookup"><span data-stu-id="8598a-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="8598a-108">Enumerar la configuración del escritorio</span><span class="sxs-lookup"><span data-stu-id="8598a-108">Listing Desktop Settings</span></span>

<span data-ttu-id="8598a-109">Comenzaremos con un comando que recopila información acerca de los escritorios en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="8598a-109">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

<span data-ttu-id="8598a-110">Devuelve información de todos los equipos de escritorio, independientemente de si están en uso.</span><span class="sxs-lookup"><span data-stu-id="8598a-110">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="8598a-111">La información devuelta por algunas clases WMI puede ser muy detallada y, a menudo, incluir metadatos acerca de la clase WMI.</span><span class="sxs-lookup"><span data-stu-id="8598a-111">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>

<span data-ttu-id="8598a-112">Dado que la mayoría de las propiedades de estos metadatos tienen nombres que comienzan por **Cim**, puede filtrarlas mediante `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="8598a-112">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span> <span data-ttu-id="8598a-113">Especifique el parámetro **-ExcludeProperty** con "Cim\*" como valor.</span><span class="sxs-lookup"><span data-stu-id="8598a-113">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span> <span data-ttu-id="8598a-114">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8598a-114">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="8598a-115">Para filtrar los metadatos, use un operador de canalización (|) para enviar los resultados del comando `Get-CimInstance` a `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="8598a-115">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="8598a-116">Enumerar información del BIOS</span><span class="sxs-lookup"><span data-stu-id="8598a-116">Listing BIOS Information</span></span>

<span data-ttu-id="8598a-117">La clase **Win32_BIOS** de WMI devuelve información bastante compacta y completa sobre el BIOS del sistema en el equipo local:</span><span class="sxs-lookup"><span data-stu-id="8598a-117">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a><span data-ttu-id="8598a-118">Enumerar información del procesador</span><span class="sxs-lookup"><span data-stu-id="8598a-118">Listing Processor Information</span></span>

<span data-ttu-id="8598a-119">Puede recuperar información general del procesador mediante la clase **Win32_Processor** de WMI, aunque probablemente desee filtrar la información:</span><span class="sxs-lookup"><span data-stu-id="8598a-119">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="8598a-120">Para obtener una cadena descriptiva genérica de la familia del procesador, puede devolver la propiedad **SystemType**:</span><span class="sxs-lookup"><span data-stu-id="8598a-120">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="8598a-121">Enumerar el modelo y el fabricante del equipo</span><span class="sxs-lookup"><span data-stu-id="8598a-121">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="8598a-122">La información del modelo del equipo también está disponible en **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="8598a-122">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="8598a-123">La salida estándar mostrada no necesita ningún filtrado para proporcionar datos de OEM:</span><span class="sxs-lookup"><span data-stu-id="8598a-123">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="8598a-124">La salida de comandos como este, que devuelven información directamente de determinado hardware, es tan buena como los datos que posee.</span><span class="sxs-lookup"><span data-stu-id="8598a-124">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="8598a-125">Los fabricantes del hardware no configuran correctamente algunos datos, por lo que podrían no estar disponibles.</span><span class="sxs-lookup"><span data-stu-id="8598a-125">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="8598a-126">Enumerar las revisiones instaladas</span><span class="sxs-lookup"><span data-stu-id="8598a-126">Listing Installed Hotfixes</span></span>

<span data-ttu-id="8598a-127">Puede enumerar todas las revisiones instaladas mediante **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="8598a-127">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

<span data-ttu-id="8598a-128">Esta clase devuelve una lista de revisiones que se ve así:</span><span class="sxs-lookup"><span data-stu-id="8598a-128">This class returns a list of hotfixes that looks like this:</span></span>

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="8598a-129">Para obtener una salida más concisa, puede excluir algunas propiedades.</span><span class="sxs-lookup"><span data-stu-id="8598a-129">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="8598a-130">Aunque puede usar el parámetro **Property** de `Get-CimInstance` para elegir solo **HotFixID**, al hacerlo se devolverá más información, porque se muestran todos los metadatos de manera predeterminada:</span><span class="sxs-lookup"><span data-stu-id="8598a-130">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixID
```

```Output
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4533002
InstalledBy           :
ServicePackInEffect   :
PSComputerName        :
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name…}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
...
```

<span data-ttu-id="8598a-131">Se devuelven los datos adicionales, ya que el parámetro **Property** de `Get-CimInstance` restringe las propiedades devueltas de instancias de la clase WMI, no el objeto que se devuelve a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8598a-131">The additional data is returned, because the **Property** parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to PowerShell.</span></span> <span data-ttu-id="8598a-132">Para reducir la salida, use `Select-Object`:</span><span class="sxs-lookup"><span data-stu-id="8598a-132">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="8598a-133">Enumerar la información de versión del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="8598a-133">Listing Operating System Version Information</span></span>

<span data-ttu-id="8598a-134">Las propiedades de la clase **Win32_OperatingSystem** incluyen información acerca de la versión y del Service Pack.</span><span class="sxs-lookup"><span data-stu-id="8598a-134">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="8598a-135">Solo puede seleccionar explícitamente estas propiedades para obtener un resumen de la información de versión de **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="8598a-135">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="8598a-136">También puede usar caracteres comodín con el parámetro **Property** de `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="8598a-136">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span> <span data-ttu-id="8598a-137">Dado que todas las propiedades que comienzan por **Build** o **ServicePack** son importantes para usar aquí, podemos reducirlo al formato siguiente:</span><span class="sxs-lookup"><span data-stu-id="8598a-137">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property Build*,OSType,ServicePack*
```

```Output
BuildNumber             : 18362
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="8598a-138">Enumerar el propietario y los usuarios locales</span><span class="sxs-lookup"><span data-stu-id="8598a-138">Listing Local Users and Owner</span></span>

<span data-ttu-id="8598a-139">La información local del usuario general (número de usuarios con licencia, número actual de usuarios y nombre del propietario) puede encontrarse con una selección de propiedades de la clase **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="8598a-139">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class properties.</span></span> <span data-ttu-id="8598a-140">Puede seleccionar explícitamente las propiedades para que tengan el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="8598a-140">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="8598a-141">Una versión más concisa con caracteres comodín es:</span><span class="sxs-lookup"><span data-stu-id="8598a-141">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="8598a-142">Obtener el espacio disponible en disco</span><span class="sxs-lookup"><span data-stu-id="8598a-142">Getting Available Disk Space</span></span>

<span data-ttu-id="8598a-143">Para ver el espacio en disco y el espacio libre de las unidades locales, puede usar la clase Win32_LogicalDisk de WMI.</span><span class="sxs-lookup"><span data-stu-id="8598a-143">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="8598a-144">Solo necesita ver las instancias con un valor de DriveType de 3 (valor que WMI usa para los discos duros fijos).</span><span class="sxs-lookup"><span data-stu-id="8598a-144">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3"
```

```Output
DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .
```

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" |
  Measure-Object -Property FreeSpace,Size -Sum |
    Select-Object -Property Property,Sum
```

```Output
Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a><span data-ttu-id="8598a-145">Obtener información de la sesión de inicio</span><span class="sxs-lookup"><span data-stu-id="8598a-145">Getting Logon Session Information</span></span>

<span data-ttu-id="8598a-146">Puede obtener información general sobre las sesiones de inicio asociadas a los usuarios a través de la clase **Win32_LogonSession** de WMI:</span><span class="sxs-lookup"><span data-stu-id="8598a-146">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="8598a-147">Ayudar al usuario a iniciar sesión en un equipo</span><span class="sxs-lookup"><span data-stu-id="8598a-147">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="8598a-148">Para ver el usuario que inició sesión en un equipo concreto use Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="8598a-148">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="8598a-149">Este comando devuelve solo el usuario que inició sesión en el escritorio del sistema:</span><span class="sxs-lookup"><span data-stu-id="8598a-149">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="8598a-150">Obtener la hora local de un equipo</span><span class="sxs-lookup"><span data-stu-id="8598a-150">Getting Local Time from a Computer</span></span>

<span data-ttu-id="8598a-151">Puede recuperar la hora local actual de un equipo específico mediante la clase **Win32_LocalTime** de WMI.</span><span class="sxs-lookup"><span data-stu-id="8598a-151">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

```powershell
Get-CimInstance -ClassName Win32_LocalTime
```

```Output
Day            : 23
DayOfWeek      : 1
Hour           : 8
Milliseconds   :
Minute         : 52
Month          : 12
Quarter        : 4
Second         : 55
WeekInMonth    : 4
Year           : 2019
PSComputerName :
```

## <a name="displaying-service-status"></a><span data-ttu-id="8598a-152">Visualizar el estado del servicio</span><span class="sxs-lookup"><span data-stu-id="8598a-152">Displaying Service Status</span></span>

<span data-ttu-id="8598a-153">Para ver el estado de todos los servicios de un equipo concreto, puede usar el cmdlet `Get-Service`localmente.</span><span class="sxs-lookup"><span data-stu-id="8598a-153">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span> <span data-ttu-id="8598a-154">Para los sistemas remotos, puede usar la clase **Win32_Service** de WMI.</span><span class="sxs-lookup"><span data-stu-id="8598a-154">For remote systems, you can use the **Win32_Service** WMI class.</span></span> <span data-ttu-id="8598a-155">Si también usa `Select-Object` para filtrar los resultados con **Status**, **Name** y **DisplayName**, el formato de salida será prácticamente idéntico al de `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="8598a-155">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="8598a-156">Para permitir la visualización completa de los nombres de los servicios ocasionales con nombres muy largos, puede usar `Format-Table` con los parámetros **AutoSize** y **Wrap** a fin de optimizar el ancho de columna y permitir que los nombres largos se ajusten en lugar de truncarse:</span><span class="sxs-lookup"><span data-stu-id="8598a-156">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
