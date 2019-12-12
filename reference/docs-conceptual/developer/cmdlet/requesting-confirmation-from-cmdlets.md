---
title: Solicitando confirmación de cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369534"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Solicitud de confirmación de los cmdlets

Los cmdlets deben solicitar confirmación cuando están a punto de hacer un cambio en el sistema que está fuera del entorno de Windows PowerShell. Por ejemplo, si un cmdlet está a punto de agregar una cuenta de usuario o detener un proceso, el cmdlet debe solicitar confirmación al usuario antes de continuar. Por el contrario, si un cmdlet está a punto de cambiar una variable de Windows PowerShell, no es necesario que el cmdlet requiera confirmación.

Para llevar a cabo una solicitud de confirmación, el cmdlet debe indicar que admite solicitudes de confirmación y debe llamar a los métodos [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (opcional) para mostrar un mensaje de solicitud de confirmación.

## <a name="supporting-confirmation-requests"></a>Compatibilidad con solicitudes de confirmación

Para admitir las solicitudes de confirmación, el cmdlet debe establecer el parámetro `SupportsShouldProcess` del atributo cmdlet en `true`. Esto habilita los parámetros de cmdlet `Confirm` y `WhatIf` que se proporcionan con Windows PowerShell. El parámetro `Confirm` permite al usuario controlar si se muestra la solicitud de confirmación. El parámetro `WhatIf` permite al usuario determinar si el cmdlet debe mostrar un mensaje o realizar su acción. No agregue manualmente los parámetros `Confirm` y `WhatIf` a un cmdlet.

En el ejemplo siguiente se muestra una declaración de atributo de cmdlet que admite solicitudes de confirmación.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Llamar a los métodos de solicitud de confirmación

En el código del cmdlet, llame al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) antes de que se realice la operación que cambia el sistema. Diseñe el cmdlet de modo que si la llamada devuelve un valor de `false`, no se realiza la operación y el cmdlet procesa la siguiente operación.

## <a name="calling-the-shouldcontinue-method"></a>Llamar al método ShouldContinue

La mayoría de los cmdlets solicitan confirmación usando solo el método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Sin embargo, algunos casos pueden requerir confirmación adicional. En estos casos, complemente la llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) con una llamada al método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . Esto permite que el cmdlet o el proveedor controlen de forma más precisa el ámbito de la respuesta de **sí a todo** en la solicitud de confirmación.

Si un cmdlet llama al método [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , el cmdlet también debe proporcionar un parámetro de modificador `Force`. Si el usuario especifica `Force` cuando el usuario invoca el cmdlet, el cmdlet todavía debe llamar a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), pero debe omitir la llamada a [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) producirá una excepción cuando se llame desde un entorno no interactivo en el que no se puede solicitar al usuario. La adición de un parámetro `Force` garantiza que el comando todavía puede realizarse cuando se invoca en un entorno no interactivo.

En el ejemplo siguiente se muestra cómo llamar a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

El comportamiento de una llamada a [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) puede variar en función del entorno en el que se invoca el cmdlet. El uso de las instrucciones anteriores le ayudará a asegurarse de que el cmdlet se comporta de forma coherente con otros cmdlets, independientemente del entorno del host.

Para obtener un ejemplo de llamada al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , vea [Cómo solicitar confirmaciones](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Especificar el nivel de impacto

Cuando cree el cmdlet, especifique el nivel de impacto (gravedad) del cambio. Para ello, establezca el valor del parámetro `ConfirmImpact` del atributo cmdlet en alto, medio o bajo. Solo puede especificar un valor para `ConfirmImpact` Cuando especifique también el parámetro `SupportsShouldProcess` para el cmdlet.

Para la mayoría de los cmdlets, no es necesario especificar explícitamente `ConfirmImpact`.  En su lugar, use el valor predeterminado del parámetro, que es medio. Si establece `ConfirmImpact` en alto, la operación se confirmará de manera predeterminada. Reserve esta configuración para acciones muy perjudiciales, como volver a formatear un volumen de disco duro.

## <a name="calling-non-confirmation-methods"></a>Llamar a métodos de no confirmación

Si el cmdlet o el proveedor deben enviar un mensaje pero no solicitar la confirmación, puede llamar a los tres métodos siguientes. Evite usar el método [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) para enviar mensajes de estos tipos porque la salida [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) se entremezcla con la salida normal del cmdlet o proveedor, lo que dificulta la escritura de scripts.

- Para precaución al usuario y continuar con la operación, el cmdlet o el proveedor pueden llamar al método [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) .

- Para proporcionar información adicional que el usuario pueda recuperar mediante el parámetro `Verbose`, el cmdlet o el proveedor pueden llamar al método [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

- Para proporcionar detalles del nivel de depuración para otros desarrolladores o para el soporte técnico del producto, el cmdlet o el proveedor pueden llamar al método [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) . El usuario puede recuperar esta información mediante el parámetro `Debug`.

Los cmdlets y los proveedores llaman primero a los métodos siguientes para solicitar confirmación antes de intentar realizar una operación que cambia un sistema fuera de Windows PowerShell:

- [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Para ello, se llama al método [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , que pide al usuario que confirme la operación en función de cómo el usuario invocó el comando.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
