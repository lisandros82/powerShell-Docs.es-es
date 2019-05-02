---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Trabajo con repositorios PSRepositories locales
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084103"
---
# <a name="working-with-local-powershellget-repositories"></a>Trabajo con repositorios de PowerShellGet locales

El módulo de PowerShellGet admite repositorios que no sean la Galería de PowerShell.
Estos cmdlets permiten los siguientes escenarios:

- Compatibilidad con un conjunto confiable y validado previamente de módulos de PowerShell para usar en su entorno
- Prueba de una canalización de CI/CD que compila los módulos o scripts de PowerShell
- Proporcionar módulos y scripts de PowerShell a los sistemas que no pueden acceder a Internet

En este artículo se describe cómo configurar un repositorio local de PowerShell. El artículo también trata el módulo [OfflinePowerShellGetDeploy][] disponible en la Galería de PowerShell. Este módulo contiene cmdlets para instalar la versión más reciente de PowerShellGet en el repositorio local.

## <a name="local-repository-types"></a>Tipos de repositorio local

Existen dos formas de crear un repositorio PSRepository local: Servidor de NuGet o recurso compartido de archivos. Cada tipo tiene ventajas y desventajas:

Servidor de NuGet

| Ventajas| Desventajas |
| --- | --- |
| Imita con precisión la funcionalidad de la Galería de PowerShell | La aplicación de varios niveles requiere la planeación y el soporte de las aplicaciones |
| NuGet se integra con Visual Studio, otras herramientas | Se necesita un modelo de autenticación y administración de cuentas de NuGet |
| NuGet es compatible con los metadatos en paquetes `.Nupkg` | La publicación requiere mantenimiento y administración de claves de API |
| Proporciona búsqueda, administración de paquetes, etc. | |

Recurso compartido de archivos

| Ventajas| Desventajas |
| --- | --- |
| Fácil configuración, proceso de copia de seguridad y mantenimiento | Los metadatos usados por PowerShellGet no están disponibles |
| Modelo de seguridad simple: permisos de usuario en el recurso compartido | Sin interfaz de usuario más allá del recurso compartido de archivos básico |
| Sin restricciones como el reemplazo de los elementos existentes | Seguridad limitada y ausencia de registro de quién actualiza qué |

PowerShellGet funciona con cualquier tipo y admite la búsqueda de versiones y la instalación de dependencias.
Sin embargo, algunas características que funcionan para la Galería de PowerShell no están disponibles para los servidores o los recursos compartidos de archivos de NuGet básicos.

- Todo es un paquete, sin diferenciación de scripts, módulos, recursos DSC o funciones de rol.
- Los servidores de los recursos compartidos de archivos no pueden ver los metadatos del paquete, incluidas las etiquetas.

## <a name="creating-a-local-repository"></a>Creación de un repositorio local

El siguiente artículo enumera los pasos para configurar su propio servidor de NuGet.

- [NuGet.Server][]

