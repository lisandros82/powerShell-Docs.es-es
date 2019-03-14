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
# <a name="how-to-name-a-helpinfo-xml-file"></a>Cómo asignar un nombre a un archivo HelpInfo XML

En este tema se explica el formato de nombre requerido para los archivos de información de ayuda actualizable, conocidos como archivos XML HelpInfo.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Cómo asignar un nombre a un archivo HelpInfo XML

Un archivo XML HelpInfo debe tener un nombre con el formato siguiente.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Los elementos del nombre son los siguientes.

ModuleName el valor de la **nombre** propiedad de la **ModuleInfo** objeto al que el [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devuelve.

ModuleGUID el valor de la **GUID** clave en el manifiesto del módulo.

Por ejemplo, si el nombre del módulo es "TestModule" y el GUID del módulo es 9cabb9ad f2ac 4914 a46b bfc1bebf07f9, sería el nombre del archivo XML HelpInfo para el módulo:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`