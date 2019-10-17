---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Solucionar problemas con cmdlets
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352113"
---
# <a name="troubleshooting-cmdlets"></a>Solucionar problemas con cmdlets

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Cómo resolver el problema "WARNING: Package 'your package name' failed to download" ("ADVERTENCIA: No se pudo descargar el paquete 'nombre del paquete'")

Se notifica que a veces se produce un error de `Install-Module` o `Update-Module` en algunos equipos. Según nuestras investigaciones, este problema está relacionado con la conexión de red. Hemos actualizado recientemente el proveedor de NuGet para que pueda descargar paquetes de forma confiable. Puede seguir las instrucciones siguientes para instalar la compilación más reciente del proveedor de NuGet y, después, instalar o actualizar el módulo. En este ejemplo se usa el módulo "Azure".

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a>Puntos de conexión de red necesarios

Los cmdlets de instalación y actualización requieren acceso a Internet para conectarse a los puntos de conexión de red que usa la Galería de PowerShell. Asegúrese de que las directivas de acceso a la red le permitan conectarse a los puntos de conexión siguientes.

- oneget.org
- go.microsoft.com
- az818661.vo.msecnd.net
- www.powershellgallery.com
- devopsgallerystorage.blob.core.windows.net
