---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WaitForSome de DSC
ms.openlocfilehash: 91589c84518a2bd0f4816d11aa011dec1d5305e1
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952982"
---
# <a name="dsc-waitforsome-resource"></a>Recurso WaitForSome de DSC

> Se aplica a: Windows PowerShell 5.x

El recurso **WaitForSome** de Desired State Configuration (DSC) se puede usar dentro de un bloque de nodos en una [configuración de DSC](../../../configurations/configurations.md) para especificar las dependencias de las configuraciones de otros nodos.

Este recurso se ejecuta si el recurso especificado por la propiedad **ResourceName** está en el estado deseado en un número mínimo de nodos (especificado por **NodeCount**) definido por la propiedad **NodeName**.

> [!NOTE]
> El recurso **WaitForSome** usa Administración remota de Windows para comprobar el estado de otros nodos. Para obtener más información sobre los requisitos de seguridad y puerto de WinRM, vea [Consideraciones de seguridad de comunicación remota de PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="syntax"></a>Sintaxis

```Syntax
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [ RetryCount = [UInt32] ]
    [ RetryIntervalSec = [UInt64] ]
    [ ThrottleLimit = [UInt32] ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|NodeCount |El número mínimo de nodos que deben tener el estado deseado para que se ejecute este recurso. |
|NodeName |Los nodos de destino del recurso de dependencia. |
|nombreDelRecurso |El nombre del recurso de dependencia. Si este recurso pertenece a una configuración diferente, dé el siguiente formato al nombre: `[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]`. |
|RetryIntervalSec |El número de segundos antes de reintentar la operación. El valor mínimo es 1. |
|RetryCount |El número máximo de reintentos. |
|ThrottleLimit |El número de máquinas que se pueden conectar de forma simultánea. El valor predeterminado es `New-CimSession`. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Ejemplo

Para un ejemplo de cómo usar este recurso, consulte [Especificación de dependencias entre nodos](../../../configurations/crossNodeDependencies.md)