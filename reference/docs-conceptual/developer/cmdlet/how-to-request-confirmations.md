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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369684"
---
# <a name="how-to-request-confirmations"></a>Cómo solicitar confirmaciones

En este ejemplo se muestra cómo llamar a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) para solicitar las confirmaciones del usuario antes de que se realice una acción.

> [!IMPORTANT]
> Para obtener más información sobre cómo Windows PowerShell controla estas solicitudes, consulte [solicitar confirmación](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Para solicitar confirmación

1. Asegúrese de que el parámetro `SupportsShouldProcess` del atributo cmdlet esté establecido en `true`. (En el caso de las funciones, es un parámetro del atributo CmdletBinding).

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Agregue un parámetro `Force` a su cmdlet para que el usuario pueda invalidar una solicitud de confirmación.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Agregue una instrucción `if` que use el valor devuelto del método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) para determinar si se llama al método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) .

4. Agregue una segunda instrucción `if` que use el valor devuelto del método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) y el valor del parámetro `Force` para determinar si se debe realizar la operación.

## <a name="example"></a>Ejemplo

En el ejemplo de código siguiente, se llama a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) desde la invalidación del método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . Sin embargo, también puede llamar a estos métodos desde los otros métodos de procesamiento de entrada.

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
