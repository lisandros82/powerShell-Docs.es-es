---
ms.date: 04/11/2018
keywords: dsc,powershell,configuration,setup
title: Configuración de un servidor de incorporación de cambios SMB de DSC
ms.openlocfilehash: 25705d9ae06b3ce8daa352142cc0b84793ab6359
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324858"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a>Configuración de un servidor de incorporación de cambios SMB de DSC

Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

> [!IMPORTANT]
> El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades. Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).

Un servidor de extracción [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) de DSC es un equipo que hospeda recursos compartidos de archivos SMB que ponen los archivos de configuración de DSC o los recursos de DSC a disposición de los nodos de destino cuando estos nodos los solicitan.

Para utilizar un servidor de incorporación de cambios SMB para DSC, debe:

- Configurar un recurso compartido de archivos SMB en un servidor que ejecute PowerShell 4.0 o posterior
- Configurar un cliente que ejecute PowerShell 4.0 o posterior para que se extraiga de ese recurso compartido SMB

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a>Usar el recurso xSmbShare para crear un recurso compartido de archivos SMB

Hay varias maneras de configurar un recurso compartido de archivos SMB, pero echemos un vistazo a cómo puede hacerlo mediante DSC.

### <a name="install-the-xsmbshare-resource"></a>Instalar el recurso xSmbShare

Llame al cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) para instalar el módulo **xSmbShare**

> [!NOTE]
> `Install-Module` está incluido en el módulo **PowerShellGet**, que se incluye en PowerShell 5.0. Puede descargar el módulo **PowerShellGet** para PowerShell 3.0 y 4.0 en [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186) (Vista previa de los módulos de PowerShell PackageManagement).
> **xSmbShare** contiene el recurso de DSC **xSmbShare**, que se puede usar para crear un recurso compartido de archivos SMB.

### <a name="create-the-directory-and-file-share"></a>Crear el directorio y el recurso compartido de archivos

La configuración siguiente utiliza el recurso **File** para crear el directorio para el recurso compartido, y el recurso **xSmbShare** para configurar el recurso compartido SMB:

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

La configuración crea el directorio `C:\DscSmbShare` si aún no existe y, a continuación, usa ese directorio como un recurso compartido de archivos SMB. **FullAccess** debe proporcionarse a cualquier cuenta que deba escribir o eliminar contenido del recurso compartido de archivo. **ReadAccess** debe proporcionarse a cualquier nodo de cliente que obtenga configuraciones o recursos de DSC del recurso compartido.

> [!NOTE]
> DSC se ejecuta como la cuenta del sistema de forma predeterminada, por lo que el mismo equipo debe tener acceso al recurso compartido.

### <a name="give-file-system-access-to-the-pull-client"></a>Conceder al sistema de archivos acceso al cliente de incorporación de cambios

Al conceder el acceso **ReadAccess** a un nodo de cliente, se permite que ese nodo acceda al recurso compartido SMB, pero no a los archivos o a las carpetas de dentro de ese recurso compartido. Tiene que conceder explícitamente a los nodos de cliente acceso a las carpetas y subcarpetas del recurso compartido SMB. Se puede hacer esto con DSC si se agrega con el recurso **cNtfsPermissionEntry**, que se encuentra en el módulo [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0). La siguiente configuración agrega un bloque **cNtfsPermissionEntry** que concede acceso ReadAndExecute al cliente de incorporación de cambios:

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a>Colocación de configuraciones y recursos

Guarde todos los archivos MOF de configuración o los recursos de DSC que quiera que los nodos de cliente extraigan en la carpeta del recurso compartido SMB.

Todos los archivos MOF de configuración deben denominarse *ConfigurationID*.mof, donde *ConfigurationID* es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino. Para más información sobre la configuración de clientes de extracción, vea [Configuración de un cliente de extracción mediante id. de configuración](pullClientConfigID.md).

> [!NOTE]
> Debe usar identificadores de configuración si está utilizando un servidor de incorporación de cambios SMB. Los nombres de configuración no son compatibles con SMB.

