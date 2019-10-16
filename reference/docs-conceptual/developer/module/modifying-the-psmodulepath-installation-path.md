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
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360674"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="fd0a8-102">Cambio de la ruta de instalación de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="fd0a8-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="fd0a8-103">La variable de entorno `PSModulePath` almacena las rutas de acceso a las ubicaciones de los módulos que están instalados en el disco.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="fd0a8-104">Windows PowerShell usa esta variable para buscar módulos cuando el usuario no especifica la ruta de acceso completa a un módulo.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="fd0a8-105">Las rutas de acceso de esta variable se buscan en el orden en que aparecen.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="fd0a8-106">Cuando Windows PowerShell se inicia, se crea `PSModulePath` como una variable de entorno del sistema con el siguiente valor predeterminado: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="fd0a8-107">Para ver la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="fd0a8-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="fd0a8-108">Para ver las rutas de acceso especificadas en la variable `PSModulePath`, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="fd0a8-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="fd0a8-109">Para agregar ubicaciones a la variable PSModulePath</span><span class="sxs-lookup"><span data-stu-id="fd0a8-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="fd0a8-110">Para agregar rutas de acceso a esta variable, use uno de los métodos siguientes:</span><span class="sxs-lookup"><span data-stu-id="fd0a8-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="fd0a8-111">Para agregar un valor temporal que solo está disponible para la sesión actual, ejecute el siguiente comando en la línea de comandos:</span><span class="sxs-lookup"><span data-stu-id="fd0a8-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="fd0a8-112">Para agregar un valor persistente que esté disponible cada vez que se abra una sesión, agregue el siguiente comando a un perfil de Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fd0a8-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="fd0a8-113">Para obtener más información acerca de los perfiles, consulte [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) en la biblioteca de Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="fd0a8-114">Para agregar una variable persistente al registro, cree una nueva variable de entorno de usuario llamada `PSModulePath` mediante el editor de variables de entorno en el cuadro de diálogo **propiedades del sistema** .</span><span class="sxs-lookup"><span data-stu-id="fd0a8-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="fd0a8-115">Para agregar una variable persistente mediante un script, use el método **SetEnvironmentVariable** en la clase Environment.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="fd0a8-116">Por ejemplo, el siguiente script agrega la ruta de acceso "C:\Archivos de Files\Fabrikam\Module al valor de la variable de entorno PSModulePath para el equipo.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="fd0a8-117">Para agregar la ruta de acceso a la variable de entorno User PSModulePath, establezca el destino en "User".</span><span class="sxs-lookup"><span data-stu-id="fd0a8-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="fd0a8-118">Para quitar ubicaciones de PSModulePath</span><span class="sxs-lookup"><span data-stu-id="fd0a8-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="fd0a8-119">Puede quitar rutas de acceso de la variable mediante métodos similares: por ejemplo, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` quitará la ruta de acceso **c:\ModulePath** de la sesión actual.</span><span class="sxs-lookup"><span data-stu-id="fd0a8-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd0a8-120">Véase también</span><span class="sxs-lookup"><span data-stu-id="fd0a8-120">See Also</span></span>

[<span data-ttu-id="fd0a8-121">Escribir un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd0a8-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
