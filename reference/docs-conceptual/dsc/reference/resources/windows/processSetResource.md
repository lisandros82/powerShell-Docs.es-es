---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso ProcessSet de DSC
ms.openlocfilehash: 72925d3a9516f5c0040427773a3b1d66034667bb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953132"
---
# <a name="dsc-processset-resource"></a>Recurso ProcessSet de DSC

> Se aplica a: Windows PowerShell 5.x

El recurso **ProcessSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para configurar procesos en un nodo de destino.

## <a name="syntax"></a>Sintaxis

```Syntax
ProcessSet [string] #ResourceName
{
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Ruta |La ruta de acceso al ejecutable del proceso. Si estos son los nombres de archivo de los ejecutables (no las rutas de acceso completas), el recurso de DSC buscará la variable `$env:Path` del entorno para buscar los archivos. Si los valores de esta propiedad son rutas completas, DSC no usará la variable de entorno `$env:Path` para buscar los archivos y generará un error si alguna de las rutas de acceso no existe. No se permiten rutas de acceso relativas. |
|Credential |Indica las credenciales para iniciar el proceso. |
|StandardErrorPath |La ruta de acceso en la que los procesos escriben los errores estándar. Se sobrescribirá cualquier archivo existente en la ubicación. |
|StandardInputPath |La secuencia desde la que el proceso recibe las entradas estándar. |
|StandardOutputPath |La ruta de acceso del archivo en la que los procesos escriben las salidas estándar. Se sobrescribirá cualquier archivo existente en la ubicación. |
|WorkingDirectory |La ubicación utilizada como directorio de trabajo actual de los procesos. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Especifica si los procesos existen. Establezca esta propiedad en **Present** para asegurarse de que el proceso exista. De lo contrario, establézcala en **Absent**. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).