---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Anidamiento de configuraciones
ms.openlocfilehash: 89badda86707a129909b1c3cc3f79afa0b5f5df6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="8590c-103">Anidamiento de configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="8590c-103">Nesting DSC configurations</span></span>

<span data-ttu-id="8590c-104">Una configuración anidada (también denominada configuración compuesta) es una configuración que se llama dentro de otra configuración, como si se tratara de un recurso.</span><span class="sxs-lookup"><span data-stu-id="8590c-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="8590c-105">Ambas configuraciones deben definirse en el mismo archivo.</span><span class="sxs-lookup"><span data-stu-id="8590c-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="8590c-106">Veamos un ejemplo sencillo:</span><span class="sxs-lookup"><span data-stu-id="8590c-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="8590c-107">En este ejemplo, `FileConfig` toma dos parámetros obligatorios, **CopyFrom** y **CopyTo**, que se utilizan como los valores para las propiedades **SourcePath** y **DestinationPath** en el bloque de recursos `File`.</span><span class="sxs-lookup"><span data-stu-id="8590c-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="8590c-108">La configuración `NestedConfig` llamada a `FileConfig` como si fuera un recurso.</span><span class="sxs-lookup"><span data-stu-id="8590c-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="8590c-109">Las propiedades del bloque de recursos `NestedConfig` (**CopyFrom** y **CopyTo**) son los parámetros de la configuración `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="8590c-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="8590c-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="8590c-110">See Also</span></span>

- [<span data-ttu-id="8590c-111">Recursos compuestos: uso de una configuración DSC como un recurso</span><span class="sxs-lookup"><span data-stu-id="8590c-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)

