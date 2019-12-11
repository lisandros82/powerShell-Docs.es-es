---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC WindowsProcess
ms.openlocfilehash: e168cdebb04f7ec83b73a537a5f188299f40d8b7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952842"
---
# <a name="dsc-windowsprocess-resource"></a>Recurso de DSC WindowsProcess

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso **WindowsProcess** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para configurar procesos en un nodo de destino.

## <a name="syntax"></a>Sintaxis

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Argumentos |Indica una cadena de argumentos que se pasa al proceso tal cual. Si necesita pasar varios argumentos, colóquelos en esta cadena. |
|Ruta |La ruta de acceso al ejecutable del proceso. Si este es el nombre de archivo del ejecutable (no la ruta de acceso completa), el recurso de DSC buscará la variable `$env:Path`del entorno para buscar el archivo ejecutable. Si el valor de esta propiedad es una ruta completa, DSC no usará la variable `$env:Path` para buscar el archivo y generará un error si la ruta de acceso no existe. No se permiten rutas de acceso relativas. |
|Credential |Indica las credenciales para iniciar el proceso. |
|StandardErrorPath |Indica la ruta de acceso del directorio donde se escribirá el error estándar. Se sobrescribirá cualquier archivo existente en la ubicación. |
|StandardInputPath |Indica la ubicación de entrada estándar. |
|StandardOutputPath |Indica la ubicación donde se escribirá la salida estándar. Se sobrescribirá cualquier archivo existente en la ubicación. |
|WorkingDirectory |Indica la ubicación que se utilizará como directorio de trabajo actual del proceso. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica si existe el proceso. Establezca esta propiedad en **Present** para asegurarse de que el proceso exista. De lo contrario, establézcala en **Absent**. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |