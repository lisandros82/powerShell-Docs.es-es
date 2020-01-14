---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Trabajo con repositorios PSRepositories locales
ms.openlocfilehash: c1bd905674ae76a3badd3eff50780f0e1bb5fc64
ms.sourcegitcommit: 1b88c280dd0799f225242608f0cbdab485357633
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/25/2019
ms.locfileid: "75415818"
---
# <a name="working-with-private-powershellget-repositories"></a><span data-ttu-id="d5d2d-103">Trabajo con repositorios de PowerShellGet privados</span><span class="sxs-lookup"><span data-stu-id="d5d2d-103">Working with Private PowerShellGet Repositories</span></span>

<span data-ttu-id="d5d2d-104">El módulo de PowerShellGet admite repositorios que no sean la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="d5d2d-105">Estos cmdlets permiten los siguientes escenarios:</span><span class="sxs-lookup"><span data-stu-id="d5d2d-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="d5d2d-106">Compatibilidad con un conjunto confiable y validado previamente de módulos de PowerShell para usar en su entorno</span><span class="sxs-lookup"><span data-stu-id="d5d2d-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="d5d2d-107">Prueba de una canalización de CI/CD que compila los módulos o scripts de PowerShell</span><span class="sxs-lookup"><span data-stu-id="d5d2d-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="d5d2d-108">Suministro de módulos y scripts de PowerShell a los sistemas que no pueden acceder a Internet</span><span class="sxs-lookup"><span data-stu-id="d5d2d-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>
- <span data-ttu-id="d5d2d-109">Entrega de scripts y módulos de PowerShell solo disponibles para su organización</span><span class="sxs-lookup"><span data-stu-id="d5d2d-109">Deliver PowerShell scripts and modules only available to your organization</span></span>

<span data-ttu-id="d5d2d-110">En este artículo se describe cómo configurar un repositorio local de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-110">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="d5d2d-111">El artículo también trata el módulo [OfflinePowerShellGetDeploy][] disponible en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-111">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="d5d2d-112">Este módulo contiene cmdlets para instalar la versión más reciente de PowerShellGet en el repositorio local.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-112">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="d5d2d-113">Tipos de repositorio local</span><span class="sxs-lookup"><span data-stu-id="d5d2d-113">Local repository types</span></span>

<span data-ttu-id="d5d2d-114">Existen dos formas de crear un repositorio PSRepository local: Servidor de NuGet o recurso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-114">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="d5d2d-115">Cada tipo tiene ventajas y desventajas:</span><span class="sxs-lookup"><span data-stu-id="d5d2d-115">Each type has advantages and disadvantages:</span></span>

### <a name="nuget-server"></a><span data-ttu-id="d5d2d-116">Servidor de NuGet</span><span class="sxs-lookup"><span data-stu-id="d5d2d-116">NuGet Server</span></span>

| <span data-ttu-id="d5d2d-117">Ventajas</span><span class="sxs-lookup"><span data-stu-id="d5d2d-117">Advantages</span></span>| <span data-ttu-id="d5d2d-118">Inconvenientes</span><span class="sxs-lookup"><span data-stu-id="d5d2d-118">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="d5d2d-119">Imita con precisión la funcionalidad de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-119">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="d5d2d-120">La aplicación de niveles múltiples requiere la planeación y la compatibilidad de las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-120">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="d5d2d-121">NuGet se integra con Visual Studio, otras herramientas.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-121">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="d5d2d-122">Se necesita un modelo de autenticación y administración de cuentas de NuGet.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-122">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="d5d2d-123">NuGet es compatible con los metadatos en paquetes `.Nupkg`.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-123">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="d5d2d-124">La publicación requiere mantenimiento y administración de claves de API.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-124">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="d5d2d-125">Proporciona búsqueda, administración de paquetes, etc.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-125">Provides search, package administration, etc.</span></span> | |

### <a name="file-share"></a><span data-ttu-id="d5d2d-126">Recurso compartido de archivos</span><span class="sxs-lookup"><span data-stu-id="d5d2d-126">File Share</span></span>

