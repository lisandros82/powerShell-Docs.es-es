---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 64a29aa87507e65a182837df538c5e695c420cb3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="0d196-102">Instrucciones de desinstalación</span><span class="sxs-lookup"><span data-stu-id="0d196-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="0d196-103">Uso de la ventana del símbolo del sistema</span><span class="sxs-lookup"><span data-stu-id="0d196-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="0d196-104">Abra el **símbolo del sistema.**</span><span class="sxs-lookup"><span data-stu-id="0d196-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="0d196-105">Ejecute [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) tal como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="0d196-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="0d196-106">En Windows Server 2012 R2 y Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="0d196-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="0d196-107">En Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="0d196-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="0d196-108">En Windows Server 2008 R2 SP1 y Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="0d196-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="0d196-109">Uso del Panel de control</span><span class="sxs-lookup"><span data-stu-id="0d196-109">Using Control Panel</span></span>
1.  <span data-ttu-id="0d196-110">Abra el **Panel de control.**</span><span class="sxs-lookup"><span data-stu-id="0d196-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="0d196-111">Abra **Programas** y, después, **Desinstalar un programa.**</span><span class="sxs-lookup"><span data-stu-id="0d196-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="0d196-112">Haga clic en **Ver actualizaciones instaladas.**</span><span class="sxs-lookup"><span data-stu-id="0d196-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="0d196-113">Seleccione **Windows Management Framework 5.0** en la lista de actualizaciones instaladas.</span><span class="sxs-lookup"><span data-stu-id="0d196-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="0d196-114">Corresponde a *KB3134758*, *KB3134759* o *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="0d196-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="0d196-115">Haga clic en **Desinstalar.**</span><span class="sxs-lookup"><span data-stu-id="0d196-115">Click **Uninstall.**</span></span>
