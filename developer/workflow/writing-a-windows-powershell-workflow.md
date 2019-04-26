---
title: Escribir un flujo de trabajo de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080329"
---
# <a name="writing-a-windows-powershell-workflow"></a>Escribir un flujo de trabajo de Windows PowerShell

Puede crear un flujo de trabajo XAML mediante la adición de actividades expuestas por los ensamblados de Windows PowerShell para el Diseñador de flujo de trabajo en Visual Studio. Los siguientes ensamblados de Windows PowerShell exponen las actividades de flujo de trabajo habilitado.

> [!IMPORTANT]
> Un flujo de trabajo XAML se debe empaquetar como un módulo si desea proporcionar ayuda para el flujo de trabajo. Para obtener información acerca de los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities)

- [Microsoft.Powershell.Core.Activities](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [Microsoft.Powershell.Diagnostics.Activities](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [Microsoft.Powershell.Security.Activities](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [Microsoft.Powershell.Utility.Activities](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  Los temas siguientes describen cómo crear un flujo de trabajo mediante actividades de Windows PowerShell.

- [Adición de actividades de Windows PowerShell en el cuadro de herramientas de Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [Creación de un flujo de trabajo con actividades de Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)

- [Creación de un flujo de trabajo mediante una secuencia de comandos de Windows PowerShell](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [Importación e invocar un flujo de trabajo de Windows PowerShell](./importing-and-invoking-a-windows-powershell-workflow.md)

- [Creación de una actividad de flujo de trabajo desde un Cmdlet de Windows PowerShell](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)