Siga los pasos hasta el momento de agregar los paquetes. Los pasos para [publicar un paquete](#publishing-to-a-local-repository) se tratan más adelante en este artículo.

En el caso de un repositorio basado en recursos compartidos de archivos, asegúrese de que los usuarios tienen permisos para acceder al recurso compartido de archivos.

## <a name="registering-a-local-repository"></a>Registro de un repositorio local

Para que un repositorio se pueda usar, debe registrarse con el comando `Register-PSRepository`.
En los ejemplos siguientes, **InstallationPolicy** está establecido en *Trusted*, dando por supuesto que confía en su propio repositorio.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Observe la diferencia entre el modo en que los dos comandos controlan **ScriptSourceLocation**. Para repositorios basados en recursos compartidos de archivos, las propiedades **SourceLocation** y **ScriptSourceLocation** deben coincidir. En el caso de un repositorio basado en web, deben ser diferentes; por tanto, en este ejemplo se agrega un "/" final a **SourceLocation**.

Si desea que el repositorio PSRepository recién creado sea el repositorio predeterminado, debe anular el registro de todos los demás repositorios PSRepositories. Por ejemplo:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> El repositorio llamado "PSGallery" está reservado para su uso por la Galería de PowerShell. Puede anular el registro de PSGallery, pero no puede reutilizar el nombre PSGallery para ningún otro repositorio.

Si necesita restaurar PSGallery, ejecute el siguiente comando:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Publicación en un repositorio local

Una vez que haya registrado la instancia local de PSRepository, puede publicar en ella. Hay dos escenarios principales de publicación: publicación de su propio módulo y publicación de un módulo desde PSGallery.

### <a name="publishing-a-module-you-authored"></a>Publicación de un módulo de su creación

Use `Publish-Module` y `Publish-Script` para publicar el módulo en su PSRepository local del mismo modo que lo hace para la Galería de PowerShell.

- Especifique la ubicación del código.
- Proporcione una clave de API.
- Especifique el nombre del repositorio. Por ejemplo, `-PSRepository LocalPSRepo`

> [!NOTE]
> Debe crear una cuenta en el servidor de NuGet y luego iniciar sesión para generar y guardar la clave de API.
> En el caso de un recurso compartido de archivos, use cualquier cadena no vacía para el valor de clave NuGetApiKey.

Ejemplos:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Para garantizar la seguridad, las claves de API no deben codificarse de forma rígida en scripts. Use un sistema de administración de claves seguro.

### <a name="publishing-a-module-from-the-psgallery"></a>Publicación de un módulo de PSGallery

Para publicar un módulo de PSGallery en su repositorio PSRepository local, puede usar el cmdlet "Save-Package".

- Especifique el nombre del paquete.
- Especifique "NuGet" como proveedor.
- Especifique la ubicación de PSGallery como origen (https://www.powershellgallery.com/api/v2)
- Especifique la ruta de acceso al repositorio local.

Ejemplo:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Si su repositorio PSRepository local está basado en web, se necesita un paso adicional que usa nuget.exe para publicar.

Consulte la documentación para usar [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Instalación de PowerShellGet en un sistema sin conexión

La implementación de PowerShellGet es difícil en entornos que necesitan que los sistemas estén desconectados de Internet. PowerShellGet ofrece un proceso de arranque que instala la versión más reciente la primera vez que se utiliza. El módulo OfflinePowerShellGetDeploy de la Galería de PowerShell proporciona cmdlets que admiten este proceso de arranque.

Para arrancar una implementación sin conexión, es preciso lo siguiente:

- Descargar e instalar OfflinePowerShellGetDeploy en su sistema conectado a Internet y sus sistemas sin conexión
- Descargar PowerShellGet y sus dependencias en el sistema conectado a Internet mediante el cmdlet `Save-PowerShellGetForOffline`
- Copiar PowerShellGet y sus dependencias del sistema conectado a Internet al sistema sin conexión
- Usar `Install-PowerShellGetOffline` en el sistema sin conexión para colocar PowerShellGet y sus dependencias en las carpetas correspondientes

Los siguientes comandos usan `Save-PowerShellGetForOffline` para poner todos los componentes en una carpeta `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

En este momento, debe poner el contenido de `F:\OfflinePowerShellGet` a disposición de los sistemas sin conexión. Ejecute el cmdlet `Install-PowerShellGetOffline` para instalar PowerShellGet en el sistema sin conexión.

> [!NOTE]
> Es importante que no ejecute PowerShellGet en la sesión de PowerShell antes de ejecutar estos comandos. Una vez que se cargue PowerShellGet en la sesión, no se pueden actualizar los componentes. Si inicia por error PowerShellGet, salga y reinicie PowerShell.

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

Después de ejecutar estos comandos, está listo para publicar PowerShellGet en el repositorio local.

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Para garantizar la seguridad, las claves de API no deben codificarse de forma rígida en scripts. Use un sistema de administración de claves seguro.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
