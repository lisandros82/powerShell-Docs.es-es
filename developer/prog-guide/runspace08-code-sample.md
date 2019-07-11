---
title: Ejemplo de código RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: ec6aae544eafea1dedc1379dab00beeed2c7c436
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734922"
---
# <a name="runspace08-code-sample"></a>Ejemplo de código Runspace08

Aquí está el código fuente para el ejemplo Runspace08 que se describen en [creación de una consola que agrega parámetros de la aplicación a un comando](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). Esta aplicación de ejemplo crea un espacio de ejecución, crea una canalización, agrega dos comandos a la canalización, agrega dos parámetros para el segundo comando y, a continuación, ejecuta la canalización. Los comandos que se agregan a la canalización son el `Get-Process` y `Sort-Object` cmdlets.

## <a name="code-sample"></a>Ejemplo de código

[!code-csharp[Runspace08.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Véase también

[Windows PowerShell SDK](../windows-powershell-reference.md)