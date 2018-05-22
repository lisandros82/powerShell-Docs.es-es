---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Uso de datos de configuración
ms.openlocfilehash: d42c43fddb54050adcbac949e7f67f3b41b540f1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="using-configuration-data-in-dsc"></a>Uso de datos de configuración en DSC

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Puede definir los datos que se pueden usar dentro de una configuración al usar el parámetro DSC integrado **ConfigurationData**.
Esto le permite crear una única configuración que puede usarse para varios nodos o para entornos diferentes.
Por ejemplo, si está desarrollando una aplicación, puede usar una configuración para los entornos de producción y desarrollo, y usar datos de configuración para especificar datos para cada entorno.

En este tema se describe la estructura de la tabla hash **ConfigurationData**.
Para ejemplos sobre cómo usar datos de configuración, consulte [Separación de los datos de entorno y configuración](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>El parámetro común ConfigurationData

Una configuración DSC toma un parámetro común **ConfigurationData**, que se especifica cuando se compila la configuración.
Para obtener más información sobre la compilación de configuraciones, consulte [Configuraciones DSC](configurations.md).

El parámetro **ConfigurationData** es un tabla hash que debe tener al menos una clave denominada **AllNodes**.
También puede tener una u otras claves más.

>**Nota:** Los ejemplos de este tema usan una clave adicional única (distinta de la clave denominada **AllNodes**) llamada `NonNodeData`, pero se puede incluir cualquier número de claves adicionales y asignarles los nombres de su preferencia.

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

El valor de la clave **AllNodes** es una matriz. Cada elemento de esta matriz también es una tabla hash que debe tener al menos una clave denominada **NodeName**:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

También puede agregar otras claves a cada tabla hash:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

Para aplicar una propiedad a todos los nodos, puede crear un miembro de la matriz **AllNodes** que tenga un **NodeName** de `*`.
Por ejemplo, para aplicar a todos los nodos una propiedad `LogPath`, se podría hacer lo siguiente:

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Esto equivale a agregar una propiedad con un nombre de `LogPath` con un valor de `"C:\Logs"` a cada uno de los otros bloques (`VM-1`, `VM-2` y `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definición de la tabla hash ConfigurationData

Puede definir **ConfigurationData** como una variable en el mismo archivo de script que una configuración (como en los ejemplos anteriores) o en un archivo `.psd1` independiente.
Para definir **ConfigurationData** en un archivo `.psd1`, cree un archivo que contenga solo la tabla hash que representa los datos de configuración.

Por ejemplo, podría crear un archivo denominado `MyData.psd1` con el siguiente contenido:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>Compilación de una configuración con datos de configuración

Para compilar una configuración para la que definió datos de configuración, pase los datos de configuración como el valor del parámetro **ConfigurationData**.

Con esto se creará un archivo MOF para cada entrada de la matriz **AllNodes**.
Cada archivo MOF se denominará con la propiedad `NodeName` de la entrada de matriz correspondiente.

Por ejemplo, si define los datos de configuración como en el archivo `MyData.psd1` anterior, compilar una configuración creará los archivos `VM-1.mof` y `VM-2.mof`.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Compilación de una configuración con datos de configuración mediante una variable

Para usar datos de configuración que se definen como variable en el mismo archivo `.ps1` que la configuración, pase el nombre de la variable como el valor del parámetro **ConfigurationData** cuando compile la configuración:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Compilación de una configuración con datos de configuración mediante un archivo de datos

Para usar datos de configuración que se definen en un archivo. psd1, pase la ruta de acceso y el nombre de ese archivo como el valor del parámetro **ConfigurationData** al compilar la configuración:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Uso de variables ConfigurationData en una configuración

DSC proporciona tres variables especiales que se pueden usar en un script de configuración:**$AllNodes**, **$Node** y **$ConfigurationData**.

- **$AllNodes** hace referencia a toda la colección de nodos que se define en **ConfigurationData**. Puede filtrar la colección **AllNodes** mediante **.Where()** y **.ForEach()**.
- **Node** hace referencia a un valor determinado en la colección **AllNodes** después de que se filtre mediante **.Where()** o **.ForEach()**.
- **ConfigurationData** hace referencia a toda la tabla hash que se pasa como parámetro al compilar una configuración.

## <a name="using-non-node-data"></a>Uso de datos que no son de nodo

Tal como vimos en ejemplos anteriores, la tabla hash **ConfigurationData** puede tener una o más claves además de la clave **AllNodes** requerida.
En los ejemplos de este tema, usamos solo un nodo adicional y lo denominamos `NonNodeData`.
Sin embargo, puede definir cualquier número de claves adicionales y asignarles el nombre que desee.

Para un ejemplo de cómo usar datos no de nodos, consulte [Separación de los datos de entorno y configuración](separatingEnvData.md).

## <a name="see-also"></a>Véase también
- [Opciones de credenciales en los datos de configuración](configDataCredentials.md)
- [Configuraciones DSC](configurations.md)