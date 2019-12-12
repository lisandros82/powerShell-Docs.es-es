---
title: Descripción de un módulo de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: b42ba6b2bf42a74213eb78f2db22e16de7e90583
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360644"
---
# <a name="understanding-a-windows-powershell-module"></a>Descripción de un módulo de Windows PowerShell

Un *módulo* es un conjunto de funcionalidades relacionadas con Windows PowerShell, agrupadas como una unidad cómoda (normalmente guardada en un solo directorio). Al definir un conjunto de archivos de scripts relacionados, ensamblados y recursos relacionados como módulo, puede hacer referencia, cargar, conservar y compartir el código mucho más fácilmente de lo contrario.

El propósito principal de un módulo es permitir la modularización (es decir, la reutilización y la abstracción) del código de Windows PowerShell. Por ejemplo, la forma más sencilla de crear un módulo es simplemente guardar un script de Windows PowerShell como un archivo. psm1. Esto le permite controlar (es decir, hacer público o privado) las funciones y las variables contenidas en el script. Guardar el script como un archivo. psm1 también le permite controlar el ámbito de ciertas variables. Por último, también puede usar cmdlets como [install-Module](/powershell/module/PowershellGet/Install-Module) para organizar, instalar y usar el script como bloques de creación para soluciones de mayor tamaño.

## <a name="module-components-and-types"></a>Componentes y tipos de módulo

Un módulo se compone de cuatro componentes básicos:

1. Algún tipo de archivo de código, normalmente un script de PowerShell o un ensamblado de cmdlet administrado.

2. Cualquier cosa que pueda necesitar el archivo de código anterior, como ensamblados adicionales, archivos de ayuda o scripts.

3. Un archivo de manifiesto que describe los archivos anteriores, así como almacenar metadatos, como la información de creación y control de versiones.

4. Directorio que contiene todo el contenido anterior y se encuentra donde PowerShell puede encontrarlo de forma razonable.

   Tenga en cuenta que ninguno de estos componentes es realmente necesario. Por ejemplo, un módulo puede ser técnicamente solo un script almacenado en un archivo. psm1. También puede tener un módulo que no sea ningún archivo de manifiesto, que se usa principalmente para fines organizativos. También puede escribir un script que cree un módulo de forma dinámica y, por lo tanto, no necesita un directorio en el que almacenar nada. En las secciones siguientes se describen los tipos de módulos que puede obtener combinando y coincidentes entre las distintas partes posibles de un módulo.

### <a name="script-modules"></a>Módulos de script

Como su nombre implica, un *módulo de script* es un archivo (. psm1) que contiene cualquier código válido de Windows PowerShell. Los desarrolladores y administradores de scripts pueden usar este tipo de módulo para crear módulos cuyos miembros incluyen funciones, variables, etc. En esencia, un módulo de script es simplemente un script de Windows PowerShell con una extensión diferente, que permite a los administradores usar funciones de importación, exportación y administración en él.

Además, puede usar un archivo de manifiesto para incluir otros recursos en el módulo, como archivos de datos, otros módulos dependientes o scripts en tiempo de ejecución. Los archivos de manifiesto también son útiles para realizar el seguimiento de metadatos, como la creación y la información de control de versiones.

