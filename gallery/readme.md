# Galería de PowerShell

La Galería de PowerShell es el repositorio central del contenido de PowerShell. En la Galería encontrará nuevos comandos de PowerShell o recursos de configuración de estado deseado (DSC).

# Información general de PowerShellGet

El módulo PowerShellGet contiene cmdlets para detectar, instalar, actualizar y publicar los artefactos de PowerShell como módulos, recursos de DSC, funcionalidades de rol y scripts desde https://www.PowerShellGallery.com y otros repositorios privados.

## Introducción a la Galería

Para instalar elementos desde la Galería se requiere la versión más reciente del módulo PowerShellGet, que está disponible en Windows 10, en Windows Management Framework (WMF) 5.0 o en el programa de instalación basado en MSI (para PowerShell 3 y 4).

- [**Obtener Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),
- [**Obtener WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) u
- [**Obtener el instalador MSI**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

Con la última versión del módulo [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), puede:

-   Buscar elementos en la Galería con [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) y [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)
-   Guardar los elementos en el sistema desde la Galería con [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) y [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)
-   Instalar elementos desde la Galería con [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)
-   Cargar elementos en la Galería con [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) y [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)
-   Agregue su propio repositorio personalizado con [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409)

Consulte la página [Introducción](psgallery/psgallery_gettingstarted.md) para obtener más información sobre el uso de comandos PowerShellGet con la Galería. También puede ejecutar *Update-Help -Module PowerShellGet* para instalar la Ayuda local para estos comandos.

## Sistemas operativos compatibles

El módulo **PowerShellGet** requiere **PowerShell 3.0 o posterior**.

Por lo tanto, **PowerShellGet** requiere uno de los siguientes sistemas operativos:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016 TP5
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** también requiere .NET Framework 4.5 o posterior. Puede instalar .NET Framework 4.5 o posterior desde [aquí](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).


## ¿Tiene alguna pregunta? ¿Tiene comentarios?

Encontrará más información sobre la Galería de PowerShell y PowerShellGet en la página [Introducción](psgallery/psgallery_gettingstarted.md). Proporcione comentarios e informe de problemas mediante [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).



<!--HONumber=Aug16_HO3-->


