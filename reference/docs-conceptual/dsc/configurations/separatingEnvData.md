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
# <a name="separating-configuration-and-environment-data"></a>Separación de los datos de entorno y configuración

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Puede ser útil separar los datos utilizados en una configuración DSC de la propia configuración mediante el uso de datos de configuración.
Al hacerlo, puede utilizar una sola configuración para varios entornos.

Por ejemplo, si está desarrollando una aplicación, puede usar una configuración para los entornos de producción y desarrollo, y usar datos de configuración para especificar datos para cada entorno.

## <a name="what-is-configuration-data"></a>¿Qué son lo datos de configuración?

Los datos de configuración son datos que se definen en una tabla hash y se pasan a una configuración DSC al compilar esa configuración.

Para una descripción detallada de la tabla hash **ConfigurationData**, consulte [Separación de los datos de entorno y configuración](configData.md).

## <a name="a-simple-example"></a>Un ejemplo sencillo

Veamos un ejemplo muy sencillo de cómo funciona esto.
Crearemos una única configuración que garantice que **IIS** esté presente en algunos nodos y que **Hyper-V** esté presente en otros:

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

La última línea de este script compila la configuración; para ello, pasa `$MyData` como el valor del parámetro **ConfigurationData**.

El resultado es que se crean dos archivos MOF:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` especifica dos nodos diferentes, cada uno con sus propios `NodeName` y `Role`. La configuración crea de forma dinámica bloques de **nodo** al tomar la colección de nodos que se obtiene de `$MyData` (específicamente, `$AllNodes`) y al filtrar esa colección en la propiedad `Role`.

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Uso de datos de configuración para definir entornos de desarrollo y producción

Veamos un ejemplo completo que usa una única configuración para configurar los entornos de desarrollo y producción de un sitio web. En el entorno de desarrollo, IIS y SQL Server se instalan en un único nodo. En el entorno de producción, IIS y SQL Server se instalan en nodos independientes. Vamos a usar un archivo. psd1 de datos de configuración para especificar los datos de los dos entornos diferentes.

### <a name="configuration-data-file"></a>Archivo de datos de configuración

Definiremos los datos del entorno de desarrollo y producción en un archivo denominado `DevProdEnvData.psd1` de la siguiente forma:

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

### <a name="configuration-script-file"></a>Archivo de script de configuración

Ahora, en la configuración, que se define en un archivo `.ps1`, filtraremos los nodos que hemos definido en `DevProdEnvData.psd1` por su rol (`MSSQL`, `Dev` o ambos) y los configuraremos según corresponda.
El entorno de desarrollo tiene SQL Server e IIS en un nodo, mientras que el entorno de producción los tiene en dos nodos diferentes.
El contenido del sitio también es diferente, según lo especificado por las propiedades `SiteContents`.

Al final del script de configuración, llamamos a la configuración (compílela en un documento MOF) al pasar `DevProdEnvData.psd1` como el parámetro `$ConfigurationData`.

>**Nota:** Esta configuración requiere que los módulos `xSqlPs` y `xWebAdministration` estén instalados en el nodo de destino.

Vamos a definir la configuración en un archivo denominado `MyWebApp.ps1`:

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

Cuando se ejecuta esta configuración, se crean tres archivos MOF (uno para cada entrada con nombre en la matriz **AllNodes**):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Uso de datos que no son de nodo

Puede agregar claves adicionales a la tabla hash **ConfigurationData** para los datos que no son específicos de un nodo.
La siguiente configuración garantiza la presencia de dos sitios web.
Los datos de cada sitio web se definen en la matriz **AllNodes**.
El archivo `Config.xml` se usa para ambos sitios web, por lo que lo definimos en una clave adicional con el nombre `NonNodeData`.
Tenga en cuenta que puede tener tantas claves adicionales como desee, y puede asignarles el nombre que desee.
`NonNodeData` no es una palabra reservada, es lo que hemos decidido para asignar nombre a la clave adicional.

Tiene acceso a claves adicionales mediante la variable especial **$ConfigurationData**.
En este ejemplo, se accede a `ConfigFileContents` con la línea:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 en el bloque de recursos `File`.


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


## <a name="see-also"></a>Véase también
- [Uso de datos de configuración](configData.md)
- [Opciones de credenciales en los datos de configuración](configDataCredentials.md)
- [Configuraciones DSC](configurations.md)
