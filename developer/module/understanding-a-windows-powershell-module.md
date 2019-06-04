---
title: Descripción de un módulo de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4e38235-9987-4347-afd2-0f7d1dc8f64a
caps.latest.revision: 19
ms.openlocfilehash: cff50d415c4c90182fa1cf015a5a5ba84d4d613a
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470774"
---
# <a name="understanding-a-windows-powershell-module"></a>Descripción de un módulo de Windows PowerShell

Un *módulo* es un conjunto de funcionalidades relacionadas de Windows PowerShell, agrupados juntos como una unidad práctica (que normalmente se guardan en un único directorio). Definiendo un conjunto de archivos de script relacionado, los ensamblados y los recursos relacionados como un módulo, puede hacer referencia a, cargar, conservar y compartir el código mucho más fácil de lo que lo haría en caso contrario.

El propósito principal de un módulo es permitir la modularización (es decir, abstracción y reutilización) de código de Windows PowerShell. Por ejemplo, la manera más sencilla de crear un módulo es simplemente guardar un script de Windows PowerShell como un archivo. psm1. Lo hace al control (es decir, hacer público o privado) las funciones y variables contenidas en la secuencia de comandos. Guardar el script como un archivo. psm1 también permite controlar el ámbito de ciertas variables. Por último, también puede usar cmdlets como [Install-Module](/powershell/module/PowershellGet/Install-Module) para organizar, instalar y usar la secuencia de comandos como bloques de creación de soluciones más grandes.

## <a name="module-components-and-types"></a>Tipos y los componentes del módulo

Un módulo está formado por cuatro componentes básicos:

1. Algún tipo de archivo de código, normalmente, un script de PowerShell o un ensamblado administrado de cmdlet.

2. Cualquier otra cosa que el archivo de código anterior, es posible que necesita, como ensamblados adicionales, ayudan a los archivos o secuencias de comandos.

3. Un archivo de manifiesto que describe los archivos anteriores, así como también almacena metadatos como la información de autor y el control de versiones...

4. Un directorio que contiene todo el contenido anterior y se encuentra donde PowerShell razonablemente puedan encontrarlo.

   Tenga en cuenta que ninguno de estos componentes, por sí mismos, son realmente necesario. Por ejemplo, un módulo técnicamente puede ser solo un script almacenado en un archivo. psm1. También puede tener un módulo que no es más que un archivo de manifiesto, que se usa principalmente por motivos organizativos. También puede escribir un script que crea dinámicamente un módulo y, por lo tanto no necesita realmente un directorio para almacenar cualquier cosa en. Las siguientes secciones describen los tipos de módulos que se puede obtener combinar y hacer coincidir las posibles distintas partes de un módulo juntos.

### <a name="script-modules"></a>Módulos de script

Como el nombre implica, un *módulo de script* es un archivo (. psm1) que contiene cualquier código válido de Windows PowerShell. Los administradores y desarrolladores de script pueden usar este tipo de módulo para crear módulos cuyos miembros incluyen funciones, variables y mucho más. En esencia, un módulo de script es simplemente un script de Windows PowerShell con una extensión distinta, que permite a los administradores usar funciones de importación, exportación y la administración en él.

Además, puede usar un archivo de manifiesto para incluir otros recursos en el módulo, como archivos de datos, otros módulos dependientes o scripts en tiempo de ejecución. Los archivos de manifiesto también son útiles para el seguimiento de los metadatos, como información de creación y control de versiones.

Por último, un módulo de script, como cualquier otro módulo que no se crea dinámicamente, debe guardarse en una carpeta que PowerShell razonablemente puede detectar. Normalmente, esto es en la ruta de acceso del módulo de PowerShell; pero si es necesario puede describir explícitamente donde está instalado el módulo. Para obtener más información, consulte [cómo escribir un módulo de Script de PowerShell](./how-to-write-a-powershell-script-module.md).

### <a name="binary-modules"></a>Módulos binarios

