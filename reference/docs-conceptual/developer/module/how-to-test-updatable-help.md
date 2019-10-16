---
title: Cómo probar la ayuda actualizable | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367154"
---
# <a name="how-to-test-updatable-help"></a>Cómo probar la Ayuda actualizable

En este tema se describen los métodos para probar la ayuda actualizable de un módulo.

## <a name="using-verbose-to-detect-errors"></a>Usar verbose para detectar errores

Después de cargar el archivo XML y los archivos. CAB de HelpInfo para el módulo, pruebe los archivos mediante la ejecución de un comando [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) con el parámetro **verbose** . El parámetro **verbose** dirige `Update-Help` para informar de los pasos críticos en sus acciones, desde la lectura de la clave **HelpInfoUri** en el manifiesto del módulo hasta la validación de los tipos de archivo en el archivo CAB Desempaquetado y la colocación de los archivos en el idioma específico. directorio del módulo.

Cuando se resuelvan todos los mensajes detallados, ejecute un comando `Update-Help` con el parámetro **Debug** . Este parámetro debe detectar cualquier problema restante con los archivos de ayuda actualizable.