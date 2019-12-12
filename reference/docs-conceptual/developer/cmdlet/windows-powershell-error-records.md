---
title: Registros de errores de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: 5412d88b690a1f5f1ef387416e3bf9da3a32c95d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369114"
---
# <a name="windows-powershell-error-records"></a>Registros de errores de Windows PowerShell

Los cmdlets deben pasar un objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) que identifica la condición de error para los errores de terminación y de no terminación.

El objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) contiene la siguiente información:

- Excepción que describe el error. A menudo, se trata de una excepción que el cmdlet ha detectado y convertido en un registro de error. Cada registro de error debe contener una excepción.

Si el cmdlet no detectó una excepción, debe crear una nueva excepción y elegir la clase de excepción que mejor describe la condición de error. Sin embargo, no es necesario iniciar la excepción porque se puede acceder a ella a través de la propiedad [System. Management. Automation. ErrorRecord. Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) del objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

- Identificador de error que proporciona un designador de destino que se puede usar con fines de diagnóstico y con scripts de Windows PowerShell para controlar condiciones de error específicas con controladores de error específicos. Cada registro de error debe contener un identificador de error (consulte identificador de error).

- Una categoría de error que proporciona un designador general que se puede usar con fines de diagnóstico. Cada registro de error debe especificar una categoría de error (vea la categoría de error).

- Un mensaje de error de reemplazo opcional y una acción recomendada (vea el mensaje de error de reemplazo).

- Información de invocación opcional sobre el cmdlet que produjo el error. Windows PowerShell especifica esta información (vea el mensaje de invocación).

- Objeto de destino que se estaba procesando cuando se produjo el error. Puede tratarse del objeto de entrada, o podría ser otro objeto que el cmdlet estaba procesando. Por ejemplo, para el `remove-item -recurse c:\somedirectory`de comandos, el error puede ser una instancia de un objeto FileInfo para "c:\somedirectory\lockedfile". La información del objeto de destino es opcional.

## <a name="error-identifier"></a>Identificador de error

Cuando cree un registro de errores, especifique un identificador que designe la condición de error dentro del cmdlet. Windows PowerShell combina el identificador de destino con el nombre del cmdlet para crear un identificador de error completo. Se puede tener acceso al identificador de error completo a través de la propiedad [System. Management. Automation. ErrorRecord. FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) del objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . El identificador de error no está disponible por sí solo. Solo está disponible como parte del identificador de error completo.

Utilice las siguientes directrices para generar identificadores de error cuando cree registros de errores:

- Crear identificadores de error específicos de una condición de error. Se dirige a los identificadores de error para fines de diagnóstico y para los scripts que administran condiciones de error específicas con controladores de error específicos. Un usuario debe poder usar el identificador de error para identificar el error y su origen. Los identificadores de error también habilitan la creación de informes para condiciones de error específicas de las excepciones existentes, de modo que no se requieren nuevas subclases de excepción.

- En general, asigne distintos identificadores de error a diferentes rutas de acceso de código. El usuario final se beneficia de los identificadores específicos. A menudo, cada ruta de acceso de código que llama a [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) tiene su propio identificador. Como regla, defina un nuevo identificador al definir una nueva cadena de plantilla para el mensaje de error y viceversa. No utilice el mensaje de error como identificador.

- Al publicar código mediante un identificador de error determinado, se establece la semántica de los errores con ese identificador para el ciclo de vida de soporte técnico completo del producto. No lo reutilice en un contexto que sea semánticamente diferente del contexto original. Si cambia la semántica de este error, cree y utilice un nuevo identificador.

- Por lo general, debe usar un identificador de error determinado solo para las excepciones de un tipo CLR determinado. Si cambia el tipo de la excepción o el tipo del objeto de destino, cree y utilice un nuevo identificador.

- Elija texto para el identificador de error que se corresponda de manera concisa con el error que está notificando. Usar convenciones de mayúsculas y minúsculas de nomenclatura de .NET Framework estándar. No utilice espacios en blanco ni signos de puntuación. No debe localizar los identificadores de error.

- No genere dinámicamente los identificadores de error de forma no reproducible. Por ejemplo, no incorpore información de error como un identificador de proceso. Los identificadores de error solo son útiles si se corresponden con los identificadores de error que ven otros usuarios que experimentan la misma condición de error.

## <a name="error-category"></a>Categoría de error

