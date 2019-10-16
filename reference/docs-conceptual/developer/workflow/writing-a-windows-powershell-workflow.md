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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366014"
---
# <a name="writing-a-windows-powershell-workflow"></a>Escribir un flujo de trabajo de Windows PowerShell

Puede crear un flujo de trabajo XAML agregando las actividades expuestas por los ensamblados de Windows PowerShell al diseñador de flujo de trabajo en Visual Studio. Los siguientes ensamblados de Windows PowerShell exponen actividades habilitadas para el flujo de trabajo.

> [!IMPORTANT]
> Un flujo de trabajo de XAML se debe empaquetar como un módulo si desea proporcionar ayuda para el flujo de trabajo. Para obtener información acerca de los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities)

- [Microsoft. PowerShell. Core. Activities](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [Microsoft. PowerShell. Diagnostics. Activities](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [Microsoft. PowerShell. Security. Activities](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [Microsoft. PowerShell. Utility. Activities](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  En los temas siguientes se describe cómo crear un flujo de trabajo mediante actividades de Windows PowerShell.

- [Agregar actividades de Windows PowerShell al cuadro de herramientas de Visual Studio](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [Crear un flujo de trabajo con actividades de Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md)

- [Crear un flujo de trabajo mediante un script de Windows PowerShell](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [Importar e invocar un flujo de trabajo de Windows PowerShell](./importing-and-invoking-a-windows-powershell-workflow.md)

- [Crear una actividad de flujo de trabajo desde un cmdlet de Windows PowerShell](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)