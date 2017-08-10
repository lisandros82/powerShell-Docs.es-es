---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: El objeto ISESnippetCollection
ms.assetid: ae974955-4282-4cbc-8c42-0fff1904ef32
ms.openlocfilehash: b19c5b5c88f7c8bd0d0c466c7861fa9288bdc7a2
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="fab51-103">El objeto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="fab51-103">The ISESnippetCollection Object</span></span>
  <span data-ttu-id="fab51-104">El objeto **ISESnippetCollection** es una colección de objetos **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="fab51-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="fab51-105">La colección de archivos que está asociada con un objeto **PowerShellTab** es un miembro de esta clase.</span><span class="sxs-lookup"><span data-stu-id="fab51-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="fab51-106">Un ejemplo es la colección **$psISE.CurrentPowerShellTab.Files**.</span><span class="sxs-lookup"><span data-stu-id="fab51-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="fab51-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="fab51-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="fab51-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="fab51-108">Load\( FilePathName \)</span></span>
  <span data-ttu-id="fab51-109">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="fab51-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="fab51-110">Carga un archivo .snippets.ps1xml que contiene fragmentos de código definidos por el usuario.</span><span class="sxs-lookup"><span data-stu-id="fab51-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="fab51-111">La manera más fácil de crear fragmentos de código es usar el cmdlet New\-IseSnippet, que los almacena automáticamente en la carpeta de perfil para que se carguen cada vez que inicie Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fab51-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

 <span data-ttu-id="fab51-112">**FilePathName** (cadena). La ruta de acceso y el nombre de un archivo .snippets.ps1xml que contiene las definiciones de fragmento de código.</span><span class="sxs-lookup"><span data-stu-id="fab51-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) “Snippets\MySnips.snippets.ps1xml” $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)

```

## <a name="see-also"></a><span data-ttu-id="fab51-113">Véase también</span><span class="sxs-lookup"><span data-stu-id="fab51-113">See Also</span></span>
- [<span data-ttu-id="fab51-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="fab51-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md) 
- [<span data-ttu-id="fab51-115">El modelo de objetos de scripting de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fab51-115">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="fab51-116">Referencia del modelo de objetos de ISE de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fab51-116">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="fab51-117">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="fab51-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
