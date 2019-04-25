---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3d74217621d00dfd68cad1c45d187a9c2ffb9980
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085288"
---
# <a name="known-issues-and-limitations"></a><span data-ttu-id="7360c-102">Problemas y limitaciones conocidos</span><span class="sxs-lookup"><span data-stu-id="7360c-102">Known Issues and Limitations</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="7360c-103">Los accesos directos de PowerShell se interrumpen cuando se usan por primera vez</span><span class="sxs-lookup"><span data-stu-id="7360c-103">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="7360c-104">**Resolución:** Realice una de las acciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="7360c-104">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="7360c-105">Haga clic con el botón derecho en el acceso directo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7360c-105">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="7360c-106">Seleccione "Windows PowerShell" para iniciar en modo sin privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="7360c-106">Select “Windows PowerShell” to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="7360c-107">Haga clic con el botón derecho en el acceso directo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7360c-107">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="7360c-108">Haga clic en "Windows PowerShell" y seleccione "Ejecutar como administrador" para iniciar en modo con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="7360c-108">Right click on “Windows PowerShell” and select “Run As Administrator” to launch in an elevated mode.</span></span>

<span data-ttu-id="7360c-109">Después de llevar a cabo cualquiera de las acciones anteriores, los accesos directos de PowerShell funcionarán.</span><span class="sxs-lookup"><span data-stu-id="7360c-109">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="7360c-110">Estas acciones deben realizarse una sola vez.</span><span class="sxs-lookup"><span data-stu-id="7360c-110">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="7360c-111">Los módulos de PowerShell y los recursos de DSC notifican errores sobre ExecutionPolicy en Windows 7</span><span class="sxs-lookup"><span data-stu-id="7360c-111">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="7360c-112">En Windows 7, el uso de módulos de PowerShell y recursos de DSC puede provocar la notificación de errores sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="7360c-112">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="7360c-113">**Resolución:** establezca ExecutionPolicy en RemoteSigned. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):</span><span class="sxs-lookup"><span data-stu-id="7360c-113">**Resolution:** Set the ExecutionPolicy to RemoteSigned by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="7360c-114">La conexión a un punto de conexión de Exchange remoto antiguo causa un bloqueo</span><span class="sxs-lookup"><span data-stu-id="7360c-114">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="7360c-115">El punto de conexión de Exchange le redirige a un nuevo punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="7360c-115">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="7360c-116">Hay un error en la lógica de redirección que causa un bloqueo.</span><span class="sxs-lookup"><span data-stu-id="7360c-116">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="7360c-117">**Resolución:** realice la conexión directamente al nuevo punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="7360c-117">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="7360c-118">La característica Registro de inventario de software se detiene erróneamente después de la instalación de WMF 5.0 en Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7360c-118">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="7360c-119">Al instalar WMF 5.0 en un sistema Windows Server 2012 R2 que ya ejecuta SIL, la característica Registro de inventario de software de detiene por error después de la instalación.</span><span class="sxs-lookup"><span data-stu-id="7360c-119">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="7360c-120">**Resolución:** ejecute el cmdlet Start-SilLogging después de la instalación de WMF, ya que el proceso de instalación detendrá por error la característica Registro de inventario de software.</span><span class="sxs-lookup"><span data-stu-id="7360c-120">**Resolution:** Run the Start-SilLogging cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="7360c-121">`Get-ChildItem` no funciona si -LiteralPath y –Recurse se usan juntos.</span><span class="sxs-lookup"><span data-stu-id="7360c-121">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="7360c-122">Si un nombre de directorio contiene un carácter comodín no válido, `Get-ChildItem` no producirá los resultados esperados si -LiteralPath y -Recurse se usan juntos.</span><span class="sxs-lookup"><span data-stu-id="7360c-122">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="7360c-123">**Resolución:** no es lo ideal, pero la solución actual es implementar la recursividad en el script en lugar de depender del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7360c-123">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="7360c-124">Se produce un error de Sysprep después de la instalación de WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="7360c-124">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="7360c-125">Hay dos soluciones alternativas para este problema según la versión de Windows Server que se ejecute.</span><span class="sxs-lookup"><span data-stu-id="7360c-125">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="7360c-126">**Resolución:**</span><span class="sxs-lookup"><span data-stu-id="7360c-126">**Resolution:**</span></span>

