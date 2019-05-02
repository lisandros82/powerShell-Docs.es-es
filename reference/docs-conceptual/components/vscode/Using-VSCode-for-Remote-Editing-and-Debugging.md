---
title: Uso de Visual Studio Code para la edición y la depuración de forma remota
description: Uso de Visual Studio Code para la edición y la depuración de forma remota
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086684"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Uso de Visual Studio Code para la edición y la depuración de forma remota

Aquellos usuarios que estuvieran familiarizados con el ISE pueden recordar que era posible ejecutar `psedit file.ps1` desde la consola integrada para abrir archivos, locales o remotos, directamente en el ISE.

Resulta que esta característica también está disponible en la extensión de PowerShell para VSCode. Esta guía le mostrará cómo hacerlo.

## <a name="prerequisites"></a>Requisitos previos

En esta guía se da por supuesto que tiene lo siguiente:

- un recurso remoto (p. ej.: una máquina virtual, un contenedor) al que tiene acceso
- PowerShell ejecutándose en él y en el equipo host
- VSCode y la extensión de PowerShell para VSCode

Esta característica funciona en Windows PowerShell y PowerShell Core.

Esta característica también funciona al conectarse a un equipo remoto a través de WinRM, PowerShell Direct o SSH. Si desea usar SSH, pero está usando Windows, consulte la [versión Win32 de SSH](https://github.com/PowerShell/Win32-OpenSSH).

## <a name="lets-go"></a>Empecemos

En esta sección, le guiaré por la edición y depuración remotas desde mi MacBook Pro en una máquina virtual de Ubuntu que se ejecuta en Azure. Aunque no use Windows, **el proceso es idéntico**.

### <a name="local-file-editing-with-open-editorfile"></a>Edición de archivo local con Open-EditorFile

Con la extensión de PowerShell para VSCode iniciada y la consola integrada de PowerShell abierta, podemos escribir `Open-EditorFile foo.ps1` o `psedit foo.ps1` para abrir el archivo foo.ps1 local directamente en el editor.

![Open-EditorFile foo.ps1 funciona localmente](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 ya debe existir.

Desde ahí, podemos hacer lo siguiente:

agregar puntos de interrupción en el medianil ![adición de punto de interrupción en el medianil](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

y presionar la tecla F5 para depurar el script de PowerShell.
![depuración del script de PowerShell local](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Durante la depuración, puede interactuar con la consola de depuración y consultar las variables en el ámbito de la izquierda y todas las demás herramientas de depuración estándar.

### <a name="remote-file-editing-with-open-editorfile"></a>Edición de archivo remoto con Open-EditorFile

Ahora veamos la edición y la depuración de un archivo remoto. Los pasos son prácticamente los mismos, solo hay una cosa que debemos hacer primero: escribir nuestra sesión de PowerShell en el servidor remoto.

Hay un cmdlet para hacerlo. Se llama `Enter-PSSession`.

La explicación desglosada del cmdlet es:

- `Enter-PSSession -ComputerName foo` inicia una sesión a través de WinRM
- `Enter-PSSession -ContainerId foo` y `Enter-PSSession -VmId foo` inician una sesión a través de PowerShell Direct
- `Enter-PSSession -HostName foo` inicia una sesión a través de SSH

Para obtener más información sobre `Enter-PSSession`, consulte los documentos [aquí](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Usaré SSH para la comunicación remota porque parto de macOS para llegar a una máquina virtual de Ubuntu en Azure.

En primer lugar, en la consola integrada, vamos a ejecutar nuestro Enter-PSSession. Sabrá que se encuentra en la sesión porque aparecerá `[something]` a la izquierda del mensaje.

![La llamada a Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

Desde ahí, podemos seguir los pasos exactos como si estuviéramos editando un script local.

1. Ejecutar `Open-EditorFile test.ps1` o `psedit test.ps1` para abrir el archivo remoto `test.ps1` ![Aplicación de Open-EditorFile al archivo test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Editar el archivo/establecer los puntos de interrupción ![edición y establecimiento de puntos de interrupción](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Iniciar la depuración (F5) del archivo remoto

![depuración del archivo remoto](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

¡Eso es todo esto! Esperamos que esta guía haya ayudado a resolver cualquier duda sobre la depuración y la edición remota de PowerShell en VSCode.

Si tiene problemas, no dude en plantearlas [en el repositorio de GitHub](http://github.com/powershell/vscode-powershell).
