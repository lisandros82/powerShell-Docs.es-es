---
title: Instrucciones de desarrollo muy recomendables | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: 0906d0d37c66b8c1538a0b2e9e0f1ff2fba12ac0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369344"
---
# <a name="strongly-encouraged-development-guidelines"></a>Directrices de desarrollo recomendadas encarecidamente

En esta sección se describen las instrucciones que debe seguir al escribir los cmdlets. Se dividen en directrices para diseñar cmdlets e instrucciones para escribir el código de cmdlet. Es posible que estas instrucciones no se apliquen a todos los escenarios. Sin embargo, si se aplican y no sigue estas instrucciones, es posible que los usuarios tengan una experiencia deficiente cuando usen sus cmdlets.

## <a name="design-guidelines"></a>Directrices de diseño

- [Usar un sustantivo específico para un nombre de cmdlet (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Usar mayúsculas y minúsculas Pascal para nombres de cmdlet (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Directrices para el diseño de parámetros (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Proporcionar comentarios al usuario (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Crear un archivo de ayuda de cmdlet (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Instrucciones de código

- [Parámetros de codificación (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Compatibilidad con entrada de canalización bien definida (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Escribir registros individuales en la canalización (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Hacer que los cmdlets no distingan entre mayúsculas y minúsculas y la conservación de casos (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Directrices de diseño

Se deben seguir las siguientes directrices al diseñar cmdlets para garantizar una experiencia de usuario coherente entre el uso de los cmdlets y otros cmdlets. Cuando encuentre una directriz de diseño que se aplique a su situación, asegúrese de consultar las instrucciones de código para obtener instrucciones similares.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Usar un sustantivo específico para un nombre de cmdlet (SD01)

Los nombres que se usan en los nombres de cmdlet deben ser muy específicos para que el usuario pueda detectar los cmdlets. Anteponga un prefijo a los nombres genéricos como "servidor" con una versión abreviada del nombre del producto. Por ejemplo, si un sustantivo hace referencia a un servidor que ejecuta una instancia de Microsoft SQL Server, use un nombre como "SQLServer". La combinación de nombres específicos y la lista corta de verbos aprobados permite al usuario detectar y anticipar rápidamente la funcionalidad al tiempo que evita la duplicación entre nombres de cmdlet.

Para mejorar la experiencia del usuario, el sustantivo que elija para un nombre de cmdlet debe ser singular. Por ejemplo, use el nombre `Get-Process` en lugar de **Get-processes**. Es mejor seguir esta regla para todos los nombres de cmdlet, incluso cuando es probable que un cmdlet actúe sobre más de un elemento.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Usar mayúsculas y minúsculas Pascal para nombres de cmdlet (SD02)

Use mayúsculas y minúsculas Pascal para los nombres de parámetros. En otras palabras, ponga en mayúscula la primera letra de verbo y todos los términos usados en el nombre. Por ejemplo, "`Clear-ItemProperty`".

### <a name="parameter-design-guidelines-sd03"></a>Directrices para el diseño de parámetros (SD03)

Un cmdlet necesita parámetros que reciban los datos en los que debe funcionar y parámetros que indiquen la información que se usa para determinar las características de la operación. Por ejemplo, un cmdlet puede tener un parámetro `Name` que recibe datos de la canalización, y el cmdlet puede tener un parámetro `Force` para indicar que el cmdlet puede verse obligado a realizar su operación. No hay ningún límite en cuanto al número de parámetros que puede definir un cmdlet.

#### <a name="use-standard-parameter-names"></a>Usar nombres de parámetros estándar

El cmdlet debe usar nombres de parámetros estándar para que el usuario pueda determinar rápidamente lo que significa un parámetro determinado. Si se requiere un nombre más específico, use un nombre de parámetro estándar y, a continuación, especifique un nombre más específico como alias. Por ejemplo, el cmdlet `Get-Service` tiene un parámetro que tiene un nombre genérico (`Name`) y un alias más específico (`ServiceName`). Ambos términos se pueden usar para especificar el parámetro.

Para obtener más información acerca de los nombres de parámetro y sus tipos de datos, consulte [instrucciones de nombre y funcionalidad del cmdlet](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Usar nombres de parámetros singulares

Evite usar nombres en plural para los parámetros cuyo valor sea un único elemento. Esto incluye los parámetros que toman matrices o listas porque el usuario puede proporcionar una matriz o una lista con un solo elemento.

Los nombres de parámetro plural solo deben usarse en aquellos casos en los que el valor del parámetro siempre sea un valor de varios elementos. En estos casos, el cmdlet debe comprobar que se proporcionan varios elementos y el cmdlet debe mostrar una advertencia al usuario si no se proporcionan varios elementos.

#### <a name="use-pascal-case-for-parameter-names"></a>Usar mayúsculas y minúsculas Pascal para nombres de parámetros

Use mayúsculas y minúsculas Pascal para los nombres de parámetros. En otras palabras, ponga en mayúscula la primera letra de cada palabra en el nombre del parámetro, incluida la primera letra del nombre. Por ejemplo, el nombre de parámetro `ErrorAction` usa el uso correcto de mayúsculas. Los nombres de parámetro siguientes usan el uso incorrecto de mayúsculas:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parámetros que toman una lista de opciones

Hay dos maneras de crear un parámetro cuyo valor se puede seleccionar en un conjunto de opciones.

- Defina un tipo de enumeración (o use un tipo de enumeración existente) que especifique los valores válidos. A continuación, use el tipo de enumeración para crear un parámetro de ese tipo.

- Agregue el atributo **ValidateSet** a la declaración de parámetro. Para obtener más información acerca de este atributo, consulte [declaración del atributo ValidateSet](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Usar tipos estándar para los parámetros

Para garantizar la coherencia con otros cmdlets, utilice los tipos estándar para los parámetros cuando sea posible. Para obtener más información sobre los tipos que se deben usar para el parámetro diferente, consulte [nombres y tipos de parámetros de cmdlet estándar](./standard-cmdlet-parameter-names-and-types.md). En este tema se proporcionan vínculos a varios temas que describen los nombres y los tipos de .NET Framework de los grupos de parámetros estándar, como los "parámetros de actividad".

#### <a name="use-strongly-typed-net-framework-types"></a>Usar tipos de .NET Framework fuertemente tipados

Los parámetros se deben definir como tipos de .NET Framework para proporcionar una mejor validación de parámetros. Por ejemplo, los parámetros que están restringidos a un valor de un conjunto de valores deben definirse como un tipo de enumeración. Para admitir un valor de identificador uniforme de recursos (URI), defina el parámetro como un tipo [System. Uri](/dotnet/api/System.Uri) . Evite los parámetros de cadena básicos para todas las propiedades de texto sin formato.

#### <a name="use-consistent-parameter-types"></a>Usar tipos de parámetro coherentes

Cuando varios cmdlets usan el mismo parámetro, use siempre el mismo tipo de parámetro.  Por ejemplo, si el parámetro `Process` es un tipo [System. Int16](/dotnet/api/System.Int16) para un cmdlet, no convierta el parámetro `Process` de otro cmdlet en un tipo [System. Uint16](/dotnet/api/System.UInt16) .

#### <a name="parameters-that-take-true-and-false"></a>Parámetros que toman true y false

Si el parámetro solo toma `true` y `false`, defina el parámetro como tipo [System. Management. Automation. parámetrodemodificador](/dotnet/api/System.Management.Automation.SwitchParameter). Un parámetro de modificador se trata como `true` cuando se especifica en un comando. Si el parámetro no se incluye en un comando, Windows PowerShell considera que el valor del parámetro es `false`. No defina parámetros booleanos.

Si el parámetro necesita diferenciar entre 3 valores: $true, $false y "sin especificar", defina un parámetro de tipo que acepte valores NULL\<bool >.  La necesidad de un tercer valor "no especificado" normalmente se produce cuando el cmdlet puede modificar una propiedad booleana de un objeto. En este caso "sin especificar" significa no cambiar el valor actual de la propiedad.

#### <a name="support-arrays-for-parameters"></a>Compatibilidad con matrices para parámetros

Con frecuencia, los usuarios deben realizar la misma operación en varios argumentos. Para estos usuarios, un cmdlet debe aceptar una matriz como entrada de parámetros para que un usuario pueda pasar los argumentos al parámetro como una variable de Windows PowerShell. Por ejemplo, el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) usa una matriz para las cadenas que identifican los nombres de los procesos que se van a recuperar.

#### <a name="support-the-passthru-parameter"></a>Compatibilidad con el parámetro PassThru

De forma predeterminada, muchos cmdlets que modifican el sistema, como el cmdlet [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) , actúan como "receptores" para los objetos y no devuelven un resultado. Estos cmdlets deben implementar el parámetro `PassThru` para obligar a que el cmdlet devuelva un objeto. Cuando se especifica el parámetro `PassThru`, el cmdlet devuelve un objeto mediante una llamada al método [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Por ejemplo, el comando siguiente detiene el proceso de cálculo y pasa el proceso resultante a la canalización.

```powershell
Stop-Process calc -passthru
```

En la mayoría de los casos, los cmdlets agregar, establecer y nuevo deben admitir un parámetro `PassThru`.

#### <a name="support-parameter-sets"></a>Compatibilidad con conjuntos de parámetros

Un cmdlet está diseñado para lograr un solo propósito. Sin embargo, a menudo hay más de una manera de describir la operación o el destino de la operación. Por ejemplo, un proceso puede identificarse por su nombre, por su identificador o por un objeto de proceso. El cmdlet debe admitir todas las representaciones razonables de sus destinos. Normalmente, el cmdlet cumple este requisito especificando los conjuntos de parámetros (denominados conjuntos de parámetros) que operan juntos. Un único parámetro puede pertenecer a cualquier número de conjuntos de parámetros. Para obtener más información sobre los conjuntos de parámetros, vea [conjuntos de parámetros de cmdlet](./cmdlet-parameter-sets.md).

Al especificar los conjuntos de parámetros, establezca un solo parámetro del conjunto en ValueFromPipeline. Para obtener más información sobre cómo declarar el atributo de **parámetro** , vea [declaración de ParameterAttribute](./parameter-attribute-declaration.md).

Cuando se usan conjuntos de parámetros, el conjunto de parámetros predeterminado se define mediante el atributo de **cmdlet** . El conjunto de parámetros predeterminado debe incluir los parámetros que es más probable que se usen en una sesión interactiva de Windows PowerShell. Para obtener más información sobre cómo declarar el atributo **cmdlet** , consulte [declaración de CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Proporcionar comentarios al usuario (SD04)

Siga las instrucciones de esta sección para proporcionar comentarios al usuario. Esta información permite al usuario tener en cuenta lo que está ocurriendo en el sistema y tomar mejores decisiones administrativas.

El tiempo de ejecución de Windows PowerShell permite a un usuario especificar cómo controlar la salida de cada llamada al método `Write` mediante el establecimiento de una variable de preferencia. El usuario puede establecer varias variables de preferencia, incluida una variable que determina si el sistema debe mostrar información y una variable que determina si el sistema debe consultar al usuario antes de realizar más acciones.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Compatibilidad con los métodos WriteWarning, WriteVerbose y WriteDebug

Un cmdlet debe llamar al método [System. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) cuando el cmdlet está a punto de realizar una operación que podría tener un resultado no deseado. Por ejemplo, un cmdlet debe llamar a este método si el cmdlet está a punto de sobrescribir un archivo de solo lectura.

Un cmdlet debe llamar al método [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) cuando el usuario requiere algunos detalles sobre lo que hace el cmdlet. Por ejemplo, un cmdlet debe llamar a esta información si el autor del cmdlet considera que hay escenarios en los que es posible que se necesite más información sobre lo que está haciendo el cmdlet.

El cmdlet debe llamar al método [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) cuando un ingeniero de soporte técnico o desarrollador debe comprender lo que ha dañado la operación del cmdlet. No es necesario que el cmdlet llame al método [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) en el mismo código que llama al método [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) porque el parámetro `Debug` presenta ambos conjuntos de información.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>Compatibilidad con WriteProgress para las operaciones que tardan mucho tiempo

Las operaciones de cmdlet que tardan mucho tiempo en completarse y que no se pueden ejecutar en segundo plano deben admitir los informes de progreso a través de llamadas periódicas al método [System. Management. Automation. cmdlet. WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) .

#### <a name="use-the-host-interfaces"></a>Usar las interfaces de host

En ocasiones, un cmdlet debe comunicarse directamente con el usuario en lugar de usar los distintos métodos de escritura o deben ser compatibles con la clase [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) . En este caso, el cmdlet debe derivar de la clase [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) y usar la propiedad [System. Management. Automation. PSCmdlet. host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) . Esta propiedad admite distintos niveles de tipo de comunicación, incluidos los tipos PromptForChoice, prompt y WriteLine/ReadLine. En el nivel más específico, también proporciona métodos para leer y escribir claves individuales y para tratar con los búferes.

A menos que un cmdlet esté diseñado específicamente para generar una interfaz gráfica de usuario (GUI), no debe omitir el host mediante la propiedad [System. Management. Automation. PSCmdlet. host *](/dotnet/api/System.Management.Automation.PSCmdlet.Host) . Un ejemplo de un cmdlet diseñado para generar una GUI es el cmdlet [out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) .

> [!NOTE]
> Los cmdlets no deben usar [System. Console](/dotnet/api/System.Console) API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Crear un archivo de ayuda de cmdlet (SD05)

Para cada ensamblado de cmdlets, cree un archivo help. XML que contenga información sobre el cmdlet. Esta información incluye una descripción del cmdlet, descripciones de los parámetros del cmdlet, ejemplos del uso del cmdlet, etc.

## <a name="code-guidelines"></a>Instrucciones de código

Se deben seguir las siguientes directrices al codificar cmdlets para garantizar una experiencia de usuario coherente entre el uso de los cmdlets y otros cmdlets. Cuando encuentre una instrucción de código que se aplique a su situación, asegúrese de consultar las instrucciones de diseño para obtener instrucciones similares.

### <a name="coding-parameters-sc01"></a>Parámetros de codificación (SC01)

Defina un parámetro declarando una propiedad pública de la clase de cmdlet que esté decorada con el atributo de **parámetro** . Los parámetros no tienen que ser miembros estáticos de la clase .NET Framework derivada del cmdlet. Para obtener más información sobre cómo declarar el atributo **Parameter** , vea [declaración de atributos de parámetros](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Compatibilidad con las rutas de Windows PowerShell

La ruta de acceso de Windows PowerShell es el mecanismo para normalizar el acceso a los espacios de nombres. Cuando se asigna una ruta de acceso de Windows PowerShell a un parámetro en el cmdlet, el usuario puede definir una "unidad" personalizada que actúe como un acceso directo a una ruta de acceso específica. Cuando un usuario designa dicha unidad, los datos almacenados, como los datos del registro, se pueden usar de forma coherente.

Si el cmdlet permite al usuario especificar un archivo o un origen de datos, debe definir un parámetro de tipo [System. String](/dotnet/api/System.String). Si se admite más de una unidad, el tipo debe ser una matriz. El nombre del parámetro debe ser `Path`, con un alias de `PSPath`. Además, el parámetro `Path` debe admitir caracteres comodín. Si no es necesario admitir caracteres comodín, defina un parámetro `LiteralPath`.

Si los datos que lee o escribe el cmdlet tienen que ser un archivo, el cmdlet debe aceptar la entrada de la ruta de Windows PowerShell y el cmdlet debe usar la propiedad [System. Management. Automation. SessionState. Path](/dotnet/api/System.Management.Automation.SessionState.Path) para traducir las rutas de acceso de Windows PowerShell en rutas de acceso que el sistema de archivos reconoce. Los mecanismos específicos incluyen los siguientes métodos:

- [System. Management. Automation. PSCmdlet. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. PSCmdlet. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System. Management. Automation. PathIntrinsics. GetResolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System. Management. Automation. PathIntrinsics. GetUnresolvedProviderPathFromPSPath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Si los datos que lee o escribe el cmdlet solo son un conjunto de cadenas en lugar de un archivo, el cmdlet debe usar la información de contenido del proveedor (`Content` miembro) para leer y escribir. Esta información se obtiene de la propiedad [System. Management. Automation. Provider. CmdletProvider. InvokeProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) . Estos mecanismos permiten a otros almacenes de datos participar en la lectura y la escritura de datos.

#### <a name="support-wildcard-characters"></a>Compatibilidad con caracteres comodín

Un cmdlet debe admitir caracteres comodín si es posible. La compatibilidad con caracteres comodín se produce en muchos lugares de un cmdlet (especialmente cuando un parámetro toma una cadena para identificar un objeto de un conjunto de objetos). Por ejemplo, el cmdlet **Stop-proc** de ejemplo del [tutorial de StopProc](./stopproc-tutorial.md) define un parámetro `Name` para controlar las cadenas que representan los nombres de los procesos. Este parámetro admite caracteres comodín para que el usuario pueda especificar fácilmente los procesos que se van a detener.

Cuando hay disponible compatibilidad con caracteres comodín, una operación de cmdlet normalmente genera una matriz. En ocasiones, no tiene sentido admitir una matriz, ya que el usuario puede usar un solo elemento cada vez. Por ejemplo, el cmdlet [set-Location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) no necesita admitir una matriz porque el usuario está estableciendo una sola ubicación. En esta instancia, el cmdlet sigue admitiendo caracteres comodín, pero fuerza la resolución en una sola ubicación.

Para obtener más información sobre los patrones de caracteres comodín, consulte [compatibilidad con caracteres comodín en parámetros de cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Definir objetos

Esta sección contiene instrucciones para definir objetos para cmdlets y para extender objetos existentes.

##### <a name="define-standard-members"></a>Definir miembros estándar

Defina los miembros estándar para extender un tipo de objeto en un archivo Types. ps1xml personalizado (use el archivo Types. ps1xml de Windows PowerShell como plantilla). Los miembros estándar se definen mediante un nodo con el nombre PSStandardMembers. Estas definiciones permiten que otros cmdlets y el tiempo de ejecución de Windows PowerShell funcionen con el objeto de una manera coherente.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Definir ObjectMembers que se usarán como parámetros

Si está diseñando un objeto para un cmdlet, asegúrese de que sus miembros se asignan directamente a los parámetros de los cmdlets que lo usarán. Esta asignación permite que el objeto se envíe fácilmente a la canalización y se pase de un cmdlet a otro.

Los objetos .NET Framework preexistentes devueltos por los cmdlets a menudo faltan algunos miembros importantes o cómodos que son necesarios para el desarrollador o el usuario de scripts. Estos miembros que faltan pueden ser especialmente importantes para la presentación y para crear los nombres de miembro correctos, de modo que el objeto pueda pasarse correctamente a la canalización. Cree un archivo Types. ps1xml personalizado para documentar estos miembros necesarios. Al crear este archivo, se recomienda la Convención de nomenclatura siguiente: *< Your_Product_Name >* . Types. ps1xml.

Por ejemplo, puede Agregar una propiedad de script `Mode` al tipo [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) para mostrar los atributos de un archivo con mayor claridad. Además, puede Agregar una propiedad alias `Count` al tipo [System. Array](/dotnet/api/System.Array) para permitir el uso coherente de ese nombre de propiedad (en lugar de `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implementar la interfaz IComparable

Implemente una interfaz [System. IComparable](/dotnet/api/System.IComparable) en todos los objetos de salida. Esto permite canalizar fácilmente los objetos de salida a varios cmdlets de ordenación y análisis.

##### <a name="update-display-information"></a>Actualizar información de pantalla

Si la presentación de un objeto no proporciona los resultados esperados, cree un *> de\<personalizado YourProductName*. Archivo Format. ps1xml para ese objeto.

### <a name="support-well-defined-pipeline-input-sc02"></a>Compatibilidad con entrada de canalización bien definida (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implementar para la mitad de una canalización

Implemente un cmdlet asumiendo que se llamará desde el medio de una canalización (es decir, otros cmdlets generarán su entrada o consumirán su salida). Por ejemplo, podría suponer que el cmdlet `Get-Process`, ya que genera datos, solo se usa como primer cmdlet en una canalización. Sin embargo, dado que este cmdlet está diseñado para la mitad de una canalización, este cmdlet permite que los cmdlets o datos anteriores de la canalización especifiquen los procesos que se van a recuperar.

#### <a name="support-input-from-the-pipeline"></a>Compatibilidad con la entrada de la canalización

En cada conjunto de parámetros de un cmdlet, incluya al menos un parámetro que admita la entrada de la canalización. La compatibilidad con la entrada de canalización permite al usuario recuperar datos u objetos, enviarlos al conjunto de parámetros correcto y pasar los resultados directamente a un cmdlet.

Un parámetro acepta la entrada de la canalización si el atributo de **parámetro** incluye la palabra clave `ValueFromPipeline`, el atributo de palabra clave `ValueFromPipelineByPropertyName` o ambas palabras clave en su declaración. Si ninguno de los parámetros de un conjunto de parámetros admite las palabras clave `ValueFromPipeline` o `ValueFromPipelineByPropertyName`, el cmdlet no se puede colocar con sentido después de otro cmdlet porque omitirá cualquier entrada de canalización.

#### <a name="support-the-processrecord-method"></a>Compatibilidad con el método ProcessRecord

Para aceptar todos los registros del cmdlet anterior en la canalización, el cmdlet debe implementar el método [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . Windows PowerShell llama a este método varias veces, una vez para cada registro que se envía al cmdlet.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Escribir registros individuales en la canalización (SC03)

Cuando un cmdlet devuelve objetos, el cmdlet debe escribir los objetos inmediatamente a medida que se generan. El cmdlet no debe contenerlos para almacenarlos en búfer en una matriz combinada. Los cmdlets que reciben los objetos como entrada podrán procesar, mostrar o procesar y mostrar los objetos de salida sin retraso. Un cmdlet que genera objetos de salida de uno en uno debe llamar al método [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) . Un cmdlet que genera objetos de salida en lotes (por ejemplo, porque una API subyacente devuelve una matriz de objetos de salida) debe llamar al método [System. Management. Automation. cmdlet. writeObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) con su segundo parámetro establecido en `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Hacer que los cmdlets no distingan entre mayúsculas y minúsculas y la conservación de casos (SC04)

De forma predeterminada, Windows PowerShell no distingue entre mayúsculas y minúsculas. Sin embargo, dado que se trata de muchos sistemas preexistentes, Windows PowerShell conserva el uso de mayúsculas y minúsculas para facilitar la operación y la compatibilidad. En otras palabras, si se proporciona un carácter en mayúsculas, Windows PowerShell lo mantiene en mayúsculas. Para que los sistemas funcionen bien, un cmdlet debe seguir esta Convención. Si es posible, debe funcionar sin distinción entre mayúsculas y minúsculas. Sin embargo, debe conservar el caso original para los cmdlets que se producen posteriormente en un comando o en la canalización.

## <a name="see-also"></a>Vea también

[Instrucciones de desarrollo necesarias](./required-development-guidelines.md)

[Instrucciones para el desarrollo de asesoría](./advisory-development-guidelines.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
