---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Desinstalación de WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147865"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="8e4a7-103">Instrucciones de desinstalación</span><span class="sxs-lookup"><span data-stu-id="8e4a7-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="8e4a7-104">Uso de la ventana del símbolo del sistema</span><span class="sxs-lookup"><span data-stu-id="8e4a7-104">Using Command Prompt</span></span>

1. <span data-ttu-id="8e4a7-105">Abra el **símbolo del sistema.**</span><span class="sxs-lookup"><span data-stu-id="8e4a7-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="8e4a7-106">Ejecute [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) tal como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="8e4a7-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="8e4a7-107">En Windows Server 2012 R2 y Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="8e4a7-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="8e4a7-108">En Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="8e4a7-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="8e4a7-109">En Windows Server 2008 R2 SP1 y Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="8e4a7-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="8e4a7-110">Uso del Panel de control</span><span class="sxs-lookup"><span data-stu-id="8e4a7-110">Using Control Panel</span></span>

1. <span data-ttu-id="8e4a7-111">Abra el **Panel de control.**</span><span class="sxs-lookup"><span data-stu-id="8e4a7-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="8e4a7-112">Abra **Programas** y, después, **Desinstalar un programa.**</span><span class="sxs-lookup"><span data-stu-id="8e4a7-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="8e4a7-113">Haga clic en **Ver actualizaciones instaladas.**</span><span class="sxs-lookup"><span data-stu-id="8e4a7-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="8e4a7-114">Seleccione **Windows Management Framework 5.0** en la lista de actualizaciones instaladas.</span><span class="sxs-lookup"><span data-stu-id="8e4a7-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="8e4a7-115">Corresponde a *KB3134758*, *KB3134759* o *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="8e4a7-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="8e4a7-116">Haga clic en **Desinstalar.**</span><span class="sxs-lookup"><span data-stu-id="8e4a7-116">Click **Uninstall.**</span></span>
