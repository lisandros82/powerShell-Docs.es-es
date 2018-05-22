---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Instalación de PowerShellGet
ms.openlocfilehash: 35be7d02ea856ea39218f05d32b43c60fa1bd53e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="installing-powershellget"></a><span data-ttu-id="29d6a-103">Instalación de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="29d6a-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="29d6a-104">PowerShellGet es un módulo incluido en las versiones siguientes</span><span class="sxs-lookup"><span data-stu-id="29d6a-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="29d6a-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) o posterior</span><span class="sxs-lookup"><span data-stu-id="29d6a-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) or newer</span></span>
- <span data-ttu-id="29d6a-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) o posterior</span><span class="sxs-lookup"><span data-stu-id="29d6a-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) or newer</span></span>
- <span data-ttu-id="29d6a-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) o posterior</span><span class="sxs-lookup"><span data-stu-id="29d6a-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="29d6a-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="29d6a-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="29d6a-109">Obtención del módulo PowerShellGet para las versiones 3.0 y 4.0 de PowerShell</span><span class="sxs-lookup"><span data-stu-id="29d6a-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="29d6a-110">MSI de PackageManagement</span><span class="sxs-lookup"><span data-stu-id="29d6a-110">PackageManagement MSI</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="29d6a-111">Obtención de la versión más reciente en la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="29d6a-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="29d6a-112">Antes de actualizar PowerShellGet, siempre debe instalar el proveedor de NuGet más reciente.</span><span class="sxs-lookup"><span data-stu-id="29d6a-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="29d6a-113">Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="29d6a-113">To do that, run the following in an elevated PowerShell session.</span></span>

```powershell
Install-PackageProvider Nuget –Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="29d6a-114">En sistemas con PowerShell 5.0 (o posterior), puede instalar el módulo PowerShellGet más reciente</span><span class="sxs-lookup"><span data-stu-id="29d6a-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="29d6a-115">Para hacer esto en Windows 10, Windows Server 2016, cualquier sistema con WMF 5.0 o 5.1 instalado o cualquier sistema con PowerShell 6, ejecute los comandos siguientes desde una sesión de PowerShell con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="29d6a-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- <span data-ttu-id="29d6a-116">Use Update-Module para obtener versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="29d6a-116">Use Update-Module to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a><span data-ttu-id="29d6a-117">En sistemas que ejecutan PowerShell 3 o PowerShell 4 que tengan instalado el [MSI de PackageManagement](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="29d6a-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span></span>

- <span data-ttu-id="29d6a-118">Use el cmdlet de PowerShellGet siguiente desde una sesión de PowerShell con privilegios elevados para guardar los módulos en un directorio local</span><span class="sxs-lookup"><span data-stu-id="29d6a-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- <span data-ttu-id="29d6a-119">Asegúrese de que los módulos PowerShellGet y PackageManagement no estén cargados en ningún otro proceso.</span><span class="sxs-lookup"><span data-stu-id="29d6a-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="29d6a-120">Elimine el contenido de las carpetas `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` y `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="29d6a-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="29d6a-121">Vuelva a abrir la consola PS con permisos elevados y, luego, ejecute los comandos siguientes.</span><span class="sxs-lookup"><span data-stu-id="29d6a-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
```