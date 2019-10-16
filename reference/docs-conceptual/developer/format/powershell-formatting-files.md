---
title: Archivos de formato de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 3ec127d5ff60754de5d7f1ac73f2965524228b9c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365014"
---
# <a name="windows-powershell-formatting-files"></a>Archivos de formato de Windows PowerShell

Windows PowerShell proporciona varios archivos de formato (. Format. ps1xml) que se encuentran en el directorio de instalación (`$pshome`). Cada uno de estos archivos define la presentación predeterminada para un conjunto específico de objetos .NET. Estos archivos nunca deben cambiarse. Sin embargo, puede usarlos como referencia para crear sus propios archivos de formato personalizados.

`Certificate.Format.ps1xml` define la presentación de los objetos en el almacén de certificados, como los certificados x. 509 y los almacenes de certificados.

`DotNetTypes.Format.ps1xml` define la presentación de objetos .NET varios, como los objetos CultureInfo, FileVersionInfo y EventLogEntry.

`FileSystem.Format.ps1xml` define la visualización de objetos del sistema de archivos, como los objetos de archivo y de directorio.

`Help.Format.ps1xml` define las distintas vistas que usa el cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) , como las vistas detallada, completa, parámetros y ejemplo.

`PowerShellCore.Format.ps1xml` define la presentación de los objetos generados por los cmdlets principales de Windows PowerShell, como los objetos devueltos por los cmdlets [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) y [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) .

`PowerShellTrace.Format.ps1xml` define la presentación de los objetos de seguimiento, como los generados por el cmdlet [Trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) .

`Registry.Format.ps1xml` define la presentación de los objetos del registro, como los objetos de entrada y de clave.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
