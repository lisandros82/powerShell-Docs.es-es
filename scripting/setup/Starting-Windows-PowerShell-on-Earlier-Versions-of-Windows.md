---
title: Iniciar Windows PowerShell en versiones anteriores de Windows
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
translationtype: Human Translation
ms.sourcegitcommit: c40ab96196531d36001e4d94a3821d20612cbfce
ms.openlocfilehash: 333469a642a4b88442a7d3ca8fa65f5755c69bcc

---

# Iniciar Windows PowerShell en versiones anteriores de Windows
En esta sección, se explica cómo iniciar Windows PowerShell y el Entorno de scripting integrado (ISE) de Windows PowerShell en Windows® 7, Windows Server® 2008 R2 y Windows Server® 2008. También se explica cómo habilitar la característica opcional para Windows PowerShell ISE de Windows PowerShell 2.0 en Windows Server® 2008 R2 y Windows Server® 2008.

Para instalar Windows PowerShell 4.0 en sistemas compatibles, descargue e instale [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881). Para obtener más información, consulte [Instalar Windows PowerShell](Installing-Windows-PowerShell.md).

Para instalar Windows PowerShell 3.0 en sistemas compatibles, descargue e instale [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290). Para obtener más información, consulte [Instalar Windows PowerShell](Installing-Windows-PowerShell.md).

## Iniciar Windows PowerShell en versiones anteriores de Windows
Use cualquiera de los métodos siguientes para iniciar la versión instalada de Windows PowerShell 3.0 o Windows PowerShell 4.0, según corresponda.

#### Desde el menú Inicio

-   Haga clic en **Inicio**, escriba **ISE** y, después, haga clic en **Windows PowerShell**.

-   Desde el menú **Inicio**, haga clic en **Inicio**, **Todos los programas**, **Accesorios**, la carpeta **Windows PowerShell** y, luego, en **Windows PowerShell**.

#### En el símbolo del sistema

-   En Cmd.exe, Windows PowerShell o Windows PowerShell ISE, para iniciar Windows PowerShell, escriba:

    ```
    PowerShell
    ```

    También puede usar los parámetros del programa de PowerShell.exe para personalizar la sesión. Para obtener más información, consulte [Ayuda de línea de comandos de PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).

#### Con privilegios administrativos ("Ejecutar como administrador")

1.  Haga clic en **Inicio**, escriba **PowerShell**, haga clic con el botón derecho en **Windows PowerShell** y, después, haga clic en **Ejecutar como administrador**.

## Iniciar Windows PowerShell ISE en versiones anteriores de Windows
Use cualquiera de los métodos siguientes para iniciar Windows PowerShell ISE.

#### Desde el menú Inicio

-   Haga clic en **Inicio**, escriba **ISE** y, después, haga clic en **Windows PowerShell ISE**.

-   Desde el menú **Inicio**, haga clic en **Inicio**, **Todos los programas**, **Accesorios**, la carpeta **Windows PowerShell** y, luego, en **Windows PowerShell ISE**.

#### En el símbolo del sistema

-   En Cmd.exe, Windows PowerShell o Windows PowerShell ISE, para iniciar Windows PowerShell, escriba:

    ```
    PowerShell_ISE
    ```

    o

    ```
    ISE
    ```

#### Con privilegios administrativos ("Ejecutar como administrador")

1.  Haga clic en **Inicio**, escriba **ISE**, haga clic con el botón derecho en **Windows PowerShell ISE** y, después, haga clic en **Ejecutar como administrador**.

## Habilitar Windows PowerShell ISE en versiones anteriores de Windows
En Windows PowerShell 4.0 y Windows PowerShell 3.0, Windows PowerShell ISE está habilitado de forma predeterminada en todas las versiones de Windows. Si aún no está habilitado, Windows Management Framework 4.0 o Windows Management Framework 3.0 lo habilitan.

En Windows PowerShell 2.0, Windows PowerShell ISE está habilitado de forma predeterminada en Windows 7. Sin embargo, en Windows Server 2008 R2 y Windows Server 2008, es una característica opcional.

Para habilitar Windows PowerShell ISE de Windows PowerShell 2.0 en Windows Server 2008 R2 o Windows Server 2008, use el procedimiento siguiente.

#### Habilitar el Entorno de scripting integrado (ISE) de Windows PowerShell

1.  Inicie el Administrador del servidor.

2.  Haz clic en **Características** y, a continuación, en **Agregar características**.

3.  En Seleccionar características, haga clic en Entorno de scripting integrado (ISE) de Windows PowerShell.




<!--HONumber=Oct16_HO2-->


