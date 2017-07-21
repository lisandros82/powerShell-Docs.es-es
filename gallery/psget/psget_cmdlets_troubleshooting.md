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
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="3b2f6-103">Cómo resolver el problema "WARNING: Package 'your package name' failed to download" (ADVERTENCIA: No se pudo descargar el paquete 'nombre del paquete'")</span><span class="sxs-lookup"><span data-stu-id="3b2f6-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="3b2f6-104">Se ha notificado que a veces se produce un error en Install-Module o Update-Module en algunos equipos.</span><span class="sxs-lookup"><span data-stu-id="3b2f6-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="3b2f6-105">Según nuestras investigaciones, este problema está relacionado con la conexión de red.</span><span class="sxs-lookup"><span data-stu-id="3b2f6-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="3b2f6-106">Hemos actualizado recientemente el proveedor de NuGet para que pueda descargar paquetes de forma confiable.</span><span class="sxs-lookup"><span data-stu-id="3b2f6-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="3b2f6-107">Puede seguir las instrucciones siguientes para instalar la compilación más reciente del proveedor de NuGet y, después, instalar o actualizar el módulo.</span><span class="sxs-lookup"><span data-stu-id="3b2f6-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="3b2f6-108">En este ejemplo se usa el módulo "Azure".</span><span class="sxs-lookup"><span data-stu-id="3b2f6-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

