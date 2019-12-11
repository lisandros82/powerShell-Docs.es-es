---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Separación de los datos de entorno y configuración
ms.openlocfilehash: b16243fc9096f786a25ed20868e94a3aa85e403e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954442"
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="08ef8-103">Separación de los datos de entorno y configuración</span><span class="sxs-lookup"><span data-stu-id="08ef8-103">Separating configuration and environment data</span></span>

><span data-ttu-id="08ef8-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="08ef8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="08ef8-105">Puede ser útil separar los datos utilizados en una configuración DSC de la propia configuración mediante el uso de datos de configuración.</span><span class="sxs-lookup"><span data-stu-id="08ef8-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="08ef8-106">Al hacerlo, puede utilizar una sola configuración para varios entornos.</span><span class="sxs-lookup"><span data-stu-id="08ef8-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="08ef8-107">Por ejemplo, si está desarrollando una aplicación, puede usar una configuración para los entornos de producción y desarrollo, y usar datos de configuración para especificar datos para cada entorno.</span><span class="sxs-lookup"><span data-stu-id="08ef8-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="08ef8-108">¿Qué son lo datos de configuración?</span><span class="sxs-lookup"><span data-stu-id="08ef8-108">What is configuration data?</span></span>

<span data-ttu-id="08ef8-109">Los datos de configuración son datos que se definen en una tabla hash y se pasan a una configuración DSC al compilar esa configuración.</span><span class="sxs-lookup"><span data-stu-id="08ef8-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="08ef8-110">Para una descripción detallada de la tabla hash **ConfigurationData**, consulte [Separación de los datos de entorno y configuración](configData.md).</span><span class="sxs-lookup"><span data-stu-id="08ef8-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="08ef8-111">Un ejemplo sencillo</span><span class="sxs-lookup"><span data-stu-id="08ef8-111">A simple example</span></span>

<span data-ttu-id="08ef8-112">Veamos un ejemplo muy sencillo de cómo funciona esto.</span><span class="sxs-lookup"><span data-stu-id="08ef8-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="08ef8-113">Crearemos una única configuración que garantice que **IIS** esté presente en algunos nodos y que **Hyper-V** esté presente en otros:</span><span class="sxs-lookup"><span data-stu-id="08ef8-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

