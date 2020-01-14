---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Anidamiento de configuraciones
ms.openlocfilehash: 07e4fb5b9d406153d2fbb4285e28b8d1f0dfdcf5
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/25/2019
ms.locfileid: "75417872"
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="ea9b3-103">Anidamiento de configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="ea9b3-103">Nesting DSC configurations</span></span>

<span data-ttu-id="ea9b3-104">Una configuración anidada (también denominada configuración compuesta) es una configuración que se llama dentro de otra configuración, como si se tratara de un recurso.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-104">A nested configuration (also called composite configuration) is a configuration that's called within another configuration as if it were a resource.</span></span> <span data-ttu-id="ea9b3-105">Ambas configuraciones deben definirse en el mismo archivo.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="ea9b3-106">Veamos un ejemplo sencillo:</span><span class="sxs-lookup"><span data-stu-id="ea9b3-106">Let's look at a simple example:</span></span>

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

<span data-ttu-id="ea9b3-107">En este ejemplo, `FileConfig` toma dos parámetros obligatorios, **CopyFrom** y **CopyTo**, que se utilizan como los valores para las propiedades **SourcePath** y **DestinationPath** en el bloque de recursos `File`.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-107">In this example, `FileConfig` takes two mandatory parameters, **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="ea9b3-108">La configuración `NestedConfig` llamada a `FileConfig` como si fuera un recurso.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span> <span data-ttu-id="ea9b3-109">Las propiedades del bloque de recursos `NestedConfig` (**CopyFrom** y **CopyTo**) son los parámetros de la configuración `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

<span data-ttu-id="ea9b3-110">DSC no admite actualmente la anidación de configuraciones dentro de configuraciones anidadas.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-110">DSC doesn't currently support nesting configurations within nested configurations.</span></span> <span data-ttu-id="ea9b3-111">Solo puede anidar un nivel de configuración de una capa.</span><span class="sxs-lookup"><span data-stu-id="ea9b3-111">You can only nest a configuration one layer deep.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea9b3-112">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ea9b3-112">See Also</span></span>

- [<span data-ttu-id="ea9b3-113">Recursos compuestos: uso de una configuración DSC como un recurso</span><span class="sxs-lookup"><span data-stu-id="ea9b3-113">Composite resources--Using a DSC configuration as a resource</span></span>](../resources/authoringResourceComposite.md)