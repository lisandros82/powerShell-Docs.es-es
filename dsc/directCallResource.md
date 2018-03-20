---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Llamada directa a los métodos de recursos de DSC"
ms.openlocfilehash: 68344d1be5c41e5ce4660e0a62019fa0a52c2541
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="calling-dsc-resource-methods-directly"></a>Llamada directa a los métodos de recursos de DSC

>Se aplica a: Windows PowerShell 5.0

Puede usar el cmdlet [Invoke-DscResource](https://technet.microsoft.com/library/mt517869.aspx) para llamar directamente a las funciones o métodos de un recurso de DSC (las funciones **Get-TargetResource**, **Set-TargetResource** y **Test-TargetResource** de un recurso basado en MOF o los métodos **Get**, **Set** y **Test** de un recurso basado en clases). Esto puede servir para terceros que quieran usar recursos de DSC, o como herramienta útil durante el desarrollo de recursos. 

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

>**Nota:** No se admite llamar directamente a métodos de recursos compuestos. En su lugar, llame a los métodos de los recursos subyacentes que forman el recurso compuesto.

## <a name="see-also"></a>Véase también
- [Escribir un recurso de DSC personalizado con MOF](authoringResourceMOF.md) 
- [Escribir un recurso de DSC personalizado con clases de PowerShell](authoringResourceClass.md)
- [Depuración de recursos de DSC](debugResource.md)

