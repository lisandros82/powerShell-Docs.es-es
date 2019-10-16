---
title: Escribir ayuda para módulos de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360564"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="140f9-102">Escritura de la Ayuda de los módulos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="140f9-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="140f9-103">Los módulos de Windows PowerShell pueden incluir temas de ayuda sobre el módulo y los miembros del módulo, como cmdlets, proveedores, funciones y scripts.</span><span class="sxs-lookup"><span data-stu-id="140f9-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="140f9-104">El cmdlet `Get-Help` muestra los temas de ayuda del módulo en el mismo formato que muestra la ayuda para otros elementos de Windows PowerShell y los usuarios usan los comandos `Get-Help` estándar para obtener los temas de ayuda.</span><span class="sxs-lookup"><span data-stu-id="140f9-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="140f9-105">En este documento se explica el formato y la ubicación correcta de los temas de ayuda del módulo, y se sugieren instrucciones para el contenido de la ayuda del módulo.</span><span class="sxs-lookup"><span data-stu-id="140f9-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="140f9-106">Tipos de ayuda de módulo</span><span class="sxs-lookup"><span data-stu-id="140f9-106">Types of Module Help</span></span>

<span data-ttu-id="140f9-107">Un módulo puede incluir los siguientes tipos de ayuda.</span><span class="sxs-lookup"><span data-stu-id="140f9-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="140f9-108">**Ayuda del cmdlet**.</span><span class="sxs-lookup"><span data-stu-id="140f9-108">**Cmdlet Help**.</span></span> <span data-ttu-id="140f9-109">Los temas de ayuda que describen los cmdlets de un módulo son archivos XML que usan el esquema de ayuda de comandos.</span><span class="sxs-lookup"><span data-stu-id="140f9-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="140f9-110">**Ayuda del proveedor**.</span><span class="sxs-lookup"><span data-stu-id="140f9-110">**Provider Help**.</span></span> <span data-ttu-id="140f9-111">Los temas de ayuda que describen los proveedores de un módulo son archivos XML que usan el esquema de ayuda del proveedor.</span><span class="sxs-lookup"><span data-stu-id="140f9-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="140f9-112">**Ayuda**de la función.</span><span class="sxs-lookup"><span data-stu-id="140f9-112">**Function Help**.</span></span> <span data-ttu-id="140f9-113">Los temas de ayuda que describen las funciones de un módulo pueden ser archivos XML que usan el esquema de ayuda del comando o los temas de ayuda basados en comentarios dentro de la función, o el módulo de script o script.</span><span class="sxs-lookup"><span data-stu-id="140f9-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="140f9-114">**Ayuda del script**.</span><span class="sxs-lookup"><span data-stu-id="140f9-114">**Script Help**.</span></span> <span data-ttu-id="140f9-115">Los temas de ayuda que describen los scripts de un módulo pueden ser archivos XML que usan el esquema de ayuda del comando o los temas de ayuda basados en comentarios del módulo script o script.</span><span class="sxs-lookup"><span data-stu-id="140f9-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="140f9-116">**Ayuda conceptual ("About")** .</span><span class="sxs-lookup"><span data-stu-id="140f9-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="140f9-117">Puede usar un tema de ayuda conceptual ("About") para describir el módulo y sus miembros, así como explicar cómo se pueden usar los miembros conjuntamente para realizar tareas.</span><span class="sxs-lookup"><span data-stu-id="140f9-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="140f9-118">Los temas de ayuda conceptual son archivos de texto con codificación Unicode (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="140f9-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="140f9-119">El nombre de archivo debe usar el formato `about_<name>.help.txt`, como about_MyModule. help. txt.</span><span class="sxs-lookup"><span data-stu-id="140f9-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="140f9-120">De forma predeterminada, Windows PowerShell incluye más de 100 de estos temas conceptuales sobre los temas de ayuda y tienen el formato del siguiente ejemplo.</span><span class="sxs-lookup"><span data-stu-id="140f9-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a><span data-ttu-id="140f9-121">Ubicación de la ayuda del módulo</span><span class="sxs-lookup"><span data-stu-id="140f9-121">Placement of Module Help</span></span>

