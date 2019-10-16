---
title: Instalación de un módulo de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367074"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="50515-102">Instalación de un módulo de PowerShell</span><span class="sxs-lookup"><span data-stu-id="50515-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="50515-103">Una vez creado el módulo de PowerShell, es probable que desee instalar el módulo en un sistema, de modo que usted u otros usuarios puedan usarlo.</span><span class="sxs-lookup"><span data-stu-id="50515-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="50515-104">Por lo general, esto consiste en copiar los archivos de módulo (por ej., psm1, el ensamblado binario, el manifiesto del módulo y cualquier otro archivo asociado) en un directorio de ese equipo.</span><span class="sxs-lookup"><span data-stu-id="50515-104">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="50515-105">Para un proyecto muy pequeño, puede ser tan sencillo como copiar y pegar los archivos con el explorador de Windows en un único equipo remoto. sin embargo, en el caso de soluciones de mayor tamaño, es posible que desee usar un proceso de instalación más sofisticado.</span><span class="sxs-lookup"><span data-stu-id="50515-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="50515-106">Independientemente de cómo obtenga el módulo en el sistema, PowerShell puede usar una serie de técnicas que permitirán a los usuarios buscar y usar los módulos.</span><span class="sxs-lookup"><span data-stu-id="50515-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="50515-107">Por lo tanto, el problema principal de la instalación es asegurarse de que PowerShell pueda encontrar el módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-107">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="50515-108">Para obtener más información, vea [importar un módulo de PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="50515-108">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="50515-109">Reglas para la instalación de módulos</span><span class="sxs-lookup"><span data-stu-id="50515-109">Rules for Installing Modules</span></span>

<span data-ttu-id="50515-110">La siguiente información pertenece a todos los módulos, incluidos los módulos que se crean para su propio uso, los módulos que se obtienen de otras partes y los módulos que se distribuyen a otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="50515-110">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="50515-111">Instalación de módulos en PSModulePath</span><span class="sxs-lookup"><span data-stu-id="50515-111">Install Modules in PSModulePath</span></span>

<span data-ttu-id="50515-112">Siempre que sea posible, instale todos los módulos en una ruta de acceso que aparece en la variable de entorno **PSModulePath** o agregue la ruta de acceso del módulo al valor de la variable de entorno **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="50515-112">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="50515-113">La variable de entorno **PSModulePath** ($env:P smodulepath) contiene las ubicaciones de los módulos de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50515-113">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="50515-114">Los cmdlets se basan en el valor de esta variable de entorno para buscar módulos.</span><span class="sxs-lookup"><span data-stu-id="50515-114">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="50515-115">De forma predeterminada, el valor de la variable de entorno **PSModulePath** contiene los siguientes directorios del módulo de usuario y del sistema, pero puede Agregar y editar el valor.</span><span class="sxs-lookup"><span data-stu-id="50515-115">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="50515-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="50515-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="50515-117">Esta ubicación está reservada para los módulos que se distribuyen con Windows.</span><span class="sxs-lookup"><span data-stu-id="50515-117">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="50515-118">No instale módulos en esta ubicación.</span><span class="sxs-lookup"><span data-stu-id="50515-118">Do not install modules to this location.</span></span>

- <span data-ttu-id="50515-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="50515-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="50515-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="50515-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="50515-121">Para obtener el valor de la variable de entorno **PSModulePath** , use cualquiera de los siguientes comandos.</span><span class="sxs-lookup"><span data-stu-id="50515-121">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="50515-122">Para agregar una ruta de acceso de módulo al valor del valor de la variable de entorno **PSModulePath** , use el siguiente formato de comando.</span><span class="sxs-lookup"><span data-stu-id="50515-122">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="50515-123">Este formato usa el método **SetEnvironmentVariable** de la clase **System. Environment** para hacer un cambio independiente de la sesión en la variable de entorno **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="50515-123">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="50515-124">Una vez que haya agregado la ruta de acceso a **PSModulePath**, debe difundir un mensaje de entorno sobre el cambio.</span><span class="sxs-lookup"><span data-stu-id="50515-124">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="50515-125">Difundir el cambio permite a otras aplicaciones, como el Shell, recoger el cambio.</span><span class="sxs-lookup"><span data-stu-id="50515-125">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="50515-126">Para difundir el cambio, haga que el código de instalación del producto envíe un mensaje **WM_SETTINGCHANGE** con `lParam` establecido en la cadena "entorno".</span><span class="sxs-lookup"><span data-stu-id="50515-126">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="50515-127">Asegúrese de enviar el mensaje después de que el código de instalación del módulo haya actualizado **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="50515-127">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="50515-128">Usar el nombre de directorio del módulo correcto</span><span class="sxs-lookup"><span data-stu-id="50515-128">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="50515-129">Un módulo con formato correcto es un módulo que se almacena en un directorio que tiene el mismo nombre que el nombre base de al menos un archivo en el directorio del módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-129">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="50515-130">Si un módulo no tiene el formato correcto, Windows PowerShell no lo reconoce como un módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-130">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="50515-131">El "nombre base" de un archivo es el nombre sin la extensión de nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="50515-131">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="50515-132">En un módulo con formato correcto, el nombre del directorio que contiene los archivos de módulo debe coincidir con el nombre base de al menos un archivo en el módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-132">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="50515-133">Por ejemplo, en el módulo Fabrikam de ejemplo, el directorio que contiene los archivos de módulo se denomina "fabrikam" y al menos un archivo tiene el nombre base "fabrikam".</span><span class="sxs-lookup"><span data-stu-id="50515-133">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="50515-134">En este caso, fabrikam. psd1 y fabrikam. dll tienen el nombre base "fabrikam".</span><span class="sxs-lookup"><span data-stu-id="50515-134">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="50515-135">Efecto de una instalación incorrecta</span><span class="sxs-lookup"><span data-stu-id="50515-135">Effect of Incorrect Installation</span></span>

<span data-ttu-id="50515-136">Si el módulo no tiene el formato correcto y su ubicación no se incluye en el valor de la variable de entorno **PSModulePath** , las características de detección básicas de Windows PowerShell, como la siguiente, no funcionan.</span><span class="sxs-lookup"><span data-stu-id="50515-136">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="50515-137">La característica de carga automática de módulos no puede importar automáticamente el módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-137">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="50515-138">El parámetro `ListAvailable` del cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) no puede encontrar el módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-138">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="50515-139">El cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) no puede encontrar el módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-139">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="50515-140">Para importar el módulo, debe proporcionar la ruta de acceso completa al archivo de módulo raíz o al archivo de manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-140">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="50515-141">Otras características, como las siguientes, no funcionan a menos que el módulo se importe en la sesión.</span><span class="sxs-lookup"><span data-stu-id="50515-141">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="50515-142">En los módulos con formato correcto de la variable de entorno **PSModulePath** , estas características funcionan incluso cuando el módulo no se importa en la sesión.</span><span class="sxs-lookup"><span data-stu-id="50515-142">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="50515-143">El cmdlet [get-command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) no puede encontrar comandos en el módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-143">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="50515-144">Los cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) y [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) no pueden actualizar ni guardar la ayuda del módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-144">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="50515-145">El cmdlet [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) no puede encontrar y mostrar los comandos en el módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-145">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="50515-146">Faltan los comandos del módulo en la ventana `Show-Command` en el entorno de scripting integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50515-146">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="50515-147">Dónde instalar los módulos</span><span class="sxs-lookup"><span data-stu-id="50515-147">Where to Install Modules</span></span>

