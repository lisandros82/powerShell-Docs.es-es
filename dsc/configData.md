---
title: "Separación de los datos de entorno y configuración"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 27d9a259d119099c45d7ecd3a15cd26654071d42
ms.sourcegitcommit: 26f4e52f3dd008b51b7eae7b634f0216eec6200e
translationtype: HT
---
# <a name="separating-configuration-and-environment-data"></a>Separación de los datos de entorno y configuración

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Puede definir los datos que se pueden usar dentro de una configuración al usar el parámetro DSC integrado **ConfigurationData**. Esto le permite crear una única configuración que puede usarse para varios nodos o para entornos diferentes. Por ejemplo, si está desarrollando una aplicación, puede usar una configuración para los entornos de producción y desarrollo, y usar datos de configuración para especificar datos para cada entorno.

Veamos un ejemplo muy sencillo de cómo funciona esto. Crearemos una única configuración que garantice que **IIS** esté presente en algunos nodos y que **Hyper-V** esté presente en otros: 

```powershell
Configuration MyDscConfiguration {
    
    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
        
    }
    Node $AllNodes.Where($_.Role -eq "VMHost").NodeName
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

La última línea de este script compila la configuración en documentos MOF; para ello, pasa `$MyData` como el valor de parámetro **ConfigurationData**. `$MyData` especifica dos nodos diferentes, cada uno con sus propios `NodeName` y `Role`. La configuración crea de forma dinámica bloques de **nodo** al tomar la colección de nodos que se obtiene de `$MyData` (específicamente, `$AllNodes`) y al filtrar esa colección en la propiedad `Role`.

Ahora veremos cómo funciona con más detalle.

## <a name="the-configurationdata-parameter"></a>El parámetro ConfigurationData

Una configuración DSC toma un parámetro denominado **ConfigurationData**, que se especifica cuando se compila la configuración. Para obtener más información sobre la compilación de configuraciones, consulte [Configuraciones DSC](configurations.md).

El parámetro **ConfigurationData** es un tabla hash que debe tener al menos una clave denominada **AllNodes**. También puede tener otras claves:

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

Para aplicar una propiedad a todos los nodos, puede crear un miembro de la matriz **AllNodes** que tenga un **NodeName** de `*`. Por ejemplo, para aplicar a todos los nodos una propiedad `LogPath`, se podría hacer lo siguiente:

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

Puede definir **ConfigurationData** como una variable en el mismo archivo de script que una configuración (como en los ejemplos anteriores) o en un archivo. psd1 independiente. Para definir **ConfigurationData** en un archivo. psd1, cree un archivo que contenga solo la tabla hash que representa los datos de configuración.

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

Para usar datos de configuración que se definen en un archivo. psd1, pase la ruta de acceso y el nombre de ese archivo como el valor del parámetro **ConfigurationData** al compilar la configuración:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Uso de variables ConfigurationData en una configuración

DSC proporciona tres variables especiales que se pueden usar en un script de configuración:**$AllNodes**, **$Node** y **$ConfigurationData**.

- **$AllNodes** hace referencia a toda la colección de nodos que se define en **ConfigurationData**. Puede filtrar la colección **AllNodes** mediante **.Where()** y **.ForEach()**.
- **Node** hace referencia a un valor determinado en la colección **AllNodes** después de que se filtre mediante **.Where()** o **.ForEach()**.
- **ConfigurationData** hace referencia a toda la tabla hash que se pasa como parámetro al compilar una configuración.

## <a name="devops-example"></a>Ejemplo de DevOps

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

Ahora, en la configuración, que se define en un archivo .ps1, filtraremos los nodos que hemos definido en `DevProdEnvData.psd1` por su rol (`MSSQL`, `Dev` o ambos) y los configuraremos según corresponda. El entorno de desarrollo tiene SQL Server e IIS en un nodo, mientras que el entorno de producción los tiene en dos nodos diferentes. El contenido del sitio también es diferente, según lo especificado por las propiedades `SiteContents`.

Al final del script de configuración, llamamos a la configuración (compílela en un documento MOF) al pasar `DevProdEnvData.psd1` como el parámetro `$ConfigurationData`.

>**Nota:** Esta configuración requiere que los módulos `xSqlPs` y `xWebAdministration` estén instalados en el nodo de destino.

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.Nodename
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

   Node $AllNodes.Where($_.Role -contains "Web").NodeName
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
            Name            = $WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

## <a name="see-also"></a>Véase también
- [Opciones de credenciales en los datos de configuración](configDataCredentials.md)
- [Configuraciones DSC](configurations.md)
