---
title: Cómo escribir un módulo de PowerShell binario | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229321"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="b3250-102">Cómo escribir un módulo binario de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3250-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="b3250-103">Un módulo binario puede ser cualquier ensamblado (.dll) que contiene las clases de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3250-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="b3250-104">De forma predeterminada, se importan todos los cmdlets en el ensamblado cuando se importa el módulo binario.</span><span class="sxs-lookup"><span data-stu-id="b3250-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="b3250-105">Sin embargo, puede restringir los cmdlets que se importan mediante la creación de un manifiesto de módulo cuyo módulo raíz es el ensamblado.</span><span class="sxs-lookup"><span data-stu-id="b3250-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="b3250-106">(Por ejemplo, la clave CmdletsToExport del manifiesto puede utilizarse para exportar únicamente los cmdlets que son necesarios.) Además, un módulo binario puede contener otras piezas útiles de información de administración que un solo cmdlet no puede, una estructura de directorios y archivos adicionales.</span><span class="sxs-lookup"><span data-stu-id="b3250-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="b3250-107">El siguiente procedimiento describe cómo crear e instalar un módulo binario de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3250-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="b3250-108">Cómo crear e instalar un módulo binario de PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3250-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="b3250-109">Crear una solución de PowerShell binaria (por ejemplo, un cmdlet escrito en C#), con las capacidades que necesita y asegurarse de que se ejecuta correctamente.</span><span class="sxs-lookup"><span data-stu-id="b3250-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="b3250-110">Desde una perspectiva de código, el núcleo de un módulo binario es simplemente un ensamblado de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b3250-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="b3250-111">De hecho, PowerShell tratará el ensamblado de un solo cmdlet como un módulo, en cuanto a carga y descarga sin ningún esfuerzo adicional por parte del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="b3250-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="b3250-112">Para obtener más información sobre cómo escribir un cmdlet, consulte [escribir un Cmdlet de Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="b3250-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="b3250-113">Si es necesario, cree el resto de la solución: (otros cmdlets, archivos XML etc.) y se describen con un manifiesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="b3250-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="b3250-114">Además de describir los ensamblados de cmdlet en la solución, un manifiesto de módulo puede describir cómo desea que el módulo exporta y se importa, se expondrán los cmdlets y lo pasará archivos adicionales en el módulo.</span><span class="sxs-lookup"><span data-stu-id="b3250-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="b3250-115">Como se indicó anteriormente sin embargo, PowerShell puede tratar un cmdlet binario como un módulo sin ningún esfuerzo adicional.</span><span class="sxs-lookup"><span data-stu-id="b3250-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="b3250-116">Por lo tanto, un manifiesto de módulo es útil principalmente para combinar varios archivos en un único paquete, o para controlar explícitamente la publicación de un ensamblado determinado.</span><span class="sxs-lookup"><span data-stu-id="b3250-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="b3250-117">Para obtener más información, consulte [cómo escribir un manifiesto del módulo de PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b3250-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="b3250-118">El siguiente código es muy sencillo C# bloque de código que contiene tres cmdlets en el mismo archivo que se pueden usar como un módulo.</span><span class="sxs-lookup"><span data-stu-id="b3250-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. <span data-ttu-id="b3250-119">Empaquetar la solución y guardar el paquete en cualquier ubicación en la ruta de acceso del módulo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3250-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="b3250-120">El `PSModulePath` variable de entorno global describe las rutas de acceso predeterminada que va a usar para buscar el módulo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3250-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="b3250-121">Por ejemplo, podría ser una ruta de acceso comunes para guardar un módulo en un sistema `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="b3250-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="b3250-122">Si no utiliza las rutas de acceso de forma predeterminada, deberá indicar explícitamente la ubicación de su módulo durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="b3250-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="b3250-123">Asegúrese de crear una carpeta para guardar el módulo, como es posible que necesite la carpeta para almacenar varios ensamblados y archivos de la solución.</span><span class="sxs-lookup"><span data-stu-id="b3250-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="b3250-124">Tenga en cuenta que técnicamente no deberá instalar el módulo en cualquier lugar en el `PSModulePath` -son simplemente las ubicaciones predeterminadas que se va a buscar el módulo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b3250-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="b3250-125">Sin embargo, se considera una práctica recomendada para ello, a menos que tenga una buena razón para almacenar el módulo en otro lugar.</span><span class="sxs-lookup"><span data-stu-id="b3250-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="b3250-126">Para obtener más información, consulte [instalar un módulo de PowerShell](./installing-a-powershell-module.md) y [modificar la ruta de instalación del módulo de PowerShell](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="b3250-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="b3250-127">Importe el módulo de PowerShell con una llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="b3250-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="b3250-128">Una llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cargará el módulo en la memoria activa.</span><span class="sxs-lookup"><span data-stu-id="b3250-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="b3250-129">Si está usando PowerShell 3.0 y versiones posteriores, basta con llamar al nombre del módulo en el código también importará Para obtener más información, consulte [importar un módulo de PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="b3250-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="b3250-130">Importando ensamblados de complementos como módulos</span><span class="sxs-lookup"><span data-stu-id="b3250-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="b3250-131">Los cmdlets y proveedores que existen en ensamblados de complementos se pueden cargar como módulos binarios.</span><span class="sxs-lookup"><span data-stu-id="b3250-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="b3250-132">Cuando los ensamblados de complementos se cargan como módulos binarios, los cmdlets y proveedores en el complemento están disponibles para el usuario, pero se omite la clase de complemento en el ensamblado y el complemento no está registrado.</span><span class="sxs-lookup"><span data-stu-id="b3250-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="b3250-133">Como resultado, los cmdlets del complemento proporcionados por Windows PowerShell no puede detectar el complemento, aunque los cmdlets y proveedores están disponibles para la sesión.</span><span class="sxs-lookup"><span data-stu-id="b3250-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="b3250-134">Además, los archivos de formato o tipos que se hace referencia mediante el complemento no se puede importar como parte de un módulo binario.</span><span class="sxs-lookup"><span data-stu-id="b3250-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="b3250-135">Para importar los archivos de formato y tipos debe crear un manifiesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="b3250-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="b3250-136">Ver, [cómo escribir un manifiesto de módulo de PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b3250-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3250-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="b3250-137">See Also</span></span>

[<span data-ttu-id="b3250-138">Escribir un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3250-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