Al crear un registro de errores, especifique la categoría del error mediante una de las constantes definidas por la enumeración [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) . Windows PowerShell usa la categoría de error para mostrar información de errores cuando los usuarios establecen el `$ErrorView` variable en `"CategoryView"`.

Evite usar la constante [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) **NotSpecified** . Si tiene información sobre el error o sobre la operación que causó el error, elija la categoría que mejor describe el error o la operación, aunque la categoría no sea una coincidencia perfecta.

La información mostrada por Windows PowerShell se conoce como cadena de vista de categoría y se genera a partir de las propiedades de la clase [System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) . (Se tiene acceso a esta clase a través de la propiedad [System. Management. Automation. ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) de error).

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

En la siguiente lista se describe la información que se muestra:

- Categoría: una constante [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) definida por Windows PowerShell.

- TargetName: de forma predeterminada, el nombre del objeto que el cmdlet estaba procesando cuando se produjo el error. O bien, otra cadena definida por el cmdlet.

- TargetType: de forma predeterminada, el tipo del objeto de destino. O bien, otra cadena definida por el cmdlet.

- Actividad: de forma predeterminada, el nombre del cmdlet que creó el registro de errores. O bien, otra cadena definida por el cmdlet.

- Motivo: de forma predeterminada, el tipo de excepción. O bien, otra cadena definida por el cmdlet.

## <a name="replacement-error-message"></a>Mensaje de error de reemplazo

Al desarrollar un registro de errores para un cmdlet, el mensaje de error predeterminado para el error proviene del texto del mensaje predeterminado en la propiedad [System. Exception. Message](/dotnet/api/System.Exception.Message) . Se trata de una propiedad de solo lectura cuyo texto de mensaje está diseñado solo para fines de depuración (según las instrucciones de .NET Framework). Se recomienda que cree un mensaje de error que reemplace o aumente el texto del mensaje predeterminado. Haga que el mensaje sea más fácil de ver y más específico del cmdlet.

Un objeto [System. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) proporciona el mensaje de reemplazo. Use uno de los siguientes constructores de este objeto porque proporcionan información de localización adicional que puede ser utilizada por Windows PowerShell.

- [ErrorDetails (cmdlet, String, String, Object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Management_Automation_Cmdlet_System_String_System_String_System_Object___): Utilice este constructor si la cadena de plantilla es una cadena de recursos en el mismo ensamblado en el que se implementa el cmdlet o si desea cargar la cadena de plantilla a través de una invalidación del método [System. Management. Automation. cmdlet. GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) .

- [ErrorDetails (Assembly, String, String, Object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Reflection_Assembly_System_String_System_String_System_Object___): Utilice este constructor si la cadena de plantilla está en otro ensamblado y no la carga a través de una invalidación de [System. Management. Automation. cmdlet. GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

El mensaje de reemplazo debe cumplir las directrices de diseño de .NET Framework para escribir mensajes de excepción con una pequeña diferencia. Las instrucciones indican que los mensajes de excepción deben escribirse para los desarrolladores. Estos mensajes de reemplazo deben escribirse para el usuario del cmdlet.

Debe agregarse el mensaje de error de reemplazo antes de llamar a los métodos [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Para agregar un mensaje de reemplazo, establezca la propiedad [System. Management. Automation. ErrorRecord. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) del registro de errores. Cuando se establece esta propiedad, Windows PowerShell muestra la propiedad [System. Management. Automation. ErrorDetails. Message *](/dotnet/api/System.Management.Automation.ErrorDetails.Message) en lugar del texto del mensaje predeterminado.

## <a name="recommended-action-information"></a>Información de acción recomendada

El objeto [System. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) también puede proporcionar información acerca de las acciones recomendadas cuando se produce el error.

## <a name="invocation-information"></a>Información de invocación

Cuando un cmdlet usa [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) para informar de un registro de errores, Windows PowerShell agrega automáticamente la información que describe el comando que se invocó cuando se produjo el error. Esta información se proporciona mediante un objeto [System. Management. Automation. Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) que contiene el nombre del cmdlet invocado por el comando, el propio comando e información sobre la canalización o el script. Esta propiedad es de sólo lectura.

## <a name="see-also"></a>Véase también

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)

[System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System. Management. Automation. Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Informe de errores de Windows PowerShell](./error-reporting-concepts.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
