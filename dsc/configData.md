---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Uso de datos de configuración
ms.openlocfilehash: 19544494a547a06d87701b38585844cb11d03e33
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="69522-103">Uso de datos de configuración en DSC</span><span class="sxs-lookup"><span data-stu-id="69522-103">Using configuration data in DSC</span></span>

><span data-ttu-id="69522-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="69522-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="69522-105">Puede definir los datos que se pueden usar dentro de una configuración al usar el parámetro DSC integrado **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="69522-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="69522-106">Esto le permite crear una única configuración que puede usarse para varios nodos o para entornos diferentes.</span><span class="sxs-lookup"><span data-stu-id="69522-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="69522-107">Por ejemplo, si está desarrollando una aplicación, puede usar una configuración para los entornos de producción y desarrollo, y usar datos de configuración para especificar datos para cada entorno.</span><span class="sxs-lookup"><span data-stu-id="69522-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="69522-108">En este tema se describe la estructura de la tabla hash **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="69522-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="69522-109">Para ejemplos sobre cómo usar datos de configuración, consulte [Separación de los datos de entorno y configuración](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="69522-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="69522-110">El parámetro común ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="69522-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="69522-111">Una configuración DSC toma un parámetro común **ConfigurationData**, que se especifica cuando se compila la configuración.</span><span class="sxs-lookup"><span data-stu-id="69522-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="69522-112">Para obtener más información sobre la compilación de configuraciones, consulte [Configuraciones DSC](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="69522-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="69522-113">El parámetro **ConfigurationData** es un tabla hash que debe tener al menos una clave denominada **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="69522-113">The **ConfigurationData** parameter is a hasthtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="69522-114">También puede tener una u otras claves más.</span><span class="sxs-lookup"><span data-stu-id="69522-114">It can also have one or more other keys.</span></span>

><span data-ttu-id="69522-115">**Nota:** Los ejemplos de este tema usan una clave adicional única (distinta de la clave denominada **AllNodes**) llamada `NonNodeData`, pero se puede incluir cualquier número de claves adicionales y asignarles los nombres de su preferencia.</span><span class="sxs-lookup"><span data-stu-id="69522-115">**Note:** The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="69522-116">El valor de la clave **AllNodes** es una matriz.</span><span class="sxs-lookup"><span data-stu-id="69522-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="69522-117">Cada elemento de esta matriz también es una tabla hash que debe tener al menos una clave denominada **NodeName**:</span><span class="sxs-lookup"><span data-stu-id="69522-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

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

<span data-ttu-id="69522-118">También puede agregar otras claves a cada tabla hash:</span><span class="sxs-lookup"><span data-stu-id="69522-118">You can add other keys to each hash table as well:</span></span>

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

<span data-ttu-id="69522-119">Para aplicar una propiedad a todos los nodos, puede crear un miembro de la matriz **AllNodes** que tenga un **NodeName** de `*`.</span><span class="sxs-lookup"><span data-stu-id="69522-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="69522-120">Por ejemplo, para aplicar a todos los nodos una propiedad `LogPath`, se podría hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="69522-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

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

<span data-ttu-id="69522-121">Esto equivale a agregar una propiedad con un nombre de `LogPath` con un valor de `"C:\Logs"` a cada uno de los otros bloques (`VM-1`, `VM-2` y `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="69522-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="69522-122">Definición de la tabla hash ConfigurationData</span><span class="sxs-lookup"><span data-stu-id="69522-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="69522-123">Puede definir **ConfigurationData** como una variable en el mismo archivo de script que una configuración (como en los ejemplos anteriores) o en un archivo `.psd1` independiente.</span><span class="sxs-lookup"><span data-stu-id="69522-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="69522-124">Para definir **ConfigurationData** en un archivo `.psd1`, cree un archivo que contenga solo la tabla hash que representa los datos de configuración.</span><span class="sxs-lookup"><span data-stu-id="69522-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="69522-125">Por ejemplo, podría crear un archivo denominado `MyData.psd1` con el siguiente contenido:</span><span class="sxs-lookup"><span data-stu-id="69522-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

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

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="69522-126">Compilación de una configuración con datos de configuración</span><span class="sxs-lookup"><span data-stu-id="69522-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="69522-127">Para compilar una configuración para la que definió datos de configuración, pase los datos de configuración como el valor del parámetro **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="69522-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="69522-128">Con esto se creará un archivo MOF para cada entrada de la matriz **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="69522-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="69522-129">Cada archivo MOF se denominará con la propiedad `NodeName` de la entrada de matriz correspondiente.</span><span class="sxs-lookup"><span data-stu-id="69522-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="69522-130">Por ejemplo, si define los datos de configuración como en el archivo `MyData.psd1` anterior, compilar una configuración creará los archivos `VM-1.mof` y `VM-2.mof`.</span><span class="sxs-lookup"><span data-stu-id="69522-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="69522-131">Compilación de una configuración con datos de configuración mediante una variable</span><span class="sxs-lookup"><span data-stu-id="69522-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="69522-132">Para usar datos de configuración que se definen como variable en el mismo archivo `.ps1` que la configuración, pase el nombre de la variable como el valor del parámetro **ConfigurationData** cuando compile la configuración:</span><span class="sxs-lookup"><span data-stu-id="69522-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="69522-133">Compilación de una configuración con datos de configuración mediante un archivo de datos</span><span class="sxs-lookup"><span data-stu-id="69522-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="69522-134">Para usar datos de configuración que se definen en un archivo. psd1, pase la ruta de acceso y el nombre de ese archivo como el valor del parámetro **ConfigurationData** al compilar la configuración:</span><span class="sxs-lookup"><span data-stu-id="69522-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="69522-135">Uso de variables ConfigurationData en una configuración</span><span class="sxs-lookup"><span data-stu-id="69522-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="69522-136">DSC proporciona tres variables especiales que se pueden usar en un script de configuración:**$AllNodes**, **$Node** y **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="69522-136">DSC provides three special variables that can be used in a configuration script: **$AllNodes**, **$Node**, and **$ConfigurationData**.</span></span>

- <span data-ttu-id="69522-137">**$AllNodes** hace referencia a toda la colección de nodos que se define en **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="69522-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="69522-138">Puede filtrar la colección **AllNodes** mediante **.Where()** y **.ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="69522-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="69522-139">**Node** hace referencia a un valor determinado en la colección **AllNodes** después de que se filtre mediante **.Where()** o **.ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="69522-139">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
- <span data-ttu-id="69522-140">**ConfigurationData** hace referencia a toda la tabla hash que se pasa como parámetro al compilar una configuración.</span><span class="sxs-lookup"><span data-stu-id="69522-140">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="69522-141">Uso de datos que no son de nodo</span><span class="sxs-lookup"><span data-stu-id="69522-141">Using non-node data</span></span>

<span data-ttu-id="69522-142">Tal como vimos en ejemplos anteriores, la tabla hash **ConfigurationData** puede tener una o más claves además de la clave **AllNodes** requerida.</span><span class="sxs-lookup"><span data-stu-id="69522-142">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="69522-143">En los ejemplos de este tema, usamos solo un nodo adicional y lo denominamos `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="69522-143">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="69522-144">Sin embargo, puede definir cualquier número de claves adicionales y asignarles el nombre que desee.</span><span class="sxs-lookup"><span data-stu-id="69522-144">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="69522-145">Para un ejemplo de cómo usar datos no de nodos, consulte [Separación de los datos de entorno y configuración](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="69522-145">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="69522-146">Véase también</span><span class="sxs-lookup"><span data-stu-id="69522-146">See Also</span></span>
- [<span data-ttu-id="69522-147">Opciones de credenciales en los datos de configuración</span><span class="sxs-lookup"><span data-stu-id="69522-147">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="69522-148">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="69522-148">DSC Configurations</span></span>](configurations.md)