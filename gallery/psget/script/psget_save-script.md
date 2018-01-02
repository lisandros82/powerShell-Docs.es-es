---
ms.date: 2017-10-17
contributor: keithb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: b54e8ba074b7cadd52df781c9021332ccc90f9fd
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2017
---
# <a name="save-script"></a><span data-ttu-id="74505-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="74505-103">Save-Script</span></span>

<span data-ttu-id="74505-104">El cmdlet Save-Script permite revisar el archivo de script, para lo cual debe guardarse en una ubicación especificada.</span><span class="sxs-lookup"><span data-stu-id="74505-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="74505-105">Descripción</span><span class="sxs-lookup"><span data-stu-id="74505-105">Description</span></span>

<span data-ttu-id="74505-106">El cmdlet Save-Script guarda el script especificado.</span><span class="sxs-lookup"><span data-stu-id="74505-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="74505-107">Sintaxis de cmdlet</span><span class="sxs-lookup"><span data-stu-id="74505-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="74505-108">Referencia de la ayuda en línea de cmdlet</span><span class="sxs-lookup"><span data-stu-id="74505-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="74505-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="74505-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="74505-110">Comandos de ejemplo</span><span class="sxs-lookup"><span data-stu-id="74505-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="74505-111">Ejemplo 1: guardar un script desde un repositorio</span><span class="sxs-lookup"><span data-stu-id="74505-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="74505-112">Este comando guarda la versión más reciente del script Fabrikam-ClientScript desde el repositorio GalleryINT en la carpeta local C:\ScriptSharingDemo.</span><span class="sxs-lookup"><span data-stu-id="74505-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="74505-113">Ejemplo 2: guardar una versión de un script mediante la canalización desde el cmdlet Find-Script</span><span class="sxs-lookup"><span data-stu-id="74505-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="74505-114">El primer comando busca la versión 1.5 de Fabrikam-ClientScript desde el repositorio GalleryINT y lo guarda en la carpeta C:\ScriptSharingDemo.</span><span class="sxs-lookup"><span data-stu-id="74505-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="74505-115">El segundo comando valida los metadatos de script guardados.</span><span class="sxs-lookup"><span data-stu-id="74505-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="74505-116">Ejemplo 3: guardar una versión preliminar de un script desde un repositorio</span><span class="sxs-lookup"><span data-stu-id="74505-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="74505-117">Este comando guarda la versión más reciente del script Fabrikam-ClientScript desde el repositorio GalleryINT en la carpeta local C:\ScriptSharingDemo.</span><span class="sxs-lookup"><span data-stu-id="74505-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```

