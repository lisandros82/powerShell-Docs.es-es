---
title: Solicitud de confirmación de los Cmdlets | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067491"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Solicitud de confirmación de los cmdlets

Los cmdlets deben solicitar confirmación cuando se va a realizar un cambio en el sistema que está fuera del entorno de Windows PowerShell. Por ejemplo, si un cmdlet está a punto de agregar una cuenta de usuario o detener un proceso, el cmdlet debe requerir confirmación del usuario antes de que continúe. En cambio, si un cmdlet se va a cambiar una variable de Windows PowerShell, el cmdlet no debe requerir confirmación.

Con el fin de realizar una solicitud de confirmación, el cmdlet debe indicar que admite solicitudes de confirmación y debe llamar a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) métodos (opcionales) para mostrar un mensaje de solicitud de confirmación.

## <a name="supporting-confirmation-requests"></a>Compatibilidad con las solicitudes de confirmación

Para admitir las solicitudes de confirmación, debe establecer el cmdlet la `SupportsShouldProcess` parámetro del atributo de Cmdlet en `true`. Esto permite la `Confirm` y `WhatIf` los parámetros de cmdlet proporcionados por Windows PowerShell. El `Confirm` parámetro permite al usuario controlar si se muestra la solicitud de confirmación. El `WhatIf` parámetro permite al usuario determinar si el cmdlet debe mostrar un mensaje o realizar su acción. No agregue manualmente el `Confirm` y `WhatIf` parámetros a un cmdlet.

En el ejemplo siguiente se muestra una declaración de atributo de Cmdlet que admite solicitudes de confirmación.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Llamar a los métodos de solicitud de confirmación

En el código del cmdlet, llame a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método antes de realizar la operación que cambia el sistema. El cmdlet de diseño, por lo que si la llamada devuelve un valor de `false`, no se realiza la operación y el cmdlet procesa la siguiente operación.

## <a name="calling-the-shouldcontinue-method"></a>Una llamada al método ShouldContinue

Mayoría de los cmdlets solicitar confirmación solo mediante la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método. Sin embargo, algunos casos podrían requerir confirmación adicional. En estos casos, complementar el [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) por una llamada a la [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método. Esto permite al cmdlet o proveedor para controlar con mayor precisión el ámbito de la **sí a todo** respuesta a la pregunta de confirmación.

Si llama un cmdlet el [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) método, el cmdlet también debe proporcionar un `Force` parámetro de modificador. Si el usuario especifica `Force` cuando el usuario invoca el cmdlet, el cmdlet debe seguir llamando a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), pero debe omitir la llamada a [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) producirá una excepción cuando se llama desde un entorno no interactivo donde no se puede pedir al usuario. Agregar un `Force` parámetro garantiza que el comando todavía se puede realizar cuando se invoca en un entorno que no es interactivo.

El ejemplo siguiente muestra cómo llamar a [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) y [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

El comportamiento de un [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) llamada puede variar según el entorno en el que se invoca el cmdlet. Las instrucciones anteriores le ayudarán a garantizar que el cmdlet se comporta de forma coherente con otros cmdlets, independientemente del entorno de host.

Para obtener un ejemplo de la llamada a la [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, consulte [cómo solicitar confirmaciones](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Especifique el nivel de impacto

Cuando se crea el cmdlet, especifique el nivel de impacto (la gravedad) del cambio. Para ello, establezca el valor de la `ConfirmImpact` parámetro del atributo de Cmdlet como alta, Media o baja. Puede especificar un valor para `ConfirmImpact` sólo al también especificar el `SupportsShouldProcess` parámetro del cmdlet.

Para la mayoría de los cmdlets, no tiene que especificar explícitamente `ConfirmImpact`.  En su lugar, use el valor predeterminado del parámetro, que es medio. Si establece `ConfirmImpact` en alta, se confirmará la operación de forma predeterminada. Reservar esta configuración para acciones muy perjudiciales, como volver a formatear un volumen de disco duro.

## <a name="calling-non-confirmation-methods"></a>Llamar a métodos de no confirmación

Si el proveedor o el cmdlet debe enviar un mensaje, pero no pedir confirmación, pueden llamar a los tres métodos siguientes. Evite el uso de la [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método para enviar mensajes de estos tipos porque [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) es entremezclar salida con la salida normal del cmdlet o del proveedor, lo que dificulta la escritura de scripts.

- Para el usuario de precaución y continuar con la operación, el cmdlet o el proveedor puede llamar el [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método.

- Para proporcionar información adicional que el usuario puede recuperar mediante el `Verbose` parámetro, el cmdlet o el proveedor puede llamar a la [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método.

- Para proporcionar detalles de nivel de depuración para otros desarrolladores o para servicios de soporte técnico, el cmdlet o el proveedor puede llamar el [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método. El usuario puede recuperar esta información mediante el `Debug` parámetro.

Los cmdlets y proveedores de llamar primero a los métodos siguientes para pedir confirmación antes de intentar realizar una operación que cambia un sistema de Windows PowerShell:

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Lo hacen mediante una llamada a la [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) método, que pide al usuario que confirme la operación en función de cómo el usuario invoca el comando.

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
