---
title: Cómo escribir un módulo binario de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367124"
---
# <a name="how-to-write-a-powershell-binary-module"></a><span data-ttu-id="a99d2-102">Cómo escribir un módulo binario de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a99d2-102">How to Write a PowerShell Binary Module</span></span>

<span data-ttu-id="a99d2-103">Un módulo binario puede ser cualquier ensamblado (. dll) que contenga clases de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a99d2-103">A binary module can be any assembly (.dll) that contains cmdlet classes.</span></span> <span data-ttu-id="a99d2-104">De forma predeterminada, todos los cmdlets del ensamblado se importan cuando se importa el módulo binario.</span><span class="sxs-lookup"><span data-stu-id="a99d2-104">By default, all the cmdlets in the assembly are imported when the binary module is imported.</span></span> <span data-ttu-id="a99d2-105">Sin embargo, puede restringir los cmdlets que se importan creando un manifiesto de módulo cuyo módulo raíz es el ensamblado.</span><span class="sxs-lookup"><span data-stu-id="a99d2-105">However, you can restrict the cmdlets that are imported by creating a module manifest whose root module is the assembly.</span></span> <span data-ttu-id="a99d2-106">(Por ejemplo, la clave CmdletsToExport del manifiesto se puede usar para exportar solo los cmdlets necesarios). Además, un módulo binario puede contener archivos adicionales, una estructura de directorios y otras partes de información útil de administración que no puede tener un único cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a99d2-106">(For example, the CmdletsToExport key of the manifest can be used to export only those cmdlets that are needed.) In addition, a binary module can contain additional files, a directory structure, and other pieces of useful management information that a single cmdlet cannot.</span></span>

<span data-ttu-id="a99d2-107">En el procedimiento siguiente se describe cómo crear e instalar un módulo binario de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a99d2-107">The following procedure describes how to create and install a PowerShell binary module.</span></span>

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a><span data-ttu-id="a99d2-108">Cómo crear e instalar un módulo binario de PowerShell</span><span class="sxs-lookup"><span data-stu-id="a99d2-108">How to create and install a PowerShell binary module</span></span>

