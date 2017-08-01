---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso nxEnvironment de DSC para Linux
ms.openlocfilehash: 3d09c9642f35627e939460c9c13dfe48d14030c3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>Recurso nxEnvironment de DSC para Linux

El recurso **nxEnvironment** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar variables de entorno del sistema en un nodo de Linux.

## <a name="syntax"></a>Sintaxis

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propiedades

|  Propiedad |  Descripción | 
|---|---|
| Nombre| Indica el nombre de la variable de entorno para la que quiere garantizar un estado específico.| 
| Value| Valor que se asigna a la variable de entorno.| 
| Ensure| Determina si se debe comprobar si existe la variable de entorno. Establezca esta propiedad en "Present" para asegurarse de que la variable exista. Establézcala en "Absent" para asegurarse de que la variable no exista. El valor predeterminado es "Present".| 
| Ruta| Define la variable de entorno que se está configurando. Establezca esta propiedad en **$true** si la variable es la variable **Path**; de lo contrario, establézcala en **$false**. El valor predeterminado es **$false**. Si la variable que se está configurando es la variable **Path**, el valor facilitado mediante la propiedad **Value** se anexará al valor existente.| 
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="additional-information"></a>Información adicional

* Si **Path** no está presente o se establece en **$false**, las variables de entorno se administran en `/etc/environment`. Los programas o scripts pueden requerir una configuración para que el archivo `/etc/environment` acceda a las variables de entorno administradas.
* Si **Path** se establece en **$true**, la variable de entorno se administra en el archivo `/etc/profile.d/DSCenvironment.sh`. Este archivo se creará si no existe. Si **Ensure** se establece en "Absent" y **Path** se establece en **$true**, solo se quitará una variable de entorno de `/etc/profile.d/DSCenvironment.sh` y no de otros archivos.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar el recurso **nxEnvironment** para asegurarse de que **TestEnvironmentVariable** existe y tiene el valor "Test-Value". Si **TestEnvironmentVariable** no existe, se creará.

```
Import-DSCResource -Module nx 


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```