Por último, un módulo de script, como cualquier otro módulo que no se haya creado dinámicamente, debe guardarse en una carpeta que PowerShell pueda detectar de forma razonable. Normalmente, se encuentra en la ruta de acceso del módulo de PowerShell; pero si es necesario, puede describir explícitamente Dónde está instalado el módulo. Para obtener más información, vea [Cómo escribir un módulo de script de PowerShell](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Módulos binarios

Un *módulo binario* es un ensamblado de .NET Framework (. dll) que contiene código compilado C#, como. Los desarrolladores de cmdlets pueden usar este tipo de módulo para compartir cmdlets, proveedores y mucho más. (Los complementos existentes también se pueden usar como módulos binarios). En comparación con un módulo de script, un módulo binario le permite crear cmdlets que son más rápidos o usan características (como multithreading) que no son tan fáciles de codificar en scripts de Windows PowerShell.

Al igual que con los módulos de script, puede incluir un archivo de manifiesto para describir los recursos adicionales que usa el módulo y para realizar un seguimiento de los metadatos sobre el módulo. Del mismo modo, es probable que deba instalar el módulo binario en una carpeta en algún lugar de la ruta de acceso del módulo de PowerShell. Para obtener más información, vea cómo [escribir un módulo binario de PowerShell](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Módulos del manifiesto

Un *módulo de manifiesto* es un módulo que utiliza un archivo de manifiesto para describir todos sus componentes, pero no tiene ningún tipo de ensamblado o script básico. (Formalmente, un módulo de manifiesto deja vacío el elemento `ModuleToProcess` o `RootModule` del manifiesto). Sin embargo, todavía puede usar las otras características de un módulo, como la capacidad de cargar ensamblados dependientes o ejecutar automáticamente ciertas secuencias de comandos previas al procesamiento. También puede usar un módulo de manifiesto como una manera cómoda de empaquetar los recursos que otros módulos van a usar, como los módulos anidados, los ensamblados, los tipos o los formatos. Para obtener más información, vea [Cómo escribir un manifiesto del módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Módulos dinámicos

Un *módulo dinámico* es un módulo que no se carga o se guarda en un archivo. En su lugar, se crean de forma dinámica mediante un script, mediante el cmdlet [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) . Este tipo de módulo permite que un script cree un módulo a petición que no es necesario cargar o guardar en el almacenamiento persistente. Por su naturaleza, un módulo dinámico está pensado para ser de corta duración y, por lo tanto, el cmdlet `Get-Module` no puede acceder a él. De forma similar, normalmente no necesitan manifiestos de módulo, ni probablemente necesitan carpetas permanentes para almacenar sus ensamblados relacionados.

## <a name="module-manifests"></a>Manifiestos de módulo

Un *manifiesto de módulo* es un archivo. psd1 que contiene una tabla hash. Las claves y los valores de la tabla hash hacen lo siguiente:

- Describa el contenido y los atributos del módulo.

- Defina los requisitos previos.

- Determine cómo se procesan los componentes.

  No es obligatorio que un módulo tenga manifiestos. Los módulos pueden hacer referencia a archivos de script (. PS1), archivos de módulo de script (. psm1), archivos de manifiesto (. psd1), archivos de formato y de tipo (. ps1xml), ensamblados de cmdlets y proveedores (. dll), archivos de recursos, archivos de ayuda, archivos de localización o cualquier otro tipo de archivo o recurso que se incluye como parte del módulo. En el caso de un script internacionalizado, la carpeta del módulo también contiene un conjunto de archivos de catálogo de mensajes. Si agrega un archivo de manifiesto a la carpeta del módulo, puede hacer referencia a varios archivos como una sola unidad haciendo referencia al manifiesto.

  El manifiesto describe las siguientes categorías de información:

- Metadatos sobre el módulo, como el número de versión del módulo, el autor y la descripción.

- Requisitos previos necesarios para importar el módulo, como la versión de Windows PowerShell, la versión de Common Language Runtime (CLR) y los módulos necesarios.

- Directivas de procesamiento, como los scripts, los formatos y los tipos que se van a procesar.

- Restricciones en los miembros del módulo que se van a exportar, como los alias, las funciones, las variables y los cmdlets que se van a exportar.

  Para obtener más información, vea [Cómo escribir un manifiesto del módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Almacenar e instalar un módulo

Una vez que haya creado un módulo de script, binario o de manifiesto, puede guardar el trabajo en una ubicación a la que otros usuarios puedan acceder. Por ejemplo, el módulo se puede almacenar en la carpeta del sistema donde está instalado Windows PowerShell, o bien se puede almacenar en una carpeta de usuario.

Por lo general, puede determinar dónde debe instalar el módulo mediante el uso de una de las rutas de acceso almacenadas en la variable `$ENV:PSModulePath`. El uso de una de estas rutas de acceso significa que PowerShell puede buscar y cargar automáticamente el módulo cuando un usuario realiza una llamada a él en su código. Si almacena el módulo en otra parte, puede permitir explícitamente que PowerShell lo sepa pasando la ubicación del módulo como parámetro al llamar a `Install-Module`.

Independientemente de la ruta de acceso de la carpeta se conoce como la *base* del módulo (ModuleBase), y el nombre del archivo de módulo de script, binario o de manifiesto debe ser el mismo que el nombre de la carpeta de módulos, con las siguientes excepciones:

- Los módulos dinámicos creados por el cmdlet `New-Module` se pueden denominar mediante el parámetro `Name` del cmdlet.

- Los módulos importados desde objetos de ensamblado mediante el comando **`Import-Module`-Assembly** se denominan según la sintaxis siguiente: `"dynamic_code_module_" + assembly.GetName()`.

  Para obtener más información, vea [instalar un módulo de PowerShell](./installing-a-powershell-module.md) y [modificar la ruta de instalación de PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Cmdlets de módulo y variables

Windows PowerShell proporciona los siguientes cmdlets y variables para la creación y administración de módulos.

Cmdlet [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) este cmdlet crea un nuevo módulo dinámico que solo existe en la memoria. El módulo se crea a partir de un bloque de script, y sus miembros exportados, como sus funciones y variables, están inmediatamente disponibles en la sesión y permanecen disponibles hasta que se cierra la sesión.

Cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) este cmdlet crea un nuevo archivo de manifiesto de módulo (. psd1), rellena sus valores y guarda el archivo de manifiesto en la ruta de acceso especificada. Este cmdlet también se puede usar para crear una plantilla de manifiesto de módulo que se puede rellenar manualmente.

Cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) este cmdlet agrega uno o más módulos a la sesión actual.

Cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) este cmdlet recupera información sobre los módulos que se han importado o que se pueden importar a la sesión actual.

Cmdlet [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) este cmdlet especifica los miembros del módulo (por ejemplo, cmdlets, funciones, variables y alias) que se exportan desde un archivo de módulo de script (. psm1) o desde un módulo dinámico creado mediante el cmdlet `New-Module`.

Cmdlet [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) este cmdlet quita los módulos de la sesión actual.

Cmdlet [Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) este cmdlet comprueba que un manifiesto de módulo describe con precisión los componentes de un módulo comprobando que los archivos que se enumeran en el archivo de manifiesto del módulo (. psd1) existen realmente en las rutas de acceso especificadas.

$PSScriptRoot esta variable contiene el directorio desde el que se ejecuta el módulo de script. Permite que los scripts usen la ruta de acceso del módulo para acceder a otros recursos.

$env:P SModulePath esta variable de entorno contiene una lista de los directorios en los que se almacenan los módulos de Windows PowerShell. Windows PowerShell usa el valor de esta variable al importar módulos automáticamente y actualizar los temas de ayuda de los módulos.

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
