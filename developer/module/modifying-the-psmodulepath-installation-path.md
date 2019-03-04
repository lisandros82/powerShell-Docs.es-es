---
title: Modificar la ruta de instalación PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855571"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="608b7-102">Cambio de la ruta de instalación de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="608b7-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="608b7-103">El `PSModulePath` variable de entorno almacena las rutas de acceso a las ubicaciones de los módulos que están instalados en el disco.</span><span class="sxs-lookup"><span data-stu-id="608b7-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="608b7-104">Windows PowerShell usa esta variable para buscar módulos cuando el usuario no especifica la ruta de acceso completa a un módulo.</span><span class="sxs-lookup"><span data-stu-id="608b7-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="608b7-105">Las rutas de acceso en esta variable se buscan en el orden en que aparecen.</span><span class="sxs-lookup"><span data-stu-id="608b7-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="608b7-106">Cuando se inicia Windows PowerShell, `PSModulePath` se crea como una variable de entorno del sistema con el siguiente valor predeterminado: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="608b7-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="608b7-107">Para ver la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="608b7-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="608b7-108">Para ver las rutas de acceso que se especifican en el `PSModulePath` variable, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="608b7-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="608b7-109">Agregar ubicaciones a la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="608b7-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="608b7-110">Para agregar las rutas de acceso a esta variable, use uno de los métodos siguientes:</span><span class="sxs-lookup"><span data-stu-id="608b7-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="608b7-111">Para agregar un valor temporal que sólo está disponible para la sesión actual, ejecute el siguiente comando en la línea de comandos:</span><span class="sxs-lookup"><span data-stu-id="608b7-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="608b7-112">Para agregar un valor persistente que está disponible cada vez que se abre una sesión, agregue el siguiente comando para un perfil de Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="608b7-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="608b7-113">Para obtener más información acerca de los perfiles, consulte [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) en la biblioteca TechNet de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="608b7-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="608b7-114">Para agregar una variable persistente en el registro, cree una nueva variable de entorno de usuario denominada `PSModulePath` con el Editor de Variables de entorno en el **las propiedades del sistema** cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="608b7-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="608b7-115">Para agregar una variable persistente mediante un script, use el **SetEnvironmentVariable** método en la clase de entorno.</span><span class="sxs-lookup"><span data-stu-id="608b7-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="608b7-116">Por ejemplo, el script siguiente agrega el "C:\Program Files\Fabrikam\Module ruta de acceso al valor de la variable de entorno PSModulePath para el equipo.</span><span class="sxs-lookup"><span data-stu-id="608b7-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="608b7-117">Para agregar la ruta de acceso a la variable de entorno PSModulePath de usuario, establecer el destino en "Usuario".</span><span class="sxs-lookup"><span data-stu-id="608b7-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="608b7-118">Para quitar las ubicaciones de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="608b7-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="608b7-119">Puede quitar las rutas de acceso de la variable mediante métodos similares: por ejemplo, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` quitará el **c:\ModulePath** ruta de acceso de la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="608b7-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="608b7-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="608b7-120">See Also</span></span>

[<span data-ttu-id="608b7-121">Escribir un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="608b7-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
