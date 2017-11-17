---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Introducción a Windows PowerShell ISE"
ms.openlocfilehash: 75242c20548e2e83397867214417a48806c897ec
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="bd02d-103">Introducción a Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="bd02d-103">Introducing the Windows PowerShell ISE</span></span>
<span data-ttu-id="bd02d-104">Windows PowerShell Integrated Scripting Environment (ISE) es una aplicación host de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd02d-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="bd02d-105">En Windows PowerShell ISE, puede ejecutar comandos y escribir, comprobar y depurar scripts en una sola interfaz gráfica de usuario basada en Windows mediante la edición de varias líneas, la finalización con tabulación, el color de sintaxis, la ejecución selectiva, la ayuda contextual y la compatibilidad con idiomas que se leen de derecha a izquierda.</span><span class="sxs-lookup"><span data-stu-id="bd02d-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface with multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span>
<span data-ttu-id="bd02d-106">Puede usar elementos de menú y métodos abreviados de teclado para realizar muchas de las mismas tareas que realizaría en la consola de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd02d-106">You can use menu items and keyboard shortcuts to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span>  <span data-ttu-id="bd02d-107">Por ejemplo, si depura un script en Windows PowerShell ISE, para establecer un punto de interrupción de la línea en un script puede hacer clic con el botón derecho en la línea de código y luego hacer clic en **Alternar punto de interrupción**.</span><span class="sxs-lookup"><span data-stu-id="bd02d-107">For example, when you debug a script in the Windows PowerShell ISE, to set a line breakpoint in a script, right-click the line of code, and then click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="bd02d-108">Pruebe estas características de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bd02d-108">Try these features in Windows PowerShell ISE.</span></span>

- <span data-ttu-id="bd02d-109">Edición de varias líneas: para insertar una línea en blanco debajo de la línea actual en el panel Comando, presione MAYÚS+ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="bd02d-109">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>

- <span data-ttu-id="bd02d-110">Ejecución selectiva: para ejecutar parte de un script, seleccione el texto que desea ejecutar y, a continuación, haga clic en el botón **Ejecutar script**.</span><span class="sxs-lookup"><span data-stu-id="bd02d-110">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="bd02d-111">También puede presionar F5.</span><span class="sxs-lookup"><span data-stu-id="bd02d-111">Or, press F5.</span></span>

- <span data-ttu-id="bd02d-112">Ayuda contextual: escriba **Invoke-Item** y después presione F1.</span><span class="sxs-lookup"><span data-stu-id="bd02d-112">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="bd02d-113">El archivo de ayuda se abre en el tema de Ayuda correspondiente al cmdlet **Invoke-Item**.</span><span class="sxs-lookup"><span data-stu-id="bd02d-113">The Help file opens to the Help topic for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="bd02d-114">Windows PowerShell ISE permite personalizar algunos aspectos de su apariencia.</span><span class="sxs-lookup"><span data-stu-id="bd02d-114">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="bd02d-115">También tiene su propio perfil de Windows PowerShell, donde puede almacenar las funciones, los alias, las variables y los comandos que usa en Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="bd02d-115">It also has its own Windows PowerShell profile, where you can store functions, aliases, variables, and commands you use in the Windows PowerShell ISE.</span></span>

### <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="bd02d-116">Para iniciar Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="bd02d-116">To start the Windows PowerShell ISE</span></span>

1. <span data-ttu-id="bd02d-117">Realice una de las siguientes acciones:</span><span class="sxs-lookup"><span data-stu-id="bd02d-117">Do one of the following:</span></span>

    -   <span data-ttu-id="bd02d-118">Haga clic en **Inicio**, elija **Todos los programas** y **Windows Powershell V2** y, después, haga clic en **Windows Powershell ISE**.</span><span class="sxs-lookup"><span data-stu-id="bd02d-118">Click **Start**, point to **All Programs**, point to **Windows PowerShell V2**, and then click **Windows PowerShell ISE**.</span></span>

    -   <span data-ttu-id="bd02d-119">En Cmd.exe en la consola de Windows PowerShell, o en el cuadro Ejecutar, escriba **powershell_ise.exe**.</span><span class="sxs-lookup"><span data-stu-id="bd02d-119">In the Windows PowerShell console Cmd.exe, or in the Run box, type, **powershell_ise.exe**.</span></span>

### <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="bd02d-120">Para obtener ayuda de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="bd02d-120">To get Help in the Windows PowerShell ISE</span></span>

- <span data-ttu-id="bd02d-121">En el menú **Ayuda**, haga clic en **Ayuda de Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="bd02d-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="bd02d-122">También puede presionar F1.</span><span class="sxs-lookup"><span data-stu-id="bd02d-122">Or, press F1.</span></span> <span data-ttu-id="bd02d-123">El archivo que se abre contiene información detallada sobre Windows PowerShell ISE y Windows PowerShell, además de toda la ayuda disponible en el cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="bd02d-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>

