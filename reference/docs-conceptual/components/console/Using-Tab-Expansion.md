---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Usar expansión de pestañas
ms.openlocfilehash: d96cbf848f464aff29a7bed9b70d0b6a000aa808
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67031013"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="62c19-103">Usar expansión de pestañas</span><span class="sxs-lookup"><span data-stu-id="62c19-103">Using Tab Expansion</span></span>

<span data-ttu-id="62c19-104">Los shells de línea de comandos suelen ofrecer un método para completar los nombres de archivos largos o comandos automáticamente, lo que acelera la entrada de comando y proporciona sugerencias.</span><span class="sxs-lookup"><span data-stu-id="62c19-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="62c19-105">PowerShell permite rellenar los nombres de archivo y de cmdlet presionando la tecla de <kbd>tabulación</kbd>.</span><span class="sxs-lookup"><span data-stu-id="62c19-105">PowerShell allows you to fill in file names and cmdlet names by pressing the <kbd>Tab</kbd> key.</span></span>

> [!NOTE]
> <span data-ttu-id="62c19-106">La función interna TabExpansion o TabExpansion2 controla la expansión de pestañas.</span><span class="sxs-lookup"><span data-stu-id="62c19-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="62c19-107">Puesto que esta función se puede modificar o reemplazar, este artículo es una guía para el comportamiento de la configuración predeterminada de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="62c19-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="62c19-108">Para rellenar automáticamente un nombre de archivo o una ruta de acceso desde las opciones disponibles, escriba parte del nombre y presione la tecla <kbd>Tab</kbd>.</span><span class="sxs-lookup"><span data-stu-id="62c19-108">To fill in a filename or path from the available choices automatically, type part of the name and press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="62c19-109">PowerShell expandirá automáticamente el nombre a la primera coincidencia que encuentre.</span><span class="sxs-lookup"><span data-stu-id="62c19-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="62c19-110">Al presionar la tecla <kbd>Tab</kbd> repetidamente recorrerá todas las opciones disponibles.</span><span class="sxs-lookup"><span data-stu-id="62c19-110">Pressing the <kbd>Tab</kbd> key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="62c19-111">La expansión de pestañas de nombres de cmdlet es ligeramente diferente.</span><span class="sxs-lookup"><span data-stu-id="62c19-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="62c19-112">Para usar la expansión de pestañas en un nombre de cmdlet, escriba la primera parte completa del nombre (verbo) y el guion que aparece detrás.</span><span class="sxs-lookup"><span data-stu-id="62c19-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="62c19-113">Puede seguir rellenando el nombre para obtener una coincidencia parcial.</span><span class="sxs-lookup"><span data-stu-id="62c19-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="62c19-114">Por ejemplo, si escribe `get-co` y, después, presiona la tecla de <kbd>tabulación</kbd>, PowerShell lo expandirá automáticamente al cmdlet `Get-Command` (tenga en cuenta que también se cambiarán las letras mayúsculas y minúsculas a su formato estándar).</span><span class="sxs-lookup"><span data-stu-id="62c19-114">For example, if you type `get-co` and then press the <kbd>Tab</kbd> key, PowerShell will automatically expand this to the `Get-Command` cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="62c19-115">Si vuelve a presionar la tecla de <kbd>tabulación</kbd>, PowerShell lo reemplazará por el otro único nombre de cmdlet coincidente, `Get-Content`.</span><span class="sxs-lookup"><span data-stu-id="62c19-115">If you press <kbd>Tab</kbd> key again, PowerShell replaces this with the only other matching cmdlet name, `Get-Content`.</span></span>

<span data-ttu-id="62c19-116">Puede usar la expansión de pestañas repetidamente en la misma línea.</span><span class="sxs-lookup"><span data-stu-id="62c19-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="62c19-117">Por ejemplo, puede usar la expansión de pestañas en el nombre del cmdlet `Get-Content` especificando lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="62c19-117">For example, you can use tab expansion on the name of the `Get-Content` cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="62c19-118">Cuando se presiona la tecla <kbd>Tab</kbd>, el comando se expande a:</span><span class="sxs-lookup"><span data-stu-id="62c19-118">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="62c19-119">Luego, puede especificar parcialmente la ruta de acceso al archivo de registro de instalación activa y volver a usar la expansión de pestañas:</span><span class="sxs-lookup"><span data-stu-id="62c19-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="62c19-120">Cuando se presiona la tecla <kbd>Tab</kbd>, el comando se expande a:</span><span class="sxs-lookup"><span data-stu-id="62c19-120">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="62c19-121">Una limitación del proceso de expansión de pestañas es que las pestañas se interpretan siempre como intentos de completar una palabra.</span><span class="sxs-lookup"><span data-stu-id="62c19-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="62c19-122">Si copia y pega ejemplos de comandos en una consola de PowerShell, asegúrese de que el ejemplo no contiene pestañas; si es así, los resultados serán impredecibles y seguramente no serán los esperados.</span><span class="sxs-lookup"><span data-stu-id="62c19-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>
