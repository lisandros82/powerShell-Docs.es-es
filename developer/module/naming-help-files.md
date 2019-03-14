---
title: Nomenclatura de archivos de ayuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795358"
---
# <a name="naming-help-files"></a><span data-ttu-id="c5596-102">Asignación de un nombre a los archivos de ayuda</span><span class="sxs-lookup"><span data-stu-id="c5596-102">Naming Help Files</span></span>

<span data-ttu-id="c5596-103">En este tema se explica cómo asignar un nombre de un archivo de ayuda basado en XML para que la [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet puede encontrarlo.</span><span class="sxs-lookup"><span data-stu-id="c5596-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="c5596-104">Los requisitos de nombre varían para cada tipo de comando.</span><span class="sxs-lookup"><span data-stu-id="c5596-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="c5596-105">Archivos de Ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="c5596-105">Cmdlet Help Files</span></span>

<span data-ttu-id="c5596-106">El archivo de ayuda para un C# cmdlet debe tener el nombre del ensamblado donde se define el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c5596-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="c5596-107">Use el siguiente formato de nombre de archivo:</span><span class="sxs-lookup"><span data-stu-id="c5596-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="c5596-108">El formato de nombre de ensamblado es necesario incluso si el ensamblado es un módulo anidado.</span><span class="sxs-lookup"><span data-stu-id="c5596-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="c5596-109">Por ejemplo, el [Get-WinEvent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet se define en el ensamblado Microsoft.PowerShell.Diagnostics.dll.</span><span class="sxs-lookup"><span data-stu-id="c5596-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="c5596-110">El `Get-Help` cmdlet busca un tema de ayuda para el `Get-WinEvent` cmdlet solo en el archivo Microsoft.PowerShell.Diagnostics.dll help.xml en el directorio del módulo.</span><span class="sxs-lookup"><span data-stu-id="c5596-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="c5596-111">Archivos de Ayuda de proveedor</span><span class="sxs-lookup"><span data-stu-id="c5596-111">Provider Help files</span></span>

<span data-ttu-id="c5596-112">El archivo de ayuda para un proveedor de Windows PowerShell debe llamarse para el ensamblado en el que se define el proveedor.</span><span class="sxs-lookup"><span data-stu-id="c5596-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="c5596-113">Use el siguiente formato de nombre de archivo:</span><span class="sxs-lookup"><span data-stu-id="c5596-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="c5596-114">El formato de nombre de ensamblado es necesario incluso si el ensamblado es un módulo anidado.</span><span class="sxs-lookup"><span data-stu-id="c5596-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="c5596-115">Por ejemplo, el proveedor de certificados se define en el ensamblado Microsoft.PowerShell.Security.dll.</span><span class="sxs-lookup"><span data-stu-id="c5596-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="c5596-116">El `Get-Help` cmdlet busca un tema de ayuda para el proveedor de certificados solo en el archivo Microsoft.PowerShell.Security.dll help.xml en el directorio del módulo.</span><span class="sxs-lookup"><span data-stu-id="c5596-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="c5596-117">Archivos de Ayuda de función</span><span class="sxs-lookup"><span data-stu-id="c5596-117">Function Help Files</span></span>

<span data-ttu-id="c5596-118">Se pueden documentar las funciones mediante el uso de [Ayuda basada en comentarios](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentados en un archivo de ayuda XML.</span><span class="sxs-lookup"><span data-stu-id="c5596-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="c5596-119">Cuando la función está documentada en un archivo XML, la función debe tener un `.ExternalHelp` comentar la palabra clave que asocia la función con el archivo XML.</span><span class="sxs-lookup"><span data-stu-id="c5596-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="c5596-120">En caso contrario, el `Get-Help` cmdlet no encuentra el archivo de ayuda.</span><span class="sxs-lookup"><span data-stu-id="c5596-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="c5596-121">No hay ningún requisito técnico para el nombre de un archivo de Ayuda de la función.</span><span class="sxs-lookup"><span data-stu-id="c5596-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="c5596-122">Sin embargo, una práctica recomendada es un nombre al archivo de ayuda para el módulo de script en el que se define la función.</span><span class="sxs-lookup"><span data-stu-id="c5596-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="c5596-123">Por ejemplo, la siguiente función se define en el archivo MyModule.psm1.</span><span class="sxs-lookup"><span data-stu-id="c5596-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="c5596-124">Archivos de Ayuda de comandos CIM</span><span class="sxs-lookup"><span data-stu-id="c5596-124">CIM Command Help Files</span></span>

<span data-ttu-id="c5596-125">El archivo de ayuda para un comando CIM debe llamarse para el archivo CDXML en el que se define el comando CIM.</span><span class="sxs-lookup"><span data-stu-id="c5596-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="c5596-126">Use el siguiente formato de nombre de archivo:</span><span class="sxs-lookup"><span data-stu-id="c5596-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="c5596-127">Los comandos CIM se definen en los archivos CDXML que pueden incluirse en módulos como módulos anidados.</span><span class="sxs-lookup"><span data-stu-id="c5596-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="c5596-128">Cuando se importa el comando CIM en la sesión como una función, Windows PowerShell agrega un `.ExternalHelp` comentario palabra clave para la definición de función que se asocia un ayuda XML a la función de archivo que se denomina para el archivo CDXML en el que se define el comando CIM.</span><span class="sxs-lookup"><span data-stu-id="c5596-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="c5596-129">Archivos de Ayuda de flujo de trabajo de script</span><span class="sxs-lookup"><span data-stu-id="c5596-129">Script Workflow Help Files</span></span>

<span data-ttu-id="c5596-130">Los flujos de trabajo que se incluyen en los módulos pueden documentarse en archivos de ayuda basado en XML.</span><span class="sxs-lookup"><span data-stu-id="c5596-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="c5596-131">No hay ningún requisito técnico para el nombre del archivo de ayuda.</span><span class="sxs-lookup"><span data-stu-id="c5596-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="c5596-132">Sin embargo, una práctica recomendada es un nombre al archivo de ayuda para el módulo de script en el que se define el flujo de trabajo de script.</span><span class="sxs-lookup"><span data-stu-id="c5596-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="c5596-133">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c5596-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="c5596-134">A diferencia de otros archivos de comandos, los flujos de trabajo no requieren un `.ExternalHelp` comentar la palabra clave para asociarlos a un archivo de ayuda.</span><span class="sxs-lookup"><span data-stu-id="c5596-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="c5596-135">En su lugar, Windows PowerShell busca los subdirectorios específicos de la referencia cultural de interfaz de usuario del directorio de módulo para los archivos de ayuda basado en XML y busca ayuda para el flujo de trabajo de script en todos los archivos.</span><span class="sxs-lookup"><span data-stu-id="c5596-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="c5596-136">`.ExternalHelp` se omite la palabra clave de comentario.</span><span class="sxs-lookup"><span data-stu-id="c5596-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="c5596-137">Dado que el `.ExternalHelp` se omite la palabra clave de comentario, el `Get-Help` cmdlet puede encontrar ayuda para los flujos de trabajo solo cuando se incluyen en los módulos.</span><span class="sxs-lookup"><span data-stu-id="c5596-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>