Un *módulo binario* es un ensamblado de .NET Framework (.dll) que contiene código compilado, como C#. Los desarrolladores de cmdlet pueden usar este tipo de módulo para compartir los cmdlets, proveedores y mucho más. (Los complementos existentes también se usa como módulos binarios.) En comparación con un módulo de script, un módulo binario le permite crear cmdlets que son más rápidos o usar las características (como multithreading) que no son tan fáciles de código en los scripts de Windows PowerShell.

Como con los módulos de script, puede incluir un archivo de manifiesto describen recursos adicionales que usa el módulo y realizar un seguimiento de los metadatos sobre el módulo. De forma similar, probablemente debería instalar el módulo binario en una carpeta en algún lugar a lo largo de la ruta de acceso del módulo de PowerShell. Para obtener más información, vea cómo [cómo escribir un módulo binario PowerShell](./how-to-write-a-powershell-binary-module.md).

### <a name="manifest-modules"></a>Módulos de manifiesto

Un *módulo del manifiesto* es un módulo que utiliza un archivo de manifiesto para describir todos sus componentes, pero no tiene ningún tipo de ensamblado principal o el script. (Formalmente, sale de un módulo de manifiesto la `ModuleToProcess` o `RootModule` elemento del manifiesto vacío.) Sin embargo, todavía puede usar otras características de un módulo, como la capacidad de cargar los ensamblados dependientes o ejecutar automáticamente algunas secuencias de comandos previas al procesamiento. También puede usar un módulo de manifiesto como una manera cómoda para empaquetar los recursos que se va a usar otros módulos, como módulos anidados, ensamblados, tipos o formatos. Para obtener más información, consulte [cómo escribir un manifiesto del módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).

### <a name="dynamic-modules"></a>Módulos dinámicos

