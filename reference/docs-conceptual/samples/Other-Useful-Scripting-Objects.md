---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Otros objetos de scripting útiles
ms.openlocfilehash: 4f236246714b0608658bbd535851489912430336
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71325155"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="c3824-103">Otros objetos de scripting útiles</span><span class="sxs-lookup"><span data-stu-id="c3824-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="c3824-104">Los objetos siguientes proporcionan funcionalidad adicional de scripting de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c3824-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="c3824-105">No forman parte de la jerarquía de **$psISE**.</span><span class="sxs-lookup"><span data-stu-id="c3824-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="c3824-106">Objetos de scripting útiles</span><span class="sxs-lookup"><span data-stu-id="c3824-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="c3824-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="c3824-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="c3824-108">Existen algunas limitaciones sobre cómo Windows PowerShell ISE interactúa con las aplicaciones de consola.</span><span class="sxs-lookup"><span data-stu-id="c3824-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="c3824-109">Un comando o un script de automatización que requiere la intervención de usuario podrían no funcionar de la misma forma que desde la consola de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c3824-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="c3824-110">Puede bloquear la ejecución de estos comandos o scripts en el panel de comandos de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="c3824-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="c3824-111">El objeto **$psUnsupportedConsoleApplications** mantiene una lista de estos comandos.</span><span class="sxs-lookup"><span data-stu-id="c3824-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="c3824-112">Si intenta ejecutar los comandos de esta lista, recibirá un mensaje donde se indica que no son compatibles.</span><span class="sxs-lookup"><span data-stu-id="c3824-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="c3824-113">El siguiente script agrega una entrada a la lista.</span><span class="sxs-lookup"><span data-stu-id="c3824-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="c3824-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="c3824-114">$psLocalHelp</span></span>

<span data-ttu-id="c3824-115">Se trata de un objeto de diccionario que mantiene una asignación contextual entre los temas de Ayuda y sus vínculos asociados en el archivo de Ayuda HTML compilado local.</span><span class="sxs-lookup"><span data-stu-id="c3824-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="c3824-116">Se utiliza para buscar la Ayuda local para un tema determinado.</span><span class="sxs-lookup"><span data-stu-id="c3824-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="c3824-117">Puede agregar o eliminar los temas de esta lista.</span><span class="sxs-lookup"><span data-stu-id="c3824-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="c3824-118">En el ejemplo de código siguiente se muestran algunos pares clave-valor de ejemplo que se encuentran en `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="c3824-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="c3824-119">El siguiente script agrega una entrada a la lista.</span><span class="sxs-lookup"><span data-stu-id="c3824-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="c3824-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="c3824-120">$psOnlineHelp</span></span>

<span data-ttu-id="c3824-121">Se trata de un objeto de diccionario que mantiene una asignación contextual entre los títulos de los temas de Ayuda y sus direcciones URL externas asociadas.</span><span class="sxs-lookup"><span data-stu-id="c3824-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="c3824-122">Se utiliza para buscar la Ayuda para un tema determinado en la Web.</span><span class="sxs-lookup"><span data-stu-id="c3824-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="c3824-123">Puede agregar o eliminar los temas de esta lista.</span><span class="sxs-lookup"><span data-stu-id="c3824-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="c3824-124">El siguiente script agrega una entrada a la lista.</span><span class="sxs-lookup"><span data-stu-id="c3824-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="c3824-125">Véase también</span><span class="sxs-lookup"><span data-stu-id="c3824-125">See Also</span></span>

[<span data-ttu-id="c3824-126">Finalidad del modelo de objetos de scripting de Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="c3824-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
