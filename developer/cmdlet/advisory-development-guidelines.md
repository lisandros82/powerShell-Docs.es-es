---
title: Las instrucciones de desarrollo asesoramiento | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854860"
---
# <a name="advisory-development-guidelines"></a>Directrices de desarrollo de consulta

En esta sección se describe instrucciones que se deben considerar para asegurarse de buenas experiencias de desarrollo y de usuario. A veces pueden aplicar y, a veces podría no.

## <a name="design-guidelines"></a>Instrucciones de diseño

Las siguientes directrices se deben considerar al diseñar los cmdlets. Cuando encuentre una guía de diseño que se aplica a su situación, asegúrese de consultar las instrucciones de código para obtener instrucciones similares.

### <a name="support-an-inputobject-parameter-ad01"></a>Admite un parámetro InputObject (AD01)

Dado que Windows PowerShell funciona directamente con objetos de Microsoft .NET Framework, un objeto de .NET Framework suele estar disponible que coincide exactamente con el tipo, el usuario debe realiza una operación determinada. `InputObject` es el nombre estándar para un parámetro que toma este tipo de objeto como entrada. Por ejemplo, el ejemplo **Stop-Proc** cmdlet en el [StopProc Tutorial](./stopproc-tutorial.md) define un `InputObject` parámetro de tipo de proceso que admite la entrada de la canalización. El usuario puede obtener un conjunto de objetos de proceso, manipularlos para seleccionar los objetos exactos para detener y, a continuación, pasarlas a la **Stop-Proc** cmdlet directamente.

### <a name="support-the-force-parameter-ad02"></a>Compatibilidad con el parámetro Force (AD02)

En ocasiones, un cmdlet debe impedir que el usuario realizando una operación solicitada. Un cmdlet de este tipo debe admitir un `Force` parámetro para permitir que el usuario invalide dicha protección si el usuario tiene permisos para realizar la operación.

Por ejemplo, el [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) cmdlet no elimina normalmente un archivo de solo lectura. Sin embargo, este cmdlet admite un `Force` parámetro para un usuario pueda forzar la eliminación de un archivo de solo lectura. Si el usuario ya tiene permiso para modificar el atributo de sólo lectura y el usuario quita el archivo, el uso de la `Force` parámetro simplifica la operación. Sin embargo, si el usuario no tiene permiso para quitar el archivo, el `Force` parámetro no tiene ningún efecto.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Controlar las credenciales a través de Windows PowerShell (AD03)

