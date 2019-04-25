---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: f80080f4207cf226fb7466c4842446d08c081347
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057985"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="d41e3-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="d41e3-103">The ISESnippetObject</span></span>

<span data-ttu-id="d41e3-104">Un objeto **ISESnippet** es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="d41e3-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="d41e3-105">Los miembros de la colección **$psISE.CurrentPowerShellTab.Snippets** son todos ejemplos de objetos **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="d41e3-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="d41e3-106">La manera más fácil de crear un fragmento de código es usar el cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).</span><span class="sxs-lookup"><span data-stu-id="d41e3-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="d41e3-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="d41e3-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="d41e3-108">Autor</span><span class="sxs-lookup"><span data-stu-id="d41e3-108">Author</span></span>

<span data-ttu-id="d41e3-109">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="d41e3-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d41e3-110">La propiedad de solo lectura que obtiene el nombre del autor del fragmento de código.</span><span class="sxs-lookup"><span data-stu-id="d41e3-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="d41e3-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="d41e3-111">CodeFragment</span></span>

<span data-ttu-id="d41e3-112">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="d41e3-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d41e3-113">La propiedad de solo lectura que obtiene el fragmento de código que va a insertar en el editor.</span><span class="sxs-lookup"><span data-stu-id="d41e3-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="d41e3-114">Directa</span><span class="sxs-lookup"><span data-stu-id="d41e3-114">Shortcut</span></span>

<span data-ttu-id="d41e3-115">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="d41e3-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d41e3-116">La propiedad de solo lectura que obtiene el método abreviado de teclado de Windows para el elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="d41e3-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="d41e3-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="d41e3-117">See Also</span></span>

- [<span data-ttu-id="d41e3-118">El objeto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="d41e3-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="d41e3-119">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d41e3-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="d41e3-120">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="d41e3-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)