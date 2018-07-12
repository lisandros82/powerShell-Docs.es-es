---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Solucionar problemas con cmdlets
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892481"
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