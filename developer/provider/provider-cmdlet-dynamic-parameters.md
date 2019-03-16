---
title: Parámetros dinámicos del cmdlet de proveedor | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058239"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Parámetros dinámicos del cmdlet de proveedor

Los proveedores pueden definir los parámetros dinámicos que se agregan a un cmdlet de proveedor cuando el usuario especifica un valor determinado para uno de los parámetros del cmdlet estáticos. Por ejemplo, un proveedor puede agregar diferentes parámetros dinámicos en función de qué ruta de acceso, el usuario especifica cuando llama a la `Get-Item` o `Set-Item` cmdlets de proveedor.

## <a name="dynamic-parameter-methods"></a>Métodos de parámetro dinámico

Los parámetros dinámicos se definen mediante la implementación de uno de los métodos de parámetros dinámicos, como el [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) y [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)métodos s. Estos métodos devuelven un objeto que tiene propiedades públicas que se decoran con atributos similares a las de los cmdlets independientes. Este es un ejemplo de una implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) método realizada desde el proveedor de certificados:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

A diferencia de los parámetros estáticos de cmdlets de proveedor, puede especificar las características de estos parámetros de la misma manera que se definen los parámetros en cmdlets independientes. Este es un ejemplo de una clase de parámetro dinámico realizada desde el proveedor de certificados:

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>Parámetros dinámicos

Esta es una lista de los parámetros estáticos que puede usarse para agregar los parámetros dinámicos.

`Clear-Content` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` parámetro del cmdlet Clear-Clear implementando la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) método.

`Clear-Item` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` parámetro de la `Clear-Item` cmdlet implementando la [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) método.

`Clear-ItemProperty` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` parámetro de la `Clear-ItemProperty` cmdlet implementando la [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) método.

`Copy-Item` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path`, `Destination`, y `Recurse` parámetros de la `Copy-Item` cmdlet implementando la [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) método.

Cmdlet Get-ChildItems puede definir los parámetros dinámicos que desencadenan la `Path` y `Recurse` parámetros de la `Get-ChildItem` cmdlet implementando la [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) y [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) métodos.

`Get-Content` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` parámetro de la `Get-Content` cmdlet implementando la [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) método.

`Get-Item` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` parámetro de la `Get-Item` cmdlet implementando la [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) método.

`Get-ItemProperty` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` y `Name` parámetros de la `Get-ItemProperty` cmdlet implementando la [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) método.

`Invoke-Item` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` parámetro de la `Invoke-Item` cmdlet implementando la [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) método.

`Move-Item` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` y `Destination` parámetros de la `Move-Item` cmdlet implementando la [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) método.

`New-Item` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path`, `ItemType`, y `Value` parámetros de la `New-Item` cmdlet implementando la [ System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) método.

`New-ItemProperty` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path`, `Name`, `PropertyType`, y `Value` parámetros de la `New-ItemProperty` cmdlet implementando la [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) método.

`New-PSDrive` cmdlet puede definir los parámetros dinámicos que desencadenan la [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto devuelto por la `New-PSDrive` cmdlet implementando la [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) método.

`Remove-Item` Puede definir los parámetros dinámicos que desencadenan la `Path` y `Recurse` parámetros de la `Remove-Item` cmdlet implementando el [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) método.

`Remove-ItemProperty` Puede definir los parámetros dinámicos que desencadenan la `Path` y `Name` parámetros de la `Remove-ItemProperty` cmdlet implementando el [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) método.

`Rename-Item` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` y `NewName` parámetros de la `Rename-Item` cmdlet implementando la [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) método.

`Rename-ItemProperty` Puede definir los parámetros dinámicos que desencadenan la `Path`, `Name`, y `NewName` parámetros de la `Rename-ItemProperty` cmdlet implementando el [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) método.

`Set-Content` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` parámetro de la `Set-Content` cmdlet implementando la [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) método.

`Set-Item` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` y `Value` parámetros de la `Set-Item` cmdlet implementando la [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) método.

`Set-ItemProperty` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` y `Value` parámetros de la `Set-Item` cmdlet implementando la [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) método.

`Test-Path` cmdlet puede definir los parámetros dinámicos que desencadenan la `Path` parámetro de la `Test-Path` cmdlet implementando la [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) método.

## <a name="see-also"></a>Véase también

[Escribir un proveedor de Windows PowerShell](./writing-a-windows-powershell-provider.md)