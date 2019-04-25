---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: d5ec95abb1d3160afc4179cff991cb5ef72d85fe
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057305"
---
# <a name="clipboard-cmdlets"></a>Cmdlets Clipboard
**Get-Clipboard** y **Set-Clipboard** facilitan la transferencia de contenido a y desde una sesión de Windows PowerShell. Por ejemplo, si usa el Explorador de Windows para copiar tres archivos en el Portapapeles (seleccionándolos y presionando `ctrl-c`, por ejemplo), puede tener acceso sencillo al contenido del Portapapeles como una lista de archivos:

```powershell
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


Los cmdlets Clipboard admiten imágenes, archivos de audio, listas de archivos y texto.
