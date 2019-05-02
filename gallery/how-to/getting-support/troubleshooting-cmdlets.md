---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Solucionar problemas con cmdlets
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084188"
---
# <a name="troubleshooting-cmdlets"></a>Solucionar problemas con cmdlets

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Cómo resolver el problema "WARNING: Package 'your package name' failed to download" ("ADVERTENCIA: No se pudo descargar el paquete 'nombre del paquete'")

Se notifica que a veces se produce un error de `Install-Module` o `Update-Module` en algunos equipos.
Según nuestras investigaciones, este problema está relacionado con la conexión de red.
Hemos actualizado recientemente el proveedor de NuGet para que pueda descargar paquetes de forma confiable.
Puede seguir las instrucciones siguientes para instalar la compilación más reciente del proveedor de NuGet y, después, instalar o actualizar el módulo.
En este ejemplo se usa el módulo "Azure".

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
