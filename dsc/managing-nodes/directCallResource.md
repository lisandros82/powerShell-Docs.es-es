---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Llamada directa a los métodos de recursos de DSC
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402290"
---
# <a name="calling-dsc-resource-methods-directly"></a>Llamada directa a los métodos de recursos de DSC

>Se aplica a: Windows PowerShell 5.0

Puede usar el cmdlet [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) para llamar directamente a las funciones o métodos de un recurso de DSC (las funciones **Get-TargetResource**, **Set-TargetResource** y **Test-TargetResource** de un recurso basado en MOF o los métodos **Get**, **Set** y **Test** de un recurso basado en clases).
Esto puede servir para terceros que quieran usar recursos de DSC, o como herramienta útil durante el desarrollo de recursos.

Este cmdlet suele usarse en combinación con una propiedad de metaconfiguración `refreshMode = 'Disabled'`, pero se puede usar independientemente de la opción establecida en **refreshMode**.

Al llamar al cmdlet **Invoke-DscResource**, debe especificar qué método o función llamar mediante el parámetro **Method**. Especifique las propiedades del recurso pasando una tabla hash como el valor del parámetro **Property**.

A continuación, se muestran ejemplos de llamada directa a los métodos de recursos:

## <a name="ensure-a-file-is-present"></a>Asegurarse de que un archivo está presente

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Comprobar que un archivo está presente

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>Obtener el contenido del archivo

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Nota:** No se admite llamar directamente a los métodos de recursos compuestos. En su lugar, llame a los métodos de los recursos subyacentes que forman el recurso compuesto.

## <a name="see-also"></a>Véase también
- [Escribir un recurso de DSC personalizado con MOF](../resources/authoringResourceMOF.md)
- [Escribir un recurso de DSC personalizado con clases de PowerShell](../resources/authoringResourceClass.md)
- [Depuración de recursos de DSC](../troubleshooting/debugResource.md)