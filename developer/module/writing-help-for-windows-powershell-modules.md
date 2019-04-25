---
title: Escribir la Ayuda de módulos de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082045"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="f2049-102">Escritura de la Ayuda de los módulos de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2049-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="f2049-103">Módulos de Windows PowerShell pueden incluir temas de ayuda sobre el módulo y los miembros de módulo, como cmdlets, proveedores, funciones y scripts.</span><span class="sxs-lookup"><span data-stu-id="f2049-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="f2049-104">El `Get-Help` cmdlet muestra los temas de Ayuda del módulo en el mismo formato, tal como muestra la Ayuda de otros elementos de Windows PowerShell y los usuarios usar estándar `Get-Help` comandos para obtener los temas de ayuda.</span><span class="sxs-lookup"><span data-stu-id="f2049-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="f2049-105">Este documento explica el formato y la ubicación correcta de temas de Ayuda del módulo, y recomienda las directrices para el contenido de Ayuda del módulo.</span><span class="sxs-lookup"><span data-stu-id="f2049-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="f2049-106">Tipos de Ayuda del módulo</span><span class="sxs-lookup"><span data-stu-id="f2049-106">Types of Module Help</span></span>

<span data-ttu-id="f2049-107">Un módulo puede incluir los siguientes tipos de ayuda.</span><span class="sxs-lookup"><span data-stu-id="f2049-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="f2049-108">**Ayuda de cmdlet**.</span><span class="sxs-lookup"><span data-stu-id="f2049-108">**Cmdlet Help**.</span></span> <span data-ttu-id="f2049-109">Los temas de ayuda que describen los cmdlets en un módulo son archivos XML que use el comando ayudarán esquema</span><span class="sxs-lookup"><span data-stu-id="f2049-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="f2049-110">**Ayuda del proveedor**.</span><span class="sxs-lookup"><span data-stu-id="f2049-110">**Provider Help**.</span></span> <span data-ttu-id="f2049-111">Los temas de ayuda que describen los proveedores en un módulo son archivos XML que utilizan el proveedor de ayudarán de esquema.</span><span class="sxs-lookup"><span data-stu-id="f2049-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="f2049-112">**Funciones**.</span><span class="sxs-lookup"><span data-stu-id="f2049-112">**Function Help**.</span></span> <span data-ttu-id="f2049-113">Los temas de ayuda que describen las funciones de un módulo puede ser archivos XML que use el comando Ayuda basada en comentarios de los temas de Ayuda de la función, o el script o un módulo de script o de esquema</span><span class="sxs-lookup"><span data-stu-id="f2049-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="f2049-114">**Ayuda de script**.</span><span class="sxs-lookup"><span data-stu-id="f2049-114">**Script Help**.</span></span> <span data-ttu-id="f2049-115">Los temas de ayuda que describen las secuencias de comandos en un módulo puede ayudar a los archivos XML que utilizan el comando esquema o basada en comentarios de los temas de ayuda en la secuencia de comandos o el módulo de script.</span><span class="sxs-lookup"><span data-stu-id="f2049-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="f2049-116">**Conceptual ("About"), ayuda**.</span><span class="sxs-lookup"><span data-stu-id="f2049-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="f2049-117">Puede usar un conceptual ("about"), el tema de ayuda para describir el módulo y sus miembros y explicar cómo se pueden usar conjuntamente para realizar tareas de los miembros.</span><span class="sxs-lookup"><span data-stu-id="f2049-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="f2049-118">Temas de ayuda conceptual son archivos de texto con codificación Unicode (UTF-8).</span><span class="sxs-lookup"><span data-stu-id="f2049-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="f2049-119">El nombre de archivo debe usar el `about_<name>.help.txt` formato, como about_MyModule.help.txt.</span><span class="sxs-lookup"><span data-stu-id="f2049-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="f2049-120">De forma predeterminada, Windows PowerShell incluye más de 100 de estos temas de Ayuda conceptuales y se les aplica formato similar al ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="f2049-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

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

