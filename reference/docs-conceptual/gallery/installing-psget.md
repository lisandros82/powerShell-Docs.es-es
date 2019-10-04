---
ms.date: 09/19/2019
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Instalación de PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328206"
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

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>Para equipos que ejecutan PowerShell 3.0 o PowerShell 4.0

Estas instrucciones se aplican a los equipos que tienen instalada la **versión preliminar de PackageManagement** o que no tienen ninguna versión de **PowerShellGet** instalada.

El cmdlet `Save-Module` se usa en ambos conjuntos de instrucciones. `Save-Module` descarga y guarda un módulo y las dependencias de un repositorio registrado. La versión más reciente del módulo se guarda en una ruta de acceso especificada en el equipo local, pero no está instalada. Para obtener más información, vea [Save-Module](/powershell/module/PowershellGet/Save-Module).

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>Equipos con la versión preliminar de PackageManagement instalada.

1. Desde una sesión de PowerShell, use `Save-Module` para guardar los módulos en un directorio local.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Asegúrese de que los módulos **PowerShellGet** y **PackageManagement** no estén cargados en ningún otro proceso.
1. Elimine el contenido de las carpetas`$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` y `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
1. Vuelva a abrir la consola de PowerShell con permisos elevados y, luego, ejecute los comandos siguientes.

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a>Equipos sin PowerShellGet

En el caso de los equipos que no tienen instalada ninguna versión de **PowerShellGet**, se necesita un equipo con **PowerShellGet** para descargar los módulos.

1. En el equipo en el que se ha instalado **PowerShellGet**, use `Save-Module` para descargar la versión actual de **PowerShellGet**. Se descargan dos carpetas: **PowerShellGet** y **PackageManagement**. Cada carpeta contiene una subcarpeta con un número de versión.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Copie las carpetas de **PowerShellGe** y **PackageManagement** en el equipo que no tenga **PowerShellGet** instalado.

   El directorio de destino es: `$env:ProgramFiles\WindowsPowerShell\Modules`
