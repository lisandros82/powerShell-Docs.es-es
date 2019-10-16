---
title: Agregar actividades de Windows PowerShell al cuadro de herramientas de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359654"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Adición de actividades de Windows PowerShell al cuadro de herramientas de Visual Studio

Antes de crear un flujo de trabajo de PowerShell mediante Diseñador de flujo de trabajo, primero debe agregar las actividades de PowerShell al cuadro de herramientas en un proyecto de aplicación de consola de flujos de trabajo de Visual Studio. En el procedimiento siguiente se muestra cómo agregar las actividades del ensamblado Microsoft. PowerShell. Core. Activities al cuadro de herramientas de Visual Studio.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Agregar actividades de Windows PowerShell al cuadro de herramientas

1. Cree un nuevo proyecto de aplicación de consola de flujos de trabajo en Visual Studio.

2. En el menú **Ver** , haga clic en **cuadro de herramientas**.

3. Agregue una nueva pestaña en el cuadro de herramientas; para ello, haga clic con el botón derecho en el cuadro de herramientas y haga clic en **Agregar pestaña**y asigne un nombre a la nueva pestaña, como "actividades de PowerShell".

   Agregar una pestaña permite agrupar las actividades de PowerShell independientes de otras herramientas del cuadro de herramientas.

4. En la pestaña nuevo cuadro de herramientas, haga clic en **elegir elementos.** ... Aparece el cuadro de diálogo **elegir elementos del cuadro de herramientas** .

5. En el cuadro de diálogo **elegir elementos del cuadro de herramientas** , haga clic en la pestaña **System. Activities** .

6. Haga clic en **examinar**.

7. Vaya a la carpeta%WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e y haga doble clic en Microsoft. PowerShell. Core. Activities. dll.

8. Haga clic en **Aceptar**. Las actividades definidas por el ensamblado Microsoft. PowerShell. Core. Activities ahora están disponibles en el cuadro de herramientas.

## <a name="see-also"></a>Véase también

[Escribir un flujo de trabajo de Windows PowerShell](./writing-a-windows-powershell-workflow.md)

[Crear un flujo de trabajo con actividades de Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)