---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Trabajar con PSRepositories local
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: 91786b03704fbd2d185f674df0bc67faddfb6288
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619220"
---
# <a name="working-with-local-powershellget-repositories"></a>Trabajo con repositorios de PowerShellGet locales

Los repositorios de soporte técnico de módulo PowerShellGet distinto de la Galería de PowerShell.
Estos cmdlets permiten los siguientes escenarios:

- Admite un conjunto de módulos de PowerShell confianza y validado previamente para su uso en su entorno
- Las pruebas de una canalización de CI/CD que compila los módulos de PowerShell o scripts
- Proporcionar módulos y scripts de PowerShell para los sistemas que no se pueden acceder a internet

En este artículo se describe cómo configurar un repositorio local de PowerShell. El artículo también trata la [OfflinePowerShellGetDeploy][] módulo disponible desde la Galería de PowerShell. Este módulo contiene cmdlets para instalar la versión más reciente de PowerShellGet en el repositorio local.

## <a name="local-repository-types"></a>Tipos de repositorios locales

Hay dos maneras de crear un PSRepository local: recurso compartido de servidor o un archivo de NuGet. Cada tipo tiene ventajas y desventajas:

Servidor NuGet

| Ventajas| Desventajas |
| --- | --- |
| Imita la funcionalidad de la Galería de PowerShell | Aplicación de varios niveles requiere planeación de operaciones y soporte técnico |
| NuGet se integra con otras herramientas de Visual Studio | Modelo de autenticación y administración de cuentas de NuGet necesitado |
| NuGet es compatible con los metadatos en `.Nupkg` paquetes | La publicación requiere mantenimiento y administración de claves de API |
| Proporciona búsqueda, administración de paquetes, etcetera. | |

Recurso compartido de archivos

| Ventajas| Desventajas |
| --- | --- |
| Fácil de configurar, realizar copias de seguridad y mantener | Metadatos usados por PowerShellGet no está disponible |
| Modelo de seguridad simple: permisos de usuario en el recurso compartido | Ninguna interfaz de usuario más allá del recurso compartido de archivos básico |
| Sin restricciones, como el reemplazo de los elementos existentes | Ninguna grabación de quién lo actualiza y seguridad limitada |

PowerShellGet funciona con tipo y permite buscar las versiones y la instalación de dependencias.
Sin embargo, algunas características que funcionan para la Galería de PowerShell no están disponibles para los servidores NuGet bases o recursos compartidos de archivos.

- Todo lo que es un paquete - ninguna diferencia de las secuencias de comandos, módulos, recursos de DSC o las funcionalidades de rol.
- Servidores de recurso compartido de archivos no pueden ver los metadatos del paquete, incluidas las etiquetas.

## <a name="creating-a-local-repository"></a>Crear un repositorio local

El siguiente artículo enumera los pasos para configurar su propio servidor NuGet.

- [NuGet.Server][]

