---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Instalación de PowerShellGet
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143589"
---
# <a name="installing-powershellget"></a><span data-ttu-id="91694-103">Instalación de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="91694-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="91694-104">PowerShellGet es un módulo incluido en las versiones siguientes</span><span class="sxs-lookup"><span data-stu-id="91694-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="91694-105">[Windows 10](https://www.microsoft.com/windows) o posterior</span><span class="sxs-lookup"><span data-stu-id="91694-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="91694-106">[Windows Server 2016](/windows-server/windows-server) o posterior</span><span class="sxs-lookup"><span data-stu-id="91694-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="91694-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) o posterior</span><span class="sxs-lookup"><span data-stu-id="91694-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="91694-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="91694-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="91694-109">Obtención de la versión más reciente en la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="91694-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="91694-110">Antes de actualizar **PowerShellGet**, siempre debe instalar el proveedor de **NuGet** más reciente.</span><span class="sxs-lookup"><span data-stu-id="91694-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="91694-111">En una sesión de PowerShell con privilegios elevados, ejecute el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="91694-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="91694-112">En sistemas con PowerShell 5.0 (o posterior), puede instalar el módulo PowerShellGet más reciente</span><span class="sxs-lookup"><span data-stu-id="91694-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="91694-113">Para instalar PowerShellGet en Windows 10, Windows Server 2016, cualquier sistema con WMF 5.0 o 5.1 instalado o cualquier sistema con PowerShell 6, ejecute los comandos siguientes desde una sesión de PowerShell con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="91694-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="91694-114">Use `Update-Module` para obtener las versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="91694-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a><span data-ttu-id="91694-115">En sistemas que ejecutan PowerShell 3 o PowerShell 4 que tengan instalada la versión preliminar de PackageManagement</span><span class="sxs-lookup"><span data-stu-id="91694-115">For systems running PowerShell 3 or PowerShell 4, that have installed the PackageManagement Preview</span></span>

1. <span data-ttu-id="91694-116">Desde una sesión de PowerShell con privilegios elevados, use `Save-Module` para guardar los módulos en un directorio local.</span><span class="sxs-lookup"><span data-stu-id="91694-116">From an elevated PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. <span data-ttu-id="91694-117">Asegúrese de que los módulos **PowerShellGet** y **PackageManagement** no estén cargados en ningún otro proceso.</span><span class="sxs-lookup"><span data-stu-id="91694-117">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="91694-118">Elimine el contenido de las carpetas`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` y `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="91694-118">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="91694-119">Vuelva a abrir la consola de PowerShell con permisos elevados y, luego, ejecute los comandos siguientes.</span><span class="sxs-lookup"><span data-stu-id="91694-119">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
