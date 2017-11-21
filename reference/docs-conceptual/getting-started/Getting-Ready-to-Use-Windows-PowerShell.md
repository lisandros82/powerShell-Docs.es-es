---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Preparativos para usar Windows PowerShell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: de09c74e938f11a130864b1620d6c169006a27be
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2017
---
# <a name="getting-ready-to-use-windows-powershell"></a>Preparativos para usar Windows PowerShell
Cuando instale e inicie Windows PowerShell ISE, considere las siguientes opciones de configuración. Puede realizar estas tareas en cualquier momento.

- **Instalar los archivos de ayuda.** Los cmdlets que se incluyen en Windows PowerShell 3.0 no se suministran con archivos de ayuda. Sin embargo, puede usar el cmdlet [Update-Help](/powershell/module/microsoft.powershell.core/update-help) para descargar e instalar los archivos de ayuda más recientes en el equipo. Una vez instalados los archivos, puede usar el cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/get-help) para que se muestren directamente en la línea de comandos. Para obtener más información, consulte [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

    Si decide no instalar los archivos de ayuda, puede leer los temas de ayuda en línea. Para encontrar la versión en línea del tema de ayuda de cualquier cmdlet, escriba: `Get-Help <CmdletName> -Online`. Para examinar los temas de Ayuda de Windows PowerShell, vea la [documentación de PowerShell](/powershell/scripting).

- **Ejecutar scripts.** Para proteger Windows PowerShell, la directiva de ejecución predeterminada en Windows PowerShell es **Restringido**. Esta directiva permite ejecutar cmdlets, pero no scripts. Para ejecutar scripts, use el cmdlet [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) para cambiar la directiva de ejecución a **AllSigned** o **RemoteSigned**. Solo los miembros del grupo Administradores en el equipo pueden ejecutar este cmdlet. Para obtener más información, vea [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

- **Habilitar la comunicación remota.** El sistema ya está configurado para que pueda ejecutar comandos remotos en otros equipos. En Windows Server 2012 R2 y Windows Server 2012, el sistema también está configurado para recibir comandos remotos, es decir, para permitir que otros equipos ejecuten comandos remotos en el equipo local. Para habilitar equipos que ejecuten otras versiones de Windows para recibir comandos remotos, ejecute el cmdlet [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) en el equipo que desea administrar de forma remota. Solo los miembros del grupo Administradores en el equipo pueden ejecutar este cmdlet. Para obtener más información, consulte [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

    NOTA: Si la comunicación remota está habilitada en un equipo que ejecuta Windows Server 2.0, lo sigue estando después de instalar Windows Management Framework 3.0. Sin embargo, en Windows Server 2008 (no Windows Server 2008 R2), debe volver a habilitar la comunicación remota después de instalar Windows Management Framework 3.0.

## <a name="see-also"></a>Véase también
- [Instalación de Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
- [Inicio de Windows PowerShell](/powershell/scripting/setup/starting-windows-powershell)

