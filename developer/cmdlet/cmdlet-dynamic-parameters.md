---
title: Parámetros dinámicos de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986247"
---
# <a name="cmdlet-dynamic-parameters"></a>Parámetros dinámicos de cmdlet

Los cmdlets pueden definir parámetros que están disponibles para el usuario en condiciones especiales, como cuando el argumento de otro parámetro es un valor específico. Estos parámetros se agregan en tiempo de ejecución y se denominan parámetros dinámicos, ya que solo se agregan cuando se necesitan. Por ejemplo, puede diseñar un cmdlet que agregue varios parámetros solo cuando se especifica un parámetro de modificador específico.

> [!NOTE]
> Los proveedores y las funciones de PowerShell también pueden definir parámetros dinámicos.

## <a name="dynamic-parameters-in-powershell-cmdlets"></a>Parámetros dinámicos en cmdlets de PowerShell

PowerShell usa parámetros dinámicos en varios de sus cmdlets de proveedor. Por ejemplo, los `Get-Item` `Get-ChildItem` cmdlets y agregan un parámetro **CodeSigningCert** en tiempo de ejecución cuando el parámetro **path** especifica la ruta de acceso del proveedor de **certificados** . Si el parámetro **path** especifica una ruta de acceso para un proveedor diferente, el parámetro **CodeSigningCert** no está disponible.

En los siguientes ejemplos se muestra cómo se agrega el parámetro **CodeSigningCert** en `Get-Item` tiempo de ejecución cuando se ejecuta.

En este ejemplo, el tiempo de ejecución de PowerShell agregó el parámetro y el cmdlet se realiza correctamente.

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

En este ejemplo, se especifica una unidad del **sistema de archivos** y se devuelve un error. El mensaje de error indica que no se encuentra el parámetro **CodeSigningCert** .

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Compatibilidad con parámetros dinámicos

Para admitir los parámetros dinámicos, se deben incluir los siguientes elementos en el código del cmdlet.

### <a name="interface"></a>Interfaz

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).
Esta interfaz proporciona el método que recupera los parámetros dinámicos.

Por ejemplo:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a>Método

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).
Este método recupera el objeto que contiene las definiciones de parámetros dinámicos.

Por ejemplo:

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

### <a name="class"></a>Clase

Una clase que define los parámetros dinámicos que se van a agregar. Esta clase debe incluir un atributo de **parámetro** para cada parámetro y cualquier atributo opcional de **alias** y **validación** que necesite el cmdlet.

Por ejemplo:

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

Para obtener un ejemplo completo de un cmdlet que admite parámetros dinámicos, vea [cómo declarar parámetros dinámicos](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Vea también

[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Cómo declarar parámetros dinámicos](./how-to-declare-dynamic-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
