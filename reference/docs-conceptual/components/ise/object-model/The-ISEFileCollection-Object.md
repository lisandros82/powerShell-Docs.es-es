---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: El objeto ISEFileCollection
ms.openlocfilehash: 96db51ee921cc0fa34803091d563bc6e118643b6
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030522"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="208d6-103">El objeto ISEFileCollection</span><span class="sxs-lookup"><span data-stu-id="208d6-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="208d6-104">El objeto **ISEFileCollection** es una colección de objetos **ISEFile**.</span><span class="sxs-lookup"><span data-stu-id="208d6-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="208d6-105">Un ejemplo es la colección $psISE.CurrentPowerShellTab.Files.</span><span class="sxs-lookup"><span data-stu-id="208d6-105">An example is the $psISE.CurrentPowerShellTab.Files collection.</span></span>

## <a name="methods"></a><span data-ttu-id="208d6-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="208d6-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="208d6-107">Add\( \[fullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="208d6-107">Add\( \[fullPath\] \)</span></span>

<span data-ttu-id="208d6-108">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="208d6-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="208d6-109">Crea y devuelve un archivo sin título nuevo y lo agrega a la colección.</span><span class="sxs-lookup"><span data-stu-id="208d6-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="208d6-110">La propiedad **IsUntitled** del archivo recién creado es **$true**.</span><span class="sxs-lookup"><span data-stu-id="208d6-110">The **IsUntitled** property of the newly created file is **$true**.</span></span>

<span data-ttu-id="208d6-111">**\[fullPath\]** : cadena opcional. Ruta de acceso completamente especificada del archivo.</span><span class="sxs-lookup"><span data-stu-id="208d6-111">**\[fullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="208d6-112">Se genera una excepción si incluye el parámetro **rutaAccesoCompleta** y una ruta de acceso relativa, o si utiliza un nombre de archivo en lugar de la ruta de acceso completa.</span><span class="sxs-lookup"><span data-stu-id="208d6-112">An exception is generated if you include the **fullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="208d6-113">Remove\( File, \[Force\] \)</span><span class="sxs-lookup"><span data-stu-id="208d6-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="208d6-114">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="208d6-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="208d6-115">Quita un archivo especificado en la pestaña actual de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="208d6-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="208d6-116">**File**: cadena. Archivo ISEFile que quiere quitar de la colección.</span><span class="sxs-lookup"><span data-stu-id="208d6-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="208d6-117">Si el archivo no se ha guardado, este método inicia una excepción.</span><span class="sxs-lookup"><span data-stu-id="208d6-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="208d6-118">Utilice el parámetro modificador **Force** parámetro para forzar la eliminación de un archivo no guardado.</span><span class="sxs-lookup"><span data-stu-id="208d6-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="208d6-119">**\[Force\]** : booleano opcional. Si se establece en **$true**, concede permiso para quitar el archivo incluso si no se ha guardado después del último uso.</span><span class="sxs-lookup"><span data-stu-id="208d6-119">**\[Force\]** - optional Boolean If set to **$true**, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="208d6-120">El valor predeterminado es **$false**.</span><span class="sxs-lookup"><span data-stu-id="208d6-120">The default is **$false**.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="208d6-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="208d6-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="208d6-122">Se admite en Windows PowerShell ISE 2.0 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="208d6-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="208d6-123">Selecciona el archivo que especifica el parámetro **archivoSeleccionado**.</span><span class="sxs-lookup"><span data-stu-id="208d6-123">Selects the file that is specified by the **selectedFile** parameter.</span></span>

<span data-ttu-id="208d6-124">**selectedFile**: Microsoft.PowerShell.Host.ISE.ISEFile. Archivo ISEFile que quiere seleccionar.</span><span class="sxs-lookup"><span data-stu-id="208d6-124">**selectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="208d6-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="208d6-125">See Also</span></span>

- [<span data-ttu-id="208d6-126">El objeto ISEFile</span><span class="sxs-lookup"><span data-stu-id="208d6-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="208d6-127">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="208d6-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="208d6-128">La jerarquía del modelo de objetos de ISE</span><span class="sxs-lookup"><span data-stu-id="208d6-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
