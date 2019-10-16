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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359954"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Parámetros dinámicos del cmdlet de proveedor

Los proveedores pueden definir los parámetros dinámicos que se agregan a un cmdlet de proveedor cuando el usuario especifica un determinado valor para uno de los parámetros estáticos del cmdlet. Por ejemplo, un proveedor puede agregar diferentes parámetros dinámicos en función de la ruta de acceso que especifica el usuario al llamar a los cmdlets de proveedor `Get-Item` o `Set-Item`.

## <a name="dynamic-parameter-methods"></a>Métodos de parámetros dinámicos

Los parámetros dinámicos se definen mediante la implementación de uno de los métodos de parámetros dinámicos, como [System. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) y [ Métodos System. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s. Estos métodos devuelven un objeto que tiene propiedades públicas que se decoran con atributos similares a los de los cmdlets independientes. Este es un ejemplo de una implementación del método [System. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) tomado del proveedor de certificados:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

A diferencia de los parámetros estáticos de los cmdlets de proveedor, puede especificar las características de estos parámetros de la misma manera que los parámetros se definen en cmdlets independientes. A continuación se muestra un ejemplo de una clase de parámetro dinámico tomada del proveedor de certificados:

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

Esta es una lista de los parámetros estáticos que se pueden usar para agregar parámetros dinámicos.

cmdlet `Clear-Content` puede definir los parámetros dinámicos desencadenados por el parámetro `Path` del cmdlet Clear-Clear implementando [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) forma.

cmdlet `Clear-Item` puede definir los parámetros dinámicos desencadenados por el parámetro `Path` del cmdlet `Clear-Item` implementando el método [System. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) .

cmdlet `Clear-ItemProperty` puede definir los parámetros dinámicos desencadenados por el parámetro `Path` del cmdlet `Clear-ItemProperty` implementando el método [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) . .

cmdlet `Copy-Item` puede definir los parámetros dinámicos desencadenados por los parámetros `Path`, `Destination` y `Recurse` del cmdlet `Copy-Item` implementando el [cmdlet Método System. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) .

Cmdlet Get-ChildItems puede definir los parámetros dinámicos desencadenados por los parámetros `Path` y `Recurse` del cmdlet `Get-ChildItem` implementando la [ Métodos System. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) y [System. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) .

cmdlet `Get-Content` puede definir los parámetros dinámicos desencadenados por el parámetro `Path` del cmdlet `Get-Content` implementando [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) forma.

cmdlet `Get-Item` puede definir los parámetros dinámicos desencadenados por el parámetro `Path` del cmdlet `Get-Item` implementando el método [System. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) .

cmdlet `Get-ItemProperty` puede definir los parámetros dinámicos desencadenados por los parámetros `Path` y `Name` del cmdlet `Get-ItemProperty` implementando [System. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters * ](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)método.

cmdlet `Invoke-Item` puede definir los parámetros dinámicos desencadenados por el parámetro `Path` del cmdlet `Invoke-Item` implementando [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) forma.

cmdlet `Move-Item` puede definir los parámetros dinámicos desencadenados por los parámetros `Path` y `Destination` del cmdlet `Move-Item` implementando [System. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters * ](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)método.

cmdlet `New-Item` puede definir los parámetros dinámicos desencadenados por los parámetros `Path`, `ItemType` y `Value` del cmdlet `New-Item` implementando el [cmdlet Método System. Management. Automation. Provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) .

cmdlet `New-ItemProperty` puede definir los parámetros dinámicos desencadenados por los parámetros `Path`, `Name`, `PropertyType` y `Value` del cmdlet `New-ItemProperty` mediante la implementación de la [ Método System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) .

cmdlet `New-PSDrive` puede definir los parámetros dinámicos desencadenados por el objeto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) que devuelve el cmdlet `New-PSDrive` implementando el [cmdlet Método System. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .

`Remove-Item` puede definir los parámetros dinámicos desencadenados por los parámetros `Path` y `Recurse` del cmdlet `Remove-Item` implementando [System. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) forma.

`Remove-ItemProperty` puede definir los parámetros dinámicos desencadenados por los parámetros `Path` y `Name` del cmdlet `Remove-ItemProperty` implementando la [ Método System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) .

cmdlet `Rename-Item` puede definir los parámetros dinámicos desencadenados por los parámetros `Path` y `NewName` del cmdlet `Rename-Item` implementando [System. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters * ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)método.

`Rename-ItemProperty` puede definir los parámetros dinámicos desencadenados por los parámetros `Path`, `Name` y `NewName` del cmdlet `Rename-ItemProperty` implementando la [ Método System. Management. Automation. Provider. Idynamicpropertycmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) .

cmdlet `Set-Content` puede definir los parámetros dinámicos desencadenados por el parámetro `Path` del cmdlet `Set-Content` implementando [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) forma.

cmdlet `Set-Item` puede definir los parámetros dinámicos desencadenados por los parámetros `Path` y `Value` del cmdlet `Set-Item` implementando [System. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) forma.

cmdlet `Set-ItemProperty` puede definir los parámetros dinámicos desencadenados por los parámetros `Path` y `Value` del cmdlet `Set-Item` implementando [System. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters * ](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)método.

cmdlet `Test-Path` puede definir los parámetros dinámicos desencadenados por el parámetro `Path` del cmdlet `Test-Path` implementando [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) forma.

## <a name="see-also"></a>Véase también

[Escribir un proveedor de Windows PowerShell](./writing-a-windows-powershell-provider.md)