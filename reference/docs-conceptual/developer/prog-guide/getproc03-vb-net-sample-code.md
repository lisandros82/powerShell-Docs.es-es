---
title: Código de ejemplo de GetProc03 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360314"
---
# <a name="getproc03-vbnet-sample-code"></a>Código de ejemplo GetProc03 (VB.NET)

En el código siguiente se muestra la implementación de un cmdlet `Get-Process` que puede aceptar la entrada canalizada. Esta implementación define un parámetro `Name` que acepta la entrada de canalización, recupera información del proceso del equipo local basándose en los nombres proporcionados y, a continuación, usa el método [writeObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) como salida. mecanismo para enviar objetos a la canalización.

## <a name="code-sample"></a>Código de ejemplo

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
