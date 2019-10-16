---
title: Tutorial de GetProc | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4663905f-560a-4e39-9b03-6db2c315c322
caps.latest.revision: 6
ms.openlocfilehash: bbd07a0d0abd30742b7e02482adedae3af43aca4
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364444"
---
# <a name="getproc-tutorial"></a>Tutorial de GetProc

En esta sección se proporciona un tutorial para crear un cmdlet Get-proc que es muy similar al cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) proporcionado por Windows PowerShell. En este tutorial se proporcionan fragmentos de código que muestran cómo se implementan los cmdlets y una explicación del código.

## <a name="topics-in-this-tutorial"></a>Temas de este tutorial

Los temas de este tutorial están diseñados para leerse secuencialmente, donde cada tema se basa en lo que se analizó en el tema anterior.

[Crear un cmdlet sin parámetros](./creating-a-cmdlet-without-parameters.md) En esta sección se describe cómo crear un cmdlet que recupera información del equipo local sin el uso de parámetros y, a continuación, escribe la información en la canalización.

[Agregar parámetros que procesan la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md) En esta sección se describe cómo agregar un parámetro al cmdlet Get-proc para que el cmdlet pueda procesar la entrada en función de los objetos explícitos pasados al cmdlet. La implementación que se describe aquí recupera procesos en función de su nombre y, a continuación, escribe la información en la canalización.

[Agregar parámetros que procesan la entrada de canalización](./adding-parameters-that-process-pipeline-input.md) En esta sección se describe cómo agregar un parámetro al cmdlet Get-proc para que el cmdlet pueda procesar los objetos que se le pasan a través de la canalización. El cmdlet de implementación que se describe aquí recupera los procesos basados en los objetos que se pasan al cmdlet y, a continuación, escribe la información en la canalización.

[Agregar informes de errores de no terminación al cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) En esta sección se describe cómo agregar informes de errores de no terminación a un cmdlet. La implementación que se describe aquí detecta los errores de no terminación que se producen al procesar la entrada y escribe un registro de error en la secuencia de error.

## <a name="see-also"></a>Véase también

[Crear un cmdlet sin parámetros](./creating-a-cmdlet-without-parameters.md)

[Agregar parámetros que procesan la entrada de la línea de comandos](./adding-parameters-that-process-command-line-input.md)

[Agregar parámetros que procesan la entrada de canalización](./adding-parameters-that-process-pipeline-input.md)

[Agregar informes de errores de no terminación al cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
