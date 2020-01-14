---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: ISESnippetObject
ms.openlocfilehash: 60456ec90f56753fa96f141b8b8299ef3f7e41c9
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736971"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="d9f6a-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="d9f6a-103">The ISESnippetObject</span></span>

<span data-ttu-id="d9f6a-104">Un objeto **ISESnippet** es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="d9f6a-105">Todos los miembros de la colección `$psISE.CurrentPowerShellTab.Snippets` son ejemplos de objetos **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-105">The members of the `$psISE.CurrentPowerShellTab.Snippets` collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="d9f6a-106">La manera más fácil de crear un fragmento de código es usar el cmdlet [New-IseSnippet](/reference/5.1/ISE/New-IseSnippet.md).</span><span class="sxs-lookup"><span data-stu-id="d9f6a-106">The easiest way to create a snippet is to use the [New-IseSnippet](/reference/5.1/ISE/New-IseSnippet.md) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="d9f6a-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="d9f6a-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="d9f6a-108">Autor</span><span class="sxs-lookup"><span data-stu-id="d9f6a-108">Author</span></span>

<span data-ttu-id="d9f6a-109">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d9f6a-110">La propiedad de solo lectura que obtiene el nombre del autor del fragmento de código.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="d9f6a-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="d9f6a-111">CodeFragment</span></span>

<span data-ttu-id="d9f6a-112">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d9f6a-113">La propiedad de solo lectura que obtiene el fragmento de código que va a insertar en el editor.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="d9f6a-114">Método abreviado</span><span class="sxs-lookup"><span data-stu-id="d9f6a-114">Shortcut</span></span>

<span data-ttu-id="d9f6a-115">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d9f6a-116">La propiedad de solo lectura que obtiene el método abreviado de teclado de Windows para el elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="d9f6a-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d9f6a-117">See Also</span></span>

- [<span data-ttu-id="d9f6a-118">El objeto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="d9f6a-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="d9f6a-119">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="d9f6a-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="d9f6a-120">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="d9f6a-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
