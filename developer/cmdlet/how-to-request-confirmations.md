---
title: Cómo solicitar confirmaciones | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058834"
---
# <a name="how-to-request-confirmations"></a>Cómo solicitar confirmaciones

En este ejemplo se muestra cómo llamar a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos para solicitar confirmaciones desde el usuario antes de que se realiza una acción.

> [!IMPORTANT]
> Para obtener más información acerca de cómo Windows PowerShell trata estas solicitudes, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Para solicitar confirmación

1. Asegúrese de que el `SupportsShouldProcess` parámetro del atributo de Cmdlet se establece en `true`. (Para las funciones de esto es un parámetro del atributo CmdletBinding).

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Agregar un `Force` parámetro al cmdlet para que el usuario puede invalidar una solicitud de confirmación.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Agregar un `if` instrucción que usa el valor devuelto de la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método para determinar si el [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) se llama al método.

4. Agregue un segundo `if` instrucción que usa el valor devuelto de la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método y el valor de la `Force` parámetro para determinar si la operación debe ser puede realizar.

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente, la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos se llaman desde dentro de la invalidación de la [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método. Sin embargo, también puede llamar a estos métodos de la entrada de otra métodos de procesamiento.

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
