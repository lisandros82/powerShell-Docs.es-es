---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: Solucionar problemas con cmdlets
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328306"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="fbe96-103">Solucionar problemas con cmdlets</span><span class="sxs-lookup"><span data-stu-id="fbe96-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="fbe96-104">Cómo resolver el problema "WARNING: Package 'your package name' failed to download" ("ADVERTENCIA: No se pudo descargar el paquete 'nombre del paquete'")</span><span class="sxs-lookup"><span data-stu-id="fbe96-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="fbe96-105">Se notifica que a veces se produce un error de `Install-Module` o `Update-Module` en algunos equipos.</span><span class="sxs-lookup"><span data-stu-id="fbe96-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="fbe96-106">Según nuestras investigaciones, este problema está relacionado con la conexión de red.</span><span class="sxs-lookup"><span data-stu-id="fbe96-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="fbe96-107">Hemos actualizado recientemente el proveedor de NuGet para que pueda descargar paquetes de forma confiable.</span><span class="sxs-lookup"><span data-stu-id="fbe96-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="fbe96-108">Puede seguir las instrucciones siguientes para instalar la compilación más reciente del proveedor de NuGet y, después, instalar o actualizar el módulo.</span><span class="sxs-lookup"><span data-stu-id="fbe96-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="fbe96-109">En este ejemplo se usa el módulo "Azure".</span><span class="sxs-lookup"><span data-stu-id="fbe96-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
