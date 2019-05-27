---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Problemas conocidos de WMF 5.0
ms.openlocfilehash: 91f556cb43ef971107f05c4041b725b1c7e4f1bd
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855710"
---
# <a name="known-issues-in-wmf-50"></a><span data-ttu-id="f9938-103">Problemas conocidos de WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="f9938-103">Known Issues in WMF 5.0</span></span>

## <a name="powershell-shortcuts-are-broken-when-used-for-the-first-time"></a><span data-ttu-id="f9938-104">Los accesos directos de PowerShell se interrumpen cuando se usan por primera vez</span><span class="sxs-lookup"><span data-stu-id="f9938-104">PowerShell Shortcuts are broken when used for the first time</span></span>

<span data-ttu-id="f9938-105">**Resolución:** Realice una de las acciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="f9938-105">**Resolution:** Perform one of the following actions:</span></span>

1. <span data-ttu-id="f9938-106">Haga clic con el botón derecho en el acceso directo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9938-106">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="f9938-107">Seleccione "Windows PowerShell" para iniciar en modo sin privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="f9938-107">Select "Windows PowerShell" to launch in a non-elevated mode.</span></span>
2. <span data-ttu-id="f9938-108">Haga clic con el botón derecho en el acceso directo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9938-108">Right click on the PowerShell shortcut.</span></span> <span data-ttu-id="f9938-109">Haga clic en "Windows PowerShell" y seleccione "Ejecutar como administrador" para iniciar en modo con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="f9938-109">Right click on "Windows PowerShell" and select "Run As Administrator" to launch in an elevated mode.</span></span>

<span data-ttu-id="f9938-110">Después de llevar a cabo cualquiera de las acciones anteriores, los accesos directos de PowerShell funcionarán.</span><span class="sxs-lookup"><span data-stu-id="f9938-110">Once you have performed either of the above actions, the PowerShell shortcuts will work.</span></span> <span data-ttu-id="f9938-111">Estas acciones deben realizarse una sola vez.</span><span class="sxs-lookup"><span data-stu-id="f9938-111">These actions need to be performed only once.</span></span>

## <a name="powershell-modules-and-dsc-resources-report-errors-about-executionpolicy-on-windows-7"></a><span data-ttu-id="f9938-112">Los módulos de PowerShell y los recursos de DSC notifican errores sobre ExecutionPolicy en Windows 7</span><span class="sxs-lookup"><span data-stu-id="f9938-112">PowerShell Modules and DSC Resources report errors about ExecutionPolicy on Windows 7</span></span>

<span data-ttu-id="f9938-113">En Windows 7, el uso de módulos de PowerShell y recursos de DSC puede provocar la notificación de errores sobre ExecutionPolicy.</span><span class="sxs-lookup"><span data-stu-id="f9938-113">On Windows 7, using PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