Cada módulo de recursos se debe comprimir y se le debe asignar un nombre de acuerdo con el patrón `{Module Name}_{Module Version}.zip`. Por ejemplo, un módulo denominado xWebAdminstration con una versión de módulo de 3.1.2.0 se denominaría 'xWebAdministration_3.2.1.0.zip'. Cada versión de un módulo debe incluirse en un solo archivo ZIP. No se admiten versiones distintas de un módulo en un archivo zip. Antes de empaquetar los módulos de recursos de DSC para su uso con el servidor de extracción, debe realizar un pequeño cambio en la estructura de directorios.

El formato predeterminado de los módulos que contienen recursos de DSC en WMF 5.0 es `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.

Antes de empaquetar para el servidor de incorporación de cambios, simplemente quite la carpeta `{Module version}` para que la ruta se quede en `{Module Folder}\DscResources\{DSC Resource Folder}\`. Con este cambio, comprima la carpeta según lo descrito anteriormente y coloque estos archivos ZIP en la carpeta compartida SMB.

## <a name="creating-the-mof-checksum"></a>Creación de la suma de comprobación MOF

Un archivo de configuración MOF debe emparejarse con un archivo de suma de comprobación para que un LCM de un nodo de destino pueda validar la configuración.
Para crear una suma de comprobación, llame al cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum). El cmdlet toma un parámetro `Path` que especifica la carpeta donde se encuentra el MOF de configuración. El cmdlet crea un archivo de suma de comprobación denominado `ConfigurationMOFName.mof.checksum`, donde `ConfigurationMOFName` es el nombre del archivo mof de configuración.
Si hay más de un archivo MOF de configuración en la carpeta especificada, se crea una suma de comprobación para cada una de las configuraciones de la carpeta.

El archivo de suma de comprobación debe estar en el mismo directorio que el archivo MOF de configuración (de forma predeterminada, `$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration`) y tener el mismo nombre con la extensión `.checksum` anexada.

> [!NOTE]
> Si cambia el archivo MOF de configuración de cualquier manera, también deberá volver a crear el archivo de suma de comprobación.

## <a name="setting-up-a-pull-client-for-smb"></a>Configuración de un cliente de extracción para SMB

Para configurar un cliente que extraiga las configuraciones o recursos desde un recurso compartido de SMB, configure el administrador de configuración local (LCM) del cliente con los bloques **ConfigurationRepositoryShare** y **ResourceRepositoryShare** que especifiquen el recurso compartido desde el que se van a extraer las configuraciones y los recursos de DSC.

Para obtener más información sobre cómo configurar el LCM, consulte [Configuración de un cliente de extracción mediante id. de configuración](pullClientConfigID.md).

> [!NOTE]
> Por motivos de simplicidad, este ejemplo usa **PSDscAllowPlainTextPassword** para permitir pasar una contraseña de texto no cifrado al parámetro **Credential**. Para obtener información sobre cómo pasar credenciales de forma más segura, consulte [Opciones de credenciales en los datos de configuración](../configurations/configDataCredentials.md).
>
> **DEBE** especificar un **ConfigurationID** en el bloque **Configuration** de una metaconfiguración para un servidor de incorporación de cambios SMB, incluso si solo está incorporando recursos.

```powershell
$secpasswd = ConvertTo-SecureString "Pass1Word" -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential ("TestUser", $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a>Agradecimientos

Agradecimientos especiales a las personas siguientes:

- Mike F. Robbins, cuyas publicaciones sobre el uso de SMB para DSC permitieron informar del contenido de este tema. Su blog es [Mike F Robbins](http://mikefrobbins.com/).
- Serge Nikalaichyk, que creó el módulo **cNtfsAccessControl**. El código de este módulo está en [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).

## <a name="see-also"></a>Vea también

[Información general sobre la configuración de estado deseado de Windows PowerShell](../overview/overview.md)

[Establecer configuraciones](enactingConfigurations.md)

[Configuración de un cliente de extracción mediante id. de configuración](pullClientConfigID.md)