1. <span data-ttu-id="a99d2-109">Cree una solución de PowerShell binaria (como un cmdlet escrito C#en), con las funcionalidades que necesita y asegúrese de que se ejecuta correctamente.</span><span class="sxs-lookup"><span data-stu-id="a99d2-109">Create a binary PowerShell solution (such as a cmdlet written in C#), with the capabilities you need, and ensure that it runs properly.</span></span>

   <span data-ttu-id="a99d2-110">Desde el punto de vista del código, el núcleo de un módulo binario es simplemente un ensamblado de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a99d2-110">From a code perspective, the core of a binary module is simply a cmdlet assembly.</span></span> <span data-ttu-id="a99d2-111">De hecho, PowerShell tratará un solo ensamblado de cmdlet como módulo, en términos de carga y descarga, sin ningún esfuerzo adicional en la parte del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="a99d2-111">In fact, PowerShell will treat a single cmdlet assembly as a module, in terms of loading and unloading, with no additional effort on the part of the developer.</span></span> <span data-ttu-id="a99d2-112">Para obtener más información sobre cómo escribir un cmdlet, consulte [escribir un cmdlet de Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="a99d2-112">For more information about writing a cmdlet, see [Writing a Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md).</span></span>

2. <span data-ttu-id="a99d2-113">Si es necesario, cree el resto de la solución: (cmdlets adicionales, archivos XML, etc.) y describirlas con un manifiesto del módulo.</span><span class="sxs-lookup"><span data-stu-id="a99d2-113">If necessary, create the rest of your solution: (additional cmdlets, XML files, and so on) and describe them with a module manifest.</span></span>

   <span data-ttu-id="a99d2-114">Además de describir los ensamblados de cmdlet en la solución, un manifiesto de módulo puede describir cómo desea que se exporte e importe el módulo, qué cmdlets se expondrán y qué archivos adicionales se incluirán en el módulo.</span><span class="sxs-lookup"><span data-stu-id="a99d2-114">In addition to describing the cmdlet assemblies in your solution, a module manifest can describe how you want your module exported and imported, what cmdlets will be exposed, and what additional files will go into the module.</span></span>
   <span data-ttu-id="a99d2-115">Como se indicó anteriormente, PowerShell puede tratar un cmdlet binario como un módulo sin ningún esfuerzo adicional.</span><span class="sxs-lookup"><span data-stu-id="a99d2-115">As stated previously however, PowerShell can treat a binary cmdlet like a module with no additional effort.</span></span>
   <span data-ttu-id="a99d2-116">Como tal, un manifiesto de módulo es útil principalmente para combinar varios archivos en un único paquete o para controlar explícitamente la publicación de un ensamblado determinado.</span><span class="sxs-lookup"><span data-stu-id="a99d2-116">As such, a module manifest is useful mainly for combining multiple files into a single package, or for explicitly controlling publication for a given assembly.</span></span>
   <span data-ttu-id="a99d2-117">Para obtener más información, vea [Cómo escribir un manifiesto del módulo de PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="a99d2-117">For more information, see [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

   <span data-ttu-id="a99d2-118">El código siguiente es un bloque de C# código muy simple que contiene tres cmdlets en el mismo archivo que se pueden usar como módulo.</span><span class="sxs-lookup"><span data-stu-id="a99d2-118">The following code is an extremely simple C# code block that contains three cmdlets in the same file that can be used as a module.</span></span>

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

3. <span data-ttu-id="a99d2-119">Empaquete la solución y guarde el paquete en algún lugar de la ruta de acceso del módulo de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a99d2-119">Package your solution, and save the package to somewhere in the PowerShell module path.</span></span>

   <span data-ttu-id="a99d2-120">La variable de entorno global `PSModulePath` describe las rutas de acceso predeterminadas que PowerShell usará para buscar el módulo.</span><span class="sxs-lookup"><span data-stu-id="a99d2-120">The `PSModulePath` global environment variable describes the default paths that PowerShell will use to locate your module.</span></span> <span data-ttu-id="a99d2-121">Por ejemplo, una ruta de acceso común para guardar un módulo en un sistema sería `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="a99d2-121">For example, a common path to save a module on a system would be `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`.</span></span> <span data-ttu-id="a99d2-122">Si no utiliza las rutas de acceso predeterminadas, tendrá que indicar explícitamente la ubicación del módulo durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="a99d2-122">If you do not use the default paths, you will need to explicitly state the location of your module during installation.</span></span> <span data-ttu-id="a99d2-123">Asegúrese de crear una carpeta para guardar el módulo en, ya que es posible que necesite la carpeta para almacenar varios ensamblados y archivos de la solución.</span><span class="sxs-lookup"><span data-stu-id="a99d2-123">Be sure to create a folder to save your module in, as you may need the folder to store multiple assemblies and files for your solution.</span></span>

   <span data-ttu-id="a99d2-124">Tenga en cuenta que técnicamente no es necesario instalar el módulo en ningún lugar del `PSModulePath`; estos son simplemente las ubicaciones predeterminadas que PowerShell buscará en el módulo.</span><span class="sxs-lookup"><span data-stu-id="a99d2-124">Note that technically you do not need to install your module anywhere on the `PSModulePath` - those are simply the default locations that PowerShell will look for your module.</span></span> <span data-ttu-id="a99d2-125">Sin embargo, se recomienda que lo haga, a menos que tenga una buena razón para almacenar el módulo en otra parte.</span><span class="sxs-lookup"><span data-stu-id="a99d2-125">However, it is considered best practice to do so, unless you have a good reason for storing your module somewhere else.</span></span> <span data-ttu-id="a99d2-126">Para obtener más información, vea [instalar un módulo de PowerShell](./installing-a-powershell-module.md) y [modificar la ruta de instalación del módulo de PowerShell](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="a99d2-126">For more information, see [Installing a PowerShell Module](./installing-a-powershell-module.md) and [Modifying the PowerShell Module Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

4. <span data-ttu-id="a99d2-127">Importe el módulo en PowerShell con una llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="a99d2-127">Import your module into PowerShell with a call to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span>

   <span data-ttu-id="a99d2-128">La llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cargará el módulo en la memoria activa.</span><span class="sxs-lookup"><span data-stu-id="a99d2-128">Calling to [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) will load your module into active memory.</span></span> <span data-ttu-id="a99d2-129">Si usa PowerShell 3,0 y versiones posteriores, la llamada al nombre del módulo en el código también lo importará; para obtener más información, vea [importar un módulo de PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="a99d2-129">If you are using PowerShell 3.0 and later, simply calling the name of your module in code will also import it; for more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="importing-snap-in-assemblies-as-modules"></a><span data-ttu-id="a99d2-130">Importar ensamblados de complementos como módulos</span><span class="sxs-lookup"><span data-stu-id="a99d2-130">Importing Snap-in Assemblies as Modules</span></span>

<span data-ttu-id="a99d2-131">Los cmdlets y proveedores que existen en ensamblados de complementos se pueden cargar como módulos binarios.</span><span class="sxs-lookup"><span data-stu-id="a99d2-131">Cmdlets and providers that exist in snap-in assemblies can be loaded as binary modules.</span></span> <span data-ttu-id="a99d2-132">Cuando los ensamblados de complemento se cargan como módulos binarios, los cmdlets y proveedores del complemento están disponibles para el usuario, pero la clase de complemento del ensamblado se omite y el complemento no está registrado.</span><span class="sxs-lookup"><span data-stu-id="a99d2-132">When the snap-in assemblies are loaded as binary modules, the cmdlets and providers in the snap-in are available to the user, but the snap-in class in the assembly is ignored, and the snap-in is not registered.</span></span> <span data-ttu-id="a99d2-133">Como resultado, los cmdlets de complemento proporcionados por Windows PowerShell no pueden detectar el complemento aunque los cmdlets y proveedores estén disponibles para la sesión.</span><span class="sxs-lookup"><span data-stu-id="a99d2-133">As a result, the snap-in cmdlets provided by Windows PowerShell cannot detect the snap-in even though the cmdlets and providers are available to the session.</span></span>

<span data-ttu-id="a99d2-134">Además, los archivos de formato o de tipos a los que hace referencia el complemento no se pueden importar como parte de un módulo binario.</span><span class="sxs-lookup"><span data-stu-id="a99d2-134">In addition, any formatting or types files that are referenced by the snap-in cannot be imported as part of a binary module.</span></span>
<span data-ttu-id="a99d2-135">Para importar los archivos de formato y tipos, debe crear un manifiesto de módulo.</span><span class="sxs-lookup"><span data-stu-id="a99d2-135">To import the formatting and types files you must create a module manifest.</span></span>
<span data-ttu-id="a99d2-136">Vea [Cómo escribir un manifiesto del módulo de PowerShell](how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="a99d2-136">See, [How to Write a PowerShell Module Manifest](how-to-write-a-powershell-module-manifest.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a99d2-137">Véase también</span><span class="sxs-lookup"><span data-stu-id="a99d2-137">See Also</span></span>

[<span data-ttu-id="a99d2-138">Escribir un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a99d2-138">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
