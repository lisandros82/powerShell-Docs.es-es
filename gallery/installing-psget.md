---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Instalación de PowerShellGet
ms.openlocfilehash: c385f7fbf6b688a11face9c3ebf4e6475a7b4c33
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893967"
---
# <a name="installing-powershellget"></a>Instalación de PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet es un módulo incluido en las versiones siguientes

- [Windows 10](https://www.microsoft.com/en-us/windows) o posterior
- [Windows Server 2016](/windows-server/windows-server) o posterior
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) o posterior
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Obtención del módulo PowerShellGet para las versiones 3.0 y 4.0 de PowerShell

- [MSI de PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Obtención de la versión más reciente en la Galería de PowerShell

- Antes de actualizar PowerShellGet, siempre debe instalar el proveedor de NuGet más reciente. Para ello, ejecute el siguiente comando en una sesión de PowerShell con privilegios elevados.

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>En sistemas con PowerShell 5.0 (o posterior), puede instalar el módulo PowerShellGet más reciente

- Para hacer esto en Windows 10, Windows Server 2016, cualquier sistema con WMF 5.0 o 5.1 instalado o cualquier sistema con PowerShell 6, ejecute los comandos siguientes desde una sesión de PowerShell con privilegios elevados.

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- Use `Update-Module` para obtener las versiones más recientes.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomen-usdownloaddetailsaspxid51451"></a>En sistemas que ejecutan PowerShell 3 o PowerShell 4 que tengan instalado el [MSI de PackageManagement](https://www.microsoft.com/en-us/download/details.aspx?id=51451)

- Use el cmdlet de PowerShellGet siguiente desde una sesión de PowerShell con privilegios elevados para guardar los módulos en un directorio local

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Asegúrese de que los módulos PowerShellGet y PackageManagement no estén cargados en ningún otro proceso.
- Elimine el contenido de las carpetas `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` y `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
- Vuelva a abrir la consola PS con permisos elevados y, luego, ejecute los comandos siguientes.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```