Siga los pasos hasta el momento de agregar los paquetes. Los pasos para [publicar un paquete](#publishing-to-a-local-repository) se tratan más adelante en este artículo.

Para un repositorio basadas en recursos compartidos de archivos, asegúrese de que los usuarios tienen permisos para acceder al recurso compartido de archivos.

## <a name="registering-a-local-repository"></a>Registrar un repositorio local

Antes de que se puede usar un repositorio, se debe registrar con el `Register-PSRepository` comando.
En los ejemplos siguientes, el **InstallationPolicy** está establecido en *confianza*, en la suposición de que confía en su propio repositorio.

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

Tome nota de la diferencia entre cómo controlan los dos comandos **ScriptSourceLocation**. Para un repositorios basados en recursos compartidos de archivos, el **SourceLocation** y **ScriptSourceLocation** deben coincidir. Para ver un repositorio basada en web, deben ser diferentes, por tanto, en este ejemplo al final "/" se agrega a la **SourceLocation**.

Si desea PSRepository recién creado en el repositorio predeterminado, debe anular el registro de todos los demás PSRepositories. Por ejemplo:

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> El nombre del repositorio 'PSGallery' está reservado para su uso por la Galería de PowerShell. Puede anular el registro de PSGallery, pero no se puede reutilizar el nombre PSGallery para cualquier otro repositorio.

Si necesita restaurar la PSGallery, ejecute el siguiente comando:

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a>Publicar en un repositorio local

Una vez que haya registrado PSRepository local, puede publicar en su PSRepository local. Hay dos escenarios principales de publicación: publicación de su propio módulo y publicar un módulo desde la PSGallery.

### <a name="publishing-a-module-you-authored"></a>Publicar un módulo que creado

Use `Publish-Module` y `Publish-Script` para publicar el módulo en su PSRepository local del mismo modo que lo hace para la Galería de PowerShell.

- Especifique la ubicación para el código
- Proporcione una clave de API
- Especifique el nombre del repositorio. Por ejemplo, `-PSRepository LocalPSRepo`

> [!NOTE]
> Debe crear una cuenta en el servidor de NuGet y luego inicie sesión para generar y guardar la clave de API.
> Un recurso compartido de archivos, use cualquier cadena no vacía para el valor de clave NuGetApiKey.

Ejemplos:

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> Para garantizar la seguridad, las claves de API no deben ser codificados de forma rígida en secuencias de comandos. Usar un sistema de administración de claves segura.

### <a name="publishing-a-module-from-the-psgallery"></a>Publicar un módulo de PSGallery

Para publicar un módulo de PSGallery para su PSRepository local, puede usar el cmdlet "Save-Package".

- Especifique el nombre del paquete
- Especifique "NuGet" como el proveedor
- Especifique la ubicación de PSGallery como el origen (https://www.powershellgallery.com/api/v2)
- Especifique la ruta de acceso al repositorio local

Ejemplo:

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

Si su PSRepository local está basado en web, requiere un paso adicional que usa nuget.exe para publicar.

Consulte la documentación para usar [nuget.exe][].

## <a name="installing-powershellget-on-a-disconnected-system"></a>Instalación de PowerShellGet en un sistema desconectado

Implementación de PowerShellGet es difícil en entornos que necesitan que los sistemas se desconecta de internet. PowerShellGet ofrece un proceso de arranque que instala la versión más reciente de la primera vez que se utiliza. El módulo OfflinePowerShellGetDeploy en la Galería de PowerShell proporciona cmdlets que admiten este proceso de arranque.

Para arrancar una implementación sin conexión, es preciso:

- Descargue e instale el sistema OfflinePowerShellGetDeploy su conexión a internet y los sistemas desconectados
- Descargar PowerShellGet y sus dependencias en el sistema conectado a internet mediante el `Save-PowerShellGetForOffline` cmdlet
- Copiar PowerShellGet y sus dependencias del sistema conectado a internet en el sistema desconectado
- Use el `Install-PowerShellGetOffline` en el sistema para colocar PowerShellGet y sus dependencias en las carpetas correspondientes desconectado

Los siguientes comandos usan `Save-PowerShellGetForOffline` poner todos los componentes en una carpeta `f:\OfflinePowerShellGet`

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

En este momento, debe hacer que el contenido de `F:\OfflinePowerShellGet` disponibles para los sistemas desconectados. Ejecute el `Install-PowerShellGetOffline` cmdlet para instalar PowerShellGet en el sistema sin conexión.

> [!NOTE]
> Es importante que ejecute PowerShellGet en la sesión de PowerShell antes de ejecutar estos comandos. Una vez que se carguen PowerShellGet en la sesión, no se puede actualizar los componentes. Si inicia por error PowerShellGet, salga y reinicie PowerShell.

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
> Para garantizar la seguridad, las claves de API no deben ser codificados de forma rígida en secuencias de comandos. Usar un sistema de administración de claves segura.

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[NuGet.exe]: /nuget/tools/nuget-exe-cli-reference
