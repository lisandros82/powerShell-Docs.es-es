---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085307"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="90a29-102">Get-ChildItem tiene el parámetro -Depth</span><span class="sxs-lookup"><span data-stu-id="90a29-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="90a29-103">**Get-ChildItem** tiene ahora un parámetro **–Depth** que se usa con **–Recurse** para limitar la recursividad:</span><span class="sxs-lookup"><span data-stu-id="90a29-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="90a29-104">PS C:\\Usuarios\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="90a29-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="90a29-105">Directorio: C:\\Usuarios\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="90a29-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="90a29-106">Nombre Hora de última escritura Longitud Nombre</span><span class="sxs-lookup"><span data-stu-id="90a29-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="90a29-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="90a29-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="90a29-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="90a29-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="90a29-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="90a29-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="90a29-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="90a29-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="90a29-111">PS C:\\Usuarios\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="90a29-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="90a29-112">Directorio: C:\\Usuarios\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="90a29-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="90a29-113">Nombre Hora de última escritura Longitud Nombre</span><span class="sxs-lookup"><span data-stu-id="90a29-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="90a29-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="90a29-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="90a29-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="90a29-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="90a29-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="90a29-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="90a29-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="90a29-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="90a29-118">Directorio: C:\\Usuarios\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="90a29-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="90a29-119">Nombre Hora de última escritura Longitud Nombre</span><span class="sxs-lookup"><span data-stu-id="90a29-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="90a29-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="90a29-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