## <a name="placement-of-module-help"></a><span data-ttu-id="f2049-121">Selección de ubicación de la Ayuda del módulo</span><span class="sxs-lookup"><span data-stu-id="f2049-121">Placement of Module Help</span></span>

<span data-ttu-id="f2049-122">El `Get-Help` cmdlet busca los archivos de tema de Ayuda del módulo en subdirectorios específicos del lenguaje del directorio de módulo.</span><span class="sxs-lookup"><span data-stu-id="f2049-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="f2049-123">Por ejemplo, el diagrama de estructura de directorios siguiente muestra la ubicación de los temas de ayuda para el módulo SampleModule.</span><span class="sxs-lookup"><span data-stu-id="f2049-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="f2049-124">En el ejemplo, el  *\<ModulePath >* marcador de posición representa una de las rutas de acceso en el `PSModulePath` variable de entorno, como home\Documents\Modules $, $pshome\Modules o una ruta de acceso personalizada que especifica el usuario.</span><span class="sxs-lookup"><span data-stu-id="f2049-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="f2049-125">Obtención de Ayuda del módulo</span><span class="sxs-lookup"><span data-stu-id="f2049-125">Getting Module Help</span></span>

<span data-ttu-id="f2049-126">Cuando un usuario importa un módulo en una sesión, los temas de ayuda para dicho módulo se importan en la sesión junto con el módulo.</span><span class="sxs-lookup"><span data-stu-id="f2049-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="f2049-127">Puede enumerar los archivos de tema de ayuda en el valor de la clave de la lista de archivos en el manifiesto del módulo, pero los temas de ayuda no se ven afectados por la `Export-ModuleMember` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2049-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="f2049-128">Puede proporcionar temas de Ayuda de módulos en diferentes idiomas.</span><span class="sxs-lookup"><span data-stu-id="f2049-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="f2049-129">El `Get-Help` cmdlet muestra automáticamente los temas de Ayuda del módulo en el idioma que se especifica para el usuario actual en el elemento de configuración Regional y de idioma en el Panel de Control.</span><span class="sxs-lookup"><span data-stu-id="f2049-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="f2049-130">En Windows Vista y versiones posteriores de Windows, `Get-Help` busca en subdirectorios específicos del lenguaje del directorio de módulo según los estándares de reserva de idioma establecidas para Windows de los temas de ayuda.</span><span class="sxs-lookup"><span data-stu-id="f2049-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="f2049-131">A partir de Windows PowerShell 3.0, ejecutando un `Get-Help` comando de un cmdlet o función desencadena la importación automática del módulo.</span><span class="sxs-lookup"><span data-stu-id="f2049-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="f2049-132">El `Get-Help` cmdlet muestra inmediatamente el contenido de los temas de Ayuda del módulo.</span><span class="sxs-lookup"><span data-stu-id="f2049-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="f2049-133">Si el módulo no contiene los temas de ayuda y hay no hay temas de ayuda para los comandos en el módulo en el equipo del usuario, `Get-Help` muestra ayuda generada automáticamente.</span><span class="sxs-lookup"><span data-stu-id="f2049-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="f2049-134">La Ayuda generada automáticamente incluye la sintaxis de comandos, parámetros y tipos de entrada y salida, pero no incluye las descripciones.</span><span class="sxs-lookup"><span data-stu-id="f2049-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="f2049-135">La Ayuda generada automáticamente incluye el texto que se dirige al usuario al intentar usar el `Update-Help` para descargar la Ayuda de comandos de Internet o de un recurso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="f2049-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="f2049-136">También recomienda el uso de la **Online** parámetro de la `Get-Help` para obtener la versión en línea del tema de ayuda.</span><span class="sxs-lookup"><span data-stu-id="f2049-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="f2049-137">Compatibilidad con la ayuda actualizable</span><span class="sxs-lookup"><span data-stu-id="f2049-137">Supporting Updatable Help</span></span>

