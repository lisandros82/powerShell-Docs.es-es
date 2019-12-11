---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso nxEnvironment de DSC para Linux
ms.openlocfilehash: 55c1b2402e23c1042ed48b40c1084aa63c515b36
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953232"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>Recurso nxEnvironment de DSC para Linux

El recurso **nxEnvironment** de Desired State Configuration (DSC) de PowerShell ofrece un mecanismo para administrar variables de entorno del sistema en un nodo de Linux.

## <a name="syntax"></a>Sintaxis

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Nombre |Indica el nombre de la variable de entorno para la que quiere garantizar un estado específico. |
|Value |Valor que se asigna a la variable de entorno. |
|Ruta |Define la variable de entorno que se está configurando. Establezca esta propiedad en `$true` si la variable es la variable **Path**; de lo contrario, establézcala en `$false`. El valor predeterminado es `$false`. Si la variable que se está configurando es la variable **Path**, el valor facilitado mediante la propiedad **Value** se anexará al valor existente. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina si se debe comprobar si existe la variable de entorno. Establezca esta propiedad en **Present** para asegurarse de que la variable exista. Establézcala en **absent** para asegurarse de que la variable no exista. El valor predeterminado es **Present**. |

## <a name="additional-information"></a>Información adicional

- Si **Path** no está presente o se establece en `$false`, las variables de entorno se administran en `/etc/environment`.
  Los programas o scripts pueden requerir una configuración para que el archivo `/etc/environment` acceda a las variables de entorno administradas.
- Si **Path** se establece en `$true`, la variable de entorno se administra en el archivo `/etc/profile.d/DSCenvironment.sh`. Este archivo se creará si no existe. Si **Ensure** se establece en **Absent** y **Path** se establece en `$true`, solo se quitará una variable de entorno de `/etc/profile.d/DSCenvironment.sh` y no de otros archivos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar el recurso **nxEnvironment** para asegurarse de que **TestEnvironmentVariable** existe y tiene el valor "Test-Value". Si **TestEnvironmentVariable** no existe, se creará.

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```