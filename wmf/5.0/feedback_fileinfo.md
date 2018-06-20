---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 63c3b8237a9883b147380dfe9cb173107cea9aa9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225647"
---
# <a name="updates-to-fileinfo-object"></a><span data-ttu-id="f5110-102">Actualizaciones del objeto FileInfo</span><span class="sxs-lookup"><span data-stu-id="f5110-102">Updates to FileInfo object</span></span>
<span data-ttu-id="f5110-103">La información de la versión de archivo puede ser errónea, especialmente en casos en el archivo se revisó.</span><span class="sxs-lookup"><span data-stu-id="f5110-103">File version information can be misleading, particularly in cases where the file was patched.</span></span> <span data-ttu-id="f5110-104">Esta versión de WMF 5.0 agrega las nuevas propiedades de script **FileVersionRaw** y **ProductVersionRaw** a los objetos FileInfo.</span><span class="sxs-lookup"><span data-stu-id="f5110-104">This release of WMF 5.0 adds new **FileVersionRaw** and **ProductVersionRaw** script properties to FileInfo objects.</span></span> <span data-ttu-id="f5110-105">Estas son las propiedades tal como se muestran para powershell.exe (teniendo en cuenta que $pid es el identificador del proceso de PowerShell):</span><span class="sxs-lookup"><span data-stu-id="f5110-105">Here are the properties as displayed for powershell.exe (assuming $pid is the ID of the PowerShell process):</span></span>

```powershell
PS C:\> Get-Process -Id $pid -FileVersionInfo | fl *version* -Force


FileVersionRaw    : 10.0.10586.117
ProductVersionRaw : 10.0.10586.117
FileVersion       : 10.0.10586.117 (th2_release.160212-2359)
ProductVersion    : 10.0.10586.117
