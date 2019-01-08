---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Apéndice 2 Crear un acceso directo de PowerShell personalizado
ms.assetid: 5d4fd421-5d43-4ec7-86fd-acfe887b066e
ms.openlocfilehash: e8081b7a64d313c8ef4bbccf95f250445dd68ad9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403377"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="8027e-103">Apéndice 2: Crear de un acceso directo de PowerShell personalizado</span><span class="sxs-lookup"><span data-stu-id="8027e-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="8027e-104">El siguiente procedimiento describe cómo crear un acceso directo a Windows PowerShell que tenga varias opciones prácticas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="8027e-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="8027e-105">Crear un acceso directo que apunte a Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="8027e-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="8027e-106">Haga clic con el botón derecho en el acceso directo y, después, haga clic en **Propiedades**.</span><span class="sxs-lookup"><span data-stu-id="8027e-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="8027e-107">Haga clic en la pestaña **Opciones**.</span><span class="sxs-lookup"><span data-stu-id="8027e-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="8027e-108">En la sección **Editar opciones**, active la casilla **Edición rápida**.</span><span class="sxs-lookup"><span data-stu-id="8027e-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="8027e-109">Esta configuración permite seleccionar texto en la ventana de la consola de Windows PowerShell arrastrando el botón izquierdo del ratón, así como copiar texto en el Portapapeles presionando ENTRAR o haciendo clic con el botón derecho.</span><span class="sxs-lookup"><span data-stu-id="8027e-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="8027e-110">En la sección **Editar opciones**, active la casilla **Modo de inserción**.</span><span class="sxs-lookup"><span data-stu-id="8027e-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="8027e-111">Esta configuración permite hacer clic con el botón derecho en la ventana de la consola para pegar texto automáticamente desde el Portapapeles.</span><span class="sxs-lookup"><span data-stu-id="8027e-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="8027e-112">En la sección **Historial de comandos**, escriba o seleccione un número entre 1 y 999 en el cuadro **Tamaño del búfer**.</span><span class="sxs-lookup"><span data-stu-id="8027e-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="8027e-113">Esta acción establece el número de comandos escritos que se mantendrán en el búfer de la consola.</span><span class="sxs-lookup"><span data-stu-id="8027e-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="8027e-114">En la sección **Historial de comandos**, active la casilla **Descartar duplicados antiguos** para eliminar los comandos repetidos del búfer de la consola.</span><span class="sxs-lookup"><span data-stu-id="8027e-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="8027e-115">Haga clic en la pestaña **Diseño**.</span><span class="sxs-lookup"><span data-stu-id="8027e-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="8027e-116">En la sección **Tamaño del búfer de pantalla** escriba un número entre 1 y 9999 en el cuadro **Alto**.</span><span class="sxs-lookup"><span data-stu-id="8027e-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="8027e-117">El alto representa el número de líneas de salida que se almacenan en búfer.</span><span class="sxs-lookup"><span data-stu-id="8027e-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="8027e-118">Este es el número máximo de líneas que se conservan para ver cuándo se desplaza por la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="8027e-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="8027e-119">Si este número es inferior al alto que se muestra en la sección **Tamaño de la ventana**, el alto del tamaño de la ventana se reducirá automáticamente al mismo valor.</span><span class="sxs-lookup"><span data-stu-id="8027e-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="8027e-120">En la sección **Tamaño de la ventana**, escriba un número entre 1 y 9999 para el ancho.</span><span class="sxs-lookup"><span data-stu-id="8027e-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="8027e-121">Este representa el número de caracteres que se muestran en la ventana de la consola.</span><span class="sxs-lookup"><span data-stu-id="8027e-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="8027e-122">El ancho predeterminado es 80 y el formato de salida de Windows PowerShell está diseñado para este ancho.</span><span class="sxs-lookup"><span data-stu-id="8027e-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="8027e-123">Si desea colocar la consola en un punto concreto del escritorio al abrirla, desactive la casilla **Dejar que el sistema ubique la ventana** en la sección **Posición de la ventana** y, luego, cambie los valores de los cuadros **Izquierda** y **Superior** de la sección **Posición de la ventana**.</span><span class="sxs-lookup"><span data-stu-id="8027e-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="8027e-124">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="8027e-124">Click **OK**.</span></span>