<span data-ttu-id="f9938-114">**Resolución:** establezca ExecutionPolicy en **RemoteSigned**. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados (Ejecutar como administrador):</span><span class="sxs-lookup"><span data-stu-id="f9938-114">**Resolution:** Set the ExecutionPolicy to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```

## <a name="connecting-to-an-old-remote-exchange-endpoint-causes-a-crash"></a><span data-ttu-id="f9938-115">La conexión a un punto de conexión de Exchange remoto antiguo causa un bloqueo</span><span class="sxs-lookup"><span data-stu-id="f9938-115">Connecting to an old remote Exchange endpoint causes a crash</span></span>

<span data-ttu-id="f9938-116">El punto de conexión de Exchange le redirige a un nuevo punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="f9938-116">The old Exchange endpoint redirects to a new endpoint.</span></span> <span data-ttu-id="f9938-117">Hay un error en la lógica de redirección que causa un bloqueo.</span><span class="sxs-lookup"><span data-stu-id="f9938-117">There is a bug in the redirection logic that results in a crash.</span></span>

<span data-ttu-id="f9938-118">**Resolución:** realice la conexión directamente al nuevo punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="f9938-118">**Resolution:** Connect directly to the new endpoint.</span></span>

## <a name="software-inventory-logging-feature-is-erroneously-stopped-after-wmf-50-installation-on-windows-server-2012-r2"></a><span data-ttu-id="f9938-119">La característica Registro de inventario de software se detiene erróneamente después de la instalación de WMF 5.0 en Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="f9938-119">Software Inventory Logging feature is erroneously stopped after WMF 5.0 installation on Windows Server 2012 R2</span></span>

<span data-ttu-id="f9938-120">Al instalar WMF 5.0 en un sistema Windows Server 2012 R2 que ya ejecuta SIL, la característica Registro de inventario de software de detiene por error después de la instalación.</span><span class="sxs-lookup"><span data-stu-id="f9938-120">When installing WMF 5.0 on a Windows Server 2012 R2 that is already running SIL, the Software Inventory Logging feature is erroneously stopped after installation.</span></span>

<span data-ttu-id="f9938-121">**Resolución:** ejecute el cmdlet `Start-SilLogging` después de la instalación de WMF, ya que el proceso de instalación detendrá por error la característica Registro de inventario de software.</span><span class="sxs-lookup"><span data-stu-id="f9938-121">**Resolution:** Run the `Start-SilLogging` cmdlet once after the WMF installation, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

## <a name="get-childitem-does-not-work-if--literalpath-and--recurse-are-used-together"></a><span data-ttu-id="f9938-122">`Get-ChildItem` no funciona si -LiteralPath y –Recurse se usan juntos.</span><span class="sxs-lookup"><span data-stu-id="f9938-122">`Get-ChildItem` does not work if -LiteralPath and -Recurse are used together</span></span>

<span data-ttu-id="f9938-123">Si un nombre de directorio contiene un carácter comodín no válido, `Get-ChildItem` no producirá los resultados esperados si -LiteralPath y -Recurse se usan juntos.</span><span class="sxs-lookup"><span data-stu-id="f9938-123">If a directory name contains an invalid wildcard character, then `Get-ChildItem` will not produce expected results when both -LiteralPath and -Recurse are used together.</span></span>

<span data-ttu-id="f9938-124">**Resolución:** no es lo ideal, pero la solución actual es implementar la recursividad en el script en lugar de depender del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f9938-124">**Resolution:** Not ideal, but current workaround is to implement recursion in the script rather than rely on the cmdlet.</span></span>

## <a name="sysprep-fails-after-wmf-50-installation"></a><span data-ttu-id="f9938-125">Se produce un error de Sysprep después de la instalación de WMF 5.0</span><span class="sxs-lookup"><span data-stu-id="f9938-125">Sysprep fails after WMF 5.0 installation</span></span>

<span data-ttu-id="f9938-126">Hay dos soluciones alternativas para este problema según la versión de Windows Server que se ejecute.</span><span class="sxs-lookup"><span data-stu-id="f9938-126">There are two workarounds for this issue depending on the version of Windows Server you are running.</span></span>

<span data-ttu-id="f9938-127">**Resolución:**</span><span class="sxs-lookup"><span data-stu-id="f9938-127">**Resolution:**</span></span>

- <span data-ttu-id="f9938-128">Para sistemas que ejecutan **Windows Server 2008 R2**</span><span class="sxs-lookup"><span data-stu-id="f9938-128">For systems running **Windows Server 2008 R2**</span></span>
  1. <span data-ttu-id="f9938-129">Abra PowerShell como administrador.</span><span class="sxs-lookup"><span data-stu-id="f9938-129">Open PowerShell as an administrator</span></span>
  2. <span data-ttu-id="f9938-130">Ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="f9938-130">Run the following command</span></span>

     ```powershell
     Set-SilLogging -TargetUri https://BlankTarget -CertificateThumbprint 0123456789
     ```

  3. <span data-ttu-id="f9938-131">Ejecute el comando y omita el error, tal como se espera.</span><span class="sxs-lookup"><span data-stu-id="f9938-131">Run the command and ignore the error, as they are expected.</span></span>

     ```powershell
     Publish-SilData
     ```

  4. <span data-ttu-id="f9938-132">Elimine los archivos del directorio \Windows\System32\Logfiles\SIL\.</span><span class="sxs-lookup"><span data-stu-id="f9938-132">Delete the files in  \Windows\System32\Logfiles\SIL\ directory</span></span>

     ```powershell
     Remove-Item -Recurse $env:SystemRoot\System32\Logfiles\SIL\
     ```

  5. <span data-ttu-id="f9938-133">Instale todas las actualizaciones disponibles de Windows importantes y comience a utilizar Sysyprep con normalidad.</span><span class="sxs-lookup"><span data-stu-id="f9938-133">Install all available important Windows Updates, and begin Sysyprep operation normally.</span></span>

- <span data-ttu-id="f9938-134">Para sistemas que ejecutan **Windows Server 2012**</span><span class="sxs-lookup"><span data-stu-id="f9938-134">For systems running **Windows Server 2012**</span></span>
  1. <span data-ttu-id="f9938-135">Después de instalar WMF 5.0 en el servidor para la preparación del sistema con Sysprep, inicie sesión como administrador.</span><span class="sxs-lookup"><span data-stu-id="f9938-135">After installing WMF 5.0 on the server to be Sysprep'd, login as administrator.</span></span>
  2. <span data-ttu-id="f9938-136">Copie Generize.xml desde el directorio `\Windows\System32\Sysprep\ActionFiles\` a una ubicación fuera del directorio de Windows, por ejemplo, `C:\`.</span><span class="sxs-lookup"><span data-stu-id="f9938-136">Copy Generize.xml from directory `\Windows\System32\Sysprep\ActionFiles\` to a location outside of the Windows directory, `C:\` for example.</span></span>
  3. <span data-ttu-id="f9938-137">Abra la copia de Generalize.xml con el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="f9938-137">Open your Generalize.xml copy with notepad.</span></span>
  4. <span data-ttu-id="f9938-138">Busque y quite el texto siguiente; hay que eliminar una instancia de cada caso (se encuentran casi al final del documento).</span><span class="sxs-lookup"><span data-stu-id="f9938-138">Find and remove the following text, one instance of each needs to be deleted (they will be near the end of the document).</span></span>

     ```xml
     <sysprepOrder order="0x3200"></sysprepOrder>
     <sysprepOrder order="0x3300"></sysprepOrder>
     ```

  5. <span data-ttu-id="f9938-139">Guarde la copia modificada de Generalize.xml y cierre el archivo.</span><span class="sxs-lookup"><span data-stu-id="f9938-139">Save the edited copy of Generalize.xml and close the file.</span></span>
  6. <span data-ttu-id="f9938-140">Abra una ventana del símbolo del sistema como administrador.</span><span class="sxs-lookup"><span data-stu-id="f9938-140">Open a command prompt as administrator</span></span>
  7. <span data-ttu-id="f9938-141">Ejecute el siguiente comando para adquirir la titularidad del archivo Generalize.xml en la carpeta system32:</span><span class="sxs-lookup"><span data-stu-id="f9938-141">Run the following command to take ownership of the Generalize.xml file in system32 folder:</span></span>

     ```powershell
     Takeown /f C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

  8. <span data-ttu-id="f9938-142">Ejecute el siguiente comando para establecer los permisos adecuados en el archivo:</span><span class="sxs-lookup"><span data-stu-id="f9938-142">Run the following command to set appropriate permission on the file:</span></span>

     ```powershell
     Cacls C:\Windows\System32\ Sysprep\ActionFiles\Generalize.xml /G `<AdministratorUserName>`:F
     ```

     - <span data-ttu-id="f9938-143">Responda de manera afirmativa cuando se le solicite confirmación.</span><span class="sxs-lookup"><span data-stu-id="f9938-143">Answer Yes at the prompt for confirmation.</span></span>
     - <span data-ttu-id="f9938-144">Tenga en cuenta que `<AdministratorUserName>` se debe reemplazar por el nombre de usuario administrador en el equipo.</span><span class="sxs-lookup"><span data-stu-id="f9938-144">Note that `<AdministratorUserName>` should be replaced by the username who is administrator on the machine.</span></span> <span data-ttu-id="f9938-145">Por ejemplo, "Administrador".</span><span class="sxs-lookup"><span data-stu-id="f9938-145">For example, "Administrator".</span></span>

  9. <span data-ttu-id="f9938-146">Copie el archivo modificado que ha guardado en el directorio Sysprep; para ello, use el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="f9938-146">Copy the file you edited and saved over to the Sysprep directory using the following command:</span></span>

     ```powershell
     xcopy C:\Generalize.xml C:\Windows\System32\Sysprep\ActionFiles\Generalize.xml
     ```

     - <span data-ttu-id="f9938-147">Responda de manera afirmativa para sobrescribir (tenga en cuenta que si no aparece ningún mensaje para sobrescribir, debe comprobar la ruta de acceso especificada).</span><span class="sxs-lookup"><span data-stu-id="f9938-147">Answer Yes to overwrite (note that if there is no prompt to overwrite, double check the path entered).</span></span>
     - <span data-ttu-id="f9938-148">Se supone que la copia modificada de Generalize.xml se ha copiado en C:\.</span><span class="sxs-lookup"><span data-stu-id="f9938-148">Assumes your edited copy of Generalize.xml was copied to C:\ .</span></span>

  10. <span data-ttu-id="f9938-149">Generalize.xml se ha actualizado con la solución alternativa.</span><span class="sxs-lookup"><span data-stu-id="f9938-149">Generalize.xml is now updated with the workaround.</span></span> <span data-ttu-id="f9938-150">Ejecute Sysprep con la opción de generalizar habilitada.</span><span class="sxs-lookup"><span data-stu-id="f9938-150">Please run Sysprep with the generalize option enabled.</span></span>