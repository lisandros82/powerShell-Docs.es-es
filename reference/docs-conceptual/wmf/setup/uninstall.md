---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: Desinstalación de WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147865"
---
# <a name="uninstallation-instructions"></a>Instrucciones de desinstalación

## <a name="using-command-prompt"></a>Uso de la ventana del símbolo del sistema

1. Abra el **símbolo del sistema.**
2. Ejecute [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) tal como se muestra a continuación:

En Windows Server 2012 R2 y Windows 8.1:

```powershell
wusa /uninstall /kb:3134758
```

En Windows Server 2012:

```powershell
wusa /uninstall /kb:3134759
```

En Windows Server 2008 R2 SP1 y Windows 7 SP1:

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a>Uso del Panel de control

1. Abra el **Panel de control.**
2. Abra **Programas** y, después, **Desinstalar un programa.**
3. Haga clic en **Ver actualizaciones instaladas.**
4. Seleccione **Windows Management Framework 5.0** en la lista de actualizaciones instaladas. Corresponde a *KB3134758*, *KB3134759* o *KB3134760*. Haga clic en **Desinstalar.**
