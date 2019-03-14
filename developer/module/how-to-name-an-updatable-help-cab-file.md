---
title: Cómo denominar un archivo .cab de ayuda actualizable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794764"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Cómo asignar un nombre a un archivo CAB de Ayuda actualizable

En este tema se explica el formato de nombre requerido para el gabinete de ayuda actualizable (. Archivos CAB).

## <a name="how-to-name-an-updatable-help-cab-file"></a>Cómo asignar un nombre a un archivo CAB de Ayuda actualizable

Un archivador actualizable (. Archivo .cab) debe tener un nombre con el formato siguiente.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Los elementos del nombre son los siguientes.

ModuleName el valor de la **nombre** propiedad de la **ModuleInfo** objeto al que el [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet devuelve.

ModuleGUID el valor de la **GUID** clave en el manifiesto del módulo.

Referencia cultural de la interfaz de usuario UICulture de los archivos de ayuda en el archivo CAB. Este valor debe coincidir con el valor de uno de los **UICulture** elementos en el archivo XML HelpInfo para el módulo.

Por ejemplo, si el nombre del módulo es "TestModule", el GUID del módulo es 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 y la referencia cultural de interfaz de usuario es "en-US", el nombre del archivo .cab sería:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`