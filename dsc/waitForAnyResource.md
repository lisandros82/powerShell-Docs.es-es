---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForAny Resource de DSC
ms.openlocfilehash: 39100f0fc52092c54bbecab55e3ef3dfabb4c70e
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226056"
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
| nombreDelRecurso| El nombre del recurso de dependencia. Si el recurso pertenece a una configuración diferente, asegúrese de que el formato del nombre sea el siguiente: "[__TipoDeRecurso__]__NombreDeRecurso__::[__NombreDeConfiguración__]::[__NombreDeConfiguración__]".|
| NodeName| Los nodos de destino del recurso de dependencia.|
| RetryIntervalSec| El número de segundos antes de reintentar la operación. El valor mínimo es 1.|
| RetryCount| El número máximo de reintentos.|
| ThrottleLimit| El número de máquinas que se pueden conectar de forma simultánea. El valor predeterminado es new-cimsession.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|


## <a name="example"></a>Ejemplo

Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](crossNodeDependencies.md)