<span data-ttu-id="50515-148">En esta sección se explica en qué parte del sistema de archivos se instalan los módulos de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="50515-148">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="50515-149">La ubicación depende de cómo se use el módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-149">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="50515-150">Instalación de módulos para un usuario específico</span><span class="sxs-lookup"><span data-stu-id="50515-150">Installing Modules for a Specific User</span></span>

<span data-ttu-id="50515-151">Si crea su propio módulo u obtiene un módulo de otra entidad, como un sitio web de la comunidad de Windows PowerShell, y desea que el módulo esté disponible solo para su cuenta de usuario, instale el módulo en el directorio de los módulos específicos del usuario.</span><span class="sxs-lookup"><span data-stu-id="50515-151">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="50515-152">De forma predeterminada, el directorio de módulos específico del usuario se agrega al valor de la variable de entorno **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="50515-152">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="50515-153">Instalación de módulos para todos los usuarios de archivos de programa</span><span class="sxs-lookup"><span data-stu-id="50515-153">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="50515-154">Si desea que un módulo esté disponible para todas las cuentas de usuario del equipo, instale el módulo en la ubicación de archivos de programa.</span><span class="sxs-lookup"><span data-stu-id="50515-154">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="50515-155">La ubicación de los archivos de programa se agrega al valor de la variable de entorno PSModulePath de forma predeterminada en Windows PowerShell 4,0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="50515-155">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="50515-156">En el caso de las versiones anteriores de Windows PowerShell, puede crear manualmente la ubicación de los archivos de programa ((%ProgramFiles%\WindowsPowerShell\Modules) y agregar esta ruta de acceso a la variable de entorno PSModulePath como se describió anteriormente.</span><span class="sxs-lookup"><span data-stu-id="50515-156">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="50515-157">Instalación de módulos en un directorio de producto</span><span class="sxs-lookup"><span data-stu-id="50515-157">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="50515-158">Si va a distribuir el módulo a otras entidades, use la ubicación predeterminada de los archivos de programa descritos anteriormente, o bien cree su propio subdirectorio específico de la empresa o específico del producto del directorio% ProgramFiles%.</span><span class="sxs-lookup"><span data-stu-id="50515-158">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="50515-159">Por ejemplo, Fabrikam Technologies, una empresa ficticia, envía un módulo de Windows PowerShell para su producto Fabrikam Manager.</span><span class="sxs-lookup"><span data-stu-id="50515-159">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="50515-160">Su instalador de módulos crea un subdirectorio modules en el subdirectorio Product de Fabrikam Manager.</span><span class="sxs-lookup"><span data-stu-id="50515-160">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="50515-161">Para habilitar las características de detección de módulos de Windows PowerShell para encontrar el módulo Fabrikam, el instalador del módulo de Fabrikam agrega la ubicación del módulo al valor de la variable de entorno **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="50515-161">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="50515-162">Instalación de módulos en el directorio de archivos comunes</span><span class="sxs-lookup"><span data-stu-id="50515-162">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="50515-163">Si un módulo se usa en varios componentes de un producto o en varias versiones de un producto, instale el módulo en un subdirectorio específico del módulo del subdirectorio%ProgramFiles%\Archivos Files\Modules.</span><span class="sxs-lookup"><span data-stu-id="50515-163">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="50515-164">En el ejemplo siguiente, el módulo Fabrikam se instala en un subdirectorio de Fabrikam del subdirectorio `%ProgramFiles%\Common Files\Modules`.</span><span class="sxs-lookup"><span data-stu-id="50515-164">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="50515-165">Tenga en cuenta que cada módulo reside en su propio subdirectorio en el subdirectorio modules.</span><span class="sxs-lookup"><span data-stu-id="50515-165">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="50515-166">A continuación, el instalador garantiza el valor de la variable de entorno **PSModulePath** incluye la ruta de acceso del subdirectorio de los módulos de archivos comunes.</span><span class="sxs-lookup"><span data-stu-id="50515-166">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="50515-167">Instalar varias versiones de un módulo</span><span class="sxs-lookup"><span data-stu-id="50515-167">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="50515-168">Para instalar varias versiones del mismo módulo, use el procedimiento siguiente.</span><span class="sxs-lookup"><span data-stu-id="50515-168">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="50515-169">Cree un directorio para cada versión del módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-169">Create a directory for each version of the module.</span></span> <span data-ttu-id="50515-170">Incluya el número de versión en el nombre del directorio.</span><span class="sxs-lookup"><span data-stu-id="50515-170">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="50515-171">Cree un manifiesto de módulo para cada versión del módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-171">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="50515-172">En el valor de la clave **ModuleVersion** del manifiesto, escriba el número de versión del módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-172">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="50515-173">Guarde el archivo de manifiesto (. psd1) en el directorio específico de la versión para el módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-173">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="50515-174">Agregue la ruta de acceso de la carpeta raíz del módulo al valor de la variable de entorno **PSModulePath** , como se muestra en los ejemplos siguientes.</span><span class="sxs-lookup"><span data-stu-id="50515-174">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="50515-175">Para importar una versión determinada del módulo, el usuario final puede usar los parámetros `MinimumVersion` o `RequiredVersion` del cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="50515-175">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="50515-176">Por ejemplo, si el módulo Fabrikam está disponible en las versiones 8,0 y 9,0, la estructura de directorios del módulo Fabrikam podría ser similar a la siguiente.</span><span class="sxs-lookup"><span data-stu-id="50515-176">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="50515-177">El instalador agrega las dos rutas de acceso del módulo al valor de la variable de entorno **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="50515-177">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="50515-178">Una vez completados estos pasos, el parámetro **ListAvailable** del cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) obtiene los dos módulos de fabrikam.</span><span class="sxs-lookup"><span data-stu-id="50515-178">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="50515-179">Para importar un módulo determinado, use los parámetros `MinimumVersion` o `RequiredVersion` del cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="50515-179">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="50515-180">Si ambos módulos se importan en la misma sesión y los módulos contienen cmdlets con los mismos nombres, los cmdlets que se importan en último lugar entran en vigor en la sesión.</span><span class="sxs-lookup"><span data-stu-id="50515-180">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="50515-181">Controlar conflictos de nombres de comando</span><span class="sxs-lookup"><span data-stu-id="50515-181">Handling Command Name Conflicts</span></span>

