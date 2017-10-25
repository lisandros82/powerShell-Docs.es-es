---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: ccb39f44e8d11f1e2a912da0c4f18b700e836c91
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Cómo resolver el problema "WARNING: Package 'your package name' failed to download" (ADVERTENCIA: No se pudo descargar el paquete 'nombre del paquete'")




Se ha notificado que a veces se produce un error en Install-Module o Update-Module en algunos equipos.
Según nuestras investigaciones, este problema está relacionado con la conexión de red.
Hemos actualizado recientemente el proveedor de NuGet para que pueda descargar paquetes de forma confiable.
Puede seguir las instrucciones siguientes para instalar la compilación más reciente del proveedor de NuGet y, después, instalar o actualizar el módulo.
En este ejemplo se usa el módulo "Azure".

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

