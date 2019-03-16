---
title: Error de Windows PowerShell registra | Microsoft Docs
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
ms.openlocfilehash: f6f5e50c55b477cbbeeaaf4f3ea665d5dc07758c
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059769"
---
# <a name="windows-powershell-error-records"></a>Registros de errores de Windows PowerShell

Los cmdlets debe pasar un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto que identifica la condición de error para errores de terminación y de no terminación.

El [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto contiene la información siguiente:

- La excepción que describe el error. A menudo, esto es una excepción que el cmdlet detecta y se convierte en un registro de errores. Cada registro de error debe contener una excepción.

Si el cmdlet no detecta una excepción, debe crear una nueva excepción y elegir la clase de excepción que mejor describe la condición de error. Sin embargo, no es necesario iniciar la excepción porque puede acceder a ella a través de la [System.Management.Automation.ErrorRecord.Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) propiedad de la [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)objeto.

- Identificador de error que proporciona un designador de destino que puede utilizarse para fines de diagnóstico y los scripts de Windows PowerShell para controlar las condiciones de error específico con los controladores de error específico. Cada registro de error debe contener un identificador de error (consulte el identificador de Error).

- Una categoría de error que proporciona un designador de general que puede usarse para fines de diagnóstico. Cada registro de error debe especificar una categoría de error (vea la categoría de Error).

- Un mensaje de error de reemplazo opcional y una acción recomendada (vea el mensaje de Error de reemplazo).

- Información de la invocación opcional sobre el cmdlet que produjo el error. Esta información se especifica mediante Windows PowerShell (vea el mensaje de invocación).

- El objeto de destino que se estaba procesando cuando se produjo el error. Esto podría ser el objeto de entrada, o podría ser otro objeto que estaba procesando el cmdlet. Por ejemplo, para el comando `remove-item -recurse c:\somedirectory`, el error puede ser una instancia de un objeto FileInfo para "c:\somedirectory\lockedfile". La información de objeto de destino es opcional.

## <a name="error-identifier"></a>Identificador de error

Cuando se crea un registro de errores, especifique un identificador que designa la condición de error dentro de su cmdlet. Windows PowerShell se combina el identificador de destino con el nombre de su cmdlet para crear un identificador de error completo. El identificador de error completo puede obtenerse a través del [System.Management.Automation.ErrorRecord.FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) propiedad de la [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)objeto. El identificador de error no está disponible por sí mismo. Está disponible únicamente como parte del identificador de error completo.

Use las directrices siguientes para generar identificadores de errores al crear registros de error:

- Asignar identificadores de errores específico a una condición de error. Tener como destino los identificadores de errores para fines de diagnóstico y los scripts que controlar las condiciones de error específico con los controladores de error específico. Un usuario debe ser capaz de utilizar el identificador de error para identificar el error y su origen. Identificadores de errores también habilitar los informes de condiciones de error específico de excepciones existentes para que las subclases de excepción nueva no son necesarias.

- En general, asignar identificadores de error diferentes a diferentes rutas de código. El usuario final se beneficia de identificadores específicos. A menudo, cada ruta de acceso de código que llama a [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) tiene su propio identificador. Como norma, definir un nuevo identificador cuando se define una nueva cadena de plantilla para el mensaje de error y viceversa. No utilice el mensaje de error como un identificador.

- Cuando se publica el código mediante un identificador de error concreto, Establece que la semántica de errores con ese identificador para el producto completo de vida de soporte. No volver a usarla en un contexto que es semánticamente diferente desde el contexto original. Si cambia la semántica de este error, cree y, a continuación, use un nuevo identificador.

- Normalmente debe usar un identificador de error concreto solo para las excepciones de un determinado tipo CLR. Si cambia el tipo de la excepción o el tipo del objeto de destino, cree y, a continuación, use un nuevo identificador.

- Elegir un texto para el identificador de error que se forma concisa se corresponde con el error que está notificando. Utilice el estándares convenciones de nomenclatura y mayúsculas y minúsculas de .NET Framework. No use signos de puntuación o espacios en blanco. No traduzca los identificadores de errores.

- No generar dinámicamente identificadores de errores de forma que no sea reproducible. Por ejemplo, no incorporar información de error como un identificador de proceso. Identificadores de errores son útiles sólo si corresponden a los identificadores de error vistos por otros usuarios que tengan la misma condición de error.

## <a name="error-category"></a>Categoría de error

Cuando se crea un registro de errores, especifique la categoría del error utilizando una de las constantes definidas por el [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeración. Windows PowerShell usa la categoría de error para mostrar información de error cuando los usuarios configuran el `$ErrorView` variable `"CategoryView"`.

Evite el uso de la [System.Management.Automation.Errorcategory.Notspecified](/dotnet/api/System.Management.Automation.ErrorCategory.NotSpecified) constante. Si tiene cualquier información sobre el error o la operación que produjo el error, elija la categoría que mejor describe el error o la operación, incluso si la categoría no es perfecta.

La información mostrada por Windows PowerShell se conoce como la cadena de la vista de categoría y se crea a partir de las propiedades de la [System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) clase. (Esta clase se tiene acceso mediante el error [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) propiedad.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

La lista siguiente describe la información que aparece:

- Categoría: Windows PowerShell-definido [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) constante.

- TargetName: De forma predeterminada, el nombre del objeto el cmdlet estaba procesando cuando se produjo el error. O bien, otra cadena definida por el cmdlet.

- TargetType: De forma predeterminada, el tipo del objeto de destino. O bien, otra cadena definida por el cmdlet.

- Actividad: De forma predeterminada, el nombre del cmdlet que creó el registro de error. O alguna otra cadena definido por el cmdlet.

- Motivo: De forma predeterminada, el tipo de excepción. O bien, otra cadena definida por el cmdlet.

## <a name="replacement-error-message"></a>Mensaje de Error de reemplazo

Al desarrollar un registro de errores para un cmdlet, el mensaje de error predeterminada para el error procede el texto del mensaje predeterminado en el [System.Exception.Message](/dotnet/api/System.Exception.Message) propiedad. Se trata de una propiedad de solo lectura cuyo texto del mensaje está pensado únicamente para propósitos de depuración (de acuerdo con las directrices de .NET Framework). Le recomendamos que cree un mensaje de error que reemplace o aumenta el texto del mensaje predeterminado. Que el mensaje más fácil de usar y más específico al cmdlet.

El mensaje de reemplazo se proporciona mediante un [System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) objeto. Utilice uno de los constructores siguientes de este objeto, ya que proporcionan información adicional de localización que se puede usar Windows PowerShell.

- [¿ErrorDetails.ErrorDetails (Cmdlet, cadena, cadena, objeto\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Utilice este constructor si la cadena de plantilla es una cadena de recurso en el mismo ensamblado en el que se implementa el cmdlet o si desea cargar la cadena de plantilla a través de un reemplazo del [System.Management.Automation.Cmdlet.GetResourceString ](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) método.

- [¿ErrorDetails.ErrorDetails (ensamblado, cadena, cadena, objeto\[System.Management.Automation.ErrorDetails.%23Ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Utilice este constructor si la cadena de plantilla está en otro ensamblado y no se cargan a través de una invalidación de [System.Management.Automation.Cmdlet.GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

El mensaje de reemplazo debe cumplir las directrices de diseño de .NET Framework para escribir mensajes de excepción con una pequeña diferencia. El estado de las directrices que deben escribirse los mensajes de excepción para los desarrolladores. Estos mensajes de reemplazo deben escribirse para que el usuario de cmdlet.

El mensaje de error de reemplazo debe agregarse antes de la [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) se llama a métodos. Para agregar un mensaje de reemplazo, establezca el [System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) propiedad del registro de error. Cuando se establece esta propiedad, Windows PowerShell muestra el [System.Management.Automation.ErrorDetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message) propiedad en lugar del texto del mensaje predeterminado.

## <a name="recommended-action-information"></a>Recomienda la información de la acción

El [System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) objeto también puede proporcionar información acerca de las acciones que se recomiendan cuando se produce el error.

## <a name="invocation-information"></a>Información de la invocación

Cuando se usa un cmdlet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) para informar de un registro de errores, Windows PowerShell agrega automáticamente la información que describe el comando que se invoca cuando se produjo el error. Esta información se proporciona mediante un [System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) objeto que contiene el nombre del cmdlet que se invocó el comando, el comando en sí e información acerca de la canalización o la secuencia de comandos. Esta propiedad es de solo lectura.

## <a name="see-also"></a>Véase también

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Informes de errores de Windows PowerShell](./error-reporting-concepts.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
