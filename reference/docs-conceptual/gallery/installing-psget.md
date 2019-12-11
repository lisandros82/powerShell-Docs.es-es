---
ms.date: 09/19/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Instalación de PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328206"
---
# <a name="installing-powershellget"></a><span data-ttu-id="d98db-103">Instalación de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d98db-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="d98db-104">PowerShellGet es un módulo incluido en las versiones siguientes</span><span class="sxs-lookup"><span data-stu-id="d98db-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="d98db-105">[Windows 10](https://www.microsoft.com/windows) o posterior</span><span class="sxs-lookup"><span data-stu-id="d98db-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="d98db-106">[Windows Server 2016](/windows-server/windows-server) o posterior</span><span class="sxs-lookup"><span data-stu-id="d98db-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="d98db-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) o posterior</span><span class="sxs-lookup"><span data-stu-id="d98db-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="d98db-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="d98db-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="d98db-109">Obtención de la versión más reciente en la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d98db-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="d98db-110">Antes de actualizar **PowerShellGet**, siempre debe instalar el proveedor de **NuGet** más reciente.</span><span class="sxs-lookup"><span data-stu-id="d98db-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="d98db-111">En una sesión de PowerShell con privilegios elevados, ejecute el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="d98db-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="d98db-112">En sistemas con PowerShell 5.0 (o posterior), puede instalar el módulo PowerShellGet más reciente</span><span class="sxs-lookup"><span data-stu-id="d98db-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="d98db-113">Para instalar PowerShellGet en Windows 10, Windows Server 2016, cualquier sistema con WMF 5.0 o 5.1 instalado o cualquier sistema con PowerShell 6, ejecute los comandos siguientes desde una sesión de PowerShell con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="d98db-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="d98db-114">Use `Update-Module` para obtener las versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="d98db-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="d98db-115">Para equipos que ejecutan PowerShell 3.0 o PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="d98db-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="d98db-116">Estas instrucciones se aplican a los equipos que tienen instalada la **versión preliminar de PackageManagement** o que no tienen ninguna versión de **PowerShellGet** instalada.</span><span class="sxs-lookup"><span data-stu-id="d98db-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="d98db-117">El cmdlet `Save-Module` se usa en ambos conjuntos de instrucciones.</span><span class="sxs-lookup"><span data-stu-id="d98db-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="d98db-118">`Save-Module` descarga y guarda un módulo y las dependencias de un repositorio registrado.</span><span class="sxs-lookup"><span data-stu-id="d98db-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="d98db-119">La versión más reciente del módulo se guarda en una ruta de acceso especificada en el equipo local, pero no está instalada.</span><span class="sxs-lookup"><span data-stu-id="d98db-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="d98db-120">Para obtener más información, vea [Save-Module](/powershell/module/PowershellGet/Save-Module).</span><span class="sxs-lookup"><span data-stu-id="d98db-120">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="d98db-121">Equipos con la versión preliminar de PackageManagement instalada.</span><span class="sxs-lookup"><span data-stu-id="d98db-121">Computers with the PackageManagement Preview installed</span></span>

1. <span data-ttu-id="d98db-122">Desde una sesión de PowerShell, use `Save-Module` para guardar los módulos en un directorio local.</span><span class="sxs-lookup"><span data-stu-id="d98db-122">From a PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="d98db-123">Asegúrese de que los módulos **PowerShellGet** y **PackageManagement** no estén cargados en ningún otro proceso.</span><span class="sxs-lookup"><span data-stu-id="d98db-123">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="d98db-124">Elimine el contenido de las carpetas`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` y `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="d98db-124">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="d98db-125">Vuelva a abrir la consola de PowerShell con permisos elevados y, luego, ejecute los comandos siguientes.</span><span class="sxs-lookup"><span data-stu-id="d98db-125">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="d98db-126">Equipos sin PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d98db-126">Computers without PowerShellGet</span></span>

<span data-ttu-id="d98db-127">En el caso de los equipos que no tienen instalada ninguna versión de **PowerShellGet**, se necesita un equipo con **PowerShellGet** para descargar los módulos.</span><span class="sxs-lookup"><span data-stu-id="d98db-127">For computer's without any version of **PowerShellGet** installed, a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="d98db-128">En el equipo en el que se ha instalado **PowerShellGet**, use `Save-Module` para descargar la versión actual de **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="d98db-128">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="d98db-129">Se descargan dos carpetas: **PowerShellGet** y **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="d98db-129">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="d98db-130">Cada carpeta contiene una subcarpeta con un número de versión.</span><span class="sxs-lookup"><span data-stu-id="d98db-130">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="d98db-131">Copie las carpetas de **PowerShellGe** y **PackageManagement** en el equipo que no tenga **PowerShellGet** instalado.</span><span class="sxs-lookup"><span data-stu-id="d98db-131">Copy the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed.</span></span>

   <span data-ttu-id="d98db-132">El directorio de destino es: `$env:ProgramFiles\WindowsPowerShell\Modules`</span><span class="sxs-lookup"><span data-stu-id="d98db-132">The destination directory is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span></span>
