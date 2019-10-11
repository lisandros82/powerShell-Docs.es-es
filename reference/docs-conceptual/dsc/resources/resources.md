---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954252"
---
# <a name="dsc-resources"></a>Recursos de DSC

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Los recursos de la configuración de estado deseado (DSC) ofrecen los bloques de creación para una configuración DSC. Un recurso expone las propiedades que se pueden configurar (el esquema) y contiene las funciones de script de PowerShell a las que el administrador de configuración local (LCM) llama para "que sea así".

Un recurso puede modelar algo tan genérico como un archivo o tan específico como una configuración de servidor IIS.  Grupos de recursos similares se combinan en un módulo de DSC, que organiza todos los archivos necesarios en una estructura portátil que incluye los metadatos para identificar cómo están diseñados para usarse los recursos.

Cada recurso tiene un *esquema que determina la sintaxis necesaria para usar el recurso en una [configuración](../configurations/configurations.md). El esquema de un recurso se puede definir de las siguientes maneras:

- Archivo **"Schema.Mof"** : La mayoría de los recursos definen su *esquema* en un archivo "schema.mof", utilizando [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- Archivo **"\<Nombre de recurso\>.schema.psm1"** : Los [recursos compuestos](../configurations/compositeConfigs.md) definen su *esquema* en un archivo "<ResourceName>.schema.psm1" usando un [bloque de parámetros](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- Archivo **"\<Nombre de recurso\>.psm1"** : Los recursos DSC basados en clase definen su *esquema* en la definición de clase. Los elementos de sintaxis se denotan como propiedades de la clase. Para más información, consulte [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc) (Acerca de las clases).

Para recuperar la sintaxis de un recurso DSC, use el cmdlet [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) con el parámetro `-Syntax`. Este uso es similar al uso de [Get-Command](/powershell/module/microsoft.powershell.core/get-command) con el parámetro `-Syntax` para obtener la sintaxis del cmdlet. La salida que ve mostrará la plantilla utilizada para un bloque de recursos para el recurso que especifique.

```powershell
Get-DscResource -Syntax Service
```

La salida que ve debe ser similar a la salida siguiente, aunque la sintaxis de este recurso podría cambiar en el futuro. Al igual que la sintaxis del cmdlet, las *claves* que aparecen entre corchetes son opcionales. Los tipos especifican el tipo de datos que espera cada clave.

> [!NOTE]
> La clave **Ensure** es opcional porque el valor predeterminado es "Present".

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

Dentro de una configuración, un bloque de recursos **Service** podría parecerse a esto para aplicar **Ensure** en relación con la ejecución del servicio Spooler.

> [!NOTE]
> Antes de usar un recurso en una configuración, debe importarlo mediante [Import-DSCResource](../configurations/import-dscresource.md).

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

Las configuraciones pueden contener varias instancias del mismo tipo de recurso. Cada instancia debe tener un nombre exclusivo. En el siguiente ejemplo, se agrega un segundo bloque de recursos **Service** para configurar el servicio "DHCP".

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> A partir de PowerShell 5.0, se agregó Intellisense para DSC. Esta nueva característica permite usar \<TAB\> y \<Ctrl+barra espaciadora\> para completar automáticamente los nombres de clave.

![Finalización con tabulación de recursos](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>Recursos integrados

Además de los recursos de la comunidad, hay recursos incorporados para Windows, para Linux y para la dependencia entre nodos. Puede usar los pasos anteriores para determinar la sintaxis de estos recursos y cómo usarlos. Las páginas relativas a estos recursos se han almacenado en **Referencia**.

Recursos integrados de Windows

* [Recurso Archive](../reference/resources/windows/archiveResource.md)
* [Recurso Environment](../reference/resources/windows/environmentResource.md)
* [Recurso File](../reference/resources/windows/fileResource.md)
* [Recurso Group](../reference/resources/windows/groupResource.md)
* [Recurso GroupSet](../reference/resources/windows/groupSetResource.md)
* [Recurso Log](../reference/resources/windows/logResource.md)
* [Recurso Package](../reference/resources/windows/packageResource.md)
* [Recurso ProcessSet](../reference/resources/windows/ProcessSetResource.md)
* [Recurso Registry](../reference/resources/windows/registryResource.md)
* [Recurso Script](../reference/resources/windows/scriptResource.md)
* [Recurso Service](../reference/resources/windows/serviceResource.md)
* [Recurso ServiceSet](../reference/resources/windows/serviceSetResource.md)
* [Recurso User](../reference/resources/windows/userResource.md)
* [Recurso WindowsFeature](../reference/resources/windows/windowsFeatureResource.md)
* [Recurso WindowsFeatureSet](../reference/resources/windows/windowsFeatureSetResource.md)
* [Recurso WindowsOptionalFeature](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [Recurso WindowsOptionalFeatureSet](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [Recurso WindowsPackageCabResource](../reference/resources/windows/windowsPackageCabResource.md)
* [Recurso WindowsProcess](../reference/resources/windows/windowsProcessResource.md)

Recursos de [dependencias entre nodos](../configurations/crossNodeDependencies.md)

* [Recurso WaitForAll](../reference/resources/windows/waitForAllResource.md)
* [Recurso WaitForSome](../reference/resources/windows/waitForSomeResource.md)
* [Recurso WaitForAny](../reference/resources/windows/waitForAnyResource.md)

Recursos de Administración de paquetes

* [Recurso PackageManagement](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [Recurso PackageManagementSource](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Recursos de Linux

* [Recurso Archive para Linux](../reference/resources/linux/lnxArchiveResource.md)
* [Recurso Environment para Linux](../reference/resources/linux/lnxEnvironmentResource.md)
* [Recurso FileLine para Linux](../reference/resources/linux/lnxFileLineResource.md)
* [Recurso File para Linux](../reference/resources/linux/lnxFileResource.md)
* [Recurso Group para Linux](../reference/resources/linux/lnxGroupResource.md)
* [Recurso Package para Linux](../reference/resources/linux/lnxPackageResource.md)
* [Recurso Script para Linux](../reference/resources/linux/lnxScriptResource.md)
* [Recurso Service para Linux](../reference/resources/linux/lnxServiceResource.md)
* [Recurso SshAuthorizedKeys para Linux](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Recurso User para Linux](../reference/resources/linux/lnxUserResource.md)
