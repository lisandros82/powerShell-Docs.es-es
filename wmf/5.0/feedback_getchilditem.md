---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 62cccabd7c63c6ba928fc2bf8addd3d11483e90f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="7ce30-102">Get-ChildItem tiene el parámetro -Depth</span><span class="sxs-lookup"><span data-stu-id="7ce30-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="7ce30-103">**Get-ChildItem** tiene ahora un parámetro **–Depth** que se usa con **–Recurse** para limitar la recursividad:</span><span class="sxs-lookup"><span data-stu-id="7ce30-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="7ce30-104">PS C:\\Usuarios\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="7ce30-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="7ce30-105">Directorio: C:\\Usuarios\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="7ce30-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="7ce30-106">Nombre Hora de última escritura Longitud Nombre</span><span class="sxs-lookup"><span data-stu-id="7ce30-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="7ce30-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="7ce30-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="7ce30-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="7ce30-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="7ce30-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="7ce30-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="7ce30-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="7ce30-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="7ce30-111">PS C:\\Usuarios\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="7ce30-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="7ce30-112">Directorio: C:\\Usuarios\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="7ce30-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="7ce30-113">Nombre Hora de última escritura Longitud Nombre</span><span class="sxs-lookup"><span data-stu-id="7ce30-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="7ce30-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="7ce30-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="7ce30-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="7ce30-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="7ce30-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="7ce30-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="7ce30-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="7ce30-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="7ce30-118">Directorio: C:\\Usuarios\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="7ce30-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="7ce30-119">Nombre Hora de última escritura Longitud Nombre</span><span class="sxs-lookup"><span data-stu-id="7ce30-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="7ce30-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="7ce30-120">d----- 4/14/2015 5:33 PM Depth1</span></span>