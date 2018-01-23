---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Uso de la herramienta Diseñador de recursos"
ms.openlocfilehash: c21602e219b5830877cc211e092e93bb7fc8ad9c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/17/2018
---
# <a name="using-the-resource-designer-tool"></a>Uso de la herramienta Diseñador de recursos

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La herramienta Diseñador de recursos es un conjunto de cmdlets que expone el módulo **xDscResourceDesigner** y facilitan la creación de recursos de configuración de estado deseado (DSC) de Windows PowerShell. Los cmdlets de este recurso ayudan a crear el esquema MOF, el módulo de scripts y la estructura de directorios del nuevo recurso. Para más información sobre los recursos DSC, consulte [Crear recursos de configuración de estado deseado de Windows PowerShell personalizados](authoringResource.md).
En este tema, se creará un recurso de DSC que administre los usuarios de Active Directory.
Use el cmdlet [Install-Module](https://technet.microsoft.com/en-us/library/dn807162.aspx) para instalar el módulo **xDscResourceDesigner**.

>**Nota**: **Install-Module** está incluido en el módulo **PowerShellGet**, que se incluye en PowerShell 5.0. Puede descargar el módulo **PowerShellGet** para PowerShell 3.0 y 4.0 en [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186) (Vista previa de los módulos de PowerShell PackageManagement).

## <a name="creating-resource-properties"></a>Crear propiedades de recursos
Lo primero que es necesario hacer es decidir qué propiedades expondrá el recurso. En este ejemplo, definimos un usuario de Active Directory con las siguientes propiedades.
 
Nombre del parámetro: descripción
* **Nombre de UserName**: propiedad clave que identifica de forma única un usuario.
* **Ensure**: especifica si la cuenta de usuario debe tener el valor Present o Absent. Este parámetro solo tendrá dos valores posibles.
* **DomainCredential**: la contraseña del dominio del usuario.
* **Password**: la contraseña deseada para el usuario a fin de permitir una configuración para cambiar la contraseña del usuario si es necesario.

Para crear las propiedades, use el cmdlet **New-xDscResourceProperty**. Los siguientes comandos de PowerShell crean las propiedades descritas anteriormente.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential-Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Crear el recurso

Ahora que se han creado las propiedades del recurso, se puede llamar al cmdlet **New-xDscResource** para crear el recurso. El cmdlet **New-xDscResource** toma la lista de propiedades como parámetros. También toma la ruta de acceso donde se debe crear el módulo, el nombre del nuevo recurso y el nombre del módulo que lo contiene. El siguiente comando de PowerShell crea el recurso:

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

El cmdlet **New-xDscResource** crea el esquema MOF, un script del recurso de esqueleto, la estructura de directorios necesaria para el nuevo recurso y un manifiesto del módulo que expone el nuevo recurso.

El archivo del esquema MOF se encuentra en **C:\Archivos de Programa\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof** y a continuación se muestran su contenido:

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

El script del recurso se encuentra en **C:\Archivos de Programa\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. No incluye la lógica real para implementar el recurso, que debe agregar usted mismo. El contenido del script de esqueleto es el que se indica a continuación.

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}


function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1


}


function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."


  <#
  $result = [System.Boolean]

  $result
  #>
}


Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a>Actualizar el recurso

Si necesita agregar o modificar la lista de parámetros del recurso, puede llamar al cmdlet **Update-xDscResource**. El cmdlet actualiza el recurso con una nueva lista de parámetros. Si ya ha agregado lógica en el script del recurso, se mantiene intacta.

Por ejemplo, suponga que quiere incluir el último registro en el tiempo del usuario en el recurso. En lugar de escribir completamente de nuevo el recurso, puede llamar a **New-xDscResourceProperty** para crear la nueva propiedad y después llamar a **Update-xDscResource** y agregar la nueva propiedad a la lista de propiedades.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Probar un esquema de recurso

La herramienta Diseñador de recursos expone un cmdlet más que puede utilizarse para probar la validez de un esquema MOF que se escribió manualmente. Llame al cmdlet **Test-xDscSchema** y pase la ruta de acceso de un esquema de recursos MOF como un parámetro. El cmdlet mostrará los errores en el esquema.

### <a name="see-also"></a>Véase también

#### <a name="concepts"></a>Conceptos
[Crear recursos de configuración de estado deseado de Windows PowerShell personalizados](authoringResource.md)

#### <a name="other-resources"></a>Otros recursos
[Módulo xDscResourceDesigner](https://powershellgallery.com/packages/xDscResourceDesigner)