Un *módulo dinámico* es un módulo que no está cargado o guardado en un archivo. En su lugar, se crean dinámicamente mediante una secuencia de comandos, utilizando el [New-Module](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet. Este tipo de módulo permite una secuencia de comandos crear un módulo a petición que no es necesario cargar o guardar en un almacenamiento persistente. Por su naturaleza, un módulo dinámico está pensado para ser de corta duración y, por lo tanto, no puede tener acceso el `Get-Module` cmdlet. De forma similar, que normalmente no necesitan los manifiestos del módulo, tampoco es probable que necesitan permanentes carpetas para almacenar sus ensamblados relacionados.

## <a name="module-manifests"></a>Manifiestos del módulo

Un *manifiesto del módulo* es un archivo. psd1 que contiene una tabla hash. Las claves y valores en la tabla hash realice lo siguiente:

- Describir el contenido y los atributos del módulo.

- Definir los requisitos previos.

- Determinar cómo se procesan los componentes.

  No es obligatorio que un módulo tenga manifiestos. Módulos pueden hacer referencia a los archivos de script (. ps1), archivos de módulo (. psm1), los archivos de manifiesto (. psd1), formato de script y escriba archivos (. ps1xml), cmdlet y proveedor de ensamblados (.dll), archivos de recursos, archivos de ayuda, archivos de localización o cualquier otro tipo de archivo o recurso que se incluye como parte del módulo. Para ver un script de uso internacional, la carpeta del módulo también contiene un conjunto de archivos de catálogo de mensajes. Si agrega un archivo de manifiesto a la carpeta del módulo, puede hacer referencia a los diversos archivos como una sola unidad haciendo referencia el manifiesto.

  El propio manifiesto describe las siguientes categorías de información:

- Metadatos acerca del módulo, como el número de versión del módulo, el autor y la descripción.

- Requisitos previos necesarios para importar el módulo, como la versión de Windows PowerShell, la versión de common language runtime (CLR) y los módulos necesarios.

- Procesamiento de directivas, como los scripts, formatos y tipos para procesar.

- Restricciones en los miembros del módulo para exportar, por ejemplo, el alias, funciones, variables y los cmdlets para exportar.

  Para obtener más información, consulte [cómo escribir un manifiesto del módulo de PowerShell](./how-to-write-a-powershell-module-manifest.md).

## <a name="storing-and-installing-a-module"></a>Almacenamiento y la instalación de un módulo

Una vez haya creado una secuencia de comandos, binario o de manifiesto de módulo, puede guardar su trabajo en una ubicación que otros usuarios pueden acceder a él. Por ejemplo, el módulo puede almacenarse en la carpeta donde está instalado Windows PowerShell, o puede almacenarse en una carpeta de usuario del sistema.

Por lo general, puede determinar dónde debe instalar el módulo mediante una de las rutas de acceso almacenadas en el `$ENV:PSModulePath` variable. Utilizando una de estas rutas de acceso significa que PowerShell puede detectar y cargar el módulo cuando un usuario realiza una llamada a él en su código. Si almacena el módulo en otro lugar, puede explícitamente informar a PowerShell pasando la ubicación de su módulo como un parámetro al llamar a `Install-Module`.

No obstante, la ruta de acceso de la carpeta se conoce como el *base* del módulo (ModuleBase) y el nombre de la secuencia de comandos, el archivo de módulo binario o manifiesto debe ser el mismo que el nombre de carpeta del módulo, con las siguientes excepciones:

- Módulos dinámicos que se crean mediante el `New-Module` cmdlet puede llamarse mediante el `Name` parámetro del cmdlet.

- Módulos importados desde los objetos de ensamblado por el  **`Import-Module` -ensamblado** comando se nombran según la siguiente sintaxis: `"dynamic_code_module_" + assembly.GetName()`.

  Para obtener más información, consulte [instalar un módulo de PowerShell](./installing-a-powershell-module.md) y [modificar la ruta de instalación PSModulePath](./modifying-the-psmodulepath-installation-path.md).

## <a name="module-cmdlets-and-variables"></a>Las variables y los Cmdlets del módulo

Los cmdlets y las variables siguientes se proporcionan mediante Windows PowerShell para la creación y administración de módulos.

[Nuevo módulo](/powershell/module/Microsoft.PowerShell.Core/New-Module) cmdlet este cmdlet crea un nuevo módulo dinámico que existe en la memoria. El módulo se crea a partir de un bloque de script y sus miembros exportados, como las funciones y variables, están inmediatamente disponibles en la sesión y permanecen disponibles hasta que se cierre la sesión.

[Nuevo-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet este cmdlet crea un nuevo archivo de manifiesto (. psd1) del módulo, rellena los valores y guarda el archivo de manifiesto en la ruta de acceso especificada. También se puede usar este cmdlet para crear una plantilla de manifiesto de módulo que se puede rellenar manualmente.

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet este cmdlet agrega uno o más módulos a la sesión actual.

[Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet este cmdlet recupera información acerca de los módulos que se importaron o que pueden importarse en la sesión actual.

[Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) cmdlet este cmdlet especifica los miembros del módulo (por ejemplo, los cmdlets, funciones, variables y alias) que se exportan desde un archivo de módulo (. psm1) de la secuencia de comandos o desde un módulo dinámico creado mediante el `New-Module` cmdlet.

[Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) cmdlet este cmdlet quita módulos de la sesión actual.

[Test-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest) cmdlet este cmdlet comprueba que un manifiesto de módulo describe con precisión los componentes de un módulo mediante la comprobación de que los archivos que aparecen en el archivo de manifiesto de módulo (. psd1) existen realmente en las rutas de acceso especificadas.

$PSScriptRoot esta variable contiene el directorio desde el que se está ejecutando el módulo de script. Permite que las secuencias de comandos usar la ruta de acceso del módulo para tener acceso a otros recursos.

$env: PSModulePath esta variable de entorno contiene una lista de los directorios en que PowerShell de Windows se almacenan los módulos. Windows PowerShell usa el valor de esta variable al importar módulos automáticamente y actualizar los temas de ayuda para módulos.

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
