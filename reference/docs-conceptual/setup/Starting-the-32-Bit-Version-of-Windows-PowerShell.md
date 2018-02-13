---
ms.date: 2017-06-05
keywords: powershell, cmdlet
title: "Iniciar la versión de 32 bits de Windows PowerShell"
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2018
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="74a31-103">Iniciar la versión de 32 bits de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="74a31-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="74a31-104">Al instalar Windows PowerShell en un equipo de 64 bits, **Windows PowerShell (x86)**, se instala una versión de 32 bits de Windows PowerShell además de la versión de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="74a31-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="74a31-105">Al ejecutar Windows PowerShell, la versión de 64 bits se ejecuta de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="74a31-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="74a31-106">Sin embargo, en ocasiones deberá ejecutar **Windows PowerShell (x86)**, como cuando usa un módulo que requiere la versión 32 bits o cuando se conecta de forma remota a un equipo de 32 bits.</span><span class="sxs-lookup"><span data-stu-id="74a31-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="74a31-107">Para iniciar una versión de 32 bits de Windows PowerShell, use uno de los procedimientos siguientes.</span><span class="sxs-lookup"><span data-stu-id="74a31-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="74a31-108">En Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="74a31-108">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="74a31-109">En la pantalla **Inicio**, escriba **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="74a31-110">Haga clic en el icono **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="74a31-110">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="74a31-111">En **Administrador del servidor**, desde el menú **Herramientas**, seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="74a31-112">En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell x86** y, a continuación, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="74a31-113">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="74a31-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="74a31-114">En Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="74a31-114">In Windows Server® 2012</span></span>

- <span data-ttu-id="74a31-115">En la página **Inicio**, escriba **Powershell** y, después, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="74a31-116">En **Administrador del servidor**, desde el menú **Herramientas**, seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="74a31-117">En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell** y, a continuación, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="74a31-118">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="74a31-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="74a31-119">En Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="74a31-119">In Windows® 8.1</span></span>

- <span data-ttu-id="74a31-120">En la pantalla **Inicio**, escriba **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="74a31-121">Haga clic en el icono **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="74a31-121">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="74a31-122">Si está ejecutando [Herramientas de administración remota del servidor](http://go.microsoft.com/fwlink/?LinkID=304145) para Windows 8.1, también puede abrir Windows PowerShell x86 desde el menú **Server Manager Tools** (Herramientas del administrador del servidor).</span><span class="sxs-lookup"><span data-stu-id="74a31-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="74a31-123">Seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-123">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="74a31-124">En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell x86** y, a continuación, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
- <span data-ttu-id="74a31-125">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="74a31-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="74a31-126">En Windows® 8</span><span class="sxs-lookup"><span data-stu-id="74a31-126">In Windows® 8</span></span>

- <span data-ttu-id="74a31-127">En la pantalla **Inicio**, mueva el cursor a la esquina superior derecha, haga clic en **Configuración**, haga clic en **Mosaicos** y, a continuación, mueva el control deslizante **Mostrar herramientas administrativas** a Sí.</span><span class="sxs-lookup"><span data-stu-id="74a31-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="74a31-128">A continuación, escriba **PowerShell** y haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="74a31-129">Si está ejecutando [Herramientas de administración remota del servidor](http://www.microsoft.com/download/details.aspx?id=28972) para Windows 8, también puede abrir Windows PowerShell x86 desde el menú **Server ManagerTools** (Herramientas del administrador del servidor).</span><span class="sxs-lookup"><span data-stu-id="74a31-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="74a31-130">Seleccione **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-130">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="74a31-131">En la página **Inicio** o en el escritorio, escriba **Powershell (x86)** y, después, haga clic en **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="74a31-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="74a31-132">Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="74a31-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

