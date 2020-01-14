---
ms.date: 12/31/2019
keywords: powershell, cmdlet
title: El objeto ISESnippetCollection
ms.openlocfilehash: 6cdc43dd1d82e94f66122d7f7b313c02e755fed7
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736052"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="78410-103">El objeto ISESnippetCollection</span><span class="sxs-lookup"><span data-stu-id="78410-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="78410-104">El objeto **ISESnippetCollection** es una colección de objetos **ISESnippet**.</span><span class="sxs-lookup"><span data-stu-id="78410-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="78410-105">La colección de archivos que está asociada con un objeto **PowerShellTab** es un miembro de esta clase.</span><span class="sxs-lookup"><span data-stu-id="78410-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="78410-106">Un ejemplo es la colección `$psISE.CurrentPowerShellTab.Files`.</span><span class="sxs-lookup"><span data-stu-id="78410-106">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="78410-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="78410-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="78410-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="78410-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="78410-109">Se admite en Windows PowerShell ISE 3.0 y versiones posteriores y no está presente en las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="78410-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="78410-110">Carga un archivo `.snippets.ps1xml` que contiene fragmentos de código definidos por el usuario.</span><span class="sxs-lookup"><span data-stu-id="78410-110">Loads a `.snippets.ps1xml` file that contains user-defined snippets.</span></span> <span data-ttu-id="78410-111">La manera más fácil de crear fragmentos de código es usar el cmdlet `New-IseSnippet`, que los almacena automáticamente en la carpeta de perfil para que se carguen cada vez que inicie Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="78410-111">The easiest way to create snippets is to use the `New-IseSnippet` cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="78410-112">**FilePathName** (cadena). La ruta de acceso y el nombre de un archivo .snippets.ps1xml que contiene las definiciones de fragmento de código.</span><span class="sxs-lookup"><span data-stu-id="78410-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="78410-113">Consulte también</span><span class="sxs-lookup"><span data-stu-id="78410-113">See Also</span></span>

- [<span data-ttu-id="78410-114">ISESnippetObject</span><span class="sxs-lookup"><span data-stu-id="78410-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="78410-115">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="78410-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="78410-116">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="78410-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
