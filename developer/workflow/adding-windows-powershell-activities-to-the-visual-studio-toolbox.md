---
title: Adición de actividades de Windows PowerShell en el cuadro de herramientas de Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080482"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a>Adición de actividades de Windows PowerShell al cuadro de herramientas de Visual Studio

Antes de crear un flujo de trabajo de PowerShell mediante el Diseñador de flujo de trabajo, primero debe agregar las actividades de PowerShell en el cuadro de herramientas en un proyecto de aplicación de consola de flujo de trabajo de Visual Studio. El siguiente procedimiento muestra cómo agregar las actividades desde el ensamblado Microsoft.PowerShell.Core.Activities al cuadro de herramientas de Visual Studio.

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a>Adición de actividades de Windows PowerShell en el cuadro de herramientas

1. Crear un nuevo proyecto de aplicación de consola de flujo de trabajo en Visual Studio.

2. En el **vista** menú, haga clic en **cuadro de herramientas**.

3. Agregar una nueva pestaña del cuadro de herramientas con el botón secundario en el cuadro de herramientas y haciendo clic en **Agregar pestaña**y asigne un nombre como "Actividades de PowerShell" a la nueva pestaña.

   Agregando una pestaña permite agrupar las actividades de PowerShell independiente de otras herramientas en el cuadro de herramientas.

4. En la nueva pestaña del cuadro de herramientas, haga clic en **elegir elementos...** . El **elegir elementos del cuadro de herramientas** aparece el cuadro de diálogo.

5. En el **elegir elementos del cuadro de herramientas** cuadro de diálogo, haga clic en el **System.Activities** ficha.

6. Haga clic en **examinar**.

7. Navegue hasta la carpeta %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e y haga doble clic en Microsoft.PowerShell.Core.Activities.dll.

8. Haga clic en **Aceptar**. Las actividades definidas por el ensamblado Microsoft.PowerShell.Core.Activities ahora están disponibles en el cuadro de herramientas.

## <a name="see-also"></a>Véase también

[Escribir un flujo de trabajo de Windows PowerShell](./writing-a-windows-powershell-workflow.md)

[Creación de un flujo de trabajo con actividades de Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)