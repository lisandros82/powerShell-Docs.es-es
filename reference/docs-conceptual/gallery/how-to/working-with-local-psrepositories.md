---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Trabajo con repositorios PSRepositories locales
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71327996"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="4c649-103">Trabajo con repositorios de PowerShellGet locales</span><span class="sxs-lookup"><span data-stu-id="4c649-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="4c649-104">El módulo de PowerShellGet admite repositorios que no sean la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c649-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="4c649-105">Estos cmdlets permiten los siguientes escenarios:</span><span class="sxs-lookup"><span data-stu-id="4c649-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="4c649-106">Compatibilidad con un conjunto confiable y validado previamente de módulos de PowerShell para usar en su entorno</span><span class="sxs-lookup"><span data-stu-id="4c649-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="4c649-107">Prueba de una canalización de CI/CD que compila los módulos o scripts de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c649-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="4c649-108">Suministro de módulos y scripts de PowerShell a los sistemas que no pueden acceder a Internet</span><span class="sxs-lookup"><span data-stu-id="4c649-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="4c649-109">En este artículo se describe cómo configurar un repositorio local de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c649-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="4c649-110">El artículo también trata el módulo [OfflinePowerShellGetDeploy][] disponible en la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c649-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="4c649-111">Este módulo contiene cmdlets para instalar la versión más reciente de PowerShellGet en el repositorio local.</span><span class="sxs-lookup"><span data-stu-id="4c649-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="4c649-112">Tipos de repositorio local</span><span class="sxs-lookup"><span data-stu-id="4c649-112">Local repository types</span></span>

<span data-ttu-id="4c649-113">Existen dos formas de crear un repositorio PSRepository local: Servidor de NuGet o recurso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="4c649-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="4c649-114">Cada tipo tiene ventajas y desventajas:</span><span class="sxs-lookup"><span data-stu-id="4c649-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="4c649-115">Servidor de NuGet</span><span class="sxs-lookup"><span data-stu-id="4c649-115">NuGet Server</span></span>

| <span data-ttu-id="4c649-116">Ventajas</span><span class="sxs-lookup"><span data-stu-id="4c649-116">Advantages</span></span>| <span data-ttu-id="4c649-117">Desventajas</span><span class="sxs-lookup"><span data-stu-id="4c649-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="4c649-118">Imita con precisión la funcionalidad de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c649-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="4c649-119">La aplicación de niveles múltiples requiere la planeación y la compatibilidad de las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="4c649-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="4c649-120">NuGet se integra con Visual Studio, otras herramientas.</span><span class="sxs-lookup"><span data-stu-id="4c649-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="4c649-121">Se necesita un modelo de autenticación y administración de cuentas de NuGet.</span><span class="sxs-lookup"><span data-stu-id="4c649-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="4c649-122">NuGet es compatible con los metadatos en paquetes `.Nupkg`.</span><span class="sxs-lookup"><span data-stu-id="4c649-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="4c649-123">La publicación requiere mantenimiento y administración de claves de API.</span><span class="sxs-lookup"><span data-stu-id="4c649-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="4c649-124">Proporciona búsqueda, administración de paquetes, etc.</span><span class="sxs-lookup"><span data-stu-id="4c649-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="4c649-125">Recurso compartido de archivos</span><span class="sxs-lookup"><span data-stu-id="4c649-125">File Share</span></span>

| <span data-ttu-id="4c649-126">Ventajas</span><span class="sxs-lookup"><span data-stu-id="4c649-126">Advantages</span></span>| <span data-ttu-id="4c649-127">Desventajas</span><span class="sxs-lookup"><span data-stu-id="4c649-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="4c649-128">Fácil configuración, proceso de copia de seguridad y mantenimiento.</span><span class="sxs-lookup"><span data-stu-id="4c649-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="4c649-129">Los metadatos usados por PowerShellGet no están disponibles.</span><span class="sxs-lookup"><span data-stu-id="4c649-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="4c649-130">Modelo de seguridad simple: permisos de usuario en el recurso compartido.</span><span class="sxs-lookup"><span data-stu-id="4c649-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="4c649-131">Sin interfaz de usuario más allá del recurso compartido de archivos básico.</span><span class="sxs-lookup"><span data-stu-id="4c649-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="4c649-132">Sin restricciones como el reemplazo de los elementos existentes.</span><span class="sxs-lookup"><span data-stu-id="4c649-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="4c649-133">Seguridad limitada y ausencia de registro de quién actualiza qué.</span><span class="sxs-lookup"><span data-stu-id="4c649-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="4c649-134">PowerShellGet funciona con cualquier tipo y admite la búsqueda de versiones y la instalación de dependencias.</span><span class="sxs-lookup"><span data-stu-id="4c649-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="4c649-135">Sin embargo, algunas características que funcionan para la Galería de PowerShell no están disponibles para los servidores o los recursos compartidos de archivos de NuGet básicos.</span><span class="sxs-lookup"><span data-stu-id="4c649-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="4c649-136">Todo es un paquete, sin diferenciación de scripts, módulos, recursos DSC o funciones de rol.</span><span class="sxs-lookup"><span data-stu-id="4c649-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="4c649-137">Los servidores de los recursos compartidos de archivos no pueden ver los metadatos del paquete, incluidas las etiquetas.</span><span class="sxs-lookup"><span data-stu-id="4c649-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="4c649-138">Creación de un repositorio local</span><span class="sxs-lookup"><span data-stu-id="4c649-138">Creating a local repository</span></span>

