# Preguntas más frecuentes

## ¿Qué es un módulo de PowerShell?

Un módulo de PowerShell es un paquete reutilizable que contiene algunas funciones de PowerShell. Todo el contenido de PowerShell (funciones, variables, recursos de DSC, etc.) se puede empaquetar en módulos. Normalmente, los módulos son carpetas que contienen tipos específicos de archivos almacenados en una ruta de acceso específica. Existen varios tipos distintos de módulos de PowerShell.

## ¿Qué es un script de PowerShell?

Un script de PowerShell es una serie de comandos que se almacenan en un archivo .ps1 para permitir la reutilización y el uso compartido. Los flujos de trabajo de PowerShell también son scripts de PowerShell, que describen un conjunto de tareas y proporcionan la secuenciación de dichas tareas. Para obtener más información, consulte [Introducción al flujo de trabajo de Windows PowerShell](https://technet.microsoft.com/en-us/library/jj134242.aspx).

## ¿En qué se diferencian los scripts de PowerShell de los módulos de PowerShell?

Los módulos suelen ser mejores para compartir, pero hemos habilitado el uso compartido de scripts para que le resulte más fácil contribuir con flujos de trabajo y scripts a la comunidad. Para obtener más información, consulte los blogs siguientes:

- [Don't Write Scripts, Write PowerShell Modules (No escriba scripts, escriba módulos de PowerShell)](http://blogs.technet.com/b/heyscriptingguy/archive/2011/06/27/don-t-write-scripts-write-powershell-modules.aspx)
- [Understanding PowerShell Modules (Descripción de los módulos de PowerShell)](http://blogs.technet.com/b/heyscriptingguy/archive/2015/07/10/understanding-powershell-modules.aspx)

## ¿Cómo puedo publicar en la Galería de PowerShell?

Debe registrar una cuenta en la Galería de PowerShell para poder publicar elementos en la Galería. Esto se debe a que la publicación de elementos requiere una clave NuGetApiKey, que se proporciona tras el registro. Para registrarse, inicie sesión con su cuenta personal, profesional o educativa en la Galería de PowerShell. Al iniciar sesión por primera vez, es necesario un proceso de registro único. Después, tendrá la clave NuGetApiKey disponible en su página de perfil.

Una vez que se haya registrado en la Galería, use los cmdlets [Publish-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) o [Publish-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) para publicar el elemento en la Galería. Para obtener más detalles sobre cómo ejecutar estos cmdlets, visite la pestaña Publicar o lea la documentación sobre [Publish-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) y [Publish-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

**No es necesario registrarse o iniciar sesión en la Galería para instalar o guardar elementos.**

## He recibido el error "Failed to process request. 'The specified API key is invalid or does not have permission to access the specified package.'. The remote server returned an error: (403) Forbidden" (Error al procesar la solicitud. 'La clave de API especificada no es válida o no tiene permiso para acceder al paquete especificado'. Error en el servidor remoto: (403) Prohibido") al intentar publicar un elemento en la Galería de PowerShell. ¿Qué significa?

Este error puede producirse por los motivos siguientes:

- **La clave de API especificada no es válida.**
     Asegúrese de que ha especificado la clave de API válida de su cuenta. Para obtener la clave API, consulte su página de perfil.
- **Usted no es el propietario del nombre de elemento especificado.**
     Si ha confirmado que la clave de API es correcta, puede que ya exista un elemento con el mismo nombre que el que está intentando usar. Es posible que el propietario haya quitado el elemento de la lista, en cuyo caso no aparecerá en los resultados de la búsqueda. Para determinar si ya existe un elemento con el mismo nombre, abra un explorador y vaya a la página de detalles del elemento: `https://www.powershellgallery.com/packages/<itemName>`. Por ejemplo, si va directamente a `https://www.powershellgallery.com/packages/pester`, se le dirigirá a la página de detalles del módulo Pester, tanto si lo han quitado de la lista como si no. Si existe un elemento con un nombre en conflicto y se ha quitado de la lista, puede hacer lo siguiente:
    - Seleccionar otro nombre para el elemento.
    - Ponerse en contacto con los propietarios del elemento existente.

## ¿Por qué no puedo iniciar sesión con mi cuenta personal, si ayer podía hacerlo?

Tenga en cuenta que la cuenta de la Galería no se adapta a los cambios que se produzcan en el alias de su correo electrónico principal. Para obtener más información, consulte el tema sobre los [alias de correo electrónico de Microsoft](http://windows.microsoft.com/en-us/windows/outlook/add-alias-account).

## ¿Por qué no veo todos los elementos de la Galería al activar todas las casillas de categoría en la pestaña Elementos?

Al seleccionar una casilla de categoría, lo que indica es que quiere ver todos los elementos de esa categoría. Solo se mostrarán los elementos de las categorías seleccionadas. Del mismo modo, al seleccionar todas las casillas de categoría, lo que indica es que quiere ver todos los elementos de cualquier categoría. Pero algunos elementos de la Galería no pertenecen a ninguna de las categorías de la lista, por lo que no aparecerán en los resultados. Para ver todos los elementos de la galería, desactive todas las categorías o vuelva a seleccionar la pestaña Elementos.

## ¿Cuáles son los requisitos para publicar un módulo en la Galería de PowerShell?

Se puede publicar cualquier tipo de módulo de PowerShell (módulos de script, módulos binarios o módulos de manifiesto) en la Galería. Para publicar un módulo, PowerShellGet necesita cierta información sobre él: la versión, la descripción, el autor y la licencia. Esta información se lee como parte del proceso de publicación en el archivo de *manifiesto de módulo* (.psd1) o en el valor del parámetro **LicenseUri** del cmdlet [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Todos los módulos publicados en la Galería deben tener manifiestos de módulo. Pueden publicarse en la Galería todos los módulos que incluyan la siguiente información en su manifiesto:

- Version
- Descripción
- Autor
- Un URI a los términos de licencia del módulo, como parte de la sección **PrivateData** del manifiesto o en el parámetro **LicenseUri** del cmdlet [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## ¿Cómo se crea un manifiesto de módulo con el formato correcto?

La manera más fácil de crear un manifiesto de módulo es ejecutar el cmdlet [**New-ModuleManifest**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). En PowerShell 5.0 o versiones posteriores, New-ModuleManifest genera un manifiesto de módulo con el formato correcto con campos en blanco para metadatos útiles, como **ProjectUri**, **LicenseUri** y **Tags**. Basta con rellenar los espacios en blanco o usar el manifiesto generado como un ejemplo de formato correcto.

Para comprobar que se han rellenado correctamente todos los campos de metadatos necesarios, use el cmdlet [**Test-ModuleManifest**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

Para actualizar los campos del archivo de manifiesto de módulo, use el cmdlet [**Update-ModuleManifest**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## ¿Cuáles son los requisitos para publicar un script en la Galería?

Se puede publicar cualquier tipo de script de PowerShell (scripts o flujos de trabajo) en la Galería. Para publicar un script, PowerShellGet necesita cierta información sobre él: la versión, la descripción, el autor y la licencia. Esta información se lee como parte del proceso de publicación en la sección *PSScriptInfo* del archivo de script o en el valor del parámetro **LicenseUri** del cmdlet [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Todos los scripts publicados en la Galería deben tener información de metadatos. Pueden publicarse en la Galería todos los scripts que incluyan la siguiente información en la sección PSScriptInfo:

- Version
- Descripción
- Autor
- Un URI a los términos de licencia del script, como parte de la sección **PSScriptInfo** del script o en el parámetro **LicenseUri** del cmdlet [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## ¿Cómo se realiza una búsqueda?

Escriba lo que quiere buscar en el cuadro de texto. Por ejemplo, si quiere encontrar módulos relacionados con SQL de Azure, escriba "sql de azure". Nuestro motor de búsqueda buscará esas palabras clave en todos los artículos publicados, incluidos los títulos, las descripciones y los metadatos. Después, en función de una puntuación de calidad ponderada, mostrará las coincidencias más cercanas. También puede buscar por campo específico usando la sintaxis field:"value" en la consulta de búsqueda para los campos siguientes:

- Etiquetas
- Funciones
- Cmdlets
- DscResources
- PowerShellVersion

Por ejemplo, cuando busque PowerShellVersion:"2.0", solo se mostrarán los resultados compatibles con PowerShellVersion 2.0 (en función de su manifiesto de módulo o script).

## ¿Cómo se crea un archivo de script con el formato correcto?

La manera más fácil de crear un archivo de script con el formato correcto es ejecutar el cmdlet [**New-ScriptFileInfo**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). En PowerShell 5.0, New-ScriptFileInfo genera un archivo de script con el formato correcto con campos en blanco para metadatos útiles, como **ProjectUri**, **LicenseUri** y **Tags**. Basta con rellenar los espacios en blanco o usar el archivo de script generado como un ejemplo de formato correcto.

Para comprobar que se han rellenado correctamente todos los campos de metadatos necesarios, use el cmdlet [**Test-ScriptFileInfo**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

Para actualizar los campos de metadatos del script, use el cmdlet [**Update-ScriptFileInfo**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## ¿Qué otros tipos de módulos de PowerShell existen?

El término "módulo de PowerShell" también hace referencia a los archivos que implementan la funcionalidad real. Los archivos de módulo de script (.psm1) contienen código de PowerShell. Los archivos de módulo binario (.dll) contienen código compilado.

Podría decirse que la carpeta que encapsula el módulo es la carpeta de módulo. La carpeta de módulo puede contener un manifiesto de módulo (.psd1) que describe el contenido de la carpeta. Los archivos que realmente realizan el trabajo son los archivos de módulo de script (.psm1) y los archivos de módulo binario (.dll). Los recursos de DSC se encuentran en una subcarpeta específica y se implementan como archivos de módulo de script o archivos de módulo binario.

Todos los módulos de la Galería contienen manifiestos de módulo y la mayoría de estos módulos contienen archivos de módulo de script o archivos de módulo binario. El término "módulo" puede resultar confuso debido a estos significados diferentes. A menos que se indique explícitamente lo contrario, siempre que se use la palabra "módulo" en esta página se hace referencia a la carpeta de módulo que contiene estos archivos.

## ¿Cómo se relaciona PackageManagement con PowerShellGet? (Respuesta de alto nivel)

PackageManagement es una interfaz común para trabajar con cualquier administrador de paquetes. Con el tiempo, tanto si trabaja con módulos de PowerShell como con MSI, RubyGems, paquetes de NuGet o módulos Perl, debería poder usar comandos de PackageManagement (Find-Package e Install-Package) para buscarlos e instalarlos. Para ello, PackageManagement dispone de un proveedor de paquete para cada administrador de paquetes que se conecta a PackageManagement. Los proveedores llevan a cabo el trabajo real, ya que capturan contenido de los repositorios y lo instalan localmente. A menudo, los proveedores de paquetes simplemente se ajustan en torno a las herramientas del administrador de paquetes existente de un tipo de paquete determinado.

PowerShellGet es el administrador de paquetes de los elementos de PowerShell. Hay un proveedor de paquete de PSModule que expone la funcionalidad de PowerShellGet a través de PackageManagement. Por esta razón, puede ejecutar [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) o Install-Package -Provider PSModule para instalar un módulo desde la Galería de PowerShell. No se puede acceder a ciertas funciones de PowerShellGet, como [Update-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) y [Publish-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), a través de comandos de PackageManagement.

En resumen, PowerShellGet se centra únicamente en ofrecer una experiencia premium de administración de paquetes para el contenido de PowerShell, mientras que PackageManagement se centra en exponer todas las experiencias de administración de paquetes a través de un conjunto general de herramientas. Si esta respuesta no le satisface, encontrará una respuesta larga en la parte inferior de este documento, en la sección **¿Cómo se relaciona realmente PackageManagement con PowerShellGet?**

Para obtener más información, visite la [página del proyecto PackageManagement](http://oneget.org/).

## ¿Cómo se relaciona NuGet con PowerShellGet?

La Galería de PowerShell es una versión modificada de la [Galería de NuGet](http://www.nuget.org/). PowerShellGet usa el proveedor de NuGet para trabajar con repositorios basados en NuGet, como la Galería de PowerShell.

Puede usar PowerShellGet con cualquier recurso compartido de archivos o repositorio de NuGet válidos. Basta con agregar el repositorio mediante la ejecución del cmdlet [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## ¿Eso significa que puedo usar NuGet.exe para trabajar con la Galería?

Sí.

## ¿Cómo se relaciona realmente PackageManagement con PowerShellGet? (Detalles técnicos)

En lo relativo a los aspectos técnicos, PowerShellGet aprovecha en gran medida la infraestructura de PackageManagement.

En la capa de cmdlet de PowerShell, [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) es en realidad un contenedor fino alrededor de Install-Package -Provider PSModule.

En la capa de proveedor de paquete de PackageManagement, el proveedor de paquete de PSModule llama a otros proveedores de paquete de PackageManagement. Por ejemplo, si trabaja con galerías basadas en NuGet (como la Galería de PowerShell), el proveedor de paquete de PSModule usa el proveedor de paquete de NuGet para trabajar con el repositorio.

![Arquitectura de PowerShellGet](Images/powershellgetArchitecture.png)

Ilustración 1: Arquitectura de PowerShellGet

## ¿Qué es necesario para ejecutar PowerShellGet?

En general, se recomienda seleccionar la versión más reciente del módulo PowerShellGet (tenga en cuenta que requiere .NET 4.5).

El módulo **PowerShellGet** requiere **PowerShell 3.0 o posterior**.

Por lo tanto, **PowerShellGet** requiere uno de los siguientes sistemas operativos:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** también requiere .NET Framework 4.5 o posterior. Puede instalar .NET Framework 4.5 o posterior desde [aquí](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).

## ¿Es posible reservar nombres para los elementos que se publicarán en el futuro?

No es posible apropiarse de nombres de elemento. Si cree que un elemento existente ha tomado un nombre que se adapta mejor a su elemento, intente [ponerse en contacto con el propietario del elemento](psgallery_contacting_item_owners.md). Si no recibe respuesta en un par de semanas, póngase en contacto con el soporte técnico y el equipo de la Galería de PowerShell le echará un vistazo al asunto.

## ¿Cómo reclamo la propiedad de un elemento?

Consulte [Administrar propietarios de elementos en PowerShellGallery.com](Managing-Item-Owners.md) para obtener más información.

## ¿Cómo actúo en caso de que el propietario de un elemento infrinja la licencia de mi elemento?

Recomendamos que la comunidad de PowerShell colabore para resolver los conflictos que puedan surgir entre los propietarios de elementos.  Hemos diseñado un [proceso de resolución de conflictos](psgallery_dispute_resolution.md) que le pedimos que siga antes de que tengan que intervenir los administradores de PowerShellGallery.com.

<!--HONumber=Aug16_HO3-->