<span data-ttu-id="f2049-138">Los usuarios de Windows PowerShell 3.0 y versiones posteriores de Windows PowerShell pueden descargar e instalar archivos de Ayuda actualizados para un módulo desde Internet o desde un recurso compartido de archivos local.</span><span class="sxs-lookup"><span data-stu-id="f2049-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="f2049-139">El `Update-Help` y `Save-Help` cmdlets ocultar los detalles de administración del usuario.</span><span class="sxs-lookup"><span data-stu-id="f2049-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="f2049-140">Los usuarios ejecuten el `Update-Help` cmdlet y, a continuación, utilice el `Get-Help` cmdlet para leer los archivos de ayuda más recientes para el módulo en el símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2049-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="f2049-141">Los usuarios no es necesario reiniciar Windows o Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2049-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="f2049-142">Los usuarios detrás de firewalls y los que no tienen acceso a Internet pueden usar la Ayuda actualizable, también.</span><span class="sxs-lookup"><span data-stu-id="f2049-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="f2049-143">Los administradores con Internet acceso utilizan el `Save-Help` cmdlet para descargar e instalar los archivos de ayuda más recientes para un recurso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="f2049-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="f2049-144">A continuación, los usuarios utilizar el **ruta de acceso** parámetro de la `Update-Help` para obtener los archivos de ayuda más recientes desde el recurso compartido de archivos.</span><span class="sxs-lookup"><span data-stu-id="f2049-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="f2049-145">Los autores de módulos pueden incluir los archivos de ayuda en el módulo y usar la Ayuda actualizable para actualizar los archivos de ayuda, u omitir los archivos de Ayuda del módulo y usar la Ayuda actualizable para instalar y actualizarlos.</span><span class="sxs-lookup"><span data-stu-id="f2049-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="f2049-146">Para obtener más información sobre la Ayuda actualizable, consulte [compatibilidad con la Ayuda actualizable](./supporting-updatable-help.md).</span><span class="sxs-lookup"><span data-stu-id="f2049-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="f2049-147">Compatibilidad con la ayuda en línea</span><span class="sxs-lookup"><span data-stu-id="f2049-147">Supporting Online Help</span></span>

<span data-ttu-id="f2049-148">Los usuarios que no se pueden o no instalen actualizan ayuda archivos en sus equipos a menudo dependen de la versión en línea de temas de Ayuda del módulo.</span><span class="sxs-lookup"><span data-stu-id="f2049-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="f2049-149">El **Online** parámetro de la `Get-Help` cmdlet abre la versión en línea de un cmdlet o una función avanzada de tema de ayuda para el usuario en su explorador de Internet predeterminado.</span><span class="sxs-lookup"><span data-stu-id="f2049-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="f2049-150">El `Get-Help` cmdlet usa el valor de la **HelpUri** propiedad del cmdlet o función para buscar la versión en línea del tema de ayuda.</span><span class="sxs-lookup"><span data-stu-id="f2049-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="f2049-151">A partir de Windows PowerShell 3.0, puede ayudar a los usuarios encontrar la versión en línea de los temas de Ayuda de cmdlet y función definiendo el atributo HelpUri en la clase del cmdlet o **HelpUri** propiedad de la **CmdletBinding** atributo.</span><span class="sxs-lookup"><span data-stu-id="f2049-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="f2049-152">El valor del atributo es el valor de la **HelpUri** propiedad del cmdlet o función.</span><span class="sxs-lookup"><span data-stu-id="f2049-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="f2049-153">Para obtener más información, consulte [compatibilidad con la Ayuda en línea](./supporting-online-help.md).</span><span class="sxs-lookup"><span data-stu-id="f2049-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2049-154">Véase también</span><span class="sxs-lookup"><span data-stu-id="f2049-154">See Also</span></span>

[<span data-ttu-id="f2049-155">Escribir un módulo de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2049-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="f2049-156">Compatibilidad con la Ayuda actualizable</span><span class="sxs-lookup"><span data-stu-id="f2049-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="f2049-157">Compatibilidad con la Ayuda en línea</span><span class="sxs-lookup"><span data-stu-id="f2049-157">Supporting Online Help</span></span>](./supporting-online-help.md)