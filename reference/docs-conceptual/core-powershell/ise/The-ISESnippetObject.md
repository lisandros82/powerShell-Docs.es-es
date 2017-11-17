---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 6112f5252d2d1e868092da4a6cd04feb1875b597
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2017
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="4191d-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="4191d-103">The ISESnippetObject</span></span>
  <span data-ttu-id="4191d-104">Un objeto **ISESnippet** es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="4191d-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="4191d-105">Los miembros de la colección **$psISE.CurrentPowerShellTab.Snippets** son todos ejemplos de objetos **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="4191d-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="4191d-106">La manera más fácil de crear un fragmento de código es usar el cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).</span><span class="sxs-lookup"><span data-stu-id="4191d-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="4191d-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="4191d-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="4191d-108">Autor</span><span class="sxs-lookup"><span data-stu-id="4191d-108">Author</span></span>
  <span data-ttu-id="4191d-109">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="4191d-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="4191d-110">La propiedad de solo lectura que obtiene el nombre del autor del fragmento de código.</span><span class="sxs-lookup"><span data-stu-id="4191d-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

### <a name="codefragment"></a><span data-ttu-id="4191d-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="4191d-111">CodeFragment</span></span>
  <span data-ttu-id="4191d-112">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="4191d-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="4191d-113">La propiedad de solo lectura que obtiene el fragmento de código que va a insertar en el editor.</span><span class="sxs-lookup"><span data-stu-id="4191d-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

### <a name="shortcut"></a><span data-ttu-id="4191d-114">Directa</span><span class="sxs-lookup"><span data-stu-id="4191d-114">Shortcut</span></span>
  <span data-ttu-id="4191d-115">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="4191d-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="4191d-116">La propiedad de solo lectura que obtiene el método abreviado de teclado de Windows para el elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="4191d-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="4191d-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="4191d-117">See Also</span></span>
- [<span data-ttu-id="4191d-118">El objeto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="4191d-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md) 
- [<span data-ttu-id="4191d-119">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4191d-119">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="4191d-120">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4191d-120">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="4191d-121">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="4191d-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
