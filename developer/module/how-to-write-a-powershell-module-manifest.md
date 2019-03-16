---
title: Cómo escribir un manifiesto de módulo de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e082c2e3-12ce-4032-9caf-bf6b2e0dcf81
caps.latest.revision: 23
ms.openlocfilehash: eaa927ec90df6053843f5c942357fed4c7dee966
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059497"
---
# <a name="how-to-write-a-powershell-module-manifest"></a>Cómo escribir un manifiesto de módulo de PowerShell

Una vez se ha escrito el módulo de Windows PowerShell, opcionalmente, puede agregar un manifiesto de módulo. Un manifiesto de módulo es un archivo de script de PowerShell que puede usar para incluir información acerca del módulo. Por ejemplo, puede describir el autor, especifique los archivos del módulo (por ejemplo, los módulos anidados), ejecutar secuencias de comandos para personalizar el entorno del usuario, cargar archivos de formato y tipo, definen los requisitos del sistema y limitan los miembros que exporta el módulo.

## <a name="creating-a-module-manifest"></a>Creación de un manifiesto de módulo

Un *manifiesto del módulo* es un archivo de datos de Windows PowerShell (. psd1) que describe el contenido de un módulo y determina cómo se procesa un módulo. El archivo de manifiesto es un archivo de texto que contiene una tabla hash de claves y valores. Para vincular un archivo de manifiesto a un módulo, asignándole el mismo que el módulo y se coloca en la raíz del directorio de módulo.

Para los módulos simple que contienen solo una. psm1 único o un ensamblado binario, un manifiesto de módulo es opcional. Sin embargo, se recomienda usar un manifiesto de módulo siempre que sea posible, ya que son útiles para ayudarle a organizar el código y para mantener la información de control de versiones. Además, se necesita un manifiesto de módulo para exportar un ensamblado que está instalado en la caché global de ensamblados. Un manifiesto de módulo también es necesario para los módulos que admiten la característica de ayuda actualizable. Es decir, se utiliza la Ayuda actualizable el **HelpInfoUri** clave en el manifiesto del módulo para buscar el archivo de ayuda (HelpInfo XML) de la información que contiene la ubicación de los archivos de Ayuda actualizados para el módulo. Para obtener más información sobre la Ayuda actualizable, consulte [compatibilidad con la Ayuda actualizable](./supporting-updatable-help.md).

### <a name="to-create-and-use-a-module-manifest"></a>Para crear y usar un manifiesto de módulo

