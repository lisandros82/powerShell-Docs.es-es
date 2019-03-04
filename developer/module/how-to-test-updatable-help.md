---
title: Cómo probar la Ayuda actualizable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: f2f319a3cab4b4bd91e9b634dda57d58a6476b62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854741"
---
# <a name="how-to-test-updatable-help"></a>Cómo probar la Ayuda actualizable

Este tema describen métodos para probar la Ayuda actualizable de un módulo.

## <a name="using-verbose-to-detect-errors"></a>Uso detallado para detectar errores

Después de cargar el archivo XML HelpInfo y los archivos .cab para el módulo, los archivos de prueba mediante la ejecución de un [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) comando con el **detallado** parámetro. El **detallado** dirige el parámetro `Update-Help` para informar de los pasos fundamentales en sus acciones, lean la **HelpInfoUri** clave en el manifiesto de módulo para validar los tipos de archivo en el archivo CAB desempaquetado y la colocación de los archivos en el directorio del módulo específico del idioma.
Después de cargar el archivo XML HelpInfo y los archivos .cab para el módulo, los archivos de prueba mediante la ejecución de un [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) comando con el **detallado** parámetro. El **detallado** dirige el parámetro `Update-Help` para informar de los pasos fundamentales en sus acciones, lean la **HelpInfoUri** clave en el manifiesto de módulo para validar los tipos de archivo en el archivo CAB desempaquetado y la colocación de los archivos en el directorio del módulo específico del idioma.

Cuando se resuelven todos los mensajes detallados, ejecute un `Update-Help` comando con el **depurar** parámetro. Este parámetro debe detectar los demás problemas con los archivos de ayuda actualizable.