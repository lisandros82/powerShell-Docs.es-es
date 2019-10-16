---
title: Instrucciones para el desarrollo de consultas | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72370044"
---
# <a name="advisory-development-guidelines"></a>Directrices de desarrollo de consulta

En esta sección se describen las instrucciones que debe tener en cuenta para garantizar un buen desarrollo y experiencias de usuario. En ocasiones, es posible que se apliquen y, en ocasiones, no.

## <a name="design-guidelines"></a>Directrices de diseño

Se deben tener en cuenta las siguientes directrices al diseñar cmdlets. Cuando encuentre una directriz de diseño que se aplique a su situación, asegúrese de consultar las instrucciones de código para obtener instrucciones similares.

### <a name="support-an-inputobject-parameter-ad01"></a>Compatibilidad con un parámetro InputObject (AD01)

Dado que Windows PowerShell funciona directamente con objetos de marco de Microsoft .NET, un objeto .NET Framework suele estar disponible que coincide exactamente con el tipo que el usuario necesita para realizar una operación determinada. `InputObject` es el nombre estándar de un parámetro que toma como entrada un objeto de este tipo. Por ejemplo, el cmdlet **Stop-proc** de ejemplo en el [tutorial de StopProc](./stopproc-tutorial.md) define un parámetro @no__t 2 de tipo Process que admite la entrada de la canalización. El usuario puede obtener un conjunto de objetos de proceso, manipularlos para seleccionar los objetos exactos que se van a detener y, a continuación, pasarlos directamente al cmdlet **Stop-proc** .

### <a name="support-the-force-parameter-ad02"></a>Compatibilidad con el parámetro Force (AD02)

En ocasiones, un cmdlet necesita proteger al usuario para que realice una operación solicitada. Este tipo de cmdlet debe admitir un parámetro `Force` para permitir que el usuario invalide esa protección si el usuario tiene permisos para realizar la operación.

Por ejemplo, el cmdlet [Remove-item](/powershell/module/microsoft.powershell.management/remove-item) no quita normalmente un archivo de solo lectura. Sin embargo, este cmdlet admite un parámetro `Force`, por lo que un usuario puede forzar la eliminación de un archivo de solo lectura. Si el usuario ya tiene permiso para modificar el atributo de solo lectura y el usuario quita el archivo, el uso del parámetro `Force` simplifica la operación. Sin embargo, si el usuario no tiene permiso para quitar el archivo, el parámetro `Force` no tiene ningún efecto.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Controlar credenciales a través de Windows PowerShell (AD03)

