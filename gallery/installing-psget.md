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
# <a name="installing-powershellget"></a>Instalación de PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet es un módulo incluido en las versiones siguientes

- [Windows 10](https://www.microsoft.com/windows) o posterior
- [Windows Server 2016](/windows-server/windows-server) o posterior
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) o posterior
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Obtención de la versión más reciente en la Galería de PowerShell

Antes de actualizar **PowerShellGet**, siempre debe instalar el proveedor de **NuGet** más reciente. En una sesión de PowerShell con privilegios elevados, ejecute el comando siguiente.

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>En sistemas con PowerShell 5.0 (o posterior), puede instalar el módulo PowerShellGet más reciente

Para instalar PowerShellGet en Windows 10, Windows Server 2016, cualquier sistema con WMF 5.0 o 5.1 instalado o cualquier sistema con PowerShell 6, ejecute los comandos siguientes desde una sesión de PowerShell con privilegios elevados.

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

Use `Update-Module` para obtener las versiones más recientes.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a>En sistemas que ejecutan PowerShell 3 o PowerShell 4 que tengan instalada la versión preliminar de PackageManagement

1. Desde una sesión de PowerShell con privilegios elevados, use `Save-Module` para guardar los módulos en un directorio local.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. Asegúrese de que los módulos **PowerShellGet** y **PackageManagement** no estén cargados en ningún otro proceso.
1. Elimine el contenido de las carpetas`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` y `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
1. Vuelva a abrir la consola de PowerShell con permisos elevados y, luego, ejecute los comandos siguientes.

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
