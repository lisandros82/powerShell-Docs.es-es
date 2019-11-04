---
title: Cómo crear un shell de consola | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Make-Shell [PowerShell Programmer's Guide]
ms.assetid: 6c24dd44-a8ec-421d-ac86-90912e1a8cc6
caps.latest.revision: 5
ms.openlocfilehash: 7166881bd1403ea8c81ec2928321f6b93e3ac58d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360274"
---
# <a name="how-to-create-a-console-shell"></a><span data-ttu-id="853f7-102">Cómo crear un shell de la consola</span><span class="sxs-lookup"><span data-stu-id="853f7-102">How to Create a Console Shell</span></span>

<span data-ttu-id="853f7-103">Windows PowerShell proporciona una herramienta de creación de Shell, también denominada "make-kit", que se usa para crear un shell de consola que no es extensible.</span><span class="sxs-lookup"><span data-stu-id="853f7-103">Windows PowerShell provides a Make-Shell tool, also referred to as the "make-kit", that is used to create a console shell that is not extensible.</span></span> <span data-ttu-id="853f7-104">Los shells creados con esta nueva herramienta no se pueden ampliar más adelante a través de un complemento de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="853f7-104">Shells created with this new tool cannot be extended later through a Windows PowerShell snap-in.</span></span>

## <a name="syntax"></a><span data-ttu-id="853f7-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="853f7-105">Syntax</span></span>

<span data-ttu-id="853f7-106">Esta es la sintaxis que se usa para ejecutar make-Shell desde un archivo make.</span><span class="sxs-lookup"><span data-stu-id="853f7-106">Here is the syntax used to run Make-Shell from within a make-file.</span></span>

```
make-shell
  -out n.exe
  -namespace ns
  [ -lib libdirectory1[,libdirectory2,..] ]
  [ -reference ca1.dll[,ca2.dll,...] ]
  [ -formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...] ]
  [ -typedata td1.type.ps1xml[,td2.type.ps1xml,...] ]
  [ -source c1.cs [,c2.cs,...] ]
  [ -authorizationmanager authorizationManagerType ]
  [ -win32icon i.ico ]
  [ -initscript p.ps1 ]
  [ -builtinscript s1.ps1[,s2.ps1,...] ]
  [ -resource resourcefile.txt ]
  [ -cscflags cscFlags ]
  [ -? | -help ]
```

## <a name="parameters"></a><span data-ttu-id="853f7-107">Parámetros</span><span class="sxs-lookup"><span data-stu-id="853f7-107">Parameters</span></span>

<span data-ttu-id="853f7-108">Esta es una breve descripción de los parámetros de make-Shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-108">Here is a brief description of the parameters of Make-Shell.</span></span>

> [!CAUTION]
> <span data-ttu-id="853f7-109">Make-Shell no admite rutas de acceso UNC a ensamblados.</span><span class="sxs-lookup"><span data-stu-id="853f7-109">UNC paths to assemblies are not supported by Make-Shell.</span></span>

|<span data-ttu-id="853f7-110">Parámetro</span><span class="sxs-lookup"><span data-stu-id="853f7-110">Parameter</span></span>|<span data-ttu-id="853f7-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="853f7-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="853f7-112">-out n. exe</span><span class="sxs-lookup"><span data-stu-id="853f7-112">-out n.exe</span></span>|<span data-ttu-id="853f7-113">Necesario.</span><span class="sxs-lookup"><span data-stu-id="853f7-113">Required.</span></span> <span data-ttu-id="853f7-114">Nombre del shell que se va a producir.</span><span class="sxs-lookup"><span data-stu-id="853f7-114">The name of the shell to produce.</span></span> <span data-ttu-id="853f7-115">La ruta de acceso se especifica como parte de este parámetro.</span><span class="sxs-lookup"><span data-stu-id="853f7-115">The path is specified as part of this parameter.</span></span><br /><br /> <span data-ttu-id="853f7-116">Make-Shell anexará ". exe" a este valor si no se especifica.</span><span class="sxs-lookup"><span data-stu-id="853f7-116">Make-shell will append ".exe" to this value if it is not specified.</span></span> <span data-ttu-id="853f7-117">**PRECAUCIÓN:**  No cree un archivo de salida con el mismo nombre que el archivo. dll al que se hace referencia.</span><span class="sxs-lookup"><span data-stu-id="853f7-117">**Caution:**  Do not create an output file with the same name as the referenced .dll file.</span></span> <span data-ttu-id="853f7-118">Si lo intenta, la herramienta make-Shell crea un archivo. CS con el mismo nombre, lo que sobrescribirá el archivo. CS que contiene el código fuente del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="853f7-118">If you attempt this, the Make-Shell tool creates a .cs file with the same name, which will overwrite the .cs file that has your cmdlet source code.</span></span>|
|<span data-ttu-id="853f7-119">-espacio de nombres NS</span><span class="sxs-lookup"><span data-stu-id="853f7-119">-namespace ns</span></span>|<span data-ttu-id="853f7-120">Necesario.</span><span class="sxs-lookup"><span data-stu-id="853f7-120">Required.</span></span> <span data-ttu-id="853f7-121">Espacio de nombres que se va a usar para la clase derivada de [System. Management. Automation. namespaces. Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) que genera y compila el make-kit.</span><span class="sxs-lookup"><span data-stu-id="853f7-121">The namespace to use for the derived [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) class that the make-kit generates and compiles.</span></span>|
|<span data-ttu-id="853f7-122">-lib libdirectory1 [, libdirectory2,..]</span><span class="sxs-lookup"><span data-stu-id="853f7-122">-lib libdirectory1[,libdirectory2,..]</span></span>|<span data-ttu-id="853f7-123">Los directorios en los que se buscan ensamblados .NET, incluidos los ensamblados de Windows PowerShell, los ensamblados especificados por el parámetro `reference`, los ensamblados a los que hace referencia indirectamente otro ensamblado y los ensamblados de sistema .NET.</span><span class="sxs-lookup"><span data-stu-id="853f7-123">The directories that are searched for .NET assemblies, including the Windows PowerShell assemblies, assemblies specified by the `reference` parameter, assemblies indirectly referenced by another assembly, and the .NET system assemblies.</span></span>|
|<span data-ttu-id="853f7-124">-Reference CA1. dll [, Ca2. dll,...]</span><span class="sxs-lookup"><span data-stu-id="853f7-124">-reference ca1.dll[,ca2.dll,...]</span></span>|<span data-ttu-id="853f7-125">Lista separada por comas de los ensamblados que se van a incluir en el shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-125">A comma-separated list of the assemblies to include in the shell.</span></span> <span data-ttu-id="853f7-126">Estos ensamblados incluyen todos los ensamblados de cmdlets y proveedores, así como los ensamblados de recursos que deben cargarse.</span><span class="sxs-lookup"><span data-stu-id="853f7-126">These assemblies  includes all cmdlet and provider assemblies, as well as resource assemblies that should be loaded.</span></span> <span data-ttu-id="853f7-127">Si no se especifica este parámetro, se genera un shell que contiene solo los cmdlets y proveedores principales proporcionados por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="853f7-127">If this parameter is not specified, then a shell is produced that contains only the core cmdlets and providers provided by Windows PowerShell.</span></span><br /><br /> <span data-ttu-id="853f7-128">Los ensamblados se pueden especificar mediante su ruta de acceso completa; de lo contrario, se buscarán usando la ruta de acceso especificada por el parámetro `lib`.</span><span class="sxs-lookup"><span data-stu-id="853f7-128">The assemblies can be specified using their full path, otherwise they will be searched for using the path specified by the `lib` parameter.</span></span>|
|<span data-ttu-id="853f7-129">-formatdata FD1. Format. ps1xml [, FD2. Format. ps1xml,...]</span><span class="sxs-lookup"><span data-stu-id="853f7-129">-formatdata fd1.format.ps1xml[,fd2.format.ps1xml,...]</span></span>|<span data-ttu-id="853f7-130">Lista separada por comas de los datos de formato que se van a incluir en el shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-130">A comma-separated list of format data to include in the shell.</span></span> <span data-ttu-id="853f7-131">Si no se especifica este parámetro, se genera un shell que solo contiene los datos de formato proporcionados por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="853f7-131">If this parameter is not specified, then a shell is produced that contains only the format data provided by Windows PowerShell.</span></span>|
|<span data-ttu-id="853f7-132">-typedata TD1. Type. ps1xml [, TD2. Type. ps1xml,...]</span><span class="sxs-lookup"><span data-stu-id="853f7-132">-typedata td1.type.ps1xml[,td2.type.ps1xml,...]</span></span>|<span data-ttu-id="853f7-133">Lista separada por comas de los datos de tipo que se van a incluir en el shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-133">A comma-separated list of type data to include in the shell.</span></span> <span data-ttu-id="853f7-134">Si no se especifica este parámetro, se genera un shell que solo contiene los datos de tipo proporcionados por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="853f7-134">If this parameter is not specified, then a shell is produced that contains only the type data provided by Windows PowerShell.</span></span>|
|<span data-ttu-id="853f7-135">-Source c1.cs [, c2.cs,...]</span><span class="sxs-lookup"><span data-stu-id="853f7-135">-source c1.cs [,c2.cs,...]</span></span>|<span data-ttu-id="853f7-136">Nombre de un archivo, proporcionado por el desarrollador del shell, que contiene cualquier código fuente necesario para compilar el shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-136">The name of a file, provided by the shell developer, that contains any source code needed to build the shell.</span></span><br /><br /> <span data-ttu-id="853f7-137">El archivo de código fuente puede contener cualquiera de los siguientes códigos fuente:</span><span class="sxs-lookup"><span data-stu-id="853f7-137">The source code file can contain any of the following source code:</span></span><br /><br /> <span data-ttu-id="853f7-138">-La implementación de administrador de autorización que invalida el administrador de autorización predeterminado.</span><span class="sxs-lookup"><span data-stu-id="853f7-138">-   The Authorization manager implementation that overrides the default authorization manager.</span></span> <span data-ttu-id="853f7-139">(También se puede proporcionar compilar en un ensamblado).</span><span class="sxs-lookup"><span data-stu-id="853f7-139">(This could also be supplied compiled into an assembly.)</span></span><br /><span data-ttu-id="853f7-140">-Declaraciones de atributos informativos de ensamblado: como AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute y AssemblyTrademarkAttribute.</span><span class="sxs-lookup"><span data-stu-id="853f7-140">-   Assembly informational attribute declarations: such as the AssemblyCompanyAttribute, AssemblyCopyrightAttribute, AssemblyFileVersionAttribute, AssemblyInformationalVersionAttribute, AssemblyProductAttribute, and AssemblyTrademarkAttribute.</span></span>|
|<span data-ttu-id="853f7-141">-authorizationmanager authorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="853f7-141">-authorizationmanager authorizationManagerType</span></span>|<span data-ttu-id="853f7-142">El tipo que contiene la implementación del administrador de autorización.</span><span class="sxs-lookup"><span data-stu-id="853f7-142">The type that contains the authorization manager implementation.</span></span> <span data-ttu-id="853f7-143">Esto puede definirse en el código fuente o compilarse en un ensamblado (especificado por el parámetro `reference`).</span><span class="sxs-lookup"><span data-stu-id="853f7-143">This can be defined in source code, or compiled into an assembly (specified by the `reference` parameter).</span></span> <span data-ttu-id="853f7-144">Si no se especifica este parámetro, se utiliza el administrador de seguridad predeterminado.</span><span class="sxs-lookup"><span data-stu-id="853f7-144">If this parameter is not specified, the default security manager is used.</span></span> <span data-ttu-id="853f7-145">El valor debe ser el nombre de tipo completo, incluidos los espacios de nombres.</span><span class="sxs-lookup"><span data-stu-id="853f7-145">The value should be the full type name, including namespaces.</span></span>|
|<span data-ttu-id="853f7-146">-win32icon i. ico</span><span class="sxs-lookup"><span data-stu-id="853f7-146">-win32icon i.ico</span></span>|<span data-ttu-id="853f7-147">Icono del archivo. exe del shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-147">The icon for the .exe file for the shell.</span></span> <span data-ttu-id="853f7-148">Si no se especifica, el shell tendrá el icono que incluye el compilador de c# (si existe).</span><span class="sxs-lookup"><span data-stu-id="853f7-148">If not specified, then the shell will have the icon that the c# compiler includes (if any).</span></span>|
|<span data-ttu-id="853f7-149">-initscript p. ps1</span><span class="sxs-lookup"><span data-stu-id="853f7-149">-initscript p.ps1</span></span>|<span data-ttu-id="853f7-150">Perfil de inicio del shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-150">The startup profile for the shell.</span></span> <span data-ttu-id="853f7-151">El archivo se incluye "tal cual"; Make-Shell no realiza ninguna comprobación de la validez.</span><span class="sxs-lookup"><span data-stu-id="853f7-151">The file is included "as-is"; no validity checking is done by Make-Shell.</span></span>|
|<span data-ttu-id="853f7-152">-builtinscript S1. PS1 [, S2. ps1,...]</span><span class="sxs-lookup"><span data-stu-id="853f7-152">-builtinscript s1.ps1[,s2.ps1,...]</span></span>|<span data-ttu-id="853f7-153">Una lista de scripts integrados para el shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-153">A list of built-in scripts for the shell.</span></span> <span data-ttu-id="853f7-154">Estos scripts se detectan antes que los scripts de la ruta de acceso y su contenido no se puede cambiar una vez compilado el shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-154">These scripts are discovered before scripts in the path, and their contents cannot be changed once the shell is built.</span></span><br /><br /> <span data-ttu-id="853f7-155">Los archivos se incluyen "tal cual"; Make-Shell no realiza ninguna comprobación de la validez.</span><span class="sxs-lookup"><span data-stu-id="853f7-155">The files are included "as-is"; no validity checking is done by Make-Shell.</span></span>|
|<span data-ttu-id="853f7-156">-Resource resourcefile. txt</span><span class="sxs-lookup"><span data-stu-id="853f7-156">-resource resourcefile.txt</span></span>|<span data-ttu-id="853f7-157">El archivo. txt que contiene los recursos de ayuda y banner del shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-157">The .txt file containing help and banner resources for the shell.</span></span> <span data-ttu-id="853f7-158">El primer recurso se denomina ShellHelp y contiene el texto que se muestra si el Shell se invoca con el parámetro `help`.</span><span class="sxs-lookup"><span data-stu-id="853f7-158">The first resource is named ShellHelp, and contains the text displayed if the shell is invoked with the `help` parameter.</span></span> <span data-ttu-id="853f7-159">El segundo recurso se denomina ShellBanner y contiene el texto y la información de copyright que se muestra cuando el Shell se inicia en modo interactivo.</span><span class="sxs-lookup"><span data-stu-id="853f7-159">The second resource is named ShellBanner, and it contains the text and copyright information displayed when the shell is launched in interactive mode.</span></span><br /><br /> <span data-ttu-id="853f7-160">Si no se proporciona este parámetro, o si estos recursos no están presentes, se usa una ayuda y un banner genéricos.</span><span class="sxs-lookup"><span data-stu-id="853f7-160">If this parameter is not provided, or these resources are not present, then a generic help and banner are used.</span></span>|
|<span data-ttu-id="853f7-161">-cscflags cscFlags</span><span class="sxs-lookup"><span data-stu-id="853f7-161">-cscflags cscFlags</span></span>|<span data-ttu-id="853f7-162">Marcas que se deben pasar al C# compilador (CSC. exe).</span><span class="sxs-lookup"><span data-stu-id="853f7-162">Flags that should be passed to the C# compiler (csc.exe).</span></span> <span data-ttu-id="853f7-163">Se pasan sin modificar.</span><span class="sxs-lookup"><span data-stu-id="853f7-163">These are passed through unchanged.</span></span> <span data-ttu-id="853f7-164">Si este parámetro incluye espacios, debe ir entre comillas dobles.</span><span class="sxs-lookup"><span data-stu-id="853f7-164">If this parameter includes spaces, it should be surrounded in double-quotes.</span></span>|
|<span data-ttu-id="853f7-165">-?</span><span class="sxs-lookup"><span data-stu-id="853f7-165">-?</span></span><br /><br /> <span data-ttu-id="853f7-166">-Help</span><span class="sxs-lookup"><span data-stu-id="853f7-166">-help</span></span>|<span data-ttu-id="853f7-167">Muestra el mensaje de copyright y las opciones de línea de comandos de make-Shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-167">Displays the copyright message and Make-Shell command line options.</span></span>|
|<span data-ttu-id="853f7-168">-verbose</span><span class="sxs-lookup"><span data-stu-id="853f7-168">-verbose</span></span>|<span data-ttu-id="853f7-169">Muestra información detallada mientras se crea el shell.</span><span class="sxs-lookup"><span data-stu-id="853f7-169">Displays detailed information while the shell is being created.</span></span>|

## <a name="see-also"></a><span data-ttu-id="853f7-170">Véase también</span><span class="sxs-lookup"><span data-stu-id="853f7-170">See Also</span></span>

[<span data-ttu-id="853f7-171">Guía del programador de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="853f7-171">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="853f7-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="853f7-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)