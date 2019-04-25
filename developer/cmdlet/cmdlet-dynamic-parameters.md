---
title: Los parámetros de cmdlet dinámica | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068545"
---
# <a name="cmdlet-dynamic-parameters"></a>Parámetros dinámicos del cmdlet

Cmdlets puede definir los parámetros que están disponibles para el usuario bajo condiciones especiales, como cuando el argumento de otro parámetro es un valor específico. Estos parámetros se agregan en tiempo de ejecución y se conocen como *parámetros dinámicos* porque se agregan solo cuando sean necesarios. Por ejemplo, puede diseñar un cmdlet que agrega varios parámetros solo cuando se especifica un parámetro de modificador específico.

> [!NOTE]
> Los proveedores y las funciones de Windows PowerShell también pueden definir los parámetros dinámicos.

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Parámetros dinámicos en los Cmdlets de Windows PowerShell

Windows PowerShell usa los parámetros dinámicos en varias de sus cmdlets de proveedor. Por ejemplo, el `Get-Item` y `Get-ChildItem` agregar cmdlets un `CodeSigningCert` parámetro en tiempo de ejecución cuando el `Path` parámetro del cmdlet especifica la ruta de acceso del proveedor de certificados. Si el `Path` parámetro del cmdlet especifica una ruta de acceso para un proveedor diferente, el `CodeSigningCert` parámetro no está disponible.

Los ejemplos siguientes muestran cómo el `CodeSigningCert` se agrega el parámetro en tiempo de ejecución cuando el `Get-Item` cmdlet se ejecuta.

En el primer ejemplo, el tiempo de ejecución de Windows PowerShell agregó el parámetro y el cmdlet es correcto.

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

En el segundo ejemplo, se especifica una unidad de sistema de archivos y se devuelve un error. El mensaje de error indica que el `CodeSigningCert` no se encuentra el parámetro.

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Compatibilidad con los parámetros dinámicos

Para admitir los parámetros dinámicos, el código del cmdlet debe incluir los siguientes elementos.

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) esta interfaz proporciona el método que recupera los parámetros dinámicos.

Ejemplo:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) este método recupera el objeto que contiene las definiciones de parámetro dinámico.

Ejemplo:

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

Clase de parámetro dinámico esta clase define los parámetros que se va a agregar. Esta clase debe incluir un atributo de parámetro para cada parámetro y los atributos opcionales de Alias y la validación que son necesarios para el cmdlet.

Ejemplo:

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

Para obtener un ejemplo completo de un cmdlet que admite parámetros dinámicos, consulte [cómo declarar los parámetros dinámicos](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Véase también

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Cómo declarar los parámetros dinámicos](./how-to-declare-dynamic-parameters.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
