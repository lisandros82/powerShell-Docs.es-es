---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForAny Resource de DSC
ms.openlocfilehash: 795c005c67c196ef9afb08af790fe2a1695392ec
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-waitforany-resource"></a>Recurso WaitForAny Resource de DSC

> Se aplica a: Windows PowerShell 5.1 y versiones posteriores

El recurso **WaitForSome** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](configurations.md) para especificar las dependencias de las configuraciones de otros nodos.

Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en cualquier nodo de destino definido en la propiedad **NodeName**.


## <a name="syntax"></a>Sintaxis

```
WaitForAny [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ RetryIntervalSec = [Uint64] ]
    [ RetryCount = [Uint32] ] 
    [ ThrottleLimit = [Uint32]]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   | 
|---|---| 
| nombreDelRecurso| El nombre del recurso de dependencia.| 
| NodeName| Los nodos de destino del recurso de dependencia.| 
| RetryIntervalSec| El número de segundos antes de reintentar la operación. El valor mínimo es 1.| 
| RetryCount| El número máximo de reintentos.| 
| ThrottleLimit| El número de máquinas que se pueden conectar de forma simultánea. El valor predeterminado es new-cimsession.| 
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Ejemplo

Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](crossNodeDependencies.md)

