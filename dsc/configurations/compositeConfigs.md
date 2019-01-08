---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Anidamiento de configuraciones
ms.openlocfilehash: 54162cd72d2d1e7773e3be636bfa681329854498
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402281"
---
# <a name="nesting-dsc-configurations"></a>Anidamiento de configuraciones DSC

Una configuración anidada (también denominada configuración compuesta) es una configuración que se llama dentro de otra configuración, como si se tratara de un recurso.
Ambas configuraciones deben definirse en el mismo archivo.

Veamos un ejemplo sencillo:

```powershell
Configuration FileConfig
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }

}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

En este ejemplo, `FileConfig` toma dos parámetros obligatorios, **CopyFrom** y **CopyTo**, que se utilizan como los valores para las propiedades **SourcePath** y **DestinationPath** en el bloque de recursos `File`.
La configuración `NestedConfig` llamada a `FileConfig` como si fuera un recurso.
Las propiedades del bloque de recursos `NestedConfig` (**CopyFrom** y **CopyTo**) son los parámetros de la configuración `FileConfig`.

## <a name="see-also"></a>Véase también

- [Recursos compuestos: uso de una configuración DSC como un recurso](../resources/authoringResourceComposite.md)