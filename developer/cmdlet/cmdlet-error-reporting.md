---
title: Informes de errores de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error records [PowerShell], terminating
- non-terminating errors [PowerShell]
- error records [PowerShell]
- terminating errors [PowerShell]
- error records [PowerShell], non-terminating
ms.assetid: 0b014035-52ea-44cb-ab38-bbe463c5465a
caps.latest.revision: 8
ms.openlocfilehash: 45f5934314a2871ceb921c7a66b9dfb658d0bd99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068596"
---
# <a name="cmdlet-error-reporting"></a>Informes de errores del cmdlet

Los cmdlets deben informar de errores de manera diferente dependiendo de si los errores que finalizan los errores o errores de no terminación. Los errores de terminación son errores que provocan la canalización se terminan inmediatamente, o errores que se producen cuando no hay ninguna razón para continuar el procesamiento. Errores de no terminación son los errores que se notifican una condición de error actual, pero el cmdlet pueda continuar procesando los objetos de entrada. Con errores de no terminación, normalmente se notifica al usuario del problema, pero el cmdlet continúa procesando el siguiente objeto de entrada.

## <a name="terminating-and-nonterminating-errors"></a>Errores de terminación y de no terminación

Las siguientes directrices se pueden usar para determinar si una condición de error es un error de terminación o un error de no terminación.

- ¿La condición de error evita el cmdlet de procesar correctamente los objetos de entrada más? Si es así, esto es un error de terminación.

- ¿Está relacionado con la condición de error para un objeto de entrada específico o un subconjunto de objetos de entrada? Si es así, esto es un error de no terminación.

- ¿El cmdlet acepta varios objetos de entrada, por ejemplo, que es posible que se realice correctamente el procesamiento en otro objeto de entrada? Si es así, esto es un error de no terminación.

- Los cmdlets que puede aceptar varios objetos de entrada debe decidir entre lo que está terminando y errores de no terminación, incluso cuando una determinada situación se aplica a un único objeto de entrada.

- Cmdlets puede recibir cualquier número de objetos de entrada y enviar cualquier número de objetos de éxito o error antes de iniciar una excepción de terminación. No hay ninguna relación entre el número de objetos de entrada recibido y el número de objetos de éxito y error enviados.

- Los cmdlets que puede aceptar sólo 0-1, los objetos de entrada y genera solo 0-1 de salida de objetos deben tratar los errores como los errores de terminación y generar excepciones de terminación.

## <a name="reporting-nonterminating-errors"></a>Informes de errores de no terminación

Los informes de un error de no terminación siempre deben realizarse dentro de la implementación de cmdlets de la [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método, el [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, o la [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Estos tipos de errores se notifican mediante una llamada a la [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método que a su vez envía un registro de errores en la secuencia de error.

## <a name="reporting-terminating-errors"></a>Informes de errores de terminación

Se notifican los errores de terminación iniciando excepciones o mediante una llamada a la [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) método. Tenga en cuenta que los cmdlets también puede detectar y volver a generar excepciones como OutOfMemory, sin embargo, no son necesarios para volver a iniciar excepciones, como el tiempo de ejecución de Windows PowerShell los detectará también.

También puede definir sus propias excepciones para problemas específicos a su situación, o agregar información adicional a una excepción existente con su registro de error.

## <a name="error-records"></a>Registros de errores

Windows PowerShell se describe una condición de error de no terminación mediante el uso de [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objetos. Cada [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) objeto proporciona información de categorías de error, un objeto de destino opcional y detalles acerca de la condición de error.

### <a name="error-identifiers"></a>Identificadores de errores

El identificador de error es una cadena simple que identifica la condición de error en el cmdlet. Windows PowerShell combina este identificador con un identificador de cmdlet para crear un identificador de error completo que se puede usar más adelante al filtrar los flujos de error o el registro de errores al responder a errores específicos o con otras actividades específicas del usuario.

Deben seguir las instrucciones siguientes al especificar identificadores de errores.

- Asignar identificadores de errores muy específica, diferente a diferentes rutas de código. Cada ruta de acceso del código que llama a [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) debe tener su propio identificador de error.

- Identificadores de errores deben ser únicos a los tipos de excepción de CLR para errores de terminación y de no terminación.

- No se cambia la semántica de un identificador de error entre las versiones de su proveedor de Windows PowerShell o el cmdlet. Una vez establecida la semántica de un identificador de error, debe permanecer constante a lo largo del ciclo de vida de su cmdlet.

- Para los errores de terminación, utilice un identificador de error único para un determinado tipo de excepción de CLR. Si cambia el tipo de excepción, use un nuevo identificador de error.

- Errores de no terminación, utilice un identificador de error específico para un determinado objeto de entrada.

- Elegir un texto para el identificador que lacónicamente corresponde a la que se informa del error. No use signos de puntuación o espacios en blanco.

- No se generan identificadores de errores que no son reproducibles. Por ejemplo, no generan identificadores que incluyen un identificador de proceso. Identificadores de errores son útiles solo cuando se corresponden con los identificadores que ven otros usuarios que experimentan el mismo problema.

### <a name="error-categories"></a>Categorías de error

Categorías de error se usan para agrupar errores para el usuario final. Windows PowerShell define estas categorías y los cmdlets y proveedores de Windows PowerShell deben elegir entre ellos al generar el registro de error.

Para obtener una descripción de las categorías de error que están disponibles, consulte el [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeración. En general, debe evitar el uso de error genérico siempre que sea posible, UndefinedError y NoError.

Los usuarios pueden ver los errores en función de categoría cuando establece "`$ErrorView`" a "CategoryView".

## <a name="see-also"></a>Véase también

[Cmdlets de Windows PowerShell](./cmdlet-overview.md)

[Salida del cmdlet](./types-of-cmdlet-output.md)

[Shell de SDK de Windows PowerShell](../windows-powershell-reference.md)
