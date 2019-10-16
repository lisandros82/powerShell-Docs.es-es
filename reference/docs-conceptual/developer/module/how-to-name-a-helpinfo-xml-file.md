---
title: Cómo asignar un nombre a un archivo XML de HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367204"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Cómo asignar un nombre a un archivo HelpInfo XML

En este tema se explica el formato de nombre requerido para los archivos de información de ayuda actualizable, comúnmente conocidos como archivos XML HelpInfo.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Cómo asignar un nombre a un archivo HelpInfo XML

Un archivo XML HelpInfo debe tener un nombre con el formato siguiente.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Los elementos del nombre son los siguientes.

ModuleName el valor de la propiedad **Name** del objeto **ModuleInfo** que devuelve el cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) .

ModuleGUID el valor de la clave **GUID** en el manifiesto del módulo.

Por ejemplo, si el nombre del módulo es "TestModule" y el GUID del módulo es 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, el nombre del archivo XML HelpInfo del módulo sería:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`