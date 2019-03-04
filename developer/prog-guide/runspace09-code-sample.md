---
title: Ejemplo de código RunSpace09 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854051"
---
# <a name="runspace09-code-sample"></a>Ejemplo de código Runspace09

Aquí está el código fuente para el ejemplo Runspace09 que se describen en [creación de una consola de aplicación que invoca una canalización de forma asincrónica](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47). Esta aplicación de ejemplo crea y abre un espacio de ejecución, crea y lo invoca una canalización de forma asincrónica y, a continuación, la canalización usa eventos para procesar la secuencia de comandos de forma asincrónica. El script que se ejecuta esta aplicación crea los enteros del 1 al 10 en intervalos de 0,5 segundos (500 ms).

## <a name="code-sample"></a>Ejemplo de código

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a>Véase también

[Windows PowerShell SDK](../windows-powershell-reference.md)