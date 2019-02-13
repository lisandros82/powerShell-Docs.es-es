---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget
title: Trabajar con PSRepositories local
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682675"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="48ba3-103">Trabajo con repositorios de PowerShellGet locales</span><span class="sxs-lookup"><span data-stu-id="48ba3-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="48ba3-104">Los repositorios de soporte técnico de módulo PowerShellGet distinto de la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48ba3-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="48ba3-105">Estos cmdlets permiten los siguientes escenarios:</span><span class="sxs-lookup"><span data-stu-id="48ba3-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="48ba3-106">Admite un conjunto de módulos de PowerShell confianza y validado previamente para su uso en su entorno</span><span class="sxs-lookup"><span data-stu-id="48ba3-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="48ba3-107">Las pruebas de una canalización de CI/CD que compila los módulos de PowerShell o scripts</span><span class="sxs-lookup"><span data-stu-id="48ba3-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="48ba3-108">Proporcionar módulos y scripts de PowerShell para los sistemas que no se pueden acceder a internet</span><span class="sxs-lookup"><span data-stu-id="48ba3-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="48ba3-109">En este artículo se describe cómo configurar un repositorio local de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48ba3-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="48ba3-110">El artículo también trata la [OfflinePowerShellGetDeploy][] módulo disponible desde la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48ba3-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="48ba3-111">Este módulo contiene cmdlets para instalar la versión más reciente de PowerShellGet en el repositorio local.</span><span class="sxs-lookup"><span data-stu-id="48ba3-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="48ba3-112">Tipos de repositorios locales</span><span class="sxs-lookup"><span data-stu-id="48ba3-112">Local repository types</span></span>

<span data-ttu-id="48ba3-113">Hay dos maneras de crear un PSRepository local: NuGet server o archivo compartido.</span><span class="sxs-lookup"><span data-stu-id="48ba3-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="48ba3-114">Cada tipo tiene ventajas y desventajas:</span><span class="sxs-lookup"><span data-stu-id="48ba3-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="48ba3-115">Servidor NuGet</span><span class="sxs-lookup"><span data-stu-id="48ba3-115">NuGet Server</span></span>

| <span data-ttu-id="48ba3-116">Ventajas</span><span class="sxs-lookup"><span data-stu-id="48ba3-116">Advantages</span></span>| <span data-ttu-id="48ba3-117">Desventajas</span><span class="sxs-lookup"><span data-stu-id="48ba3-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="48ba3-118">Imita la funcionalidad de la Galería de PowerShell</span><span class="sxs-lookup"><span data-stu-id="48ba3-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="48ba3-119">Aplicación de varios niveles requiere planeación de operaciones y soporte técnico</span><span class="sxs-lookup"><span data-stu-id="48ba3-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="48ba3-120">NuGet se integra con otras herramientas de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="48ba3-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="48ba3-121">Modelo de autenticación y administración de cuentas de NuGet necesitado</span><span class="sxs-lookup"><span data-stu-id="48ba3-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="48ba3-122">NuGet es compatible con los metadatos en `.Nupkg` paquetes</span><span class="sxs-lookup"><span data-stu-id="48ba3-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="48ba3-123">La publicación requiere mantenimiento y administración de claves de API</span><span class="sxs-lookup"><span data-stu-id="48ba3-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="48ba3-124">Proporciona búsqueda, administración de paquetes, etcetera.</span><span class="sxs-lookup"><span data-stu-id="48ba3-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="48ba3-125">Recurso compartido de archivos</span><span class="sxs-lookup"><span data-stu-id="48ba3-125">File Share</span></span>

| <span data-ttu-id="48ba3-126">Ventajas</span><span class="sxs-lookup"><span data-stu-id="48ba3-126">Advantages</span></span>| <span data-ttu-id="48ba3-127">Desventajas</span><span class="sxs-lookup"><span data-stu-id="48ba3-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="48ba3-128">Fácil de configurar, realizar copias de seguridad y mantener</span><span class="sxs-lookup"><span data-stu-id="48ba3-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="48ba3-129">Metadatos usados por PowerShellGet no está disponible</span><span class="sxs-lookup"><span data-stu-id="48ba3-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="48ba3-130">Modelo de seguridad simple: permisos de usuario en el recurso compartido</span><span class="sxs-lookup"><span data-stu-id="48ba3-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="48ba3-131">Ninguna interfaz de usuario más allá del recurso compartido de archivos básico</span><span class="sxs-lookup"><span data-stu-id="48ba3-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="48ba3-132">Sin restricciones, como el reemplazo de los elementos existentes</span><span class="sxs-lookup"><span data-stu-id="48ba3-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="48ba3-133">Ninguna grabación de quién lo actualiza y seguridad limitada</span><span class="sxs-lookup"><span data-stu-id="48ba3-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="48ba3-134">PowerShellGet funciona con tipo y permite buscar las versiones y la instalación de dependencias.</span><span class="sxs-lookup"><span data-stu-id="48ba3-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="48ba3-135">Sin embargo, algunas características que funcionan para la Galería de PowerShell no están disponibles para los servidores NuGet bases o recursos compartidos de archivos.</span><span class="sxs-lookup"><span data-stu-id="48ba3-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="48ba3-136">Todo lo que es un paquete - ninguna diferencia de las secuencias de comandos, módulos, recursos de DSC o las funcionalidades de rol.</span><span class="sxs-lookup"><span data-stu-id="48ba3-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="48ba3-137">Servidores de recurso compartido de archivos no pueden ver los metadatos del paquete, incluidas las etiquetas.</span><span class="sxs-lookup"><span data-stu-id="48ba3-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="48ba3-138">Crear un repositorio local</span><span class="sxs-lookup"><span data-stu-id="48ba3-138">Creating a local repository</span></span>

