---
title: Uso de Visual Studio Code para la edición y la depuración de forma remota
description: Uso de Visual Studio Code para la edición y la depuración de forma remota
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67263932"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Uso de Visual Studio Code para la edición y la depuración de forma remota

Aquellos usuarios que están familiarizados con el ISE pueden recordar que era posible ejecutar `psedit file.ps1` desde la consola integrada para abrir archivos, locales o remotos, directamente en el ISE.

Esta característica también está disponible en la extensión de PowerShell para VSCode. Esta guía muestra cómo hacerlo.

## <a name="prerequisites"></a>Requisitos previos

En esta guía se da por supuesto que tiene lo siguiente:

- un recurso remoto (p. ej.: una máquina virtual, un contenedor) al que tiene acceso.
- PowerShell ejecutándose en él y en el equipo host
- VSCode y la extensión de PowerShell para VSCode

Esta característica funciona en Windows PowerShell y PowerShell Core.

Esta característica también funciona al conectarse a un equipo remoto a través de WinRM, PowerShell Direct o SSH. Si desea usar SSH, pero está usando Windows, consulte la [versión Win32 de SSH](https://github.com/PowerShell/Win32-OpenSSH).

> [!IMPORTANT]
> Los comandos `Open-EditorFile` y `psedit` solo funcionan en la **consola integrada de PowerShell** que la extensión de PowerShell crea para VSCode.

## <a name="usage-examples"></a>Ejemplos de uso

Estos ejemplos muestran la depuración y la edición remotas desde un equipo MacBook Pro a una máquina virtual Ubuntu que se ejecuta en Azure. El proceso es idéntico en Windows.

### <a name="local-file-editing-with-open-editorfile"></a>Edición de archivo local con Open-EditorFile

Con la extensión de PowerShell para VSCode iniciada y la consola integrada de PowerShell abierta, podemos escribir `Open-EditorFile foo.ps1` o `psedit foo.ps1` para abrir el archivo foo.ps1 local directamente en el editor.

![Open-EditorFile foo.ps1 funciona localmente](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> El archivo `foo.ps1` ya debería existir.

Desde ahí, podemos hacer lo siguiente:

- Agregar puntos de interrupción en el medianil.

  ![agregar punto de interrupción en el medianil](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- Presionar F5 para depurar el script de PowerShell.

  ![depurar el script local de PowerShell](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

Durante la depuración, puede interactuar con la consola de depuración y consultar las variables en el ámbito de la izquierda y todas las demás herramientas de depuración estándar.

### <a name="remote-file-editing-with-open-editorfile"></a>Edición de archivo remoto con Open-EditorFile

Ahora veamos la edición y la depuración de un archivo remoto. Los pasos son prácticamente los mismos, solo hay una cosa que debemos hacer primero: escribir nuestra sesión de PowerShell en el servidor remoto.

Hay un cmdlet para hacerlo. Se llama `Enter-PSSession`.

La explicación desglosada del cmdlet es:

- `Enter-PSSession -ComputerName foo` inicia una sesión a través de WinRM
- `Enter-PSSession -ContainerId foo` y `Enter-PSSession -VmId foo` inician una sesión a través de PowerShell Direct
- `Enter-PSSession -HostName foo` inicia una sesión a través de SSH

Para más información, consulte la documentación para [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

Como vamos desde macOS a una máquina virtual Ubuntu en Azure, usamos SSH para la comunicación remota.

En primer lugar, ejecute `Enter-PSSession` en la consola integrada. Se conecta a la sesión remota cuando `[<hostname>]` aparece a la izquierda del símbolo del sistema.

![La llamada a Enter-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

Ahora, podemos completar los mismos pasos que llevaríamos a cabo si estuviéramos editando un script local.

1. Ejecute `Open-EditorFile test.ps1` o `psedit test.ps1` para abrir el archivo `test.ps1` remoto.

  ![El archivo test.ps1 Open-EditorFile](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. Editar el archivo/establecer los puntos de interrupción

   ![edición y establecimiento de puntos de interrupción](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. Iniciar la depuración (F5) del archivo remoto

   ![depuración del archivo remoto](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

Si tiene algún problema, puede abrir los problemas que hay en el [repositorio de GitHub](https://github.com/powershell/vscode-powershell).