1. Para crear un manifiesto de módulo, tiene varias opciones:

   1. Directamente la creación de la tabla hash con la información mínima necesaria y guardarlo en un archivo. psd1 que tiene el mismo nombre que el módulo. Una vez haya hecho esto, puede abrir el archivo y agregar manualmente los valores adecuados.

      `'@{ModuleVersion="1.0"}' > myModuleName.psd1`

   2. O bien, llamar a la [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet con uno o varios de los valores predeterminados que se pasa como parámetros. (Tenga en cuenta que el solo se requiere para generar un manifiesto, pero el nombre del archivo.) Esto creará un manifiesto de módulo con todos los manifiestos valores que proporcionó explícitamente y con el resto que contiene el valor predeterminado adecuado.

      `New-ModuleManifest myModuleName.psd1 -ModuleVersion "2.0" -Author "YourNameHere"`

   3. Por último, también puede crear un archivo. psd1 vacío y copie la plantilla en la parte inferior de este tema en el archivo y rellene los valores pertinentes. El único requisito real en este caso sería asegurarse de que el archivo se denomina el mismo que el módulo.

2. Agregar en cualquier elemento adicional al que desea que estén en el archivo de manifiesto.

   Por lo general, esto probablemente se realizará en cualquier editor de texto que prefiera, como el Bloc de notas. Sin embargo esto es técnicamente un archivo de script que contiene el código, por lo que desea editar en un entorno de scripting o desarrollo real, como PowerShell ISE. De nuevo, tenga en cuenta que todos los elementos de un archivo de manifiesto son opcionales, salvo el número de ModuleVersion.

   Para obtener descripciones de las claves y valores que puede tener un manifiesto de módulo, consulte el **elementos del manifiesto de módulo** a continuación. Para obtener más información, vea las descripciones de parámetros en el [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet.

3. Si lo desea, puede agregar código adicional para el manifiesto de módulo, para tratar los escenarios que no cubiertos por los elementos del manifiesto base del módulo.

   Por motivos de seguridad, PowerShell ejecutará solo un pequeño subconjunto de las operaciones disponibles en un archivo de manifiesto de módulo. Por lo general, puede usar el **si** instrucción, operadores aritméticos y de comparación y los tipos de datos básicos de PowerShell.

4. Una vez haya creado su manifiesto de módulo, puede probarlo (para confirmar que las rutas de acceso se describe en el manifiesto son corrijan) con una llamada a [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest).

   `Test-ModuleManifest myModuleName.psd1`

5. Asegúrese de que el manifiesto de módulo se encuentra en el nivel superior del directorio que contiene el módulo.

   Al copiar el módulo en un sistema e importarlo, PowerShell usará el manifiesto del módulo para importar el módulo.

6. Si lo desea, puede probar directamente el manifiesto de módulo con una llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) por el propio manifiesto la prefijación por puntos.

   `Import-Module .\myModuleName.psd1`

## <a name="module-manifest-elements"></a>Elementos del manifiesto de módulo

En la tabla siguiente se describe los elementos que puede tener un manifiesto de módulo

|Elemento|Valor predeterminado|Descripción|
|-------------|-------------|-----------------|
|RootModule<br /><br /> Tipo: cadena|' '|Módulo o binario módulo archivo de script asociado con este manifiesto. Las versiones anteriores de PowerShell llama a este elemento la ModuleToProcess.<br /><br /> Posibles tipos para el módulo raíz pueden estar vacíos (que hará esto un **manifiesto** módulo), el nombre de un módulo de script (. psm1, lo que hace que esto un **Script** módulo), o el nombre de un módulo binario (.exe o .dll, lo que lo convierte un **binario** módulo). Colocar el nombre de un manifiesto de módulo (. psd1) o un archivo de script (. ps1) en este elemento se producirá un error que se produzca.|
|ModuleVersion<br /><br /> Tipo: cadena|1.0|Número de versión de este módulo. La cadena debe ser capaz de convertir a [System.Version]. Es decir, ' #. #. #. #. #'. `Import-Module` se cargará el primer módulo que se encuentra en la **$psModulePath** que coincide con el nombre y tiene al menos tan alto un ModuleVersion, como el `-MinimumVersion` parámetro. Para importar una versión específica, use el`-RequiredVersion` parámetro, en su lugar.<br /><br /> Ejemplo: `ModuleVersion = '1.0'`|
|GUID<br /><br /> Tipo: cadena|GUID generado automáticamente|Identificador utilizado para identificar de forma única este módulo. Tenga en cuenta que actualmente no se puede importar un módulo por GUID.<br /><br /> Ejemplo: `GUID = 'cfc45206-1e49-459d-a8ad-5b571ef94857'`|
|Autor<br /><br /> Tipo: cadena|Ninguno|Autor de este módulo.<br /><br /> Ejemplo: `Author = 'AuthorNameHere'`|
|CompanyName<br /><br /> Tipo: cadena|Desconocido|La empresa o proveedor de este módulo.<br /><br /> Ejemplo: `CompanyName = 'Fabrikam'`|
|Copyright<br /><br /> Tipo: cadena|(c) [currentYear] [autor]. Todos los derechos reservados.|Declaración de copyright para este módulo.<br /><br /> Ejemplo: `Copyright = '2016 AuthorName. All rights reserved.'`|
|Descripción<br /><br /> Tipo: cadena|' '|Descripción de la funcionalidad proporcionada por este módulo.<br /><br /> Ejemplo: `Description = 'This is a description of a module.'`|
|PowerShellVersion<br /><br /> Tipo: cadena|' '|Versión mínima del motor de Windows PowerShell requerido por este módulo. Valores válidos son 1.0, 2.0, 3.0, 4.0 y 5.0.<br /><br /> Ejemplo: `PowerShellVersion = '5.0'`|
|PowerShellHostName<br /><br /> Tipo: cadena|' '|Especifica el nombre del host de Windows PowerShell que se requiere el módulo. Este nombre se proporciona mediante Windows PowerShell. Para buscar el nombre de un programa host, en el programa, escriba: `$host.name` .<br /><br /> Ejemplo: `PowerShellHostName = 'Windows PowerShell ISE Host'`|
|PowerShellHostVersion<br /><br /> Tipo: cadena|' '|Versión mínima del host de Windows PowerShell requerido por este módulo.<br /><br /> Ejemplo: `PowerShellHostVersion = '2.0'`|
|DotNetFrameworkVersion<br /><br /> Tipo: cadena|' '|Versión mínima de este módulo requiere Microsoft .NET Framework.<br /><br /> Ejemplo: `DotNetFrameworkVersion = '3.5'`|
|CLRVersion<br /><br /> Tipo: cadena|' '|Versión mínima de common language runtime (CLR) requerido por este módulo.<br /><br /> Ejemplo: `CLRVersion = '3.5'`|
|ProcessorArchitecture<br /><br /> Tipo: cadena|' '|Arquitectura de procesador (ninguno, X86, Amd64) requerido por este módulo. Los valores válidos son x86, AMD64, IA64 y None (desconocido o no especificado).<br /><br /> Ejemplo: `ProcessorArchitecture = 'x86'`|
|RequiredModules<br /><br /> Type: [string[]]|@()|Módulos que se deben importar en el entorno global antes de importar este módulo. Esto cargará los módulos que aparecen a menos que ya se han cargado. (Por ejemplo, algunos módulos pueden estar ya cargados por un módulo diferente.). También es posible especificar una versión específica para cargar mediante `RequiredVersion` lugar `ModuleVersion`. Cuando se usa `ModuleVersion` cargará la versión más reciente disponible con un mínimo de la versión especificada.<br /><br /> Ejemplo: `RequiredModules = @(@{ModuleName="myDependentModule", ModuleVersion="2.0",Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`<br /><br /> Ejemplo: `RequiredModules = @(@{ModuleName="myDependentModule", RequiredVersion="1.5",Guid="cfc45206-1e49-459d-a8ad-5b571ef94857"})`|
|RequiredAssemblies<br /><br /> Type: [string[]]|@()|Ensamblados que se deben cargar antes de importar este módulo.<br /><br /> Tenga en cuenta que a diferencia de RequiredModules, PowerShell cargará el RequiredAssemblies si ya no están cargados.|
|ScriptsToProcess<br /><br /> Type: [string[]]|@()|Archivos de script (. ps1) que se ejecutan en el estado de sesión del llamador cuando se importa el módulo. Podría tratarse de la sesión global, estada o, para los módulos anidados, el estado de sesión de otro módulo. Puede usar estas secuencias de comandos para preparar un entorno tal como se puede usar un script de inicio de sesión.<br /><br /> Estos scripts se ejecutan antes de cargar cualquiera de los módulos enumerados en el manifiesto.|
|TypesToProcess<br /><br /> Tipo: [objeto]|@()|Tipo de archivos (. ps1xml) que se cargue al importar este módulo.|
|FormatsToProcess<br /><br /> Tipo: [objeto]|@()|Dar formato a los archivos (. ps1xml) que se cargue al importar este módulo.|
|NestedModules<br /><br /> Tipo: [objeto]|@()|Módulos de importación como módulos anidados del módulo especificado en RootModule/ModuleToProcess.<br /><br /> Adición de un nombre de módulo para este elemento es similar a llamar a `Import-Module` desde dentro del código de script o un ensamblado. La principal diferencia es que resulta más fácil ver lo que va a cargar aquí en el archivo de manifiesto. Además, si un módulo no se puede cargar aquí, no se habrá cargado su módulo real.<br /><br /> Además de otros módulos, también se pueden cargar los archivos de script (. ps1) aquí. Estos archivos se ejecutarán en el contexto del módulo raíz. (Esto es equivalente al punto de abastecimiento de la secuencia de comandos en el módulo raíz).|
|FunctionsToExport<br /><br /> Tipo: Cadena|'*'|Especifica las funciones que exporta el módulo (se permiten caracteres de comodín) al estado de sesión del llamador. De forma predeterminada, se exportan todas las funciones. Puede usar esta clave para restringir las funciones que exportan el módulo.<br /><br /> Estado de sesión del llamador puede ser la sesión global, estada o, para los módulos anidados, el estado de sesión de otro módulo. Cuando se encadenan módulos anidados, se exportarán todas las funciones que exportan un módulo anidado en el estado de sesión global, a menos que un módulo en la cadena restringe la función con la clave FunctionsToExport.<br /><br /> Si el manifiesto también exporta los alias para las funciones, esta clave puede quitar funciones cuyos alias se enumeran en la clave AliasesToExport, pero esta clave no puede agregar los alias de función a la lista.|
|CmdletsToExport<br /><br /> Tipo: Cadena|'*'|Especifica los cmdlets que exporta el módulo (se permiten caracteres de comodín). De forma predeterminada, se exportan todos los cmdlets. Puede usar esta clave para restringir los cmdlets que exporta el módulo.<br /><br /> Estado de sesión del llamador puede ser la sesión global, estada o, para los módulos anidados, el estado de sesión de otro módulo. Cuando se encadena módulos anidados, todos los cmdlets que exporta un módulo anidado se exportarán en última instancia al estado de sesión global, a menos que un módulo en la cadena restringe el cmdlet con la clave CmdletsToExport.<br /><br /> Si el manifiesto también exporta los alias para los cmdlets, esta clave puede quitar los cmdlets cuyos alias se enumeran en la clave AliasesToExport, pero esta clave no puede agregar alias de cmdlet en la lista.|
|VariablesToExport<br /><br /> Tipo: Cadena|'*'|Especifica las variables que exporta el módulo (se permiten caracteres de comodín) al estado de sesión del llamador. De forma predeterminada, se exportan todas las variables. Puede usar esta clave para restringir las variables que exportan el módulo.<br /><br /> Estado de sesión del llamador puede ser la sesión global, estada o, para los módulos anidados, el estado de sesión de otro módulo. Cuando encadena módulos anidados, se exportarán todas las variables que exportan un módulo anidado en el estado de sesión global, a menos que un módulo en la cadena restringe la variable mediante el uso de la clave VariablesToExport.<br /><br /> Si el manifiesto también exporta los alias para las variables, esta clave puede quitar las variables cuyos alias se enumeran en la clave AliasesToExport, pero esta clave no puede agregar alias de variable a la lista.|
|AliasesToExport<br /><br /> Tipo: Cadena|'*'|Especifica los alias que exporta el módulo (se permiten caracteres de comodín) al estado de sesión del llamador. De forma predeterminada, se exportan todos los alias. Puede usar esta clave para restringir los alias que exportan el módulo.<br /><br /> Estado de sesión del llamador puede ser la sesión global, estada o, para los módulos anidados, el estado de sesión de otro módulo. Cuando se encadena módulos anidados, todos los alias que exportan un módulo anidado se exportarán en última instancia al estado de sesión global, a menos que un módulo en la cadena restringe el alias mediante el uso de la clave AliasesToExport.|
|ModuleList<br /><br /> Type: [string[]]|@()|Especifica todos los módulos que se empaquetan con este módulo. Estos módulos se pueden escribir por su nombre (una cadena separada por comas) o como una tabla hash con las claves ModuleName y GUID. La tabla hash puede tener también una clave ModuleVersion opcional. La clave ModuleList está diseñada para que actúe como un inventario de módulo. Estos módulos no se procesarán automáticamente.|
|Lista de archivos<br /><br /> Type: [string[]]|@()|Lista de todos los archivos empaquetados con este módulo. Como con ModuleList, FileList le ayudará a como una lista de inventario y no se procesa en caso contrario.|
|PrivateData<br /><br /> Tipo: [objeto]|' '|Especifica los datos privados que deben pasarse al módulo raíz especificado por la clave RootModule/ModuleToProcess.|
|HelpInfoURI<br /><br /> Tipo: cadena|' '|HelpInfo URI de este módulo.|
|DefaultCommandPrefix<br /><br /> Tipo: cadena|' '|Prefijo predeterminado para los comandos que se exporta desde este módulo. Invalidar el prefijo predeterminado mediante `Import-Module` -prefijo.|

## <a name="sample-module-manifest"></a>Manifiesto de módulo de ejemplo

El manifiesto de módulo de ejemplo siguiente muestra las claves y valores predeterminados en un manifiesto de módulo. En este ejemplo se creó mediante el `New-ModuleManifest` cmdlet de Windows PowerShell 3.0. Al crear varios módulos, puede usar este cmdlet para crear una plantilla de manifiesto que, a continuación, se puede modificar para los distintos módulos.

```powershell
#
# Module manifest for module 'myManifest'
#
# Generated by: User01
#
# Generated on: 1/24/2012
#

@{

# Script module or binary module file associated with this manifest
#RootModule = ''

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = 'd0a9150d-b6a4-4b17-a325-e3a24fed0aa9'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2012 User01. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the Windows PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of the .NET Framework required by this module
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module
FunctionsToExport = '*'

# Cmdlets to export from this module
CmdletsToExport = '*'

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module
AliasesToExport = '*'

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess
# PrivateData = ''

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}

```

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
