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
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794814"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="e0490-102">Cómo asignar un nombre a un archivo HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="e0490-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="e0490-103">En este tema se explica el formato de nombre requerido para los archivos de información de ayuda actualizable, conocidos como archivos XML HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="e0490-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="e0490-104">Cómo asignar un nombre a un archivo HelpInfo XML</span><span class="sxs-lookup"><span data-stu-id="e0490-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="e0490-105">Un archivo XML HelpInfo debe tener un nombre con el formato siguiente.</span><span class="sxs-lookup"><span data-stu-id="e0490-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="e0490-106">Los elementos del nombre son los siguientes.</span><span class="sxs-lookup"><span data-stu-id="e0490-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="e0490-107">ModuleName el valor de la **nombre** propiedad de la **ModuleInfo** objeto al que el [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devuelve.</span><span class="sxs-lookup"><span data-stu-id="e0490-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="e0490-108">ModuleGUID el valor de la **GUID** clave en el manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="e0490-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="e0490-109">Por ejemplo, si el nombre del módulo es "TestModule" y el GUID del módulo es 9cabb9ad f2ac 4914 a46b bfc1bebf07f9, sería el nombre del archivo XML HelpInfo para el módulo:</span><span class="sxs-lookup"><span data-stu-id="e0490-109">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`