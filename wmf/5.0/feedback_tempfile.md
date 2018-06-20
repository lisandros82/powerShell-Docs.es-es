---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34217998"
---
# <a name="new-temporaryfile"></a>New-TemporaryFile
A veces es necesario crear un archivo temporal en los scripts. Puede hacerlo fácilmente con el cmdlet **New-TemporaryFile**:

PS C:\\&gt; $tempFile = New-TemporaryFile

PS C:\\&gt; $tempFile.FullName

C:\\Usuarios\\slee\\AppData\\Local\\Temp\\tmp375.tmp