```powershell
Configuration MyDscConfiguration {

    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }

    }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

<span data-ttu-id="08ef8-114">La última línea de este script compila la configuración; para ello, pasa `$MyData` como el valor del parámetro **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="08ef8-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="08ef8-115">El resultado es que se crean dos archivos MOF:</span><span class="sxs-lookup"><span data-stu-id="08ef8-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="08ef8-116">`$MyData` especifica dos nodos diferentes, cada uno con sus propios `NodeName` y `Role`.</span><span class="sxs-lookup"><span data-stu-id="08ef8-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="08ef8-117">La configuración crea de forma dinámica bloques de **nodo** al tomar la colección de nodos que se obtiene de `$MyData` (específicamente, `$AllNodes`) y al filtrar esa colección en la propiedad `Role`.</span><span class="sxs-lookup"><span data-stu-id="08ef8-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="08ef8-118">Uso de datos de configuración para definir entornos de desarrollo y producción</span><span class="sxs-lookup"><span data-stu-id="08ef8-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="08ef8-119">Veamos un ejemplo completo que usa una única configuración para configurar los entornos de desarrollo y producción de un sitio web.</span><span class="sxs-lookup"><span data-stu-id="08ef8-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="08ef8-120">En el entorno de desarrollo, IIS y SQL Server se instalan en un único nodo.</span><span class="sxs-lookup"><span data-stu-id="08ef8-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="08ef8-121">En el entorno de producción, IIS y SQL Server se instalan en nodos independientes.</span><span class="sxs-lookup"><span data-stu-id="08ef8-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="08ef8-122">Vamos a usar un archivo. psd1 de datos de configuración para especificar los datos de los dos entornos diferentes.</span><span class="sxs-lookup"><span data-stu-id="08ef8-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

### <a name="configuration-data-file"></a><span data-ttu-id="08ef8-123">Archivo de datos de configuración</span><span class="sxs-lookup"><span data-stu-id="08ef8-123">Configuration data file</span></span>

<span data-ttu-id="08ef8-124">Definiremos los datos del entorno de desarrollo y producción en un archivo denominado `DevProdEnvData.psd1` de la siguiente forma:</span><span class="sxs-lookup"><span data-stu-id="08ef8-124">We'll define the development and production environment data in a file named `DevProdEnvData.psd1` as follows:</span></span>

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        WebSiteName     = "New website"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a><span data-ttu-id="08ef8-125">Archivo de script de configuración</span><span class="sxs-lookup"><span data-stu-id="08ef8-125">Configuration script file</span></span>

<span data-ttu-id="08ef8-126">Ahora, en la configuración, que se define en un archivo `.ps1`, filtraremos los nodos que hemos definido en `DevProdEnvData.psd1` por su rol (`MSSQL`, `Dev` o ambos) y los configuraremos según corresponda.</span><span class="sxs-lookup"><span data-stu-id="08ef8-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="08ef8-127">El entorno de desarrollo tiene SQL Server e IIS en un nodo, mientras que el entorno de producción los tiene en dos nodos diferentes.</span><span class="sxs-lookup"><span data-stu-id="08ef8-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="08ef8-128">El contenido del sitio también es diferente, según lo especificado por las propiedades `SiteContents`.</span><span class="sxs-lookup"><span data-stu-id="08ef8-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="08ef8-129">Al final del script de configuración, llamamos a la configuración (compílela en un documento MOF) al pasar `DevProdEnvData.psd1` como el parámetro `$ConfigurationData`.</span><span class="sxs-lookup"><span data-stu-id="08ef8-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="08ef8-130">**Nota:** Esta configuración requiere que los módulos `xSqlPs` y `xWebAdministration` estén instalados en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="08ef8-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="08ef8-131">Vamos a definir la configuración en un archivo denominado `MyWebApp.ps1`:</span><span class="sxs-lookup"><span data-stu-id="08ef8-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

<span data-ttu-id="08ef8-132">Cuando se ejecuta esta configuración, se crean tres archivos MOF (uno para cada entrada con nombre en la matriz **AllNodes**):</span><span class="sxs-lookup"><span data-stu-id="08ef8-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="08ef8-133">Uso de datos que no son de nodo</span><span class="sxs-lookup"><span data-stu-id="08ef8-133">Using non-node data</span></span>

<span data-ttu-id="08ef8-134">Puede agregar claves adicionales a la tabla hash **ConfigurationData** para los datos que no son específicos de un nodo.</span><span class="sxs-lookup"><span data-stu-id="08ef8-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="08ef8-135">La siguiente configuración garantiza la presencia de dos sitios web.</span><span class="sxs-lookup"><span data-stu-id="08ef8-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="08ef8-136">Los datos de cada sitio web se definen en la matriz **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="08ef8-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="08ef8-137">El archivo `Config.xml` se usa para ambos sitios web, por lo que lo definimos en una clave adicional con el nombre `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="08ef8-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="08ef8-138">Tenga en cuenta que puede tener tantas claves adicionales como desee, y puede asignarles el nombre que desee.</span><span class="sxs-lookup"><span data-stu-id="08ef8-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="08ef8-139">`NonNodeData` no es una palabra reservada, es lo que hemos decidido para asignar nombre a la clave adicional.</span><span class="sxs-lookup"><span data-stu-id="08ef8-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="08ef8-140">Tiene acceso a claves adicionales mediante la variable especial **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="08ef8-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="08ef8-141">En este ejemplo, se accede a `ConfigFileContents` con la línea:</span><span class="sxs-lookup"><span data-stu-id="08ef8-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="08ef8-142">en el bloque de recursos `File`.</span><span class="sxs-lookup"><span data-stu-id="08ef8-142">in the `File` resource block.</span></span>


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

        @{
            NodeName = "VM-1"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },


        @{
            NodeName = "VM-2"
            SiteContents = "C:\Site2"
            SiteName = "Website2"
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a><span data-ttu-id="08ef8-143">Véase también</span><span class="sxs-lookup"><span data-stu-id="08ef8-143">See Also</span></span>
- [<span data-ttu-id="08ef8-144">Uso de datos de configuración</span><span class="sxs-lookup"><span data-stu-id="08ef8-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="08ef8-145">Opciones de credenciales en los datos de configuración</span><span class="sxs-lookup"><span data-stu-id="08ef8-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="08ef8-146">Configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="08ef8-146">DSC Configurations</span></span>](configurations.md)