- <span data-ttu-id="7360c-127">Para sistemas que ejecutan **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="7360c-127">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="7360c-128">Abra PowerShell como administrador.</span><span class="sxs-lookup"><span data-stu-id="7360c-128">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="7360c-129">Ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="7360c-129">Run the following command</span></span>

     ```powershell
     Set-SilLogging –TargetUri https://BlankTarget –CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="7360c-130">Ejecute el comando y omita el error, tal como se espera.</span><span class="sxs-lookup"><span data-stu-id="7360c-130">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="7360c-131">Elimine los archivos del directorio \Windows\System32\Logfiles\SIL\.</span><span class="sxs-lookup"><span data-stu-id="7360c-131">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="7360c-132">Instale todas las actualizaciones disponibles de Windows importantes y comience a utilizar Sysyprep con normalidad.</span><span class="sxs-lookup"><span data-stu-id="7360c-132">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="7360c-133">Para sistemas que ejecutan **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="7360c-133">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="7360c-134">Después de instalar WMF 5.0 en el servidor para la preparación del sistema con Sysprep, inicie sesión como administrador.</span><span class="sxs-lookup"><span data-stu-id="7360c-134">After installing WMF 5.0 on the server to be Sysprep’d, login as administrator.</span></span>
  2. <span data-ttu-id="7360c-135">Copie Generize.xml desde el directorio \Windows\System32\Sysprep\ActionFiles\ a una ubicación fuera del directorio de Windows, como C:\.</span><span class="sxs-lookup"><span data-stu-id="7360c-135">Copy Generize.xml from directory \Windows\System32\Sysprep\ActionFiles\ to a location outside of the Windows directory, C:\ for example.</span></span>
  3. <span data-ttu-id="7360c-136">Abra la copia de Generalize.xml con el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="7360c-136">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="7360c-137">Busque y quite el texto siguiente; hay que eliminar una instancia de cada caso (se encuentran casi al final del documento).</span><span class="sxs-lookup"><span data-stu-id="7360c-137">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="7360c-138">Guarde la copia modificada de Generalize.xml y cierre el archivo.</span><span class="sxs-lookup"><span data-stu-id="7360c-138">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="7360c-139">Abra una ventana del símbolo del sistema como administrador.</span><span class="sxs-lookup"><span data-stu-id="7360c-139">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="7360c-140">Ejecute el siguiente comando para adquirir la titularidad del archivo Generalize.xml en la carpeta system32:</span><span class="sxs-lookup"><span data-stu-id="7360c-140">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="7360c-141">Ejecute el siguiente comando para establecer los permisos adecuados en el archivo:</span><span class="sxs-lookup"><span data-stu-id="7360c-141">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="7360c-142">Responda de manera afirmativa cuando se le solicite confirmación.</span><span class="sxs-lookup"><span data-stu-id="7360c-142">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="7360c-143">Tenga en cuenta que `<AdministratorUserName>` se debe reemplazar por el nombre de usuario administrador en el equipo.</span><span class="sxs-lookup"><span data-stu-id="7360c-143">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="7360c-144">Por ejemplo, "Administrador".</span><span class="sxs-lookup"><span data-stu-id="7360c-144">For example, "Administrator".</span></span>

  9. <span data-ttu-id="7360c-145">Copie el archivo modificado que ha guardado en el directorio Sysprep; para ello, use el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="7360c-145">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="7360c-146">Responda de manera afirmativa para sobrescribir (tenga en cuenta que si no aparece ningún mensaje para sobrescribir, debe comprobar la ruta de acceso especificada).</span><span class="sxs-lookup"><span data-stu-id="7360c-146">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="7360c-147">Se supone que la copia modificada de Generalize.xml se ha copiado en C:\.</span><span class="sxs-lookup"><span data-stu-id="7360c-147">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="7360c-148">Generalize.xml se ha actualizado con la solución alternativa.</span><span class="sxs-lookup"><span data-stu-id="7360c-148">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="7360c-149">Ejecute Sysprep con la opción de generalizar habilitada.</span><span class="sxs-lookup"><span data-stu-id="7360c-149">Please run Sysprep with the generalize option enabled.</span></span>