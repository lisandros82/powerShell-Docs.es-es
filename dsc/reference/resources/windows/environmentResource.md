---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Environment
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048019"
---
# <a name="dsc-environment-resource"></a>Recursos de DSC Environment

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

El recurso __Environment__ de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar variables de entorno del sistema.

## <a name="syntax"></a>Sintaxis
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   |
|---|---|
| Nombre| Indica el nombre de la variable de entorno para la que quiere garantizar un estado específico.|
| Ensure| Indica si existe una variable. Establezca esta propiedad en __Present__ para crear la variable de entorno si no existe o para garantizar que su valor coincida con el que se proporciona mediante la propiedad __Value__ si la variable ya existe. Establézcala en __Absent__ para eliminar la variable si existe.|
| Ruta| Define la variable de entorno que se está configurando. Establezca esta propiedad en __$true__ si la variable es la variable __Path__; de lo contrario, establézcala en __$false__. El valor predeterminado es __$false__. Si la variable que se está configurando es la variable __Path__, el valor facilitado mediante la propiedad __Value__ se anexará al valor existente.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|
| Value| Valor que se asigna a la variable de entorno.|

## <a name="example"></a>Ejemplo

El ejemplo siguiente se asegura de que __TestEnvironmentVariable__ exista y tenga el valor __TestValue__. Si no existe, se crea.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```