<span data-ttu-id="140f9-122">El cmdlet `Get-Help` busca archivos de tema de ayuda del módulo en subdirectorios específicos del lenguaje del directorio del módulo.</span><span class="sxs-lookup"><span data-stu-id="140f9-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="140f9-123">Por ejemplo, en el diagrama de la estructura de directorios siguiente se muestra la ubicación de los temas de ayuda para el módulo SampleModule.</span><span class="sxs-lookup"><span data-stu-id="140f9-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="140f9-124">En el ejemplo, el marcador de posición *\<ModulePath >* representa una de las rutas de acceso de la variable de entorno `PSModulePath`, como $Home \documents\modules, $pshome nueva \modules. o una ruta de acceso personalizada que el usuario especifica.</span><span class="sxs-lookup"><span data-stu-id="140f9-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="140f9-125">Obtener ayuda de módulo</span><span class="sxs-lookup"><span data-stu-id="140f9-125">Getting Module Help</span></span>

<span data-ttu-id="140f9-126">Cuando un usuario importa un módulo en una sesión, los temas de ayuda de ese módulo se importan en la sesión junto con el módulo.</span><span class="sxs-lookup"><span data-stu-id="140f9-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="140f9-127">Puede enumerar los archivos de tema de ayuda en el valor de la clave FileList en el manifiesto del módulo, pero los temas de ayuda no se ven afectados por el cmdlet `Export-ModuleMember`.</span><span class="sxs-lookup"><span data-stu-id="140f9-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="140f9-128">Puede proporcionar temas de ayuda de módulo en distintos idiomas.</span><span class="sxs-lookup"><span data-stu-id="140f9-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="140f9-129">El cmdlet `Get-Help` muestra automáticamente los temas de ayuda del módulo en el idioma especificado para el usuario actual en el elemento configuración regional y de idioma del panel de control.</span><span class="sxs-lookup"><span data-stu-id="140f9-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="140f9-130">En Windows Vista y versiones posteriores de Windows, `Get-Help` busca los temas de ayuda en subdirectorios específicos del lenguaje del directorio del módulo de acuerdo con los estándares de reserva del lenguaje establecidos para Windows.</span><span class="sxs-lookup"><span data-stu-id="140f9-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="140f9-131">A partir de Windows PowerShell 3,0, la ejecución de un comando `Get-Help` para un cmdlet o una función desencadena la importación automática del módulo.</span><span class="sxs-lookup"><span data-stu-id="140f9-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="140f9-132">El cmdlet `Get-Help` muestra inmediatamente el contenido de los temas de ayuda en el módulo.</span><span class="sxs-lookup"><span data-stu-id="140f9-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="140f9-133">Si el módulo no contiene temas de ayuda y no hay ningún tema de ayuda para los comandos del módulo en el equipo del usuario, `Get-Help` muestra la ayuda generada automáticamente.</span><span class="sxs-lookup"><span data-stu-id="140f9-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="140f9-134">La ayuda generada automáticamente incluye la sintaxis de comandos, los parámetros y los tipos de entrada y salida, pero no incluye ninguna descripción.</span><span class="sxs-lookup"><span data-stu-id="140f9-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="140f9-135">La ayuda generada automáticamente incluye texto que indica al usuario que intente usar el cmdlet `Update-Help` para descargar la ayuda del comando desde Internet o desde un recurso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="140f9-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="140f9-136">También recomienda usar el parámetro **online** del cmdlet `Get-Help` para obtener la versión en línea del tema de ayuda.</span><span class="sxs-lookup"><span data-stu-id="140f9-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="140f9-137">Compatibilidad con la ayuda actualizable</span><span class="sxs-lookup"><span data-stu-id="140f9-137">Supporting Updatable Help</span></span>

