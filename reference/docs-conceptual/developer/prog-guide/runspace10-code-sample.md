---
title: Código de ejemplo de RunSpace10 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: fcc424f83275452e223ef025cc8d95128520bdbc
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417870"
---
# <a name="runspace10-code-sample"></a>Ejemplo de código Runspace10

Este es el código fuente del ejemplo Runspace10. Esta aplicación de ejemplo agrega un cmdlet a [System. Management. Automation. runspace. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) y, a continuación, usa la información de configuración modificada para crear el espacio de ejecución.

> [!NOTE]
> Puede descargar el archivo C# de código fuente (runspace10.CS) mediante el kit de desarrollo de software de Windows para Windows Vista y los componentes de tiempo de ejecución de Microsoft .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .

## <a name="code-sample"></a>Código de ejemplo

[!code-csharp[Runspace10.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a>Vea también

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
