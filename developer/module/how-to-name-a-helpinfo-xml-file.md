---
title: Cómo denominar un archivo XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857831"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="c8405-102">Cómo asignar un nombre a un archivo HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="c8405-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="c8405-103">En este tema se explica el formato de nombre requerido para los archivos de información de ayuda actualizable, conocidos como archivos XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="c8405-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="c8405-104">Cómo asignar un nombre a un archivo HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="c8405-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="c8405-105">Un archivo XML HelpInfo debe tener un nombre con el formato siguiente.</span><span class="sxs-lookup"><span data-stu-id="c8405-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="c8405-106">Los elementos del nombre son los siguientes.</span><span class="sxs-lookup"><span data-stu-id="c8405-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="c8405-107">ModuleName el valor de la **nombre** propiedad de la **ModuleInfo** objeto al que el [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devuelve.</span><span class="sxs-lookup"><span data-stu-id="c8405-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
<span data-ttu-id="c8405-108">El valor de la **nombre** propiedad de la **ModuleInfo** objeto al que el [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devuelve.</span><span class="sxs-lookup"><span data-stu-id="c8405-108">The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="c8405-109">ModuleGUID el valor de la **GUID** clave en el manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="c8405-109">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="c8405-110">Por ejemplo, si el nombre del módulo es "TestModule" y el GUID del módulo es 9cabb9ad f2ac 4914 a46b bfc1bebf07f9, sería el nombre del archivo XML HelpInfo para el módulo:</span><span class="sxs-lookup"><span data-stu-id="c8405-110">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`