<span data-ttu-id="140f9-138">Los usuarios de Windows PowerShell 3,0 y versiones posteriores de Windows PowerShell pueden descargar e instalar archivos de ayuda actualizados para un módulo desde Internet o desde un recurso compartido de archivos local.</span><span class="sxs-lookup"><span data-stu-id="140f9-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="140f9-139">Los cmdlets `Update-Help` y `Save-Help` ocultan los detalles de administración del usuario.</span><span class="sxs-lookup"><span data-stu-id="140f9-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="140f9-140">Los usuarios ejecutan el cmdlet `Update-Help` y, a continuación, usan el cmdlet `Get-Help` para leer los archivos de ayuda más recientes para el módulo en el símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="140f9-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="140f9-141">Los usuarios no necesitan reiniciar Windows ni Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="140f9-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="140f9-142">Los usuarios detrás de firewalls y aquellos que no tienen acceso a Internet también pueden usar la ayuda actualizable.</span><span class="sxs-lookup"><span data-stu-id="140f9-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="140f9-143">Los administradores con acceso a Internet usan el cmdlet `Save-Help` para descargar e instalar los archivos de ayuda más recientes en un recurso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="140f9-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="140f9-144">A continuación, los usuarios usan el parámetro **path** del cmdlet `Update-Help` para obtener los archivos de ayuda más recientes del recurso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="140f9-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="140f9-145">Los autores de módulos pueden incluir archivos de ayuda en el módulo y usar la ayuda actualizable para actualizar los archivos de ayuda, u omitir los archivos de ayuda del módulo y usar la ayuda actualizable para instalarlos y actualizarlos.</span><span class="sxs-lookup"><span data-stu-id="140f9-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="140f9-146">Para obtener más información acerca de la ayuda actualizable, consulte compatibilidad con la [ayuda actualizable](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="140f9-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="140f9-147">Compatibilidad con la ayuda en línea</span><span class="sxs-lookup"><span data-stu-id="140f9-147">Supporting Online Help</span></span>

<span data-ttu-id="140f9-148">Los usuarios que no pueden instalar archivos de ayuda actualizados en sus equipos suelen basarse en la versión en línea de los temas de ayuda de los módulos.</span><span class="sxs-lookup"><span data-stu-id="140f9-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="140f9-149">El parámetro **online** del cmdlet `Get-Help` abre la versión en línea del tema de ayuda de un cmdlet o una función avanzada para el usuario en su explorador de Internet predeterminado.</span><span class="sxs-lookup"><span data-stu-id="140f9-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="140f9-150">El cmdlet `Get-Help` usa el valor de la propiedad **HelpUri** del cmdlet o la función para encontrar la versión en línea del tema de ayuda.</span><span class="sxs-lookup"><span data-stu-id="140f9-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="140f9-151">A partir de Windows PowerShell 3,0, puede ayudar a los usuarios a encontrar la versión en línea de los temas de ayuda de cmdlets y funciones definiendo el atributo HelpUri en la clase de cmdlet o la propiedad **HelpUri** del atributo **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="140f9-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="140f9-152">El valor del atributo es el valor de la propiedad **HelpUri** del cmdlet o la función.</span><span class="sxs-lookup"><span data-stu-id="140f9-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="140f9-153">Para obtener más información, consulte compatibilidad con la [ayuda en línea](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="140f9-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="140f9-154">Véase también</span><span class="sxs-lookup"><span data-stu-id="140f9-154">See Also</span></span>

[<span data-ttu-id="140f9-155">Escribir un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="140f9-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="140f9-156">Compatibilidad con la ayuda actualizable</span><span class="sxs-lookup"><span data-stu-id="140f9-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="140f9-157">Compatibilidad con la ayuda en línea</span><span class="sxs-lookup"><span data-stu-id="140f9-157">Supporting Online Help</span></span>](./supporting-online-help.md)