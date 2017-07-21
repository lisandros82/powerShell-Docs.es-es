---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="516ec-102">Get-ChildItem tiene el parámetro -Depth</span><span class="sxs-lookup"><span data-stu-id="516ec-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="516ec-103">**Get-ChildItem** tiene ahora un parámetro **–Depth** que se usa con **–Recurse** para limitar la recursividad:</span><span class="sxs-lookup"><span data-stu-id="516ec-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="516ec-104">PS C:\\Usuarios\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="516ec-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="516ec-105">Directorio: C:\\Usuarios\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="516ec-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="516ec-106">Nombre Hora de última escritura Longitud Nombre</span><span class="sxs-lookup"><span data-stu-id="516ec-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="516ec-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="516ec-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="516ec-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="516ec-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="516ec-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="516ec-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="516ec-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="516ec-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="516ec-111">PS C:\\Usuarios\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="516ec-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="516ec-112">Directorio: C:\\Usuarios\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="516ec-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="516ec-113">Nombre Hora de última escritura Longitud Nombre</span><span class="sxs-lookup"><span data-stu-id="516ec-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="516ec-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="516ec-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="516ec-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="516ec-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="516ec-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="516ec-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="516ec-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="516ec-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="516ec-118">Directorio: C:\\Usuarios\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="516ec-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="516ec-119">Nombre Hora de última escritura Longitud Nombre</span><span class="sxs-lookup"><span data-stu-id="516ec-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="516ec-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="516ec-120">d----- 4/14/2015 5:33 PM Depth1</span></span>