Debe definir un cmdlet un `Credential` parámetro para representar las credenciales. Este parámetro debe ser de tipo [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) y debe definirse mediante una declaración de atributo de la credencial. Esta compatibilidad automáticamente solicita al usuario para el nombre de usuario, la contraseña o para ambos cuando no se proporciona directamente una credencial completa. Para obtener más información sobre el atributo de credencial, vea [declaración de atributo de credencial](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Admite los parámetros de codificación (AD04)

Si su cmdlet lee o escribe texto en o desde un formato binario, por ejemplo, escribir o leer desde un archivo en un sistema de archivos, el cmdlet debe tener el parámetro de codificación que especifica cómo se codifica el texto en el formato binario.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Los Cmdlets de prueba debe devolver un valor booleano (AD05)

Los cmdlets que llevan a cabo las pruebas con sus recursos debe devolver un [System.Boolean](/dotnet/api/System.Boolean) escriba a la canalización para que se pueden usar en expresiones condicionales.

## <a name="code-guidelines"></a>Instrucciones de código

Las siguientes directrices se deben considerar al escribir el código del cmdlet. Cuando encuentre una directriz que se aplica a su situación, asegúrese de consultar las instrucciones de diseño para obtener instrucciones similares.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Siga convenciones de nomenclatura de clase de Cmdlet (AC01)

Mediante la siguiente convención de nomenclatura estándar, realiza sus cmdlets sean más reconocibles y ayudar al usuario comprender exactamente lo que hacen los cmdlets. Esta práctica es especialmente importante para otros desarrolladores mediante Windows PowerShell porque los cmdlets son tipos públicos.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Definir un Cmdlet en el Namespace correcto

Lo normal es definir la clase para un cmdlet en un espacio de nombres de .NET Framework que se anexa ". Comandos"para el espacio de nombres que representa el producto en el que se ejecuta el cmdlet. Por ejemplo, los cmdlets que se incluyen con Windows PowerShell se definen en el `Microsoft.PowerShell.Commands` espacio de nombres.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Nombre de la clase del Cmdlet para que coincida con el nombre del Cmdlet

Cuando asigne nombre a la clase de .NET Framework que implementa un cmdlet, la clase el nombre "*\<verbo >**\<sustantivo >**\<comando >*", donde debe reemplazar el  *\<Verbo >* y  *\<sustantivo >* marcadores de posición con el verbo y sustantivo que se usa para el nombre del cmdlet. Por ejemplo, el [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet se implementa mediante una clase denominada `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Si ninguna entrada de la canalización invalida el método BeginProcessing (AC02)

Si el cmdlet no acepta entradas de la canalización, se debería implementar el procesamiento en el [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método. Uso de este método permite que Windows PowerShell mantener el orden entre los cmdlets. El primer cmdlet en la canalización siempre devuelve sus objetos antes de que los cmdlets restantes en la canalización Obtenga una oportunidad para iniciar su procesamiento.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Para controlar las solicitudes de detención invalidación el método StopProcessing (AC03)

Invalidar el [System.Management.Automation.Cmdlet.StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) método para que el cmdlet puede controlar la señal de detención. Algunos cmdlets tardar mucho tiempo para completar su funcionamiento, y permiten pasar entre llamadas en el tiempo de ejecución de Windows PowerShell, por ejemplo, cuando el cmdlet bloquea el subproceso en las llamadas RPC de larga ejecución mucho tiempo. Esto incluye los cmdlets que realizan llamadas a la [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método, a la [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) método y a otros comentarios mecanismos que pueden tardar mucho tiempo en completarse. En estos casos el usuario deba enviar una señal de detención a estos cmdlets.

### <a name="implement-the-idisposable-interface-ac04"></a>Implementar la interfaz IDisposable (AC04)

Si su cmdlet tiene objetos que no se eliminan de (escrito en la canalización) por el [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, el cmdlet puede requerir la eliminación de objetos adicionales. Por ejemplo, si su cmdlet abre un identificador de archivo en su [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) método y conserva el identificador se abra para su uso por el [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método, este identificador debe cerrarse al final del procesamiento.

El tiempo de ejecución de Windows PowerShell siempre no llama a la [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) método. Por ejemplo, el [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) no es posible que se llama el método si el cmdlet se ha cancelado a medio camino a través de su operación o si un carácter de terminación se produce error en cualquier parte del cmdlet. Por lo tanto, la clase de .NET Framework para un cmdlet que requiere la limpieza de objetos debe implementar toda [System.IDisposable](/dotnet/api/System.IDisposable) patrón de interfaz, incluidos el finalizador, para que el tiempo de ejecución de Windows PowerShell puede llamar a la [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) y [System.IDisposable.Dispose*](/dotnet/api/System.IDisposable.Dispose) métodos al final del procesamiento.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Usar tipos de parámetros de serialización sencillo (AC05)

Para admitir la ejecución del cmdlet en equipos remotos, use los tipos que se pueden serializar con facilidad en el equipo cliente y rehidratarse, a continuación, en el equipo del servidor. Los tipos de seguimiento son fáciles de serialización.

Tipos primitivos:

- Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, Uint16, UInt32 y UInt64.

- Boolean, Guid, Byte [], intervalo de tiempo, DateTime, Uri y versión.

- Char, String, XmlDocument.

Tipos integrados de rehydratable:

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- Dirección IP, MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- RegistrySecurity DirectorySecurity, FileSecurity,

Otros tipos:

- SecureString

- Contenedores (listas y los diccionarios del tipo anterior)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Use SecureString para datos confidenciales (AC06)

Cuando se administran datos confidenciales siempre use la [System.Security.Securestring](/dotnet/api/System.Security.SecureString) tipo de datos. Esto puede incluir parámetros, así como devolver datos confidenciales a la canalización de entrada de la canalización.

## <a name="see-also"></a>Véase también

[Directrices de desarrollo necesarias](./required-development-guidelines.md)

[Instrucciones de desarrollo recomienda encarecidamente](./strongly-encouraged-development-guidelines.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
