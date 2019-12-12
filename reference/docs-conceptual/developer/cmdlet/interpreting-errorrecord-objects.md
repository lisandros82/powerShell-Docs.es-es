---
title: Interpretar objetos ErrorRecord | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365424"
---
# <a name="interpreting-errorrecord-objects"></a>Interpretación de los objetos ErrorRecord

En la mayoría de los casos, un objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) representa un error de no terminación generado por un comando o script. Los errores de terminación también pueden especificar la información adicional en un ErrorRecord a través de la interfaz [System. Management. Automation. Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) .

Si desea escribir un controlador de errores en el script o en un host para controlar los errores específicos que se producen durante la ejecución de comandos o scripts, debe interpretar el objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) para determinar si representa la clase de error que desea controlar.

Cuando un cmdlet encuentra un error de terminación o de no terminación, debe crear un registro de error que describa la condición de error. La aplicación host debe investigar estos registros de errores y realizar cualquier acción que mitigará el error. La aplicación host también debe investigar los registros de errores en busca de errores de no terminación que no hayan podido procesar un registro pero hayan podido continuar, y debe investigar los registros de errores para finalizar los errores que provocaron la detención de la canalización.

> [!NOTE]
> Para los errores de terminación, el cmdlet llama al método [System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . En el caso de los errores de no terminación, el cmdlet llama al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) .

## <a name="error-record-design"></a>Diseño de registro de errores

Los registros de errores están diseñados para proporcionar información de error adicional que no está disponible en las excepciones a la vez que se garantiza que la información combinada en cada registro de errores sea única. Esta unicidad permite a la aplicación host inspeccionar las distintas partes del registro de errores para que pueda identificar la condición de error y la acción que debe realizar el host.

## <a name="interpreting-error-records"></a>Interpretar registros de errores

Puede revisar varias partes del registro de errores para identificar el error. Entre estas partes se incluyen las siguientes:

- La categoría de error

- Excepción de error

- El identificador de error completo (FQID)

- Otra información

### <a name="the-error-category"></a>La categoría de error

La categoría de error del registro de errores es una de las constantes predefinidas que proporciona la enumeración [System. Management. Automation. errorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) . Esta información está disponible a través de la propiedad [System. Management. Automation. ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) del objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

El cmdlet puede especificar las categorías CloseError, OpenError, InvalidType, ReadError y WriteError y otras categorías de error. La aplicación host puede usar la categoría de error para capturar grupos de errores.

### <a name="the-exception"></a>La excepción

El cmdlet proporciona la excepción incluida en el registro de errores y se puede acceder a ella a través de la propiedad [System. Management. Automation. ErrorRecord. Exception *](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) del objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

Las aplicaciones host pueden utilizar la palabra clave `is` para identificar que la excepción es de una clase concreta o de una clase derivada. Es mejor bifurcar en el tipo de excepción, tal y como se muestra en el ejemplo siguiente.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

De este modo, se detectan las clases derivadas. Sin embargo, hay problemas si se deserializa la excepción.

### <a name="the-fqid"></a>FQID

FQID es la información más específica que puede usar para identificar el error. Es una cadena que incluye un identificador definido por el cmdlet, el nombre de la clase de cmdlet y el origen que ha generado el error. En general, un registro de error es análogo a un registro de eventos de un registro de eventos de Windows. FQID es análogo a la siguiente tupla, que identifica la clase del registro de eventos: (*nombre de registro*, *origen*, *ID*. de evento).

FQID está diseñado para ser inspeccionado como una sola cadena. Sin embargo, existen casos en los que el identificador de error está diseñado para ser analizado por la aplicación host. El ejemplo siguiente es un identificador de error completo con formato correcto.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

En el ejemplo anterior, el primer token es el identificador de error, que va seguido del nombre de la clase de cmdlet. El identificador de error puede ser un token único o puede ser un identificador separado por puntos que permita la bifurcación en la inspección del identificador. No use espacios en blanco ni signos de puntuación en el identificador de error. Es especialmente importante no usar una coma; Windows PowerShell usa una coma para separar el identificador y el nombre de la clase de cmdlet.

### <a name="other-information"></a>Otros datos

El objeto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) también podría proporcionar información que describe el entorno en el que se produjo el error. Esta información incluye elementos como detalles del error, información de invocación y el objeto de destino que se estaba procesando cuando se produjo el error. Aunque esta información puede ser útil para la aplicación host, normalmente no se utiliza para identificar el error. Esta información está disponible a través de las siguientes propiedades:

[System. Management. Automation. ErrorRecord. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System. Management. Automation. ErrorRecord. InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System. Management. Automation. ErrorRecord. TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Véase también

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. errorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. Throwterminatingerror *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Agregar informes de errores de no terminación al cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Informe de errores de Windows PowerShell](./error-reporting-concepts.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
