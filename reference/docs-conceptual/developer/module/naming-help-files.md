---
title: Asignar nombres a los archivos de ayuda | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367014"
---
# <a name="naming-help-files"></a><span data-ttu-id="f6e37-102">Asignación de un nombre a los archivos de ayuda</span><span class="sxs-lookup"><span data-stu-id="f6e37-102">Naming Help Files</span></span>

<span data-ttu-id="f6e37-103">En este tema se explica cómo asignar un nombre a un archivo de ayuda basado en XML para que el cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) pueda encontrarlo.</span><span class="sxs-lookup"><span data-stu-id="f6e37-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="f6e37-104">Los requisitos de nombre difieren para cada tipo de comando.</span><span class="sxs-lookup"><span data-stu-id="f6e37-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="f6e37-105">Archivos de ayuda de cmdlet</span><span class="sxs-lookup"><span data-stu-id="f6e37-105">Cmdlet Help Files</span></span>

<span data-ttu-id="f6e37-106">El archivo de ayuda de C# un cmdlet se debe denominar para el ensamblado en el que se define el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f6e37-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="f6e37-107">Use el siguiente formato de nombre de archivo:</span><span class="sxs-lookup"><span data-stu-id="f6e37-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="f6e37-108">El formato del nombre del ensamblado es necesario incluso cuando el ensamblado es un módulo anidado.</span><span class="sxs-lookup"><span data-stu-id="f6e37-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="f6e37-109">Por ejemplo, [Get-WinEvent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) se define en el ensamblado Microsoft. PowerShell. Diagnostics. dll.</span><span class="sxs-lookup"><span data-stu-id="f6e37-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="f6e37-110">El cmdlet `Get-Help` busca un tema de ayuda para el cmdlet `Get-WinEvent` solo en el archivo Microsoft. PowerShell. Diagnostics. dll-help. XML en el directorio del módulo.</span><span class="sxs-lookup"><span data-stu-id="f6e37-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="f6e37-111">Archivos de ayuda del proveedor</span><span class="sxs-lookup"><span data-stu-id="f6e37-111">Provider Help files</span></span>

<span data-ttu-id="f6e37-112">El archivo de ayuda de un proveedor de Windows PowerShell debe tener un nombre para el ensamblado en el que se define el proveedor.</span><span class="sxs-lookup"><span data-stu-id="f6e37-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="f6e37-113">Use el siguiente formato de nombre de archivo:</span><span class="sxs-lookup"><span data-stu-id="f6e37-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="f6e37-114">El formato del nombre del ensamblado es necesario incluso cuando el ensamblado es un módulo anidado.</span><span class="sxs-lookup"><span data-stu-id="f6e37-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="f6e37-115">Por ejemplo, el proveedor de certificados se define en el ensamblado Microsoft. PowerShell. Security. dll.</span><span class="sxs-lookup"><span data-stu-id="f6e37-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="f6e37-116">El cmdlet `Get-Help` busca un tema de ayuda para el proveedor de certificados solo en el archivo Microsoft. PowerShell. Security. dll-help. XML en el directorio del módulo.</span><span class="sxs-lookup"><span data-stu-id="f6e37-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="f6e37-117">Archivos de ayuda de función</span><span class="sxs-lookup"><span data-stu-id="f6e37-117">Function Help Files</span></span>

<span data-ttu-id="f6e37-118">Las funciones se pueden documentar mediante [la ayuda basada en comentarios](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) o documentada en un archivo de ayuda XML.</span><span class="sxs-lookup"><span data-stu-id="f6e37-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="f6e37-119">Cuando la función está documentada en un archivo XML, la función debe tener una palabra clave `.ExternalHelp` comment que asocie la función con el archivo XML.</span><span class="sxs-lookup"><span data-stu-id="f6e37-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="f6e37-120">De lo contrario, el cmdlet `Get-Help` no puede encontrar el archivo de ayuda.</span><span class="sxs-lookup"><span data-stu-id="f6e37-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="f6e37-121">No hay ningún requisito técnico para el nombre de un archivo de ayuda de función.</span><span class="sxs-lookup"><span data-stu-id="f6e37-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="f6e37-122">Sin embargo, se recomienda asignar un nombre al archivo de ayuda para el módulo de script en el que se define la función.</span><span class="sxs-lookup"><span data-stu-id="f6e37-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="f6e37-123">Por ejemplo, la siguiente función se define en el archivo MyModule. psm1.</span><span class="sxs-lookup"><span data-stu-id="f6e37-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="f6e37-124">Archivos de ayuda de comandos CIM</span><span class="sxs-lookup"><span data-stu-id="f6e37-124">CIM Command Help Files</span></span>

<span data-ttu-id="f6e37-125">El archivo de ayuda de un comando CIM debe tener el nombre del archivo CDXML en el que se define el comando CIM.</span><span class="sxs-lookup"><span data-stu-id="f6e37-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="f6e37-126">Use el siguiente formato de nombre de archivo:</span><span class="sxs-lookup"><span data-stu-id="f6e37-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="f6e37-127">Los comandos CIM se definen en los archivos CDXML que se pueden incluir en los módulos como módulos anidados.</span><span class="sxs-lookup"><span data-stu-id="f6e37-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="f6e37-128">Cuando el comando CIM se importa en la sesión como una función, Windows PowerShell agrega una palabra clave de comentario `.ExternalHelp` a la definición de función que asocia la función a un archivo de ayuda XML denominado para el archivo CDXML en el que se define el comando CIM.</span><span class="sxs-lookup"><span data-stu-id="f6e37-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="f6e37-129">Archivos de ayuda del flujo de trabajo de script</span><span class="sxs-lookup"><span data-stu-id="f6e37-129">Script Workflow Help Files</span></span>

<span data-ttu-id="f6e37-130">Los flujos de trabajo de script que se incluyen en los módulos se pueden documentar en archivos de ayuda basados en XML.</span><span class="sxs-lookup"><span data-stu-id="f6e37-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="f6e37-131">No hay ningún requisito técnico para el nombre del archivo de ayuda.</span><span class="sxs-lookup"><span data-stu-id="f6e37-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="f6e37-132">Sin embargo, se recomienda asignar un nombre al archivo de ayuda para el módulo de script en el que se define el flujo de trabajo de script.</span><span class="sxs-lookup"><span data-stu-id="f6e37-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="f6e37-133">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f6e37-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="f6e37-134">A diferencia de otros comandos scripts, los flujos de trabajo de scripts no requieren una palabra clave `.ExternalHelp` comment para asociarlos con un archivo de ayuda.</span><span class="sxs-lookup"><span data-stu-id="f6e37-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="f6e37-135">En su lugar, Windows PowerShell busca en los subdirectorios específicos de la referencia cultural de la interfaz de usuario del directorio de módulos para los archivos de ayuda basados en XML y busca ayuda para el flujo de trabajo de script en todos los archivos.</span><span class="sxs-lookup"><span data-stu-id="f6e37-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="f6e37-136">`.ExternalHelp` palabra clave comment se omiten.</span><span class="sxs-lookup"><span data-stu-id="f6e37-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="f6e37-137">Dado que se omite la palabra clave `.ExternalHelp` comment, el cmdlet `Get-Help` puede buscar ayuda para flujos de trabajo de scripts solo cuando se incluyen en módulos.</span><span class="sxs-lookup"><span data-stu-id="f6e37-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>