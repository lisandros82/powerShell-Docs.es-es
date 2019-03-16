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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057049"
---
# <a name="provider-cmdlet-parameters"></a>Parámetros del cmdlet de proveedor

Cmdlets de proveedor vienen con un conjunto de parámetros estáticos que están disponibles para todos los proveedores que admiten el cmdlet, los parámetros dinámicos, así como que se agregan cuando el usuario especifica un valor determinado para ciertos parámetros estáticos del cmdlet de proveedor.

## <a name="provider-cmdlet-static-parameters"></a>Parámetros de Cmdlet estático de proveedor

Parámetros estáticos se definen mediante Windows PowerShell. Un conjunto grande de estos parámetros se implementa mediante Windows PowerShell para proporcionar coherencia entre todos los proveedores y para proporcionar una experiencia de desarrollo más sencilla. Algunos ejemplos de estos parámetros son el `literalPath`, `exclude`, y `include` parámetros de la `Get-Item` cmdlet. Para proporcionar acciones específicas para el proveedor se puede sobrescribir un conjunto menor de estos parámetros. Algunos ejemplos de estos parámetros son el `Path` y `Value` parámetro de la `Set-Item` cmdlet. Presentamos una lista de los parámetros que se puede sobrescribir para los cmdlets de proveedor.

`Clear-Content` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` parámetro de la `Clear-Content` cmdlet mediante la implementación de la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)método.

`Clear-Item` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` parámetro de la `Clear-Item` cmdlet mediante la implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) método.

`Clear-ItemProperty` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` y `Name` parámetros de la `Clear-ItemProperty` cmdlet mediante la implementación de la [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) método.

`Copy-Item` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path`, `Destination`, y `Recurse` parámetros de la `Copy-Item` cmdlet mediante la implementación de la [ System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método.

Cmdlet Get-ChildItems puede definir cómo el proveedor usará los valores pasados a la `Path` y `Recurse` parámetros de la `Get-ChildItem` cmdlet implementando la [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) y [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) métodos.

`Get-Content` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` parámetro de la `Get-Content` cmdlet mediante la implementación de la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método.

`Get-Item` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` parámetro de la `Get-Item` cmdlet mediante la implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método.

`Get-ItemProperty` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` y `Name` parámetros de la `Get-ItemProperty` cmdlet mediante la implementación de la [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) método.

`Invoke-Item` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` parámetro de la `Invoke-Item` cmdlet mediante la implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)método.

`Move-Item` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` y `Destination` parámetros de la `Move-Item` cmdlet mediante la implementación de la [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método.

`New-Item` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path`, `ItemType`, y `Value` parámetros de la `New-Item` cmdlet mediante la implementación de la [ System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método.

`New-ItemProperty` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path`, `Name`, `PropertyType`, y `Value` parámetros de la `New-ItemProperty` cmdlet mediante la implementación de la [ Microsoft.PowerShell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) método.

`Remove-Item` Puede definir cómo el proveedor usará los valores pasados a la `Path` y `Recurse` parámetros de la `Remove-Item` cmdlet implementando la [System.Management.Automation.Provider.Containercmdletprovider.Removeitem* ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método.

`Remove-ItemProperty` Puede definir cómo el proveedor usará los valores pasados a la `Path` y `Name` parámetros de la `Remove-ItemProperty` cmdlet implementando la [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) método.

`Rename-Item` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` y `NewName` parámetros de la `Rename-Item` cmdlet mediante la implementación de la [ System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método.

`Rename-ItemProperty` Puede definir cómo el proveedor usará los valores pasados a la `Path`, `NewName`, y `Name` parámetros de la `Rename-ItemProperty` cmdlet implementando la [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) método.

`Set-Content` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` parámetro de la `Set-Content` cmdlet mediante la implementación de la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método.

`Set-Item` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` y `Value` parámetros de la `Set-Item` cmdlet mediante la implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Setitem* ](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método.

`Set-ItemProperty` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` y `Value` parámetros de la `Set-Item` cmdlet mediante la implementación de la [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método.

`Test-Path` cmdlet puede definir cómo el proveedor usará los valores pasados a la `Path` parámetro de la `Test-Path` cmdlet mediante la implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)método.

Además, no se puede especificar las características de estos parámetros, como si son opcionales u obligatorias, ni puede proporcionar un alias de estos parámetros o especificar cualquiera de los atributos de validación. En cambio, puede especificar las características de parámetro en los cmdlets independientes mediante atributos, como el `Parameters` atributo.

## <a name="provider-cmdlet-dynamic-parameters"></a>Parámetros de Cmdlet dinámicos del proveedor

Los parámetros dinámicos para proveedores de cmdlet son similares a proveedores dinámicos para cmdlets independientes. En ambos casos, los parámetros se agregan al cmdlet cuando el usuario especifica un valor determinado para uno de los parámetros predeterminados, como el `path` parámetro. Sin embargo, no todos los parámetros estáticos pueden usarse para desencadenar la adición de parámetros dinámicos. Para obtener más información sobre los parámetros dinámicos, consulte [parámetros dinámicos del Cmdlet de proveedor](./provider-cmdlet-dynamic-parameters.md).

## <a name="see-also"></a>Véase también

[Parámetros de Cmdlet dinámicos del proveedor](./provider-cmdlet-dynamic-parameters.md)

[Escribir un proveedor de Windows PowerShell](./writing-a-windows-powershell-provider.md)