<span data-ttu-id="50515-182">Pueden producirse conflictos de nombres de comando cuando los comandos que exporta un módulo tienen el mismo nombre que los comandos de la sesión del usuario.</span><span class="sxs-lookup"><span data-stu-id="50515-182">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="50515-183">Cuando una sesión contiene dos comandos con el mismo nombre, Windows PowerShell ejecuta el tipo de comando que tiene prioridad.</span><span class="sxs-lookup"><span data-stu-id="50515-183">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="50515-184">Cuando una sesión contiene dos comandos que tienen el mismo nombre y el mismo tipo, Windows PowerShell ejecuta el comando que se agregó a la sesión más recientemente.</span><span class="sxs-lookup"><span data-stu-id="50515-184">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="50515-185">Para ejecutar un comando que no se ejecuta de forma predeterminada, los usuarios pueden calificar el nombre del comando con el nombre del módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-185">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="50515-186">Por ejemplo, si la sesión contiene una función `Get-Date` y el cmdlet `Get-Date`, Windows PowerShell ejecuta la función de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="50515-186">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="50515-187">Para ejecutar el cmdlet, anteponga al comando el nombre del módulo, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="50515-187">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="50515-188">Para evitar conflictos de nombres, los autores de módulos pueden usar la clave **DefaultCommandPrefix** en el manifiesto del módulo para especificar un prefijo de sustantivo para todos los comandos exportados desde el módulo.</span><span class="sxs-lookup"><span data-stu-id="50515-188">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="50515-189">Los usuarios pueden usar el parámetro **prefix** del cmdlet `Import-Module` para utilizar un prefijo alternativo.</span><span class="sxs-lookup"><span data-stu-id="50515-189">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="50515-190">El valor del parámetro **prefix** tiene prioridad sobre el valor de la clave **DefaultCommandPrefix** .</span><span class="sxs-lookup"><span data-stu-id="50515-190">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="50515-191">Véase también</span><span class="sxs-lookup"><span data-stu-id="50515-191">See Also</span></span>

[<span data-ttu-id="50515-192">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="50515-192">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="50515-193">Escribir un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="50515-193">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