| <span data-ttu-id="d5d2d-127">Ventajas</span><span class="sxs-lookup"><span data-stu-id="d5d2d-127">Advantages</span></span>| <span data-ttu-id="d5d2d-128">Inconvenientes</span><span class="sxs-lookup"><span data-stu-id="d5d2d-128">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="d5d2d-129">Fácil configuración, proceso de copia de seguridad y mantenimiento.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-129">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="d5d2d-130">Los metadatos usados por PowerShellGet no están disponibles.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-130">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="d5d2d-131">Modelo de seguridad simple: permisos de usuario en el recurso compartido.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-131">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="d5d2d-132">Sin interfaz de usuario más allá del recurso compartido de archivos básico.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-132">No UI beyond basic file share</span></span> |
| <span data-ttu-id="d5d2d-133">Sin restricciones como el reemplazo de los elementos existentes.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-133">No constraints such as replacing existing items</span></span> | <span data-ttu-id="d5d2d-134">Seguridad limitada y ausencia de registro de quién actualiza qué.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-134">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="d5d2d-135">PowerShellGet funciona con cualquier tipo y admite la búsqueda de versiones y la instalación de dependencias.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-135">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="d5d2d-136">Sin embargo, algunas características que funcionan para la Galería de PowerShell no están disponibles para los servidores o los recursos compartidos de archivos de NuGet básicos.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-136">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="d5d2d-137">Todo es un paquete, sin diferenciación de scripts, módulos, recursos DSC o funciones de rol.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-137">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="d5d2d-138">Los servidores de los recursos compartidos de archivos no pueden ver los metadatos del paquete, incluidas las etiquetas.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-138">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="d5d2d-139">Creación de un repositorio local</span><span class="sxs-lookup"><span data-stu-id="d5d2d-139">Creating a local repository</span></span>

<span data-ttu-id="d5d2d-140">El siguiente artículo enumera los pasos para configurar su propio servidor de NuGet.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-140">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="d5d2d-141">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="d5d2d-141">[NuGet.Server][]</span></span>

<span data-ttu-id="d5d2d-142">Siga los pasos hasta el momento de agregar los paquetes.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-142">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="d5d2d-143">Los pasos para [publicar un paquete](#publishing-to-a-local-repository) se tratan más adelante en este artículo.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-143">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="d5d2d-144">En el caso de un repositorio basado en recursos compartidos de archivos, asegúrese de que los usuarios tienen permisos para acceder a dicho recurso.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-144">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="d5d2d-145">Registro de un repositorio local</span><span class="sxs-lookup"><span data-stu-id="d5d2d-145">Registering a local repository</span></span>

<span data-ttu-id="d5d2d-146">Para que un repositorio se pueda usar, debe registrarse con el comando `Register-PSRepository`.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-146">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="d5d2d-147">En los ejemplos siguientes, **InstallationPolicy** está establecido en *Trusted*, dando por supuesto que confía en su propio repositorio.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-147">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="d5d2d-148">Observe la diferencia entre el modo en que los dos comandos controlan **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-148">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="d5d2d-149">Para repositorios basados en recursos compartidos de archivos, las propiedades **SourceLocation** y **ScriptSourceLocation** deben coincidir.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-149">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="d5d2d-150">En el caso de un repositorio basado en web, deben ser diferentes; por tanto, en este ejemplo se agrega "/" final a **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-150">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="d5d2d-151">Si desea que el repositorio PSRepository recién creado sea el repositorio predeterminado, debe anular el registro de todos los demás repositorios PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-151">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="d5d2d-152">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d5d2d-152">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="d5d2d-153">El repositorio llamado "PSGallery" está reservado para su uso por la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-153">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="d5d2d-154">Puede anular el registro de PSGallery, pero no puede reutilizar el nombre PSGallery para ningún otro repositorio.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-154">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="d5d2d-155">Si necesita restaurar PSGallery, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="d5d2d-155">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="d5d2d-156">Publicación en un repositorio local</span><span class="sxs-lookup"><span data-stu-id="d5d2d-156">Publishing to a local repository</span></span>

<span data-ttu-id="d5d2d-157">Una vez que haya registrado la instancia local de PSRepository, puede publicar en ella.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-157">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="d5d2d-158">Hay dos escenarios principales de publicación: publicación de su propio módulo y publicación de un módulo desde PSGallery.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-158">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="d5d2d-159">Publicación de un módulo que ha creado</span><span class="sxs-lookup"><span data-stu-id="d5d2d-159">Publishing a module you authored</span></span>

