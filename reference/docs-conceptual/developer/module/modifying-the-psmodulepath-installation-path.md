---
title: Modificando la ruta de instalación de PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953847"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="b56fe-102">Cambio de la ruta de instalación de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="b56fe-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="b56fe-103">La variable de entorno `PSModulePath` almacena las rutas de acceso a las ubicaciones de los módulos que están instalados en el disco.</span><span class="sxs-lookup"><span data-stu-id="b56fe-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="b56fe-104">PowerShell usa esta variable para buscar módulos cuando el usuario no especifica la ruta de acceso completa a un módulo.</span><span class="sxs-lookup"><span data-stu-id="b56fe-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="b56fe-105">Las rutas de acceso de esta variable se buscan en el orden en que aparecen.</span><span class="sxs-lookup"><span data-stu-id="b56fe-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="b56fe-106">Cuando se inicia PowerShell, `PSModulePath` se crea como una variable de entorno del sistema con el siguiente valor predeterminado: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` o `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b56fe-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` or `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="b56fe-107">Para ver la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="b56fe-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="b56fe-108">Para ver las rutas de acceso que se especifican en la variable `PSModulePath`, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="b56fe-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="b56fe-109">Para agregar ubicaciones a la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="b56fe-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="b56fe-110">Para agregar rutas de acceso a esta variable, use uno de los métodos siguientes:</span><span class="sxs-lookup"><span data-stu-id="b56fe-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="b56fe-111">Para agregar un valor temporal que solo está disponible para la sesión actual, ejecute el siguiente comando en la línea de comandos:</span><span class="sxs-lookup"><span data-stu-id="b56fe-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="b56fe-112">Para agregar un valor persistente que esté disponible cada vez que se abra una sesión, agregue el comando anterior a un archivo de Perfil de PowerShell (`$PROFILE`) ></span><span class="sxs-lookup"><span data-stu-id="b56fe-112">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="b56fe-113">Para obtener más información sobre los perfiles, consulte [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="b56fe-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="b56fe-114">Para agregar una variable persistente al registro, cree una nueva variable de entorno de usuario denominada `PSModulePath` mediante el editor de variables de entorno en el cuadro de diálogo **propiedades del sistema** .</span><span class="sxs-lookup"><span data-stu-id="b56fe-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="b56fe-115">Para agregar una variable persistente mediante un script, use el método .net [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) en la clase [System. Environment](https://docs.microsoft.com/dotnet/api/system.environment) .</span><span class="sxs-lookup"><span data-stu-id="b56fe-115">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](https://docs.microsoft.com/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="b56fe-116">Por ejemplo, el siguiente script agrega el `C:\Program Files\Fabrikam\Module` ruta de acceso al valor de la variable de entorno `PSModulePath` para el equipo.</span><span class="sxs-lookup"><span data-stu-id="b56fe-116">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="b56fe-117">Para agregar la ruta de acceso a la variable de entorno User `PSModulePath`, establezca el destino en "User".</span><span class="sxs-lookup"><span data-stu-id="b56fe-117">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="b56fe-118">Para quitar ubicaciones de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="b56fe-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="b56fe-119">Puede quitar rutas de acceso de la variable mediante métodos similares: por ejemplo, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` quitará la ruta de acceso **c:\ModulePath** de la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="b56fe-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="b56fe-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="b56fe-120">See Also</span></span>

[<span data-ttu-id="b56fe-121">Escribir un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b56fe-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
