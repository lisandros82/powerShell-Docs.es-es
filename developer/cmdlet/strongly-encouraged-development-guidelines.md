---
title: Recomienda encarecidamente las instrucciones de desarrollo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d68a8f3-fba0-44c5-97b9-9fc191d269a5
caps.latest.revision: 13
ms.openlocfilehash: c11e50913d2654b786e0e8cfeaf41454999bf75e
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794984"
---
# <a name="strongly-encouraged-development-guidelines"></a>Directrices de desarrollo recomendadas encarecidamente

En esta sección se describe instrucciones que debe seguir al escribir sus cmdlets. Se dividen en las directrices para diseñar los cmdlets y las instrucciones para escribir el código del cmdlet. Es posible que estas instrucciones no son aplicables para cada escenario. Sin embargo, si se aplican y no se siguen estas directrices, los usuarios podrían tener una experiencia deficiente al usar los cmdlets.

## <a name="design-guidelines"></a>Instrucciones de diseño

- [Use un sustantivo específico para un nombre de Cmdlet (SD01)](./strongly-encouraged-development-guidelines.md#use-a-specific-noun-for-a-cmdlet-name-sd01)

- [Utilice mayúsculas y minúsculas Pascal para los nombres de Cmdlet (SD02)](./strongly-encouraged-development-guidelines.md#use-pascal-case-for-cmdlet-names-sd02)

- [Instrucciones de diseño de parámetro (SD03)](./strongly-encouraged-development-guidelines.md#parameter-design-guidelines-sd03)

- [Proporcionar comentarios al usuario (SD04)](./strongly-encouraged-development-guidelines.md#provide-feedback-to-the-user-sd04)

- [Crear un archivo de Ayuda de Cmdlet (SD05)](./strongly-encouraged-development-guidelines.md#create-a-cmdlet-help-file-sd05)

## <a name="code-guidelines"></a>Instrucciones de código

- [Parámetros de codificación (SC01)](./strongly-encouraged-development-guidelines.md#coding-parameters-sc01)

- [Admite la entrada de canalización bien definido (SC02)](./strongly-encouraged-development-guidelines.md#support-well-defined-pipeline-input-sc02)

- [Escribir registros solo en la canalización (SC03)](./strongly-encouraged-development-guidelines.md#write-single-records-to-the-pipeline-sc03)

- [Asegúrese de Cmdlets de mayúsculas y minúsculas y conservar el modelo (SC04)](./strongly-encouraged-development-guidelines.md#make-cmdlets-case-insensitive-and-case-preserving-sc04)

## <a name="design-guidelines"></a>Instrucciones de diseño

Deben seguir las siguientes directrices al diseñar los cmdlets para garantizar una experiencia de usuario coherente entre el uso de los cmdlets y otros cmdlets. Cuando encuentre una guía de diseño que se aplica a su situación, asegúrese de consultar las instrucciones de código para obtener instrucciones similares.

### <a name="use-a-specific-noun-for-a-cmdlet-name-sd01"></a>Use un sustantivo específico para un nombre de Cmdlet (SD01)

Sustantivos usar en el nombre de cmdlet deben ser muy específicos para que el usuario puede detectar sus cmdlets. Prefijo de nombres genéricos como "server" con una versión abreviada del nombre del producto. Por ejemplo, si un nombre hace referencia a un servidor que ejecuta una instancia de Microsoft SQL Server, use un sustantivo como "SQLServer". La combinación de nombres específicos y la breve lista de verbos aprobados permiten al usuario a detectar rápidamente y anticipación de su funcionalidad al evitar la duplicación entre los nombres de cmdlet.

Para mejorar la experiencia del usuario, el nombre que elija para un nombre de cmdlet debe ser singular. Por ejemplo, use el nombre `Get-Process` en lugar de **Get procesos**. Es mejor seguir esta regla para todos los nombres de cmdlet, incluso cuando un cmdlet es probable que actúen en más de un elemento.

### <a name="use-pascal-case-for-cmdlet-names-sd02"></a>Utilice mayúsculas y minúsculas Pascal para los nombres de Cmdlet (SD02)

Utilice mayúsculas y minúsculas Pascal para los nombres de parámetro. En otras palabras, poner en mayúsculas la primera letra del verbo y todos los términos usados en el nombre. Por ejemplo, "`Clear-ItemProperty`".

### <a name="parameter-design-guidelines-sd03"></a>Instrucciones de diseño de parámetro (SD03)

Un cmdlet tiene parámetros que reciben los datos en el que debe operar y parámetros que indican la información que se usa para determinar las características de la operación. Por ejemplo, podría tener un cmdlet un `Name` parámetro que recibe los datos de la canalización y el cmdlet podría tener un `Force` parámetro para indicar que el cmdlet puede verse obligado a realizar su operación. No hay ningún límite al número de parámetros que puede definir un cmdlet.

#### <a name="use-standard-parameter-names"></a>Utilice nombres de parámetros estándar

El cmdlet debe usar nombres de los parámetros estándar para que el usuario pueda determinar rápidamente lo que significa que un parámetro concreto. Si se requiere un nombre más específico, use un nombre de parámetro estándar y, a continuación, especifique un nombre más específico como un alias. Por ejemplo, el `Get-Service` cmdlet tiene un parámetro que tiene un nombre genérico (`Name`) y un alias más específico (`ServiceName`). Ambos términos pueden usarse para especificar el parámetro.

Para obtener más información acerca de los nombres de parámetro y sus tipos de datos, vea [nombre de parámetro de Cmdlet y directrices de funcionalidad](./standard-cmdlet-parameter-names-and-types.md).

#### <a name="use-singular-parameter-names"></a>Use los nombres de parámetro simples

Evite usar nombres plurales para los parámetros cuyo valor es un elemento único. Esto incluye parámetros que toman matrices o listas porque el usuario podría proporcionar una matriz o lista con un solo elemento.

Los nombres de parámetro plural deben usarse solo en esos casos donde el valor del parámetro es siempre un valor de varios elementos. En estos casos, el cmdlet debe comprobar que se proporcionan varios elementos y el cmdlet debe mostrar una advertencia al usuario si no se proporcionan varios elementos.

#### <a name="use-pascal-case-for-parameter-names"></a>Utilice mayúsculas y minúsculas Pascal para los nombres de parámetro

Utilice mayúsculas y minúsculas Pascal para los nombres de parámetro. En otras palabras, poner en mayúsculas la primera letra de cada palabra en el nombre de parámetro, incluida la primera letra del nombre. Por ejemplo, el nombre del parámetro `ErrorAction` usa las mayúsculas correctas. Los siguientes nombres de parámetro usan incorrecto de mayúsculas y minúsculas:

- `errorAction`

- `erroraction`

#### <a name="parameters-that-take-a-list-of-options"></a>Parámetros que toman una lista de opciones

Hay dos maneras de crear un parámetro cuyo valor se puede seleccionar de un conjunto de opciones.

- Definir un tipo de enumeración (o utilice un tipo de enumeración existente) que especifica los valores válidos. A continuación, utilice el tipo de enumeración para crear un parámetro de ese tipo.

- Agregar el **ValidateSet** a la declaración de parámetro de atributo. Para obtener más información acerca de este atributo, vea [ValidateSet la declaración de atributo](./validateset-attribute-declaration.md).

#### <a name="use-standard-types-for-parameters"></a>Utilizar tipos estándar para los parámetros

Para garantizar la coherencia con otros cmdlets, utiliza los tipos estándar para los parámetros donde cada vez que sea posible. Para obtener más información sobre los tipos que se debe usar para parámetros diferentes, consulte [tipos y nombres de parámetro de Cmdlet estándar](./standard-cmdlet-parameter-names-and-types.md). Este tema proporciona vínculos a varios temas que describen los nombres y tipos de .NET Framework para los grupos de los parámetros estándares, como los "parámetros de actividad".

#### <a name="use-strongly-typed-net-framework-types"></a>Usar tipos fuertemente tipada de .NET Framework

Los parámetros deben definirse como tipos de .NET Framework para proporcionar una mejor validación de parámetros. Por ejemplo, los parámetros que están restringidos a un valor de un conjunto de valores deben definirse como un tipo de enumeración. Para admitir un valor de identificador uniforme de recursos (URI), defina el parámetro como un [System.Uri](/dotnet/api/System.Uri) tipo. Evite los parámetros de cadena básicas de las propiedades de todos excepto texto sin formato.

#### <a name="use-consistent-parameter-types"></a>Usar tipos de parámetro coherentes

Cuando se usa el mismo parámetro de varios cmdlets, use siempre el mismo tipo de parámetro.  Por ejemplo, si la `Process` parámetro es un [System.Int16](/dotnet/api/System.Int16) tipo para un cmdlet, no realice el `Process` parámetro de otro cmdlet un [System.Uint16](/dotnet/api/System.UInt16) tipo.

#### <a name="parameters-that-take-true-and-false"></a>Parámetros que toman True y False

Si el parámetro toma solo `true` y `false`, defina el parámetro como tipo [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter). Se considera un parámetro de modificador `true` cuando se especifica en un comando. Si el parámetro no se incluye en un comando, Windows PowerShell se considera que el valor del parámetro sea `false`. No defina parámetros booleanos.

Si el parámetro debe diferenciar entre los 3 valores: $true, $false y "unspecified", a continuación, defina un parámetro de tipo Nullable\<bool >.  La necesidad de un 3, "no especificado" valor normalmente se produce cuando el cmdlet puede modificar una propiedad booleana de un objeto. En este caso "sin especificar" significa que no cambie el valor actual de la propiedad.

#### <a name="support-arrays-for-parameters"></a>Admite matrices de parámetros

Con frecuencia, los usuarios deben realizar la misma operación frente a varios argumentos. Para estos usuarios, un cmdlet debe aceptar una matriz como parámetro de entrada para que un usuario pueda pasar los argumentos en el parámetro como una variable de Windows PowerShell. Por ejemplo, el [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet usa una matriz para las cadenas que identifican los nombres de los procesos que se va a recuperar.

#### <a name="support-the-passthru-parameter"></a>Admite el parámetro PassThru

De forma predeterminada, muchos de los cmdlets que modifique el sistema, tales como la [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) actúan como "receptores" para los objetos de cmdlet y no devuelven un resultado. Debe implementar estos cmdlet la `PassThru` parámetro para forzar el cmdlet para devolver un objeto. Cuando el `PassThru` parámetro se especifica, el cmdlet devuelve un objeto mediante el uso de una llamada a la [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Por ejemplo, el siguiente comando detiene el proceso Calc y pasa el proceso resultante a la canalización.

```powershell
Stop-Process calc -passthru
```

En la mayoría de los casos, debe admitir los cmdlets de conjunto, nuevos y agregar un `PassThru` parámetro.

#### <a name="support-parameter-sets"></a>Admitir conjuntos de parámetros

Un cmdlet está pensado para lograr un propósito único. Sin embargo, con frecuencia hay más de una manera de describir la operación o el destino de la operación. Por ejemplo, un proceso puede identificarse por su nombre, mediante su identificador o por un objeto de proceso. El cmdlet debe admitir todas las representaciones de razonables de sus destinos. Normalmente, el cmdlet cumple este requisito mediante la especificación de conjuntos de parámetros (denominados conjuntos de parámetros) que funcionan conjuntamente. Un parámetro único puede pertenecer a cualquier número de conjuntos de parámetros. Para obtener más información acerca de conjuntos de parámetros, vea [conjuntos de parámetros de Cmdlet](./cmdlet-parameter-sets.md).

Al especificar conjuntos de parámetros, establezca solo un parámetro en el conjunto de ValueFromPipeline. Para obtener más información acerca de cómo declarar el **parámetro** atributo, vea [ParameterAttribute declaración](./parameter-attribute-declaration.md).

Cuando se utilizan conjuntos de parámetros, el conjunto de parámetros de forma predeterminada se define mediante el **Cmdlet** atributo. El conjunto de parámetro predeterminado debe incluir los parámetros más probables que se usará en una sesión interactiva de Windows PowerShell. Para obtener más información acerca de cómo declarar el **Cmdlet** atributo, vea [declaración CmdletAttribute](./cmdlet-attribute-declaration.md).

### <a name="provide-feedback-to-the-user-sd04"></a>Proporcionar comentarios al usuario (SD04)

Use las instrucciones de esta sección para proporcionar comentarios al usuario. Estos comentarios permite al usuario tener en cuenta lo que ocurre en el sistema y tomar mejor decisiones administrativas.

El tiempo de ejecución de Windows PowerShell permite al usuario especificar cómo controlar la salida de cada llamada a la `Write` método estableciendo una variable de preferencia. El usuario puede establecer varias variables de preferencia, como una variable que determina si el sistema debe mostrar información y una variable que determina si el sistema debe solicitar al usuario antes de realizar una acción posterior.

#### <a name="support-the-writewarning-writeverbose-and-writedebug-methods"></a>Admitir la WriteWarning, WriteVerbose y métodos WriteDebug

Debe llamar un cmdlet el [System.Management.Automation.Cmdlet.Writewarning*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) método cuando el cmdlet que se va a realizar una operación que podría tener un resultado no deseado. Por ejemplo, un cmdlet debe llamar a este método si el cmdlet está a punto de sobrescribir un archivo de solo lectura.

Debe llamar un cmdlet el [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método cuando el usuario necesita algunos detalles sobre lo que hace el cmdlet. Por ejemplo, un cmdlet debe llamar a esta información si el autor del cmdlet se siente que hay escenarios que podrían requerir obtener más información sobre lo que hace el cmdlet.

El cmdlet debe llamar a la [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método cuando un ingeniero de soporte técnico de producto o el desarrollador debe entender lo que ha dañado la operación de cmdlet. No es necesario para el cmdlet para llamar a la [System.Management.Automation.Cmdlet.Writedebug*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) método en el mismo código que llama a la [System.Management.Automation.Cmdlet.Writeverbose*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) método porque el `Debug` parámetro presenta ambos conjuntos de información.

#### <a name="support-writeprogress-for-operations-that-take-a-long-time"></a>WriteProgress de soporte técnico para las operaciones que llevan mucho tiempo

Las operaciones de cmdlet que toman mucho tiempo en completarse y que no se puede ejecutar en segundo plano debe admitir el progreso de la generación de informes mediante llamadas periódicas a la [System.Management.Automation.Cmdlet.Writeprogress*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) método.

#### <a name="use-the-host-interfaces"></a>Usar las Interfaces de Host

En ocasiones, un cmdlet debe comunicarse directamente con el usuario en lugar de mediante el uso de los distintos escribir o deben métodos admitidos por el [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) clase. En este caso, el cmdlet debe derivar de la [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) clase y usar el [System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) propiedad. Esta propiedad admite distintos niveles de tipo de comunicación, incluidos los tipos PromptForChoice, símbolo del sistema y WriteLine/ReadLine. Nivel más específico, también proporciona maneras para leer y escribir las claves individuales y para tratar con los búferes.

A menos que un cmdlet está diseñado específicamente para generar una interfaz gráfica de usuario (GUI), no debe omitir el host utilizando la [System.Management.Automation.Pscmdlet.Host*](/dotnet/api/System.Management.Automation.PSCmdlet.Host) propiedad. Un ejemplo de un cmdlet que está diseñado para generar una interfaz gráfica de usuario es el [Out-GridView](/powershell/module/Microsoft.PowerShell.Utility/Out-GridView) cmdlet.

> [!NOTE]
> No debe usar los cmdlets del [System.Console](/dotnet/api/System.Console) API.

### <a name="create-a-cmdlet-help-file-sd05"></a>Crear un archivo de Ayuda de Cmdlet (SD05)

Para cada ensamblado de cmdlet, cree un archivo de Help.xml que contiene información sobre el cmdlet. Esta información incluye una descripción del cmdlet, las descripciones de los parámetros del cmdlet, ejemplos de uso del cmdlet y mucho más.

## <a name="code-guidelines"></a>Instrucciones de código

Las siguientes directrices se deben seguir al codificar los cmdlets para garantizar una experiencia de usuario coherente entre el uso de los cmdlets y otros cmdlets. Cuando encuentre una directriz de código que se aplica a su situación, asegúrese de consultar las instrucciones de diseño para obtener instrucciones similares.

### <a name="coding-parameters-sc01"></a>Parámetros de codificación (SC01)

Definir un parámetro al declarar una propiedad pública de la clase del cmdlet que está decorada con el **parámetro** atributo. Parámetros no tiene que ser miembros estáticos de la clase derivada de .NET Framework para el cmdlet. Para obtener más información acerca de cómo declarar el **parámetro** atributo, vea [declaración de atributo de parámetro](./parameter-attribute-declaration.md).

#### <a name="support-windows-powershell-paths"></a>Admite rutas de acceso de Windows PowerShell

La ruta de acceso de Windows PowerShell es el mecanismo para la normalización de acceso a los espacios de nombres. Cuando asigna una ruta de acceso de Windows PowerShell a un parámetro en el cmdlet, el usuario puede definir una "unidad" que actúa como un acceso directo a una ruta de acceso específica personalizada. Cuando un usuario designa una unidad de este tipo, los datos almacenados, como los datos en el registro, pueden usarse de forma coherente.

Si el cmdlet permite al usuario especificar un archivo o un origen de datos, debe definir un parámetro de tipo [System.String](/dotnet/api/System.String). Si se admite más de una unidad, el tipo debe ser una matriz. El nombre del parámetro debe ser `Path`, con un alias de `PSPath`. Además, el `Path` parámetro debería admite caracteres comodín. Si la compatibilidad con caracteres comodín no es necesario, defina un `LiteralPath` parámetro.

Si los datos que el cmdlet lee o escribe debe ser un archivo, el cmdlet debe aceptar la entrada de ruta de acceso de Windows PowerShell y debe usar el cmdlet la [System.Management.Automation.Sessionstate.Path](/dotnet/api/System.Management.Automation.SessionState.Path) propiedad para traducir el Windows Rutas de acceso de PowerShell en rutas de acceso que reconozca el sistema de archivos. Los mecanismos específicos incluyen los siguientes métodos:

- [System.Management.Automation.Pscmdlet.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pscmdlet.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PSCmdlet.GetUnresolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetResolvedProviderPathFromPSPath)

- [System.Management.Automation.Pathintrinsics.Getunresolvedproviderpathfrompspath](/dotnet/api/System.Management.Automation.PathIntrinsics.GetUnresolvedProviderPathFromPSPath)

Si los datos que el cmdlet lee o escribe sólo están un conjunto de cadenas en lugar de un archivo, el cmdlet debe usar la información del proveedor de contenido (`Content` miembro) para leer y escribir. Esta información se obtiene desde el [System.Management.Automation.Provider.Cmdletprovider.Invokeprovider*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.InvokeProvider) propiedad. Estos mecanismos permiten participar en la lectura y escritura de datos de otros almacenes de datos.

#### <a name="support-wildcard-characters"></a>Admite caracteres comodín

Un cmdlet debe admitir caracteres comodín si es posible. Compatibilidad con caracteres comodín se produce en varios lugares de un cmdlet (especialmente cuando un parámetro toma una cadena para identificar un objeto de un conjunto de objetos). Por ejemplo, el ejemplo **Stop-Proc** cmdlet desde el [StopProc Tutorial](./stopproc-tutorial.md) define un `Name` parámetro para controlar las cadenas que representan los nombres de proceso. Este parámetro admite caracteres comodín para que el usuario puede especificar fácilmente los procesos que se va a detener.

Cuando se admite para el comodín caracteres está disponible, normalmente, una operación de cmdlet genera una matriz. En ocasiones, no tiene sentido para admitir una matriz porque el usuario podría usar sólo un elemento a la vez. Por ejemplo, el [Set-Location](/powershell/module/Microsoft.PowerShell.Management/Set-Location) cmdlet no es necesario admitir una matriz porque el usuario establezca una única ubicación. En este caso, el cmdlet todavía admite caracteres comodín, pero fuerza la resolución a una única ubicación.

Para obtener más información acerca de los patrones de caracteres comodín, consulte [que admiten caracteres comodín en los parámetros de Cmdlet](./supporting-wildcard-characters-in-cmdlet-parameters.md).

#### <a name="defining-objects"></a>Definición de objetos

Esta sección contiene instrucciones para definir objetos para los cmdlets y para extender los objetos existentes.

##### <a name="define-standard-members"></a>Definir a miembros estándar

Definir miembros estándares para extender un tipo de objeto en un archivo Types.ps1xml personalizado (use el archivo Types.ps1xml de Windows PowerShell como una plantilla). Miembros estándar se definen mediante un nodo con el nombre PSStandardMembers. Estas definiciones de permitir que otros cmdlets y el tiempo de ejecución de Windows PowerShell para trabajar con el objeto de una manera coherente.

##### <a name="define-objectmembers-to-be-used-as-parameters"></a>Definir ObjectMembers para usarse como parámetros

Si está diseñando un objeto de un cmdlet, asegúrese de que sus miembros se asignan directamente a los parámetros de los cmdlets que lo utilizará. Esta asignación permite que el objeto fácilmente se envíen a la canalización y pasar de un cmdlet a otro.

Con frecuencia, objetos ya existentes de .NET Framework que se devuelven los cmdlets de faltan a algunos miembros importantes o convenientes que son necesarios para el desarrollador de script o el usuario. Estos miembros que faltan pueden ser especialmente importantes para su presentación y para crear nombres de miembro correcto para que el objeto se puede pasar correctamente a la canalización. Cree un archivo Types.ps1xml personalizado para documentar estos miembros requeridos. Cuando se crea este archivo, se recomienda la siguiente convención de nomenclatura: *< Your_Product_Name >*. Types.ps1xml.

Por ejemplo, podría agregar un `Mode` script propiedad a la [System.IO.Fileinfo](/dotnet/api/System.IO.FileInfo) tipo para mostrar los atributos de un archivo con mayor claridad. Además, puede agregar un `Count` propiedad de alias para el [System.Array](/dotnet/api/System.Array) tipo para permitir el uso coherente de ese nombre de propiedad (en lugar de `Length`).

##### <a name="implement-the-icomparable-interface"></a>Implemente la interfaz IComparable

Implemente un [System.Icomparable](/dotnet/api/System.IComparable) interfaz en todos los objetos de salida. Esto permite que los objetos de salida canalizar fácilmente varios cmdlets de ordenación y el análisis.

##### <a name="update-display-information"></a>Mostrar información de actualización

Si la presentación de un objeto no proporciona los resultados esperados, cree un personalizado  *\<YourProductName >*. Archivo Format.ps1xml para ese objeto.

### <a name="support-well-defined-pipeline-input-sc02"></a>Admite la entrada de canalización bien definido (SC02)

#### <a name="implement-for-the-middle-of-a-pipeline"></a>Implemente para el medio de una canalización

Implementar un cmdlet suponiendo que se llamará desde la mitad de una canalización (es decir, otros cmdlets se generar su entrada o usar su salida). Por ejemplo, podría suponer que el `Get-Process` cmdlet, porque genera datos, solo se usa como el primer cmdlet en una canalización. Sin embargo, dado que este cmdlet está diseñado para el medio de una canalización, este cmdlet permite los cmdlets anteriores o los datos en la canalización para especificar los procesos que se va a recuperar.

#### <a name="support-input-from-the-pipeline"></a>Compatibilidad con entrada de la canalización

En cada conjunto de parámetros para un cmdlet, incluya al menos un parámetro que admite la entrada de la canalización. Entrada de la canalización permite al usuario recuperar datos u objetos, enviarlos al conjunto de parámetros correctos y pasar los resultados directamente a un cmdlet.

Un parámetro acepta la entrada de la canalización si la **parámetro** atributo incluye la `ValueFromPipeline` palabra clave, el `ValueFromPipelineByPropertyName` el atributo de la palabra clave o las dos palabras clave en su declaración. Si ninguno de los parámetros en un parámetro de compatibilidad con juego el `ValueFromPipeline` o `ValueFromPipelineByPropertyName` palabras clave, el cmdlet significativamente no se pueden colocar después de otro cmdlet porque pasará por alto cualquier entrada de la canalización.

#### <a name="support-the-processrecord-method"></a>Admite el método ProcessRecord

Para aceptar todos los registros desde el cmdlet anterior en la canalización, el cmdlet debe implementar la [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) método. Windows PowerShell llama a este método varias veces, una vez para cada registro que se envía al cmdlet.

### <a name="write-single-records-to-the-pipeline-sc03"></a>Escribir registros solo en la canalización (SC03)

Cuando un cmdlet devuelve objetos, el cmdlet debe escribir los objetos inmediatamente a medida que se generan. El cmdlet no debe almacenar ellos con el fin de almacenar en búfer en una matriz combinada. Los cmdlets que recibe los objetos como entrada, a continuación, podrá procesar, mostrar, o procesar y mostrar los objetos de salida sin retraso. Objetos de un cmdlet que genera la salida una vez debe llamar a la [System.Management.Automation.Cmdlet.Writeobject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) método. Debe llamar un cmdlet que genera objetos de salida por lotes (por ejemplo, dado que una API subyacente devuelve una matriz de objetos de salida) la [System.Managemet.Automation.Cmdlet.Writeobject](/dotnet/api/System.Managemet.Automation.Cmdlet.WriteObject) método con su segundo parámetro establecido para `true`.

### <a name="make-cmdlets-case-insensitive-and-case-preserving-sc04"></a>Asegúrese de Cmdlets de mayúsculas y minúsculas y conservar el modelo (SC04)

De forma predeterminada, el propio Windows PowerShell distingue mayúsculas de minúsculas. Sin embargo, como trata con muchos sistemas preexistentes, Windows PowerShell conserve el caso para facilidad de operación y compatibilidad. En otras palabras, si se proporciona un carácter en mayúsculas, Windows PowerShell mantiene en letras mayúsculas. Para que los sistemas funcionan bien, un cmdlet debe seguir esta convención. Si es posible, debería funcionar en una forma de mayúsculas y minúsculas. Sin embargo, debe, conserve el caso original para los cmdlets que se producen más adelante en un comando o en la canalización.

## <a name="see-also"></a>Véase también

[Directrices de desarrollo necesarias](./required-development-guidelines.md)

[Instrucciones de desarrollo de asesoría](./advisory-development-guidelines.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
