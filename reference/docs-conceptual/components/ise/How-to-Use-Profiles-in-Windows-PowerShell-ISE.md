---
ms.date: 01/02/2020
keywords: powershell, cmdlet
title: Cómo usar perfiles en ISE de Windows PowerShell
ms.openlocfilehash: da7dc2f234ad0c2968fbb213e9e57da875f456e4
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736256"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="d2e24-103">Cómo usar perfiles en ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d2e24-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="d2e24-104">En este tema se explica cómo usar perfiles en el Entorno de scripting integrado (ISE) de Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="d2e24-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="d2e24-105">Antes de realizar las tareas de esta sección, se recomienda consultar [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles). O bien, en el panel de consola, escriba `Get-Help about_Profiles` y presione <kbd>ENTRAR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="d2e24-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press <kbd>ENTER</kbd>.</span></span>

<span data-ttu-id="d2e24-106">Un perfil es un script de Windows PowerShell ISE que se ejecuta automáticamente cuando se inicia una nueva sesión.</span><span class="sxs-lookup"><span data-stu-id="d2e24-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>
<span data-ttu-id="d2e24-107">Puede crear uno o varios perfiles de Windows PowerShell para Windows PowerShell ISE y usarlos para configurar el entorno de Windows PowerShell o Windows PowerShell ISE y prepararlo para su uso, con las variables, los alias, las funciones, y las preferencias de color y fuente que desee que estén disponibles.</span><span class="sxs-lookup"><span data-stu-id="d2e24-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="d2e24-108">Un perfil afecta a todas las sesiones de Windows PowerShell ISE que inicia.</span><span class="sxs-lookup"><span data-stu-id="d2e24-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="d2e24-109">La directiva de ejecución de Windows PowerShell determina si puede ejecutar scripts y cargar un perfil.</span><span class="sxs-lookup"><span data-stu-id="d2e24-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span>
> <span data-ttu-id="d2e24-110">La directiva de ejecución predeterminada, "Restricted", impide que se ejecuten todos los scripts, incluidos los perfiles.</span><span class="sxs-lookup"><span data-stu-id="d2e24-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span>
> <span data-ttu-id="d2e24-111">Si usa la directiva "Restricted", no se puede cargar el perfil.</span><span class="sxs-lookup"><span data-stu-id="d2e24-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="d2e24-112">Para obtener más información sobre la directiva de ejecución, vea [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="d2e24-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="d2e24-113">Seleccionar un perfil para usarlo en Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d2e24-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="d2e24-114">Windows PowerShell ISE admite perfiles para el usuario actual y para todos los usuarios.</span><span class="sxs-lookup"><span data-stu-id="d2e24-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="d2e24-115">También admite los perfiles de Windows PowerShell que se aplican a todos los hosts.</span><span class="sxs-lookup"><span data-stu-id="d2e24-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="d2e24-116">El perfil que use viene determinado por la forma en que se usa Windows PowerShell y Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d2e24-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="d2e24-117">Si solo usa Windows PowerShell ISE para ejecutar Windows PowerShell, guarde todos los elementos en uno de los perfiles específicos de ISE, como el perfil **CurrentUserCurrentHost** de Windows PowerShell ISE o el perfil **AllUsersCurrentHost** de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d2e24-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the **CurrentUserCurrentHost** profile for Windows PowerShell ISE or the **AllUsersCurrentHost** profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="d2e24-118">Si usa varios programas host para ejecutar Windows PowerShell, guarde sus funciones, alias, variables y comandos en un perfil que afecte a todos los programas host, como el perfil CurrentUserAllHosts o **AllUsersAllHosts** y guarde las características específicas de ISE, como la personalización de color y fuente en el perfil **CurrentUserCurrentHost** de Windows PowerShell ISE o el perfil **AllUsersCurrentHost** de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d2e24-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the **AllUsersAllHosts** profile, and save ISE-specific features, like color and font customization in the **CurrentUserCurrentHost** profile for Windows PowerShell ISE profile or the **AllUsersCurrentHost** profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="d2e24-119">Los siguientes son perfiles que se pueden crear y usar en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d2e24-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="d2e24-120">Cada perfil se guarda en su propia ruta de acceso específica.</span><span class="sxs-lookup"><span data-stu-id="d2e24-120">Each profile is saved to its own specific path.</span></span>

