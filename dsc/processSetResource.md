---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso ProcessSet de DSC
ms.openlocfilehash: 33000786a9e17e11168b5e08c3bcfcacf3af2611
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268024"
---
# <a name="dsc-windowsprocess-resource"></a>Recurso de DSC WindowsProcess

_Se aplica a: Windows PowerShell 5.0_

El recurso **ProcessSet** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para configurar procesos en un nodo de destino. Este es un [recurso compuesto](authoringResourceComposite.md) que llama al [recurso WindowsProcess](windowsProcessResource.md) de cada uno de los grupos que se especifican en el parámetro `GroupName`.

## <a name="syntax"></a>Sintaxis

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Propiedades

| Propiedad | Descripción |
| --- | --- |
| Argumentos| Una cadena que tiene argumentos que se pasa al proceso tal cual. Si necesita pasar varios argumentos, colóquelos en esta cadena.|
| Ruta| Las rutas de acceso a los ejecutables del proceso. Si estos son los nombres de archivo de los ejecutables (no las rutas de acceso completas), el recurso de DSC buscará la variable **Path** del entorno (`$env:Path`) para buscar los archivos. Si los valores de esta propiedad son rutas completas, DSC no usará la variable de entorno **Path** para buscar los archivos y generará un error si alguna de las rutas de acceso no existe. No se permiten rutas de acceso relativas.|
| Credential| Indica las credenciales para iniciar el proceso.|
| Ensure| Especifica si los procesos existen. Establezca esta propiedad en "Present" para asegurarse de que el proceso exista. De lo contrario, establézcala en "Absent". El valor predeterminado es "Present".|
| StandardErrorPath| La ruta de acceso en la que los procesos escriben los errores estándar. Se sobrescribirá cualquier archivo existente en la ubicación.|
| StandardInputPath| La secuencia desde la que el proceso recibe las entradas estándar.|
| StandardOutputPath| La ruta de acceso del archivo en la que los procesos escriben las salidas estándar. Se sobrescribirá cualquier archivo existente en la ubicación.|
| WorkingDirectory| La ubicación utilizada como directorio de trabajo actual de los procesos.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|