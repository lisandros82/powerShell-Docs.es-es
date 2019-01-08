---
title: Uso de Visual Studio Code para la edición y la depuración de forma remota
description: Uso de Visual Studio Code para la edición y la depuración de forma remota
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655639"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Uso de Visual Studio Code para la edición y la depuración de forma remota

Para aquellos de ustedes que estaba familiarizado con el ISE, es posible que recuerde que podría ejecutar `psedit file.ps1` desde la consola integrada para abrir archivos - locales o remotos: derecho en el ISE.

Según parece, esta característica también está disponible en la extensión de PowerShell para VSCode. Esta guía le mostrará cómo hacerlo.

## <a name="prerequisites"></a>Requisitos previos

Esta guía se da por supuesto que tiene:

- un recurso remoto (p. ej.: una máquina virtual, un contenedor) que tienen acceso a
- PowerShell que se ejecutan en él y el equipo host
- VSCode y la extensión de PowerShell para VSCode

Esta característica funciona en Windows PowerShell y PowerShell Core.

Esta característica también funciona al conectarse a un equipo remoto a través de WinRM, PowerShell Direct o SSH. Si desea usar SSH, pero está usando Windows, consulte el [versión Win32 de SSH](https://github.com/PowerShell/Win32-OpenSSH)!

## <a name="lets-go"></a>Empecemos

En esta sección, lo guiaré a través de una edición y depuración de mi MacBook Pro a una VM de Ubuntu que se ejecuta en Azure remota. Podría no estar usando Windows, pero **el proceso es idéntico**.

### <a name="local-file-editing-with-open-editorfile"></a>Edición con Open EditorFile de archivos local

Con la extensión de PowerShell para VSCode iniciado y se abre la consola de PowerShell integrado, además podemos escribir `Open-EditorFile foo.ps1` o `psedit foo.ps1` para abrir el archivo local foo.ps1 directamente en el editor.

![Abrir EditorFile foo.ps1 funciona localmente](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 ya debe existir.

Desde allí, se puede:

agregar puntos de interrupción en el medianil ![agregar punto de interrupción para medianil](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

y presione la tecla F5 para depurar el script de PowerShell.
![depurar el script de PowerShell local](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Durante la depuración, puede interactuar con la consola de depuración, consulte las variables en el ámbito a la izquierda y todos los demás estándar las herramientas de depuración.

### <a name="remote-file-editing-with-open-editorfile"></a>Archivo remoto abierto EditorFile de edición

Ahora pasemos a archivos remotos, edición y depuración. Los pasos son prácticamente los mismos, hay solo una cosa que debemos hacer primero: escriba nuestra sesión de PowerShell en el servidor remoto.

Hay un cmdlet para hacerlo. Se llama `Enter-PSSession`.

La explicación pero hacia abajo del cmdlet es:

- `Enter-PSSession -ComputerName foo` inicia una sesión a través de WinRM
- `Enter-PSSession -ContainerId foo` y `Enter-PSSession -VmId foo` iniciar una sesión a través de PowerShell Direct
- `Enter-PSSession -HostName foo` inicia una sesión a través de SSH

Para obtener más información sobre `Enter-PSSession`, consulte los documentos [aquí](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Vamos a usar SSH para la comunicación remota puesto que voy a una VM de Ubuntu en Azure desde macOS.

En primer lugar, en la consola integrada, vamos a ejecutar nuestro Enter-PSSession. Sabrá que se encuentra en la sesión porque `[something]` aparecerán a la izquierda del símbolo del sistema.

![La llamada a Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

A partir de ahí, podemos realizar los pasos exactos como si nos estábamos editar una secuencia de comandos local.

1. Ejecute `Open-EditorFile test.ps1` o `psedit test.ps1` para abrir el servidor remoto `test.ps1` archivo ![EditorFile-abrir el archivo test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Editar los puntos de interrupción/conjunto de archivos ![Editar y establezca puntos de interrupción](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Iniciar la depuración (F5) el archivo remoto

![depurar el archivo remoto](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

Eso es todo esto! Esperamos que esta guía ayudó a borrar de alguna pregunta sobre la depuración remota y edición de PowerShell en VSCode.

Si tiene problemas, no dude abrir problemas [en el repositorio de GitHub](http://github.com/powershell/vscode-powershell).
