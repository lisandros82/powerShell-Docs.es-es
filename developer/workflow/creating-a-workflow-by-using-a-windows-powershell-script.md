---
title: Creación de un flujo de trabajo mediante un Script de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 70532e7e-9cac-43c3-9687-e77011ecc878
caps.latest.revision: 4
ms.openlocfilehash: 5eb2186cbceee21f8b4a8c88b812e9c71f15e0af
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853051"
---
# <a name="creating-a-workflow-by-using-a-windows-powershell-script"></a>Creación de un flujo de trabajo mediante un script de Windows PowerShell

Puede crear un flujo de trabajo mediante la escritura de un script de Windows PowerShell. Para crear un flujo de trabajo, use la palabra clave de flujo de trabajo seguida por un nombre para el flujo de trabajo antes del cuerpo de la secuencia de comandos. Por ejemplo:

```powershell

workflow Invoke-HelloWorld {"Hello World from workflow"}
```

Encuentre el flujo de trabajo de la misma manera que lo haría con cualquier otro comando de Windows PowerShell.

## <a name="implementing-parallel-and-sequence"></a>Implementación de secuencia y paralelas

[Windows Workflow Foundation](https://msdn.microsoft.com/en-us/library/ms735967.aspx) admite la ejecución de actividades en paralelo. Para implementar esta funcionalidad en un script de Windows PowerShell, use el `parallel` palabra clave delante de un bloque de script. También puede usar el `foreach -parallel` construcción para recorrer en iteración una colección de objetos en paralelo. Para ejecutar un grupo de actividades en orden secuencial dentro de un bloque paralelo, incluir ese grupo de actividades en un bloque de script y delante del bloque con la palabra clave de la secuencia.

## <a name="joining-computers-to-a-domain"></a>Unir equipos a un dominio

El script siguiente crea un flujo de trabajo que comprueba el estado de dominio de un grupo de equipos especificado por el usuario, se une a un dominio si ya no están combinadas y, a continuación, comprueba el estado de nuevo. Esta es una versión de la secuencia de comandos del flujo de trabajo XAML se explica en [crear un flujo de trabajo con actividades de Windows PowerShell](./creating-a-workflow-with-windows-powershell-activities.md).

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