<span data-ttu-id="d5d2d-160">Use `Publish-Module` y `Publish-Script` para publicar el módulo en su PSRepository local del mismo modo que lo hace para la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-160">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="d5d2d-161">Especifique la ubicación del código.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-161">Specify the location for your code</span></span>
- <span data-ttu-id="d5d2d-162">Proporcione una clave de API.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-162">Supply an API key</span></span>
- <span data-ttu-id="d5d2d-163">Especifique el nombre del repositorio.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-163">Specify the repository name.</span></span> <span data-ttu-id="d5d2d-164">Por ejemplo: `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="d5d2d-164">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="d5d2d-165">Debe crear una cuenta en el servidor de NuGet y luego iniciar sesión para generar y guardar la clave de API.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-165">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="d5d2d-166">En el caso de un recurso compartido de archivos, use cualquier cadena no vacía para el valor de clave NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-166">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="d5d2d-167">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="d5d2d-167">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'
```

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="d5d2d-168">Para garantizar la seguridad, las claves de API no deben codificarse de forma rígida en scripts.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-168">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="d5d2d-169">Use un sistema de administración de claves seguro.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-169">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="d5d2d-170">Publicación de un módulo de PSGallery</span><span class="sxs-lookup"><span data-stu-id="d5d2d-170">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="d5d2d-171">Para publicar un módulo de PSGallery en su repositorio PSRepository local, puede usar el cmdlet "Save-Package".</span><span class="sxs-lookup"><span data-stu-id="d5d2d-171">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="d5d2d-172">Especifique el nombre del paquete.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-172">Specify the Name of the Package</span></span>
- <span data-ttu-id="d5d2d-173">Especifique "NuGet" como proveedor.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-173">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="d5d2d-174">Especifique la ubicación de PSGallery como origen (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="d5d2d-174">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="d5d2d-175">Especifique la ruta de acceso al repositorio local.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-175">Specify the path to your local Repository</span></span>

<span data-ttu-id="d5d2d-176">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d5d2d-176">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="d5d2d-177">Si su repositorio PSRepository local está basado en web, se necesita un paso adicional que usa nuget.exe para publicar.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-177">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="d5d2d-178">Consulte la documentación para usar [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="d5d2d-178">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="d5d2d-179">Instalación de PowerShellGet en un sistema sin conexión</span><span class="sxs-lookup"><span data-stu-id="d5d2d-179">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="d5d2d-180">La implementación de PowerShellGet es difícil en entornos que necesitan que los sistemas estén desconectados de Internet.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-180">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="d5d2d-181">PowerShellGet ofrece un proceso de arranque que instala la versión más reciente la primera vez que se utiliza.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-181">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="d5d2d-182">El módulo OfflinePowerShellGetDeploy de la Galería de PowerShell proporciona cmdlets que admiten este proceso de arranque.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-182">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="d5d2d-183">Para arrancar una implementación sin conexión, es preciso lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d5d2d-183">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="d5d2d-184">Descargar e instalar OfflinePowerShellGetDeploy en su sistema conectado a Internet y sus sistemas sin conexión</span><span class="sxs-lookup"><span data-stu-id="d5d2d-184">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="d5d2d-185">Descargar PowerShellGet y sus dependencias en el sistema conectado a Internet mediante el cmdlet `Save-PowerShellGetForOffline`</span><span class="sxs-lookup"><span data-stu-id="d5d2d-185">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="d5d2d-186">Copiar PowerShellGet y sus dependencias del sistema conectado a Internet al sistema sin conexión</span><span class="sxs-lookup"><span data-stu-id="d5d2d-186">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="d5d2d-187">Usar `Install-PowerShellGetOffline` en el sistema sin conexión para colocar PowerShellGet y sus dependencias en las carpetas correspondientes</span><span class="sxs-lookup"><span data-stu-id="d5d2d-187">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="d5d2d-188">Los siguientes comandos usan `Save-PowerShellGetForOffline` para poner todos los componentes en una carpeta `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="d5d2d-188">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="d5d2d-189">En este momento, debe poner el contenido de `F:\OfflinePowerShellGet` a disposición de los sistemas sin conexión.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-189">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="d5d2d-190">Ejecute el cmdlet `Install-PowerShellGetOffline` para instalar PowerShellGet en el sistema sin conexión.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-190">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="d5d2d-191">Es importante que no ejecute PowerShellGet en la sesión de PowerShell antes de ejecutar estos comandos.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-191">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="d5d2d-192">Una vez que se cargue PowerShellGet en la sesión, no se pueden actualizar los componentes.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-192">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="d5d2d-193">Si inicia por error PowerShellGet, salga y reinicie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-193">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="d5d2d-194">Después de ejecutar estos comandos, está listo para publicar PowerShellGet en el repositorio local.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-194">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a><span data-ttu-id="d5d2d-195">Uso de soluciones de empaquetado para hospedar repositorios de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d5d2d-195">Use Packaging solutions to host PowerShellGet repositories</span></span>

<span data-ttu-id="d5d2d-196">También puede usar soluciones de empaquetado como Azure Artifacts para hospedar un repositorio de PowerShellGet privado o público.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-196">You can also use packaging solutions like Azure Artifacts to host a private or public PowerShellGet repository.</span></span> <span data-ttu-id="d5d2d-197">Para más información e instrucciones, consulte la [documentación de Azure Artifacts](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library).</span><span class="sxs-lookup"><span data-stu-id="d5d2d-197">For more information and instructions, see the [Azure Artifacts documentation](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d5d2d-198">Para garantizar la seguridad, las claves de API no deben codificarse de forma rígida en scripts.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-198">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="d5d2d-199">Use un sistema de administración de claves seguro.</span><span class="sxs-lookup"><span data-stu-id="d5d2d-199">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
