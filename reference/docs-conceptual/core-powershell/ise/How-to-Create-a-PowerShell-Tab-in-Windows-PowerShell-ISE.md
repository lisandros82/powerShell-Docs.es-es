---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Cómo crear una pestaña de PowerShell en Windows PowerShell ISE"
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 3cfeb18babe6b63f0e02da8cf0fd460950f1afce
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="4f54d-103">Cómo crear una pestaña de PowerShell en Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4f54d-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>
<span data-ttu-id="4f54d-104">Las pestañas del Entorno de scripting integrado de Windows PowerShell permiten crear y usar varios entornos de ejecución simultáneamente dentro de la misma aplicación.</span><span class="sxs-lookup"><span data-stu-id="4f54d-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="4f54d-105">Cada pestaña de PowerShell corresponde a una sesión o un entorno de ejecución independiente.</span><span class="sxs-lookup"><span data-stu-id="4f54d-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> <span data-ttu-id="4f54d-106">**NOTA**:</span><span class="sxs-lookup"><span data-stu-id="4f54d-106">**NOTE**:</span></span>
>
> <span data-ttu-id="4f54d-107">Las variables, las funciones y los alias que se crean en una pestaña no se mantienen en otra.</span><span class="sxs-lookup"><span data-stu-id="4f54d-107">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="4f54d-108">Son sesiones diferentes de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f54d-108">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="4f54d-109">Use los pasos siguientes para abrir o cerrar una pestaña en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f54d-109">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="4f54d-110">Para cambiar el nombre de una pestaña, configure la propiedad [DisplayName](The-PowerShellTab-Object.md#displayname) del objeto de scripting Tab de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f54d-110">To rename a tab, set the [DisplayName](The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="4f54d-111">Para crear y usar una nueva pestaña de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f54d-111">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="4f54d-112">En el menú **Archivo**, haga clic en **Nueva pestaña de PowerShell**. La nueva pestaña de PowerShell se abre siempre como la ventana activa.</span><span class="sxs-lookup"><span data-stu-id="4f54d-112">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="4f54d-113">Las pestañas de PowerShell se numeran de forma incremental en el orden en que se abren.</span><span class="sxs-lookup"><span data-stu-id="4f54d-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="4f54d-114">Cada pestaña está asociada a su propia ventana de la consola de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f54d-114">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="4f54d-115">Puede tener hasta 32 pestañas de PowerShell con su propia sesión abierta a la vez (este valor se limita a 8 en Windows PowerShell ISE 2.0).</span><span class="sxs-lookup"><span data-stu-id="4f54d-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="4f54d-116">Tenga en cuenta que al hacer clic en los iconos **Nuevo** o **Abrir** de la barra de herramientas no se crea una nueva pestaña con una sesión independiente.</span><span class="sxs-lookup"><span data-stu-id="4f54d-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="4f54d-117">En su lugar, estos botones abren un archivo de script nuevo o existente en la pestaña activa con una sesión.</span><span class="sxs-lookup"><span data-stu-id="4f54d-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="4f54d-118">Puede tener varios archivos de script abiertos con cada pestaña y cada sesión.</span><span class="sxs-lookup"><span data-stu-id="4f54d-118">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="4f54d-119">Las pestañas de script de una sesión solo aparecen debajo de las pestañas de la sesión cuando la sesión asociada está activa.</span><span class="sxs-lookup"><span data-stu-id="4f54d-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="4f54d-120">Para activar una pestaña de PowerShell, haga clic en ella. Para seleccionar entre las pestañas de PowerShell abiertas, en el menú **Ver**, haga clic en la pestaña de PowerShell que quiera usar.</span><span class="sxs-lookup"><span data-stu-id="4f54d-120">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="4f54d-121">Para crear y usar una pestaña de PowerShell remoto</span><span class="sxs-lookup"><span data-stu-id="4f54d-121">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="4f54d-122">En el menú **Archivo**, haga clic en **Nueva pestaña de PowerShell en remoto** para establecer una sesión en un equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="4f54d-122">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="4f54d-123">Aparece un cuadro de diálogo que le pide que escriba los detalles necesarios para establecer la conexión remota.</span><span class="sxs-lookup"><span data-stu-id="4f54d-123">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="4f54d-124">La pestaña remota funciona igual que una pestaña de PowerShell local, pero los comandos y los scripts se ejecutan en el equipo remoto.</span><span class="sxs-lookup"><span data-stu-id="4f54d-124">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="4f54d-125">Para cerrar la pestaña de PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f54d-125">To close a PowerShell Tab</span></span>

<span data-ttu-id="4f54d-126">Para cerrar una pestaña, puede usar cualquiera de las técnicas siguientes:</span><span class="sxs-lookup"><span data-stu-id="4f54d-126">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="4f54d-127">Haga clic en la pestaña que quiera cerrar.</span><span class="sxs-lookup"><span data-stu-id="4f54d-127">Click the tab that you want to close.</span></span>

- <span data-ttu-id="4f54d-128">En el menú **Archivo**, haga clic en **Cerrar pestaña de PowerShell**, o bien haga clic en el botón Cerrar (**X**) en una pestaña activa para cerrarla.</span><span class="sxs-lookup"><span data-stu-id="4f54d-128">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="4f54d-129">Si tiene archivos sin guardar abiertos en la pestaña de PowerShell que está cerrando, se le pedirá que los guarde o los descarte.</span><span class="sxs-lookup"><span data-stu-id="4f54d-129">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="4f54d-130">Para obtener más información acerca de cómo guardar un script, consulte [Cómo guardar un script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="4f54d-130">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="4f54d-131">Véase también</span><span class="sxs-lookup"><span data-stu-id="4f54d-131">See Also</span></span>

- [<span data-ttu-id="4f54d-132">Usar Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4f54d-132">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="4f54d-133">Cómo usar el panel de consola en Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="4f54d-133">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)

