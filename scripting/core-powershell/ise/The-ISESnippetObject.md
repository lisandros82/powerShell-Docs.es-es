---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: ISESnippetObject
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 5cc49cd504a1343a5737f78eb886bb41591d087d
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="0b8c2-103">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="0b8c2-103">The ISESnippetObject</span></span>
  <span data-ttu-id="0b8c2-104">Un objeto **ISESnippet** es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISESnippet.</span><span class="sxs-lookup"><span data-stu-id="0b8c2-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="0b8c2-105">Los miembros de la colección **$psISE.CurrentPowerShellTab.Snippets** son todos ejemplos de objetos **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="0b8c2-105">The members of the **$psISE.CurrentPowerShellTab.Snippets** collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="0b8c2-106">La manera más fácil de crear un fragmento de código es usar el cmdlet [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0).</span><span class="sxs-lookup"><span data-stu-id="0b8c2-106">The easiest way to create a snippet is to use the [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="0b8c2-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="0b8c2-107">Properties</span></span>

###  <span data-ttu-id="0b8c2-108"><a name="DisplayName"></a> Author</span><span class="sxs-lookup"><span data-stu-id="0b8c2-108"><a name="DisplayName"></a> Author</span></span>
  <span data-ttu-id="0b8c2-109">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="0b8c2-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="0b8c2-110">La propiedad de solo lectura que obtiene el nombre del autor del fragmento de código.</span><span class="sxs-lookup"><span data-stu-id="0b8c2-110">The read-only property that gets the name of the author of the snippet.</span></span>

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

###  <span data-ttu-id="0b8c2-111"><a name="Action"></a> CodeFragment</span><span class="sxs-lookup"><span data-stu-id="0b8c2-111"><a name="Action"></a> CodeFragment</span></span>
  <span data-ttu-id="0b8c2-112">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="0b8c2-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="0b8c2-113">La propiedad de solo lectura que obtiene el fragmento de código que va a insertar en el editor.</span><span class="sxs-lookup"><span data-stu-id="0b8c2-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

###  <span data-ttu-id="0b8c2-114"><a name="Shortcut"></a> Shortcut</span><span class="sxs-lookup"><span data-stu-id="0b8c2-114"><a name="Shortcut"></a> Shortcut</span></span>
  <span data-ttu-id="0b8c2-115">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="0b8c2-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="0b8c2-116">La propiedad de solo lectura que obtiene el método abreviado de teclado de Windows para el elemento de menú.</span><span class="sxs-lookup"><span data-stu-id="0b8c2-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="0b8c2-117">Véase también</span><span class="sxs-lookup"><span data-stu-id="0b8c2-117">See Also</span></span>
- [<span data-ttu-id="0b8c2-118">El objeto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="0b8c2-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md) 
- [<span data-ttu-id="0b8c2-119">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b8c2-119">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="0b8c2-120">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="0b8c2-120">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="0b8c2-121">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="0b8c2-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
