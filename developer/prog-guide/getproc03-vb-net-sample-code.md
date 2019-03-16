---
title: GetProc03 código de ejemplo (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: 0cfb5c203c97a4d20e7fadf8183e608e9e31b881
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058256"
---
# <a name="getproc03-vbnet-sample-code"></a>Código de ejemplo GetProc03 (VB.NET)

El código siguiente muestra la implementación de un `Get-Process` cmdlet que puede aceptar canaliza la entrada. Esta implementación define un `Name` parámetro que acepta la entrada de la canalización, recupera información de proceso del equipo local en función de los nombres proporcionados y, a continuación, usa el [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) método como el mecanismo de salida para enviar objetos a la canalización.

## <a name="code-sample"></a>Ejemplo de código

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->