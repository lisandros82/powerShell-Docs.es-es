---
title: Cómo asignar un nombre a un archivo. CAB de ayuda actualizable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367164"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Cómo asignar un nombre a un archivo CAB de Ayuda actualizable

En este tema se explica el formato de nombre necesario para el archivo. cab de ayuda actualizable (. Archivos. CAB).

## <a name="how-to-name-an-updatable-help-cab-file"></a>Cómo asignar un nombre a un archivo CAB de Ayuda actualizable

Un archivo. cab actualizable (. CAB) debe tener un nombre con el formato siguiente.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Los elementos del nombre son los siguientes.

ModuleName el valor de la propiedad **Name** del objeto **ModuleInfo** que devuelve el cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) .

ModuleGUID el valor de la clave **GUID** en el manifiesto del módulo.

UICulture la referencia cultural de la interfaz de usuario de los archivos de ayuda en el archivo. CAB. Este valor debe coincidir con el valor de uno de los elementos **UICulture** del archivo XML HelpInfo para el módulo.

Por ejemplo, si el nombre del módulo es "TestModule", el GUID del módulo es 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 y la referencia cultural de la interfaz de usuario es "en-US", el nombre del archivo. CAB sería:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`