Un cmdlet debe definir un parámetro `Credential` para representar las credenciales. Este parámetro debe ser de tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) y debe definirse mediante una declaración de atributo de credencial. Esta compatibilidad solicita automáticamente al usuario el nombre de usuario, la contraseña o ambos cuando no se proporciona una credencial completa directamente. Para obtener más información sobre el atributo Credential, vea la [declaración de atributo Credential](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Compatibilidad con los parámetros de codificación (AD04)

Si el cmdlet lee o escribe texto en o desde un formato binario, como escribir o leer desde un archivo en un sistema de archivos, el cmdlet tiene que tener un parámetro de codificación que especifica cómo se codifica el texto en el formato binario.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>Los cmdlets de prueba deben devolver un valor booleano (AD05)

Los cmdlets que realizan pruebas en sus recursos deben devolver un tipo [System. Boolean](/dotnet/api/System.Boolean) a la canalización para que se puedan usar en expresiones condicionales.

## <a name="code-guidelines"></a>Instrucciones de código

Las siguientes directrices se deben tener en cuenta al escribir código de cmdlet. Cuando encuentre una directriz que se aplique a su situación, asegúrese de consultar las instrucciones de diseño para obtener instrucciones similares.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Siga las convenciones de nomenclatura de la clase de cmdlet (AC01)

Según las convenciones de nomenclatura estándar, hace que los cmdlets sean más reconocibles y ayuda al usuario a comprender exactamente cuáles son los cmdlets. Esta práctica es especialmente importante para otros desarrolladores que usan Windows PowerShell porque los cmdlets son tipos públicos.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Definir un cmdlet en el espacio de nombres correcto

Normalmente se define la clase para un cmdlet en un espacio de nombres .NET Framework que anexa ". Comandos "al espacio de nombres que representa el producto en el que se ejecuta el cmdlet. Por ejemplo, los cmdlets que se incluyen con Windows PowerShell se definen en el espacio de nombres `Microsoft.PowerShell.Commands`.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Asigne un nombre a la clase de cmdlet para que coincida con el nombre del cmdlet

Cuando asigne un nombre a la clase .NET Framework que implementa un cmdlet, asigne a la clase el nombre " *\<Verb > **\<Noun >** \<Command >* ", donde se reemplazan los marcadores de posición @no__t *-6Verb* > y @no__t *-8Noun >* el verbo y el sustantivo usados para el nombre del cmdlet. Por ejemplo, el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) se implementa mediante una clase llamada `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Si ninguna entrada de canalización invalida el método BeginProcessing (AC02)

Si el cmdlet no acepta la entrada de la canalización, el procesamiento debe implementarse en el método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) . El uso de este método permite que Windows PowerShell mantenga el orden entre los cmdlets. El primer cmdlet de la canalización siempre devuelve sus objetos antes de que los cmdlets restantes de la canalización tengan la oportunidad de iniciar su procesamiento.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Para controlar las solicitudes de detención, invalide el método StopProcessing (AC03)

Invalide el método [System. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) para que el cmdlet pueda controlar la señal de detención. Algunos cmdlets tardan mucho tiempo en completarse y permiten que pasen mucho tiempo entre las llamadas al tiempo de ejecución de Windows PowerShell, por ejemplo, cuando el cmdlet bloquea el subproceso en llamadas RPC de ejecución prolongada. Esto incluye los cmdlets que realizan llamadas al método [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) , al método [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) y a otros mecanismos de comentarios que pueden tardar mucho tiempo en completarse. . En estos casos, es posible que el usuario necesite enviar una señal de detención a estos cmdlets.

### <a name="implement-the-idisposable-interface-ac04"></a>Implementar la interfaz IDisposable (AC04)

Si el cmdlet tiene objetos que no se eliminan (se escriben en la canalización) mediante el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , es posible que el cmdlet requiera la eliminación de objetos adicionales. Por ejemplo, si el cmdlet abre un identificador de archivo en su método [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) y mantiene el identificador abierto para su uso por el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , este identificador debe ser cerrado al final del procesamiento.

El tiempo de ejecución de Windows PowerShell no siempre llama al método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Por ejemplo, no se puede llamar al método [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) si el cmdlet se cancela a lo largo de su operación o si se produce un error de terminación en cualquier parte del cmdlet. Por lo tanto, la clase .NET Framework para un cmdlet que requiera la limpieza de objetos debe implementar el patrón de interfaz [System. IDisposable](/dotnet/api/System.IDisposable) completo, incluido el finalizador, de modo que el tiempo de ejecución de Windows PowerShell pueda llamar a ambos [. Métodos System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) y [System. IDisposable. Dispose *](/dotnet/api/System.IDisposable.Dispose) al final del procesamiento.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Usar tipos de parámetros compatibles con la serialización (AC05)

Para admitir la ejecución del cmdlet en equipos remotos, use tipos que se pueden serializar fácilmente en el equipo cliente y, a continuación, rehidratar en el equipo servidor. Los tipos siguientes son compatibles con la serialización.

Tipos primitivos:

- Byte, SByte, decimal, single, Double, Int16, Int32, Int64, Uint16, UInt32 y UInt64.

- Boolean, GUID, Byte [], TimeSpan, DateTime, Uri y version.

- Char, String, XmlDocument.

Tipos de rehydratable integrados:

- PSPrimitiveDictionary

- Parámetrodemodificador

- PSListModifier

- PSCredential

- IPAddress, MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- DirectorySecurity, FileSecurity, RegistrySecurity

Otros tipos:

- SecureString

- Contenedores (listas y diccionarios del tipo anterior)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Usar SecureString para datos confidenciales (AC06)

Al controlar los datos confidenciales, utilice siempre el tipo de datos [System. Security. SecureString](/dotnet/api/System.Security.SecureString) . Esto podría incluir la entrada de canalización a los parámetros, así como devolver datos confidenciales a la canalización.

## <a name="see-also"></a>Véase también

[Instrucciones de desarrollo necesarias](./required-development-guidelines.md)

[Instrucciones de desarrollo muy recomendables](./strongly-encouraged-development-guidelines.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
