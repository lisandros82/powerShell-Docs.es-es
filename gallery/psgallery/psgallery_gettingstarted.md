# Introducción a la Galería de PowerShell

## ¿Qué es la Galería de PowerShell?

La Galería de PowerShell es el repositorio central del contenido de PowerShell.
En ella, encontrará módulos útiles de PowerShell que contienen comandos de PowerShell y los recursos de configuración de estado deseado (DSC). También encontrará scripts de PowerShell (algunos de los cuales pueden contener flujos de trabajo de PowerShell), que describen un conjunto de tareas y proporcionan la secuenciación de dichas tareas.
Algunos de estos elementos son creación de Microsoft y otros son creación de la comunidad de PowerShell.

## Requisitos

Para descargar elementos de la Galería de PowerShell en el sistema, se requiere el módulo [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). A continuación se indica dónde puede encontrar el módulo PowerShellGet. No es necesario iniciar sesión para descargar los elementos de la Galería de PowerShell.

-   [Windows 10](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)
-   [Windows Management Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=398175)
-   [Instalador MSI (para PowerShell 3 y 4)](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

Para funcionar con la Galería de PowerShell, PowerShellGet también requiere el [proveedor de NuGet](http://go.microsoft.com/fwlink/?LinkId=722208). Se le pedirá que instale el proveedor de NuGet automáticamente la primera vez que use PowerShellGet si el proveedor de NuGet no se encuentra en ninguna de las siguientes ubicaciones:

-   $env:ProgramFiles\\PackageManagement\\ProviderAssemblies
-   $env:LOCALAPPDATA\\PackageManagement\\ProviderAssemblies

También puede ejecutar **Install-PackageProvider -Name NuGet -Force** para automatizar la descarga y la instalación del proveedor de NuGet.

  
Si tiene una versión de NuGet anterior a 2.8.5.201, debe llamar a los siguientes cmdlets de PowerShell para instalar la versión más reciente de NuGet y cambiar a dicha versión.

1.  Install-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force
2.  Import-PackageProvider NuGet -MinimumVersion '2.8.5.201' -Force
3.  Elimine la versión anterior de NuGet de la ubicación de instalación anterior.

Para obtener más información, consulte <http://oneget.org/>.

  
Nota: Debido a cambios en los formatos de empaquetado, se recomienda actualizar a la versión más reciente de PowerShellGet y PackageManagement para instalar los elementos que se han actualizado recientemente. PowerShellGet se incluye en Windows 10. Puede obtener más información [aquí](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409).
PowerShellGet también forma parte de Windows Management Framework (WMF) 5.0, que puede descargar [aquí](http://go.microsoft.com/fwlink/?LinkId=398175).

## Detectar elementos de la Galería de PowerShell

Puede buscar elementos en la Galería de PowerShell mediante el control de **búsqueda** en este sitio web o la examinación de las páginas Scripts y Módulos. También puede buscar elementos de la Galería de PowerShell al ejecutar los cmdlets [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) y [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), en función del tipo de elemento, con **-Repository PSGallery**.

Puede filtrar los resultados de la Galería mediante los siguientes parámetros de [Find-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) y [Find-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

- Nombre
- AllVersions
- MinimumVersion
- RequiredVersion
- Etiqueta
- Includes
- DscResource
- RoleCapability
- Comando
- Filtro

Si solo le interesa detectar recursos de DSC específicos en la Galería, puede ejecutar el cmdlet [**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).
[**Find-DscResource**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) devuelve datos sobre los recursos de DSC contenidos en la Galería. Dado que los recursos de DSC siempre se entregan como parte de un módulo, debe ejecutar [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) para instalar dichos recursos de DSC.

## Obtener información sobre los elementos de la Galería de PowerShell

Una vez que haya identificado el elemento que le interesa, tal vez quiera obtener más información. Puede hacerlo examinando la página específica de ese elemento en la Galería. En la página, podrá ver todos los metadatos cargados con el elemento. El autor del elemento es quien proporciona estos metadatos del elemento, que Microsoft no comprueba. El propietario del elemento está estrechamente ligado a la cuenta de la Galería que se usa para publicar el elemento, y es más confiable que el campo Autor.

Si cree que un elemento no se ha publicado de buena fe, haga clic en **Notificar abuso** en la página de ese elemento.

Si está ejecutando [Find-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) o [Find-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), puede ver estos datos en el objeto PSGetModuleInfo devuelto. Por ejemplo, si ejecuta [**Find-Module -Name PSReadLine -Repository PSGallery | Get-Member**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), se devuelven datos en el módulo PSReadLine de la Galería.

## Descargar elementos de la Galería de PowerShell

Se recomienda el proceso siguiente al descargar elementos de la Galería de PowerShell:

### Inspeccionar

Para descargar un elemento de la Galería para su inspección, ejecute el cmdlet [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) o [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), en función del tipo de elemento. Esto le permite guardar el elemento localmente sin instalarlo e inspeccionar su contenido. Recuerde eliminar el elemento guardado manualmente.

Algunos de estos elementos son creación de Microsoft y otros son creación de la comunidad de PowerShell. Microsoft recomienda que se revisen el contenido y el código de los elementos de esta Galería antes de la instalación.

Si cree que un elemento no se ha publicado de buena fe, haga clic en **Notificar abuso** en la página de ese elemento.

### Instalar

Para instalar un elemento desde la Galería para su uso, ejecute el cmdlet [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) o [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), en función del tipo de elemento.

[Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) instala el módulo en $env:ProgramFiles\\WindowsPowerShell\\Modules de forma predeterminada. Para ello es necesaria una cuenta de administrador. Si agrega el parámetro **-Scope CurrentUser**, el módulo se instala en $env:USERPROFILE\\Documents\\WindowsPowerShell\\Modules.

[Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) instala el script en $env:ProgramFiles\\WindowsPowerShell\\Scripts de forma predeterminada. Para ello es necesaria una cuenta de administrador. Si agrega el parámetro **-Scope CurrentUser**, el script se instala en $env:USERPROFILE\\Documents\\WindowsPowerShell\\Scripts.

De forma predeterminada, [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) instalan la versión más reciente de un elemento. Para instalar una versión anterior del elemento, agregue el parámetro **-RequiredVersion**.

### Implementar

Para implementar un elemento desde la Galería de PowerShell en Automatización de Azure, haga clic en **Deploy to Azure Automation** (Implementar en Automatización de Azure) en la página de detalles del elemento. Se le redirigirá al Portal de administración de Azure, donde deberá iniciar sesión con sus credenciales de la cuenta de Azure. Tenga en cuenta que si se implementan elementos con dependencias, se implementarán todas las dependencias en Automatización de Azure. El botón Deploy to Azure Automation (Implementar en Automatización de Azure) se puede deshabilitar agregando la etiqueta **AzureAutomationNotSupported** a los metadatos del elemento.

Para obtener más información sobre Automatización de Azure, consulte el [sitio web de Automatización de Azure](http://azure.microsoft.com/en-us/services/automation/).

## Actualizar elementos de la Galería de PowerShell

Para actualizar elementos instalados desde la Galería de PowerShell, ejecute el cmdlet [Update-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) o [Update-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Cuando se ejecuta sin parámetros adicionales, [Update-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) intenta actualizar cada módulo instalado mediante la ejecución de [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).
Para actualizar módulos de forma selectiva, agregue el parámetro **-Name**.

Del mismo modo, cuando se ejecuta sin parámetros adicionales, [Update-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) también intenta actualizar cada script instalado mediante la ejecución de [Install-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).
Para actualizar scripts de forma selectiva, agregue el parámetro **-Name**.

## Enumerar los elementos instalados desde la Galería de PowerShell

Para averiguar qué módulos ha instalado desde la Galería de PowerShell, ejecute el cmdlet [**Get-InstalledModule**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Este comando enumera todos los módulos del sistema que se instalaron directamente desde la Galería de PowerShell.

Del mismo modo, para averiguar qué scripts ha instalado desde la Galería de PowerShell, ejecute el cmdlet [**Get-InstalledScript**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). Este comando enumera todos los scripts del sistema que se instalaron directamente desde la Galería de PowerShell.


<!--HONumber=Aug16_HO3-->


