---
title: Archivos de formato de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d4c8f84-ebd2-4405-bb10-cfc5400d4ad6
caps.latest.revision: 6
ms.openlocfilehash: 49344d32dfcef36a904772b4a7237646a63cb12a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065389"
---
# <a name="windows-powershell-formatting-files"></a>Archivos de formato de Windows PowerShell

Windows PowerShell proporciona varios archivos de formato (. format.ps1xml) que se encuentran en el directorio de instalación (`$pshome`). Cada uno de estos archivos define la visualización predeterminada para un conjunto específico de objetos. NET. Estos archivos no deben modificarse nunca. Sin embargo, puede usar ellos como referencia para crear sus propios archivos de formato personalizados.

Certificate.Format.ps1xml define la visualización de objetos en el almacén de certificados como los certificados x.509 y almacenes de certificados.

DotNetTypes.Format.ps1xml define la presentación de varios objetos. NET, como los objetos CultureInfo, FileVersionInfo y EventLogEntry.

FileSystem.Format.ps1xml define la presentación de los objetos de sistema de archivos como archivos y directorios de los objetos.

Define Help.Format.ps1xml las distintas vistas utilizadas por el [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet, como las vistas detalladas, ejemplo, parámetros y completo.

PowerShellCore.Format.ps1xml define la presentación de los objetos generados por los cmdlets principales de Windows PowerShell, como los objetos devueltos por la [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) y [Get-History](/powershell/module/Microsoft.PowerShell.Core/Get-History) cmdlets.

PowerShellTrace.Format.ps1xml define la visualización de objetos de seguimiento, como las generadas por el [Trace-Command](/powershell/module/Microsoft.PowerShell.Utility/Trace-Command) cmdlet.

Registry.Format.ps1xml define la presentación de los objetos del registro como entradas y claves.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md)
