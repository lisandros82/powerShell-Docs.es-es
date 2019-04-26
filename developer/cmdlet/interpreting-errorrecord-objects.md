---
title: Interpretación de los objetos de ErrorRecord | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067644"
---
# <a name="interpreting-errorrecord-objects"></a>Interpretación de los objetos ErrorRecord

En la mayoría de los casos, un [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto representa un error de no terminación generado por un comando o script. La terminación también puede especificar la información adicional en un ErrorRecord a través de la [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) interfaz.

Si desea escribir un controlador de errores en la secuencia de comandos o un host para administrar errores concretos que se producen durante la ejecución del comando o script, se debe interpretar el [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto para determinar si se representa la clase de error que se desea controlar.

Cuando un cmdlet encuentra un carácter de terminación o error de no terminación, debe crear un registro de error que describe la condición de error. La aplicación host debe investigar estos registros de error y realizar cualquier acción que mitigará el error. La aplicación host también debe investigar los registros de error para errores de no terminación no pudo procesar un registro pero eran capaces de continuar, y deben investigar los registros de error para errores de terminación que provocó la canalización detener.

> [!NOTE]
> Para los errores de terminación, el cmdlet llama el [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método. Para errores de no terminación, el cmdlet llama el [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método.

## <a name="error-record-design"></a>Diseño de registros de error

Registros de error están diseñados para proporcionar información adicional que no está disponible en las excepciones asegurándose de que la información combinada en cada registro de error es única. Esta singularidad permite que la aplicación host inspeccionar las diferentes partes del registro de errores para que puede identificar la condición de error y debe realizar la acción del host.

## <a name="interpreting-error-records"></a>Interpretar los registros de errores

Puede revisar varias partes del registro de errores para identificar el error. Estos elementos incluyen lo siguiente:

- La categoría de error

- La excepción de error

- El identificador de error completo (FQID)

- Otra información

### <a name="the-error-category"></a>La categoría de Error

La categoría de error del registro de error es una de las constantes predefinidas proporcionadas por el [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeración. Esta información está disponible a través de la [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) propiedad de la [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto.

El cmdlet puede especificar las categorías de CloseError, OpenError, tipo no válido, ReadError y WriteError y otras categorías de error. La aplicación host puede utilizar la categoría de error para capturar los grupos de errores.

### <a name="the-exception"></a>La excepción

La excepción que se incluye en el registro de error proporcionada por el cmdlet y puede accederse a través de la [System.Management.Automation.ErrorRecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) propiedad de la [ System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto.

Las aplicaciones host pueden utilizar el `is` palabra clave para identificar que la excepción es de una clase específica o de una clase derivada. Es mejor rama en el tipo de excepción, tal como se muestra en el ejemplo siguiente.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

De este modo, detecta las clases derivadas. Sin embargo, existen problemas si se puede deserializar la excepción.

### <a name="the-fqid"></a>The FQID

El FQID es la información más específica, que puede usar para identificar el error. Es una cadena que incluye un identificador definido por el cmdlet, el nombre de la clase de cmdlet y el origen que notifica el error. En general, un registro de errores es análogo a un registro de eventos de un registro de eventos de Windows. El FQID es análoga a la siguiente tupla, que identifica la clase del registro de eventos: (*nombre del registro*, *origen*, *Id. de evento*).

El FQID está diseñado para ser inspeccionado como una sola cadena. Sin embargo, los casos existen en el que el identificador de error está diseñado para analizar la aplicación host. El ejemplo siguiente es un identificador de error completo tiene el formato correcto.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

En el ejemplo anterior, el primer token es el identificador de error, seguido por el nombre de la clase del cmdlet. El identificador de error puede ser un token único o puede ser un identificador separados por puntos que permite la inspección del identificador de la bifurcación. No use signos de puntuación o espacios en blanco en el identificador de error. Es especialmente importante para que no use una coma; una coma se usa Windows PowerShell para separar el identificador y el nombre de clase del cmdlet.

### <a name="other-information"></a>Otra información

El [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto también puede proporcionar información que describe el entorno en el que se produjo el error. Esta información incluye elementos como el objeto de destino que se estaba procesando cuando se produjo el error, información de la invocación y detalles del error. Aunque esta información puede ser útil a la aplicación host, no se utiliza normalmente para identificar el error. Esta información está disponible a través de las siguientes propiedades:

[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.ErrorRecord.InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.ErrorRecord.TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Véase también

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Agregar informes de errores para el Cmdlet de no terminación](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Informes de errores de Windows PowerShell](./error-reporting-concepts.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