<span data-ttu-id="4c649-139">El siguiente artículo enumera los pasos para configurar su propio servidor de NuGet.</span><span class="sxs-lookup"><span data-stu-id="4c649-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="4c649-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="4c649-140">[NuGet.Server][]</span></span>

<span data-ttu-id="4c649-141">Siga los pasos hasta el momento de agregar los paquetes.</span><span class="sxs-lookup"><span data-stu-id="4c649-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="4c649-142">Los pasos para [publicar un paquete](#publishing-to-a-local-repository) se tratan más adelante en este artículo.</span><span class="sxs-lookup"><span data-stu-id="4c649-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="4c649-143">En el caso de un repositorio basado en recursos compartidos de archivos, asegúrese de que los usuarios tienen permisos para acceder a dicho recurso.</span><span class="sxs-lookup"><span data-stu-id="4c649-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="4c649-144">Registro de un repositorio local</span><span class="sxs-lookup"><span data-stu-id="4c649-144">Registering a local repository</span></span>

<span data-ttu-id="4c649-145">Para que un repositorio se pueda usar, debe registrarse con el comando `Register-PSRepository`.</span><span class="sxs-lookup"><span data-stu-id="4c649-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="4c649-146">En los ejemplos siguientes, **InstallationPolicy** está establecido en *Trusted*, dando por supuesto que confía en su propio repositorio.</span><span class="sxs-lookup"><span data-stu-id="4c649-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="4c649-147">Observe la diferencia entre el modo en que los dos comandos controlan **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="4c649-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="4c649-148">Para repositorios basados en recursos compartidos de archivos, las propiedades **SourceLocation** y **ScriptSourceLocation** deben coincidir.</span><span class="sxs-lookup"><span data-stu-id="4c649-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="4c649-149">En el caso de un repositorio basado en web, deben ser diferentes; por tanto, en este ejemplo se agrega "/" final a **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="4c649-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="4c649-150">Si desea que el repositorio PSRepository recién creado sea el repositorio predeterminado, debe anular el registro de todos los demás repositorios PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="4c649-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="4c649-151">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4c649-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="4c649-152">El repositorio llamado "PSGallery" está reservado para su uso por la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c649-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="4c649-153">Puede anular el registro de PSGallery, pero no puede reutilizar el nombre PSGallery para ningún otro repositorio.</span><span class="sxs-lookup"><span data-stu-id="4c649-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="4c649-154">Si necesita restaurar PSGallery, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="4c649-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="4c649-155">Publicación en un repositorio local</span><span class="sxs-lookup"><span data-stu-id="4c649-155">Publishing to a local repository</span></span>

<span data-ttu-id="4c649-156">Una vez que haya registrado la instancia local de PSRepository, puede publicar en ella.</span><span class="sxs-lookup"><span data-stu-id="4c649-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="4c649-157">Hay dos escenarios principales de publicación: publicación de su propio módulo y publicación de un módulo desde PSGallery.</span><span class="sxs-lookup"><span data-stu-id="4c649-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="4c649-158">Publicación de un módulo que ha creado</span><span class="sxs-lookup"><span data-stu-id="4c649-158">Publishing a module you authored</span></span>

