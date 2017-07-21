---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 8d5f8cc8c85d584b195483e464e878857629a78e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="37b6f-102">Cmdlets Clipboard</span><span class="sxs-lookup"><span data-stu-id="37b6f-102">Clipboard cmdlets</span></span>
<span data-ttu-id="37b6f-103">**Get-Clipboard** y **Set-Clipboard** facilitan la transferencia de contenido a y desde una sesión de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="37b6f-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="37b6f-104">Por ejemplo, si usa el Explorador de Windows para copiar tres archivos en el Portapapeles (seleccionándolos y presionando `ctrl-c`, por ejemplo), puede tener acceso sencillo al contenido del Portapapeles como una lista de archivos:</span><span class="sxs-lookup"><span data-stu-id="37b6f-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell 
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="37b6f-105">Los cmdlets Clipboard admiten imágenes, archivos de audio, listas de archivos y texto.</span><span class="sxs-lookup"><span data-stu-id="37b6f-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

