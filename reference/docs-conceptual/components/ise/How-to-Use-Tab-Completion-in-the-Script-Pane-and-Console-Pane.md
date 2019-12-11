---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola
ms.openlocfilehash: 9fcb85668673adb1de596660d37e56f6607a4064
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67031001"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a><span data-ttu-id="8e69f-103">Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola</span><span class="sxs-lookup"><span data-stu-id="8e69f-103">How to Use Tab Completion in the Script Pane and Console Pane</span></span>

<span data-ttu-id="8e69f-104">La finalización con tabulación proporciona ayuda automática al escribir en el panel de scripts o el panel de comandos.</span><span class="sxs-lookup"><span data-stu-id="8e69f-104">Tab completion provides automatic help when you are typing in the Script Pane or in the Command Pane.</span></span> <span data-ttu-id="8e69f-105">Para aprovechar esta característica, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="8e69f-105">Use the following steps to take advantage of this feature:</span></span>

## <a name="to-automatically-complete-a-command-entry"></a><span data-ttu-id="8e69f-106">Para completar automáticamente una entrada de comando</span><span class="sxs-lookup"><span data-stu-id="8e69f-106">To automatically complete a command entry</span></span>

<span data-ttu-id="8e69f-107">En el panel de comandos o el panel de scripts, escriba algunos caracteres de un comando y, después, presione la tecla TAB para seleccionar el texto de finalización deseado.</span><span class="sxs-lookup"><span data-stu-id="8e69f-107">In the Command Pane or Script Pane, type a few characters of a command and then press TAB to select the desired completion text.</span></span> <span data-ttu-id="8e69f-108">Si varios elementos empiezan por el texto que ha escrito inicialmente, siga presionando la tecla Tab hasta que aparezca el elemento deseado.</span><span class="sxs-lookup"><span data-stu-id="8e69f-108">If multiple items begin with the text that you initially typed, then continue pressing Tab until the item you want appears.</span></span> <span data-ttu-id="8e69f-109">La finalización con tabulación puede ayudarle a escribir un nombre de cmdlet, de parámetro, de variable o de propiedad de objeto, o bien una ruta de acceso de archivo.</span><span class="sxs-lookup"><span data-stu-id="8e69f-109">Tab completion can help with typing a cmdlet name, parameter name, variable name, object property name, or a file path.</span></span>

> [!NOTE]
> <span data-ttu-id="8e69f-110">En el panel de scripts, al presionar TAB, se completa automáticamente un comando solo cuando se editan archivos .ps1, .psd1 o .psm1.</span><span class="sxs-lookup"><span data-stu-id="8e69f-110">In the Script Pane, pressing TAB will automatically complete a command only when you are editing .ps1, .psd1, or .psm1 files.</span></span> <span data-ttu-id="8e69f-111">La finalización con tabulación funciona siempre al escribir en el panel de comandos.</span><span class="sxs-lookup"><span data-stu-id="8e69f-111">Tab completion works any time when you are typing in the Command Pane.</span></span>

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a><span data-ttu-id="8e69f-112">Para completar automáticamente la entrada de un parámetro de cmdlet</span><span class="sxs-lookup"><span data-stu-id="8e69f-112">To automatically complete a cmdlet parameter entry</span></span>

<span data-ttu-id="8e69f-113">En el panel de comandos o el panel de scripts, escriba un cmdlet seguido por un guion y, después, presione la tecla Tab.</span><span class="sxs-lookup"><span data-stu-id="8e69f-113">In the Command Pane or Script pane, type a cmdlet followed by a dash and then press TAB.</span></span>

<span data-ttu-id="8e69f-114">Por ejemplo, escriba `Get-Process -` y, a continuación, presione TAB varias veces para mostrar cada uno de los parámetros del cmdlet de uno en uno.</span><span class="sxs-lookup"><span data-stu-id="8e69f-114">For example, type `Get-Process -` and then press TAB multiple times to display each of the parameters for the cmdlet in turn.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e69f-115">Véase también</span><span class="sxs-lookup"><span data-stu-id="8e69f-115">See Also</span></span>

- [<span data-ttu-id="8e69f-116">Presentación de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8e69f-116">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="8e69f-117">Cómo crear una pestaña de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8e69f-117">How to Create a PowerShell Tab</span></span>](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
