---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Uso de la herramienta Diseñador de recursos
ms.openlocfilehash: 4f678f4586c75c830bf876b891fe4784aa3b4e95
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323755"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="0854f-103">Uso de la herramienta Diseñador de recursos</span><span class="sxs-lookup"><span data-stu-id="0854f-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="0854f-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0854f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0854f-105">La herramienta Diseñador de recursos es un conjunto de cmdlets que expone el módulo **xDscResourceDesigner** y facilitan la creación de recursos de configuración de estado deseado (DSC) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0854f-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="0854f-106">Los cmdlets de este recurso ayudan a crear el esquema MOF, el módulo de scripts y la estructura de directorios del nuevo recurso.</span><span class="sxs-lookup"><span data-stu-id="0854f-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="0854f-107">Para más información sobre los recursos DSC, consulte [Crear recursos de configuración de estado deseado de Windows PowerShell personalizados](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="0854f-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="0854f-108">En este tema, se creará un recurso de DSC que administre los usuarios de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0854f-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="0854f-109">Use el cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) para instalar el módulo **xDscResourceDesigner**.</span><span class="sxs-lookup"><span data-stu-id="0854f-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="0854f-110">**Nota**: Install-Module está incluido en el módulo **PowerShellGet**, que se incluye en PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="0854f-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="0854f-111">Puede descargar el módulo **PowerShellGet** para PowerShell 3.0 y 4.0 en [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186) (Vista previa de los módulos de PowerShell PackageManagement).</span><span class="sxs-lookup"><span data-stu-id="0854f-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="0854f-112">Crear propiedades de recursos</span><span class="sxs-lookup"><span data-stu-id="0854f-112">Creating resource properties</span></span>
<span data-ttu-id="0854f-113">Lo primero que es necesario hacer es decidir qué propiedades expondrá el recurso.</span><span class="sxs-lookup"><span data-stu-id="0854f-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="0854f-114">En este ejemplo, definimos un usuario de Active Directory con las siguientes propiedades.</span><span class="sxs-lookup"><span data-stu-id="0854f-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="0854f-115">Nombre del parámetro: descripción</span><span class="sxs-lookup"><span data-stu-id="0854f-115">Parameter name  Description</span></span>
* <span data-ttu-id="0854f-116">**UserName**: propiedad clave que identifica de forma única un usuario.</span><span class="sxs-lookup"><span data-stu-id="0854f-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="0854f-117">**Ensure**: especifica si la cuenta de usuario debe tener el valor Present o Absent.</span><span class="sxs-lookup"><span data-stu-id="0854f-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="0854f-118">Este parámetro solo tendrá dos valores posibles.</span><span class="sxs-lookup"><span data-stu-id="0854f-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="0854f-119">**DomainCredential**: la contraseña del dominio del usuario.</span><span class="sxs-lookup"><span data-stu-id="0854f-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="0854f-120">**Password**: la contraseña deseada para el usuario a fin de permitir una configuración para cambiar la contraseña del usuario si es necesario.</span><span class="sxs-lookup"><span data-stu-id="0854f-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="0854f-121">Para crear las propiedades, use el cmdlet **New-xDscResourceProperty**.</span><span class="sxs-lookup"><span data-stu-id="0854f-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="0854f-122">Los siguientes comandos de PowerShell crean las propiedades descritas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0854f-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="0854f-123">Crear el recurso</span><span class="sxs-lookup"><span data-stu-id="0854f-123">Create the resource</span></span>

<span data-ttu-id="0854f-124">Ahora que se han creado las propiedades del recurso, se puede llamar al cmdlet **New-xDscResource** para crear el recurso.</span><span class="sxs-lookup"><span data-stu-id="0854f-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="0854f-125">El cmdlet **New-xDscResource** toma la lista de propiedades como parámetros.</span><span class="sxs-lookup"><span data-stu-id="0854f-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="0854f-126">También toma la ruta de acceso donde se debe crear el módulo, el nombre del nuevo recurso y el nombre del módulo que lo contiene.</span><span class="sxs-lookup"><span data-stu-id="0854f-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="0854f-127">El siguiente comando de PowerShell crea el recurso:</span><span class="sxs-lookup"><span data-stu-id="0854f-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

<span data-ttu-id="0854f-128">El cmdlet **New-xDscResource** crea el esquema MOF, un script del recurso de esqueleto, la estructura de directorios necesaria para el nuevo recurso y un manifiesto del módulo que expone el nuevo recurso.</span><span class="sxs-lookup"><span data-stu-id="0854f-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="0854f-129">El archivo del esquema MOF se encuentra en **C:\Archivos de Programa\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof** y a continuación se muestran su contenido:</span><span class="sxs-lookup"><span data-stu-id="0854f-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="0854f-130">El script del recurso se encuentra en **C:\Archivos de Programa\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="0854f-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="0854f-131">No incluye la lógica real para implementar el recurso, que debe agregar usted mismo.</span><span class="sxs-lookup"><span data-stu-id="0854f-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="0854f-132">El contenido del script de esqueleto es el que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="0854f-132">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="0854f-133">Actualizar el recurso</span><span class="sxs-lookup"><span data-stu-id="0854f-133">Updating the resource</span></span>

<span data-ttu-id="0854f-134">Si necesita agregar o modificar la lista de parámetros del recurso, puede llamar al cmdlet **Update-xDscResource**.</span><span class="sxs-lookup"><span data-stu-id="0854f-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="0854f-135">El cmdlet actualiza el recurso con una nueva lista de parámetros.</span><span class="sxs-lookup"><span data-stu-id="0854f-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="0854f-136">Si ya ha agregado lógica en el script del recurso, se mantiene intacta.</span><span class="sxs-lookup"><span data-stu-id="0854f-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="0854f-137">Por ejemplo, suponga que quiere incluir el último registro en el tiempo del usuario en el recurso.</span><span class="sxs-lookup"><span data-stu-id="0854f-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="0854f-138">En lugar de escribir completamente de nuevo el recurso, puede llamar a **New-xDscResourceProperty** para crear la nueva propiedad y después llamar a **Update-xDscResource** y agregar la nueva propiedad a la lista de propiedades.</span><span class="sxs-lookup"><span data-stu-id="0854f-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="0854f-139">Probar un esquema de recurso</span><span class="sxs-lookup"><span data-stu-id="0854f-139">Testing a resource schema</span></span>

<span data-ttu-id="0854f-140">La herramienta Diseñador de recursos expone un cmdlet más que puede utilizarse para probar la validez de un esquema MOF que se escribió manualmente.</span><span class="sxs-lookup"><span data-stu-id="0854f-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="0854f-141">Llame al cmdlet **Test-xDscSchema** y pase la ruta de acceso de un esquema de recursos MOF como un parámetro.</span><span class="sxs-lookup"><span data-stu-id="0854f-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="0854f-142">El cmdlet mostrará los errores en el esquema.</span><span class="sxs-lookup"><span data-stu-id="0854f-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="0854f-143">Véase también</span><span class="sxs-lookup"><span data-stu-id="0854f-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="0854f-144">Conceptos</span><span class="sxs-lookup"><span data-stu-id="0854f-144">Concepts</span></span>
[<span data-ttu-id="0854f-145">Crear recursos de configuración de estado deseado de Windows PowerShell personalizados</span><span class="sxs-lookup"><span data-stu-id="0854f-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="0854f-146">Otros recursos</span><span class="sxs-lookup"><span data-stu-id="0854f-146">Other Resources</span></span>
[<span data-ttu-id="0854f-147">Módulo xDscResourceDesigner</span><span class="sxs-lookup"><span data-stu-id="0854f-147">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
