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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068103"
---
# <a name="getproc-tutorial"></a>Tutorial de GetProc

Esta sección proporciona un tutorial para crear un cmdlet Get-Proc que es muy similar a la [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet proporcionado por Windows PowerShell. Este tutorial proporciona fragmentos de código que ilustran cómo se implementan los cmdlets y obtener una explicación del código.

## <a name="topics-in-this-tutorial"></a>Temas de este Tutorial

Los temas de este tutorial están diseñados para que se leen secuencialmente, con cada tema Creación en lo que se ha explicado en el tema anterior.

[Creación de un Cmdlet sin parámetros](./creating-a-cmdlet-without-parameters.md) en esta sección se describe cómo crear un cmdlet que recupera información desde el equipo local sin el uso de parámetros y, a continuación, escribe la información en la canalización.

[Adición de parámetros de esa entrada de línea de comandos del proceso](./adding-parameters-that-process-command-line-input.md) en esta sección se describe cómo agregar un parámetro al cmdlet Get-Proc para que el cmdlet pueda procesar entradas basadas en objetos explícitos que se pasa al cmdlet. La implementación que se describe aquí recupera los procesos según su nombre y, a continuación, escribe la información en la canalización.

[Agregar parámetros de entrada de la canalización de ese proceso](./adding-parameters-that-process-pipeline-input.md) en esta sección se describe cómo agregar un parámetro al cmdlet Get-Proc para que el cmdlet pueda procesar los objetos que se pasen a través de la canalización. El cmdlet de implementación que se describe aquí recupera los procesos basados en objetos que se pasan al cmdlet y, a continuación, escribe la información en la canalización.

[Agregar informes de errores de no terminación para su Cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md) en esta sección se describe cómo agregar informes a un cmdlet de errores de no terminación. La implementación que se describen aquí detecta errores de no terminación que se producen al procesar la entrada y escribe un registro de errores en la secuencia de error.

## <a name="see-also"></a>Véase también

[Creación de un Cmdlet sin parámetros](./creating-a-cmdlet-without-parameters.md)

[Adición de parámetros que procesa la entrada de línea de comandos](./adding-parameters-that-process-command-line-input.md)

[Agregar parámetros de entrada de la canalización de proceso](./adding-parameters-that-process-pipeline-input.md)

[Agregar informes al Cmdlet de errores de no terminación](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
