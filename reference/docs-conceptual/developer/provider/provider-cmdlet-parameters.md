---
title: Parámetros de cmdlet de proveedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366314"
---
# <a name="provider-cmdlet-parameters"></a>Parámetros del cmdlet de proveedor

Los cmdlets de proveedor incluyen un conjunto de parámetros estáticos que están disponibles para todos los proveedores que admiten el cmdlet, así como los parámetros dinámicos que se agregan cuando el usuario especifica un valor determinado para determinados parámetros estáticos del cmdlet Provider.

## <a name="provider-cmdlet-static-parameters"></a>Parámetros estáticos de cmdlet de proveedor

Los parámetros estáticos se definen mediante Windows PowerShell. Windows PowerShell implementa un gran conjunto de estos parámetros para proporcionar coherencia en todos los proveedores y proporcionar una experiencia de desarrollo más sencilla. Entre los ejemplos de estos parámetros se incluyen los parámetros `literalPath`, `exclude` y `include` del cmdlet `Get-Item`. Se puede sobrescribir un conjunto más pequeño de estos parámetros para proporcionar acciones específicas del proveedor. Entre los ejemplos de estos parámetros se incluyen los parámetros `Path` y `Value` del cmdlet `Set-Item`. Esta es una lista de los parámetros que se pueden sobrescribir para los cmdlets de proveedor.

cmdlet `Clear-Content` puede definir el modo en que el proveedor usará los valores pasados al parámetro `Path` del cmdlet `Clear-Content` implementando el método [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) .

cmdlet `Clear-Item` puede definir el modo en que el proveedor usará los valores pasados al parámetro `Path` del cmdlet `Clear-Item` implementando el método [System. Management. Automation. Provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) .

cmdlet `Clear-ItemProperty` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path` y `Name` del cmdlet `Clear-ItemProperty` implementando el método [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) .

cmdlet `Copy-Item` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path`, `Destination` y `Recurse` del cmdlet `Copy-Item` implementando [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) forma.

Cmdlet Get-ChildItems puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path` y `Recurse` del cmdlet `Get-ChildItem` implementando [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) y [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) .

cmdlet `Get-Content` puede definir el modo en que el proveedor usará los valores pasados al parámetro `Path` del cmdlet `Get-Content` implementando el método [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) .

cmdlet `Get-Item` puede definir el modo en que el proveedor usará los valores pasados al parámetro `Path` del cmdlet `Get-Item` implementando el método [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) .

cmdlet `Get-ItemProperty` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path` y `Name` del cmdlet `Get-ItemProperty` implementando el método [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) .

cmdlet `Invoke-Item` puede definir el modo en que el proveedor usará los valores pasados al parámetro `Path` del cmdlet `Invoke-Item` implementando el método [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

cmdlet `Move-Item` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path` y `Destination` del cmdlet `Move-Item` implementando el método [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) .

cmdlet `New-Item` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path`, `ItemType` y `Value` del cmdlet `New-Item` implementando [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) forma.

cmdlet `New-ItemProperty` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path`, `Name`, `PropertyType` y `Value` del cmdlet `New-ItemProperty` mediante la implementación de [Microsoft. PowerShell. Commands. Registryprovider. newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) forma.

`Remove-Item` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path` y `Recurse` del cmdlet `Remove-Item` implementando el método [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) .

`Remove-ItemProperty` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path` y `Name` del cmdlet `Remove-ItemProperty` implementando [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removeproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) forma.

cmdlet `Rename-Item` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path` y `NewName` del cmdlet `Rename-Item` implementando el método [System. Management. Automation. Provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) .

`Rename-ItemProperty` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path`, `NewName` y `Name` del cmdlet `Rename-ItemProperty` implementando [System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renameproperty * ](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)método.

cmdlet `Set-Content` puede definir el modo en que el proveedor usará los valores pasados al parámetro `Path` del cmdlet `Set-Content` implementando el método [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) .

cmdlet `Set-Item` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path` y `Value` del cmdlet `Set-Item` implementando el método [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) .

cmdlet `Set-ItemProperty` puede definir el modo en que el proveedor usará los valores pasados a los parámetros `Path` y `Value` del cmdlet `Set-Item` implementando el método [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) .

cmdlet `Test-Path` puede definir el modo en que el proveedor usará los valores pasados al parámetro `Path` del cmdlet `Test-Path` implementando el método [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) .

Además, no se pueden especificar las características de estos parámetros, como si son opcionales o obligatorios, ni se puede asignar a estos parámetros un alias o especificar cualquiera de los atributos de validación. Por el contrario, puede especificar características de parámetros en cmdlets independientes mediante el uso de atributos como el atributo `Parameters`.

## <a name="provider-cmdlet-dynamic-parameters"></a>Parámetros dinámicos del cmdlet de proveedor

Los parámetros dinámicos para los proveedores de cmdlets son similares a los proveedores dinámicos para cmdlets independientes. En ambos casos, los parámetros se agregan al cmdlet cuando el usuario especifica un valor determinado para uno de los parámetros predeterminados, como el parámetro `path`. Sin embargo, no todos los parámetros estáticos se pueden usar para desencadenar la adición de parámetros dinámicos. Para obtener más información sobre los parámetros dinámicos, consulte [parámetros dinámicos de cmdlet de proveedor](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Véase también

[Parámetros dinámicos del cmdlet de proveedor](./provider-cmdlet-dynamic-parameters.md)

[Escribir un proveedor de Windows PowerShell](./writing-a-windows-powershell-provider.md)