|           <span data-ttu-id="d2e24-121">Tipo de perfil</span><span class="sxs-lookup"><span data-stu-id="d2e24-121">Profile Type</span></span>           |                   <span data-ttu-id="d2e24-122">Ruta de acceso al perfil</span><span class="sxs-lookup"><span data-stu-id="d2e24-122">Profile Path</span></span>                   |
| -------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="d2e24-123">**Usuario actual, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="d2e24-123">**Current user, PowerShell ISE**</span></span> | <span data-ttu-id="d2e24-124">`$PROFILE.CurrentUserCurrentHost` o `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="d2e24-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="d2e24-125">**Todos los usuarios, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="d2e24-125">**All users, PowerShell ISE**</span></span>    | `$PROFILE.AllUsersCurrentHost`                   |
| <span data-ttu-id="d2e24-126">**Usuario actual, todos los hosts**</span><span class="sxs-lookup"><span data-stu-id="d2e24-126">**Current user, All hosts**</span></span>      | `$PROFILE.CurrentUserAllHosts`                   |
| <span data-ttu-id="d2e24-127">**Todos los usuarios, todos los hosts**</span><span class="sxs-lookup"><span data-stu-id="d2e24-127">**All users, All hosts**</span></span>         | `$PROFILE.AllUsersAllHosts`                      |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="d2e24-128">Para crear un nuevo perfil</span><span class="sxs-lookup"><span data-stu-id="d2e24-128">To create a new profile</span></span>

<span data-ttu-id="d2e24-129">Para crear un nuevo perfil "Usuario actual, Windows PowerShell ISE", ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="d2e24-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="d2e24-130">Para crear un nuevo perfil "Todos los usuarios, Windows PowerShell ISE", ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="d2e24-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="d2e24-131">Para crear un nuevo perfil "Usuario actual, todos los hosts", ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="d2e24-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="d2e24-132">Para crear un nuevo perfil "Todos los usuarios, todos los hosts", escriba:</span><span class="sxs-lookup"><span data-stu-id="d2e24-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="d2e24-133">Para editar un perfil</span><span class="sxs-lookup"><span data-stu-id="d2e24-133">To edit a profile</span></span>

1. <span data-ttu-id="d2e24-134">Para abrir el perfil, ejecute el comando `psEdit` con la variable que especifica el perfil que quiere editar.</span><span class="sxs-lookup"><span data-stu-id="d2e24-134">To open the profile, run the command `psEdit` with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="d2e24-135">Por ejemplo, para abrir el perfil "Usuario actual, Windows PowerShell ISE", escriba: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="d2e24-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="d2e24-136">Agregue algunos elementos a su perfil.</span><span class="sxs-lookup"><span data-stu-id="d2e24-136">Add some items to your profile.</span></span> <span data-ttu-id="d2e24-137">Estos son algunos ejemplos para comenzar:</span><span class="sxs-lookup"><span data-stu-id="d2e24-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="d2e24-138">Para cambiar el color de fondo predeterminado del panel de consola a azul, en el archivo de perfil, escriba: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="d2e24-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="d2e24-139">Para más información sobre la variable `$psISE`, consulte [Referencia del modelo de objetos de Windows PowerShell ISE](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="d2e24-139">For more information about the `$psISE` variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="d2e24-140">Para cambiar el tamaño de fuente a 20, en el archivo de perfil, escriba: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="d2e24-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="d2e24-141">Para guardar el archivo de perfil, en el menú **Archivo**, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="d2e24-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="d2e24-142">La próxima vez que abra Windows PowerShell ISE, se aplicarán sus opciones personalizadas.</span><span class="sxs-lookup"><span data-stu-id="d2e24-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2e24-143">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d2e24-143">See Also</span></span>

- [<span data-ttu-id="d2e24-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="d2e24-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="d2e24-145">Presentación de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d2e24-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
