---
title: Crear un flujo de trabajo mediante un script de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5720200ce32f114cd4965d961b9e2804bd154b2e
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870853"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Creación de un flujo de trabajo mediante un script de Windows PowerShell

Puede crear un flujo de trabajo escribiendo un script de Windows PowerShell. Para crear un flujo de trabajo, utilice la palabra clave Workflow seguida de un nombre para el flujo de trabajo antes del cuerpo del script. Por ejemplo:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

El flujo de trabajo se encuentra de la misma manera que con cualquier otro comando de Windows PowerShell.

## <a name="implementing-parallel-and-sequence"></a>Implementar Parallel y Sequence

[Windows Workflow Foundation](/previous-versions/dotnet/netframework-3.5/ms735967(v=vs.90)) admite la ejecución de actividades en paralelo. Para implementar esta funcionalidad en un script de Windows PowerShell, use la palabra clave `parallel` delante de un bloque de script. También puede utilizar la construcción `foreach -parallel` para recorrer en iteración una colección de objetos en paralelo. Para ejecutar un grupo de actividades en orden secuencial dentro de un bloque paralelo, incluya ese grupo de actividades en un bloque de script y preceda el bloque con la palabra clave Sequence.

## <a name="joining-computers-to-a-domain"></a>Unir equipos a un dominio

El siguiente script crea un flujo de trabajo que comprueba el estado de dominio de un grupo de equipos especificados por el usuario, los une a un dominio si aún no están Unidos y, a continuación, vuelve a comprobar el estado.
Se trata de una versión de script del flujo de trabajo de XAML que se explica en [creación de un flujo de trabajo con actividades de Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md).

```powershell
workflow Join-Domain
{
    param([string[]] $ComputerName, [PSCredential] $DomainCred, [PsCredential] $MachineCred)

    foreach -parallel($Computer in $ComputerName)
    {
        sequence {
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        Add-Computer -PSComputerName $Computer -PSCredential $DomainCred
        Restart-Computer -ComputerName $Computer -Credential $MachineCred -For PowerShell -Force -Wait -PSComputerName ""
        Get-WmiObject -PSComputerName $Computer -PSCredential $MachineCred
        }
    }
}
```