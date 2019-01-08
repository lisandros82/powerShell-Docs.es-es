---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046698"
---
# <a name="dsc-resources"></a>Recursos de DSC

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Los recursos de la configuración de estado deseado (DSC) ofrecen los bloques de creación para una configuración DSC. Un recurso expone las propiedades que se pueden configurar (el esquema) y contiene las funciones de script de PowerShell a las que el administrador de configuración local (LCM) llama para "que sea así".

Un recurso puede modelar algo tan genérico como un archivo o tan específico como una configuración de servidor IIS.  Grupos de recursos similares se combinan en un módulo de DSC, que organiza todos los archivos necesarios en una estructura portátil que incluye los metadatos para identificar cómo están diseñados para usarse los recursos.

Cada recurso tiene un * esquema que determina la sintaxis necesaria para usar el recurso en un [configuración](../configurations/configurations.md). Esquema de un recurso puede definirse de las maneras siguientes:

- **'Schema.Mof'** archivo: Define la mayoría de los recursos sus *esquema* en un 'schema.mof' de archivos, mediante [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- **'\<Nombre de recurso\>. schema.psm1'** archivo: [Recursos compuestos](../configurations/compositeConfigs.md) definir sus *esquema* en un '<ResourceName>. schema.psm1' archivo empleando un [bloque de parámetros](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- **'\<Nombre de recurso\>. psm1 '** archivo: Definen recursos de DSC en función de clase sus *esquema* en la definición de clase. Los elementos de sintaxis se denotan como propiedades de la clase. Para obtener más información, consulte [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Para recuperar la sintaxis para un recurso de DSC, use el [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet con el `-Syntax` parámetro. Este uso es similar a usar [Get-Command](/powershell/module/microsoft.powershell.core/get-command) con el `-Syntax` para obtener la sintaxis del cmdlet. La salida, vea mostrará la plantilla usada para un bloque de recursos para el recurso que especifique.

```powershell
Get-DscResource -Syntax Service
```

La salida, vea debe ser similar a la salida siguiente, aunque la sintaxis de este recurso podrían cambiar en el futuro. Al igual que la sintaxis de cmdlet, el *claves* visto incluido entre corchetes, son opcionales. Los tipos de especifican el tipo de datos que se espera que cada clave.

> [!NOTE]
> El **Asegúrese** clave es opcional porque el valor predeterminado es "Present".

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

Dentro de una configuración, un **servicio** bloque de recursos podría parecerse a esto a **Asegúrese** que se está ejecutando el servicio de cola.

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

Las configuraciones pueden contener varias instancias del mismo tipo de recurso. Cada instancia debe llamarse de forma exclusiva. En el ejemplo siguiente, un segundo **servicio** se agrega el bloque de recursos para configurar el servicio "DHCP".

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
> A partir de PowerShell 5.0, intellisense se agregó para DSC. Esta nueva característica permite usar \<ficha\> y \<Ctrl+barra espaciadora\> para Autocompletar los nombres de clave.

![Finalización con tabulación recursos](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>Recursos integrados

Además de recursos de la Comunidad, hay recursos integrados para Windows, los recursos para Linux y recursos para la dependencia entre nodos. Puede usar los pasos anteriores para determinar la sintaxis de estos recursos y cómo usarlas. Las páginas que sirven a estos recursos se han almacenado en **referencia**.

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
* [Recursos WindowsPackageCabResource](../reference/resources/windows/windowsPackageCabResource.md)
* [Recurso WindowsProcess](../reference/resources/windows/windowsProcessResource.md)

[Dependencias entre nodos](../configurations/crossNodeDependencies.md) recursos

* [Recurso WaitForAll](../reference/resources/windows/waitForAllResource.md)
* [Recurso WaitForSome](../reference/resources/windows/waitForSomeResource.md)
* [Recurso WaitForAny](../reference/resources/windows/waitForAnyResource.md)

Recursos del paquete de administración

* [Recurso PackageManagement](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [Recurso PackageManagementSource](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Recursos de Linux

* [Recurso Linux Archive](../reference/resources/linux/lnxArchiveResource.md)
* [Recursos del entorno de Linux](../reference/resources/linux/lnxEnvironmentResource.md)
* [Linux FileLine recursos](../reference/resources/linux/lnxFileLineResource.md)
* [Recurso de archivos de Linux](../reference/resources/linux/lnxFileResource.md)
* [Recurso de grupo de Linux](../reference/resources/linux/lnxGroupResource.md)
* [Recursos del paquete Linux](../reference/resources/linux/lnxPackageResource.md)
* [Recurso de Script de Linux](../reference/resources/linux/lnxScriptResource.md)
* [Recurso del servicio de Linux](../reference/resources/linux/lnxServiceResource.md)
* [Linux SshAuthorizedKeys recursos](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Recursos de usuario de Linux](../reference/resources/linux/lnxUserResource.md)
