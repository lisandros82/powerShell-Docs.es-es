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
ms.openlocfilehash: 5dfec318438ca139518c596011ac5e56445738ea
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365924"
---
# <a name="cmdlet-error-reporting"></a>Informes de errores de cmdlet

Los cmdlets deben notificar los errores de manera diferente, en función de si los errores están finalizando o no los errores. Los errores de terminación son errores que hacen que la canalización finalice inmediatamente, o errores que se producen cuando no hay ningún motivo para continuar el procesamiento. Los errores de no terminación son los que notifican una condición de error actual, pero el cmdlet puede continuar procesando los objetos de entrada. Con errores de no terminación, normalmente el usuario recibe una notificación del problema, pero el cmdlet continúa procesando el siguiente objeto de entrada.

## <a name="terminating-and-nonterminating-errors"></a>Errores de terminación y de no terminación

Se pueden usar las siguientes directrices para determinar si una condición de error es un error de terminación o un error de no terminación.

- ¿La condición de error impide que el cmdlet procese correctamente cualquier objeto de entrada adicional? Si es así, se trata de un error de terminación.

- ¿Es la condición de error relacionada con un objeto de entrada concreto o con un subconjunto de objetos de entrada? Si es así, se trata de un error de no terminación.

- ¿El cmdlet acepta varios objetos de entrada, de modo que el procesamiento puede realizarse correctamente en otro objeto de entrada? Si es así, se trata de un error de no terminación.

- Los cmdlets que pueden aceptar varios objetos de entrada deben decidir entre los errores de terminación y de no terminación, incluso cuando una situación determinada se aplica solo a un único objeto de entrada.

- Los cmdlets pueden recibir cualquier número de objetos de entrada y enviar cualquier número de objetos correctos o de error antes de producir una excepción de terminación. No hay ninguna relación entre el número de objetos de entrada recibidos y el número de objetos correctos y de error enviados.

- Los cmdlets que pueden aceptar solo 0-1 objetos de entrada y generar solo 0-1 objetos de salida deben tratar los errores como errores de terminación y generar excepciones de terminación.

## <a name="reporting-nonterminating-errors"></a>Informes de errores de no terminación

Los informes de un error de no terminación siempre deben realizarse dentro de la implementación del cmdlet del método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) , el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , o bien el método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Estos tipos de errores se indican mediante una llamada al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) que, a su vez, envía un registro de error al flujo de error.

## <a name="reporting-terminating-errors"></a>Notificar errores de terminación

Los errores de terminación se registran iniciando excepciones o llamando al método [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Tenga en cuenta que los cmdlets también pueden detectar y volver a producir excepciones como **OutOfMemory**; sin embargo, no es necesario que vuelvan a producir excepciones ya que el tiempo de ejecución de PowerShell las detectará también.

También puede definir sus propias excepciones para los problemas específicos de su situación o agregar información adicional a una excepción existente mediante su registro de errores.

## <a name="error-records"></a>Registros de error

PowerShell describe una condición de error de no terminación con objetos [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . Cada objeto proporciona información de categoría de error, un objeto de destino opcional y detalles sobre la condición de error.

### <a name="error-identifiers"></a>Identificadores de error

El identificador de error es una cadena simple que identifica la condición de error dentro del cmdlet.
PowerShell combina este identificador con un identificador de cmdlet para crear un identificador de error completo que se puede usar más adelante al filtrar flujos de error o errores de registro, al responder a errores específicos o a otras actividades específicas del usuario.

Se deben seguir las siguientes directrices al especificar los identificadores de error:

- Asignar identificadores de error diferentes y muy específicos a diferentes rutas de código. Cada ruta de acceso del código que llama a [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) debe tener su propio identificador de error.

- Los identificadores de error deben ser únicos en los tipos de excepción de Common Language Runtime (CLR) para los errores de terminación y de no terminación.

- No cambie la semántica de un identificador de error entre las versiones del cmdlet o del proveedor de PowerShell. Después de establecer la semántica de un identificador de error, debe permanecer constante a lo largo del ciclo de vida del cmdlet.

- Para terminar los errores, utilice un identificador de error único para un tipo de excepción de CLR determinado. Si el tipo de excepción cambia, use un nuevo identificador de error.

- En el caso de los errores de no terminación, use un identificador de error específico para un objeto de entrada concreto.

- Elija texto para el identificador que tersely corresponda con el error que se va a informar. No use espacios en blanco ni signos de puntuación.

- No genere identificadores de error que no se reproducirán. Por ejemplo, no genere identificadores que incluyan un identificador de proceso. Los identificadores de error solo son útiles cuando se corresponden con los identificadores que ven otros usuarios que experimentan el mismo problema.

### <a name="error-categories"></a>Categorías de error

Las categorías de error se usan para agrupar los errores del usuario. PowerShell define estas categorías y cmdlets, y los proveedores de PowerShell deben elegir entre ellos al generar el registro de errores.

Para obtener una descripción de las categorías de error que están disponibles, consulte la enumeración [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) . En general, debe evitar usar **NoError**, **UndefinedError**y **GenericError** siempre que sea posible.

Los usuarios pueden ver los errores en función de la categoría cuando establecen `$ErrorView` en **CategoryView**.

## <a name="see-also"></a>Consulta también

[Introducción a los cmdlets](./cmdlet-overview.md)

[Tipos de salida de cmdlet](./types-of-cmdlet-output.md)

[Referencia de Windows PowerShell](../windows-powershell-reference.md)
