---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Iniciar Windows PowerShell
ms.openlocfilehash: d2cb77027f404c5b008a902c5147d018dd741a67
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030461"
---
# <a name="starting-windows-powershell"></a>Iniciar Windows PowerShell
PowerShell es una dll de motor de scripting que se inserta en varios hosts.  Los hosts más comunes que iniciará son la línea de comandos interactiva PowerShell.exe y el entorno de scripting interactivo PowerShell_ISE.exe.

Para iniciar Windows PowerShell® en Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 y Windows 8, consulte [Navegación y tareas de administración comunes en Windows](https://technet.microsoft.com/library/hh831491.aspx).

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a>Iniciar Windows PowerShell en versiones anteriores de Windows

En esta sección, se explica cómo iniciar Windows PowerShell y el Entorno de scripting integrado (ISE) de Windows PowerShell en Windows® 7, Windows Server® 2008 R2 y Windows Server® 2008. También se explica cómo habilitar la característica opcional para Windows PowerShell ISE de Windows PowerShell 2.0 en Windows Server® 2008 R2 y Windows Server® 2008.

Use cualquiera de los métodos siguientes para iniciar la versión instalada de Windows PowerShell 3.0 o Windows PowerShell 4.0, según corresponda.

#### <a name="from-the-start-menu"></a>Desde el menú Inicio

- Haga clic en **Inicio**, escriba **ISE** y, después, haga clic en **Windows PowerShell**.
- Desde el menú **Inicio**, haga clic en **Inicio**, **Todos los programas**, **Accesorios**, la carpeta **Windows PowerShell** y, luego, en **Windows PowerShell**.

#### <a name="at-the-command-prompt"></a>En el símbolo del sistema

En Cmd.exe, Windows PowerShell o Windows PowerShell ISE, para iniciar Windows PowerShell, escriba:

```
PowerShell
```

También puede usar los parámetros del programa de PowerShell.exe para personalizar la sesión. Para obtener más información, consulte [Ayuda de línea de comandos de PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### <a name="with-administrative-privileges-run-as-administrator"></a>Con privilegios administrativos ("Ejecutar como administrador")

Haga clic en **Inicio**, escriba **PowerShell**, haga clic con el botón derecho en **Windows PowerShell** y, después, haga clic en **Ejecutar como administrador**.

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a>Iniciar Windows PowerShell ISE en versiones anteriores de Windows

Use cualquiera de los métodos siguientes para iniciar Windows PowerShell ISE.

#### <a name="from-the-start-menu"></a>Desde el menú Inicio

- Haga clic en **Inicio**, escriba **ISE** y, después, haga clic en **Windows PowerShell ISE**.
- Desde el menú **Inicio**, haga clic en **Inicio**, **Todos los programas**, **Accesorios**, la carpeta **Windows PowerShell** y, luego, en **Windows PowerShell ISE**.

#### <a name="at-the-command-prompt"></a>En el símbolo del sistema

En Cmd.exe, Windows PowerShell o Windows PowerShell ISE, para iniciar Windows PowerShell, escriba:

```
PowerShell_ISE
```

o

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a>Con privilegios administrativos ("Ejecutar como administrador")

Haga clic en **Inicio**, escriba **ISE**, haga clic con el botón derecho en **Windows PowerShell ISE** y, después, haga clic en **Ejecutar como administrador**.

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a>Habilitar Windows PowerShell ISE en versiones anteriores de Windows

En Windows PowerShell 4.0 y Windows PowerShell 3.0, Windows PowerShell ISE está habilitado de forma predeterminada en todas las versiones de Windows. Si aún no está habilitado, Windows Management Framework 4.0 o Windows Management Framework 3.0 lo habilitan.

En Windows PowerShell 2.0, Windows PowerShell ISE está habilitado de forma predeterminada en Windows 7. Sin embargo, en Windows Server 2008 R2 y Windows Server 2008, es una característica opcional.

Para habilitar Windows PowerShell ISE de Windows PowerShell 2.0 en Windows Server 2008 R2 o Windows Server 2008, use el procedimiento siguiente.

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a>Habilitar el Entorno de scripting integrado (ISE) de Windows PowerShell

1. Inicie el Administrador del servidor.
2. Haz clic en **Características** y, a continuación, en **Agregar características**.
3. En Seleccionar características, haga clic en Entorno de scripting integrado (ISE) de Windows PowerShell.

## <a name="starting-the-32-bit-version-of-windows-powershell"></a>Iniciar la versión de 32 bits de Windows PowerShell

Al instalar Windows PowerShell en un equipo de 64 bits, **Windows PowerShell (x86)** , se instala una versión de 32 bits de Windows PowerShell además de la versión de 64 bits. Al ejecutar Windows PowerShell, la versión de 64 bits se ejecuta de forma predeterminada.

Sin embargo, en ocasiones deberá ejecutar **Windows PowerShell (x86)** , como cuando usa un módulo que requiere la versión 32 bits o cuando se conecta de forma remota a un equipo de 32 bits.

Para iniciar una versión de 32 bits de Windows PowerShell, use uno de los procedimientos siguientes.

#### <a name="in-windows-server-2012-r2"></a>En Windows Server® 2012 R2

- En la pantalla **Inicio**, escriba **Windows PowerShell (x86)** . Haga clic en el icono **Windows PowerShell x86**.
- En **Administrador del servidor**, desde el menú **Herramientas**, seleccione **Windows PowerShell (x86)** .
- En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell x86** y, a continuación, haga clic en **Windows PowerShell (x86)** .
- Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-server-2012"></a>En Windows Server® 2012

- En la página **Inicio**, escriba **Powershell** y, después, haga clic en **Windows PowerShell (x86)** .
- En **Administrador del servidor**, desde el menú **Herramientas**, seleccione **Windows PowerShell (x86)** .
- En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell** y, a continuación, haga clic en **Windows PowerShell (x86)** .
- Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-81"></a>En Windows® 8.1

- En la pantalla **Inicio**, escriba **Windows PowerShell (x86)** . Haga clic en el icono **Windows PowerShell x86**.
- Si está ejecutando [Herramientas de administración remota del servidor](https://go.microsoft.com/fwlink/?LinkID=304145) para Windows 8.1, también puede abrir Windows PowerShell x86 desde el menú **Server Manager Tools** (Herramientas del administrador del servidor).
  Seleccione **Windows PowerShell (x86)** .
- En el escritorio, mueva el cursor a la esquina superior derecha, haga clic en **Buscar**, escriba **PowerShell x86** y, a continuación, haga clic en **Windows PowerShell (x86)** .
- Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`

#### <a name="in-windows-8"></a>En Windows® 8

- En la pantalla **Inicio**, mueva el cursor a la esquina superior derecha, haga clic en **Configuración**, haga clic en **Mosaicos** y, a continuación, mueva el control deslizante **Mostrar herramientas administrativas** a Sí. A continuación, escriba **PowerShell** y haga clic en **Windows PowerShell (x86)** .
- Si está ejecutando [Herramientas de administración remota del servidor](https://www.microsoft.com/download/details.aspx?id=28972) para Windows 8, también puede abrir Windows PowerShell x86 desde el menú **Server ManagerTools** (Herramientas del administrador del servidor). Seleccione **Windows PowerShell (x86)** .
- En la página **Inicio** o en el escritorio, escriba **Powershell (x86)** y, después, haga clic en **Windows PowerShell (x86)** .
- Mediante la línea de comandos, escriba: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`