<span data-ttu-id="48ba3-139">El siguiente artículo enumera los pasos para configurar su propio servidor NuGet.</span><span class="sxs-lookup"><span data-stu-id="48ba3-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="48ba3-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="48ba3-140">[NuGet.Server][]</span></span>

<span data-ttu-id="48ba3-141">Siga los pasos hasta el momento de agregar los paquetes.</span><span class="sxs-lookup"><span data-stu-id="48ba3-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="48ba3-142">Los pasos para [publicar un paquete](#publishing-to-a-local-repository) se tratan más adelante en este artículo.</span><span class="sxs-lookup"><span data-stu-id="48ba3-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="48ba3-143">Para un repositorio basadas en recursos compartidos de archivos, asegúrese de que los usuarios tienen permisos para acceder al recurso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="48ba3-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="48ba3-144">Registrar un repositorio local</span><span class="sxs-lookup"><span data-stu-id="48ba3-144">Registering a local repository</span></span>

<span data-ttu-id="48ba3-145">Antes de que se puede usar un repositorio, se debe registrar con el `Register-PSRepository` comando.</span><span class="sxs-lookup"><span data-stu-id="48ba3-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="48ba3-146">En los ejemplos siguientes, el **InstallationPolicy** está establecido en *confianza*, en la suposición de que confía en su propio repositorio.</span><span class="sxs-lookup"><span data-stu-id="48ba3-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="48ba3-147">Tome nota de la diferencia entre cómo controlan los dos comandos **ScriptSourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="48ba3-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="48ba3-148">Para un repositorios basados en recursos compartidos de archivos, el **SourceLocation** y **ScriptSourceLocation** deben coincidir.</span><span class="sxs-lookup"><span data-stu-id="48ba3-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="48ba3-149">Para ver un repositorio basada en web, deben ser diferentes, por tanto, en este ejemplo al final "/" se agrega a la **SourceLocation**.</span><span class="sxs-lookup"><span data-stu-id="48ba3-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="48ba3-150">Si desea PSRepository recién creado en el repositorio predeterminado, debe anular el registro de todos los demás PSRepositories.</span><span class="sxs-lookup"><span data-stu-id="48ba3-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="48ba3-151">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="48ba3-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="48ba3-152">El nombre del repositorio 'PSGallery' está reservado para su uso por la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48ba3-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="48ba3-153">Puede anular el registro de PSGallery, pero no se puede reutilizar el nombre PSGallery para cualquier otro repositorio.</span><span class="sxs-lookup"><span data-stu-id="48ba3-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="48ba3-154">Si necesita restaurar la PSGallery, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="48ba3-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="48ba3-155">Publicar en un repositorio local</span><span class="sxs-lookup"><span data-stu-id="48ba3-155">Publishing to a local repository</span></span>

<span data-ttu-id="48ba3-156">Una vez que haya registrado PSRepository local, puede publicar en su PSRepository local.</span><span class="sxs-lookup"><span data-stu-id="48ba3-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="48ba3-157">Hay dos escenarios principales de publicación: publicación de su propio módulo y publicar un módulo desde la PSGallery.</span><span class="sxs-lookup"><span data-stu-id="48ba3-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="48ba3-158">Publicar un módulo que creado</span><span class="sxs-lookup"><span data-stu-id="48ba3-158">Publishing a module you authored</span></span>