<span data-ttu-id="4c649-159">Use `Publish-Module` y `Publish-Script` para publicar el módulo en su PSRepository local del mismo modo que lo hace para la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c649-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="4c649-160">Especifique la ubicación del código.</span><span class="sxs-lookup"><span data-stu-id="4c649-160">Specify the location for your code</span></span>
- <span data-ttu-id="4c649-161">Proporcione una clave de API.</span><span class="sxs-lookup"><span data-stu-id="4c649-161">Supply an API key</span></span>
- <span data-ttu-id="4c649-162">Especifique el nombre del repositorio.</span><span class="sxs-lookup"><span data-stu-id="4c649-162">Specify the repository name.</span></span> <span data-ttu-id="4c649-163">Por ejemplo, `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="4c649-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="4c649-164">Debe crear una cuenta en el servidor de NuGet y luego iniciar sesión para generar y guardar la clave de API.</span><span class="sxs-lookup"><span data-stu-id="4c649-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="4c649-165">En el caso de un recurso compartido de archivos, use cualquier cadena no vacía para el valor de clave NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="4c649-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="4c649-166">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="4c649-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="4c649-167">Para garantizar la seguridad, las claves de API no deben codificarse de forma rígida en scripts.</span><span class="sxs-lookup"><span data-stu-id="4c649-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="4c649-168">Use un sistema de administración de claves seguro.</span><span class="sxs-lookup"><span data-stu-id="4c649-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="4c649-169">Publicación de un módulo de PSGallery</span><span class="sxs-lookup"><span data-stu-id="4c649-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="4c649-170">Para publicar un módulo de PSGallery en su repositorio PSRepository local, puede usar el cmdlet "Save-Package".</span><span class="sxs-lookup"><span data-stu-id="4c649-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="4c649-171">Especifique el nombre del paquete.</span><span class="sxs-lookup"><span data-stu-id="4c649-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="4c649-172">Especifique "NuGet" como proveedor.</span><span class="sxs-lookup"><span data-stu-id="4c649-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="4c649-173">Especifique la ubicación de PSGallery como origen (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="4c649-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="4c649-174">Especifique la ruta de acceso al repositorio local.</span><span class="sxs-lookup"><span data-stu-id="4c649-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="4c649-175">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4c649-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="4c649-176">Si su repositorio PSRepository local está basado en web, se necesita un paso adicional que usa nuget.exe para publicar.</span><span class="sxs-lookup"><span data-stu-id="4c649-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="4c649-177">Consulte la documentación para usar [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="4c649-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="4c649-178">Instalación de PowerShellGet en un sistema sin conexión</span><span class="sxs-lookup"><span data-stu-id="4c649-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="4c649-179">La implementación de PowerShellGet es difícil en entornos que necesitan que los sistemas estén desconectados de Internet.</span><span class="sxs-lookup"><span data-stu-id="4c649-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="4c649-180">PowerShellGet ofrece un proceso de arranque que instala la versión más reciente la primera vez que se utiliza.</span><span class="sxs-lookup"><span data-stu-id="4c649-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="4c649-181">El módulo OfflinePowerShellGetDeploy de la Galería de PowerShell proporciona cmdlets que admiten este proceso de arranque.</span><span class="sxs-lookup"><span data-stu-id="4c649-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="4c649-182">Para arrancar una implementación sin conexión, es preciso lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4c649-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="4c649-183">Descargar e instalar OfflinePowerShellGetDeploy en su sistema conectado a Internet y sus sistemas sin conexión</span><span class="sxs-lookup"><span data-stu-id="4c649-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="4c649-184">Descargar PowerShellGet y sus dependencias en el sistema conectado a Internet mediante el cmdlet `Save-PowerShellGetForOffline`</span><span class="sxs-lookup"><span data-stu-id="4c649-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="4c649-185">Copiar PowerShellGet y sus dependencias del sistema conectado a Internet al sistema sin conexión</span><span class="sxs-lookup"><span data-stu-id="4c649-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="4c649-186">Usar `Install-PowerShellGetOffline` en el sistema sin conexión para colocar PowerShellGet y sus dependencias en las carpetas correspondientes</span><span class="sxs-lookup"><span data-stu-id="4c649-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="4c649-187">Los siguientes comandos usan `Save-PowerShellGetForOffline` para poner todos los componentes en una carpeta `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="4c649-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="4c649-188">En este momento, debe poner el contenido de `F:\OfflinePowerShellGet` a disposición de los sistemas sin conexión.</span><span class="sxs-lookup"><span data-stu-id="4c649-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="4c649-189">Ejecute el cmdlet `Install-PowerShellGetOffline` para instalar PowerShellGet en el sistema sin conexión.</span><span class="sxs-lookup"><span data-stu-id="4c649-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="4c649-190">Es importante que no ejecute PowerShellGet en la sesión de PowerShell antes de ejecutar estos comandos.</span><span class="sxs-lookup"><span data-stu-id="4c649-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="4c649-191">Una vez que se cargue PowerShellGet en la sesión, no se pueden actualizar los componentes.</span><span class="sxs-lookup"><span data-stu-id="4c649-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="4c649-192">Si inicia por error PowerShellGet, salga y reinicie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c649-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="4c649-193">Después de ejecutar estos comandos, está listo para publicar PowerShellGet en el repositorio local.</span><span class="sxs-lookup"><span data-stu-id="4c649-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="4c649-194">Para garantizar la seguridad, las claves de API no deben codificarse de forma rígida en scripts.</span><span class="sxs-lookup"><span data-stu-id="4c649-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="4c649-195">Use un sistema de administración de claves seguro.</span><span class="sxs-lookup"><span data-stu-id="4c649-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
