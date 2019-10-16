---
title: Código de ejemplo de RunSpace08 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f286201-8a02-4b00-9a2c-1b833ccdbdbf
caps.latest.revision: 7
ms.openlocfilehash: 20032913969606f722f3768b0433775aeaa8c3a8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366484"
---
# <a name="runspace08-code-sample"></a>Ejemplo de código Runspace08

Este es el código fuente del ejemplo Runspace08 que se describe en [crear una aplicación de consola que agrega parámetros a un comando](https://msdn.microsoft.com/en-us/848b2b46-60f1-4a86-b448-cfc7c0cccfba). En esta aplicación de ejemplo se crea un espacio de ejecución, se crea una canalización, se agregan dos comandos a la canalización, se agregan dos parámetros al segundo comando y, a continuación, se ejecuta la canalización. Los comandos que se agregan a la canalización son los cmdlets `Get-Process` y `Sort-Object`.

## <a name="code-sample"></a>Código de ejemplo

[!code-csharp[Runspace08.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs#L11-L86 "Runspace08.cs")]

## <a name="see-also"></a>Véase también

[Windows PowerShell SDK](../windows-powershell-reference.md)