<span data-ttu-id="48ba3-159">Use `Publish-Module` y `Publish-Script` para publicar el módulo en su PSRepository local del mismo modo que lo hace para la Galería de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48ba3-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="48ba3-160">Especifique la ubicación para el código</span><span class="sxs-lookup"><span data-stu-id="48ba3-160">Specify the location for your code</span></span>
- <span data-ttu-id="48ba3-161">Proporcione una clave de API</span><span class="sxs-lookup"><span data-stu-id="48ba3-161">Supply an API key</span></span>
- <span data-ttu-id="48ba3-162">Especifique el nombre del repositorio.</span><span class="sxs-lookup"><span data-stu-id="48ba3-162">Specify the repository name.</span></span> <span data-ttu-id="48ba3-163">Por ejemplo, `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="48ba3-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="48ba3-164">Debe crear una cuenta en el servidor de NuGet y luego inicie sesión para generar y guardar la clave de API.</span><span class="sxs-lookup"><span data-stu-id="48ba3-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="48ba3-165">Un recurso compartido de archivos, use cualquier cadena no vacía para el valor de clave NuGetApiKey.</span><span class="sxs-lookup"><span data-stu-id="48ba3-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="48ba3-166">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="48ba3-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="48ba3-167">Para garantizar la seguridad, las claves de API no deben ser codificados de forma rígida en secuencias de comandos.</span><span class="sxs-lookup"><span data-stu-id="48ba3-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="48ba3-168">Usar un sistema de administración de claves segura.</span><span class="sxs-lookup"><span data-stu-id="48ba3-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="48ba3-169">Publicar un módulo de PSGallery</span><span class="sxs-lookup"><span data-stu-id="48ba3-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="48ba3-170">Para publicar un módulo de PSGallery para su PSRepository local, puede usar el cmdlet "Save-Package".</span><span class="sxs-lookup"><span data-stu-id="48ba3-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="48ba3-171">Especifique el nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="48ba3-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="48ba3-172">Especifique "NuGet" como el proveedor</span><span class="sxs-lookup"><span data-stu-id="48ba3-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="48ba3-173">Especifique la ubicación de PSGallery como el origen (https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="48ba3-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="48ba3-174">Especifique la ruta de acceso al repositorio local</span><span class="sxs-lookup"><span data-stu-id="48ba3-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="48ba3-175">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="48ba3-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="48ba3-176">Si su PSRepository local está basado en web, requiere un paso adicional que usa nuget.exe para publicar.</span><span class="sxs-lookup"><span data-stu-id="48ba3-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="48ba3-177">Consulte la documentación para usar [nuget.exe][].</span><span class="sxs-lookup"><span data-stu-id="48ba3-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="48ba3-178">Instalación de PowerShellGet en un sistema desconectado</span><span class="sxs-lookup"><span data-stu-id="48ba3-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="48ba3-179">Implementación de PowerShellGet es difícil en entornos que necesitan que los sistemas se desconecta de internet.</span><span class="sxs-lookup"><span data-stu-id="48ba3-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="48ba3-180">PowerShellGet ofrece un proceso de arranque que instala la versión más reciente de la primera vez que se utiliza.</span><span class="sxs-lookup"><span data-stu-id="48ba3-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="48ba3-181">El módulo OfflinePowerShellGetDeploy en la Galería de PowerShell proporciona cmdlets que admiten este proceso de arranque.</span><span class="sxs-lookup"><span data-stu-id="48ba3-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="48ba3-182">Para arrancar una implementación sin conexión, es preciso:</span><span class="sxs-lookup"><span data-stu-id="48ba3-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="48ba3-183">Descargue e instale el sistema OfflinePowerShellGetDeploy su conexión a internet y los sistemas desconectados</span><span class="sxs-lookup"><span data-stu-id="48ba3-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="48ba3-184">Descargar PowerShellGet y sus dependencias en el sistema conectado a internet mediante el `Save-PowerShellGetForOffline` cmdlet</span><span class="sxs-lookup"><span data-stu-id="48ba3-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="48ba3-185">Copiar PowerShellGet y sus dependencias del sistema conectado a internet en el sistema desconectado</span><span class="sxs-lookup"><span data-stu-id="48ba3-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="48ba3-186">Use el `Install-PowerShellGetOffline` en el sistema para colocar PowerShellGet y sus dependencias en las carpetas correspondientes desconectado</span><span class="sxs-lookup"><span data-stu-id="48ba3-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="48ba3-187">Los siguientes comandos usan `Save-PowerShellGetForOffline` poner todos los componentes en una carpeta `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="48ba3-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="48ba3-188">En este momento, debe hacer que el contenido de `F:\OfflinePowerShellGet` disponibles para los sistemas desconectados.</span><span class="sxs-lookup"><span data-stu-id="48ba3-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="48ba3-189">Ejecute el `Install-PowerShellGetOffline` cmdlet para instalar PowerShellGet en el sistema sin conexión.</span><span class="sxs-lookup"><span data-stu-id="48ba3-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="48ba3-190">Es importante que ejecute PowerShellGet en la sesión de PowerShell antes de ejecutar estos comandos.</span><span class="sxs-lookup"><span data-stu-id="48ba3-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="48ba3-191">Una vez que se carguen PowerShellGet en la sesión, no se puede actualizar los componentes.</span><span class="sxs-lookup"><span data-stu-id="48ba3-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="48ba3-192">Si inicia por error PowerShellGet, salga y reinicie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48ba3-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="48ba3-193">Después de ejecutar estos comandos, está listo para publicar PowerShellGet en el repositorio local.</span><span class="sxs-lookup"><span data-stu-id="48ba3-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="48ba3-194">Para garantizar la seguridad, las claves de API no deben ser codificados de forma rígida en secuencias de comandos.</span><span class="sxs-lookup"><span data-stu-id="48ba3-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="48ba3-195">Usar un sistema de administración de claves segura.</span><span class="sxs-lookup"><span data-stu-id="48ba3-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
