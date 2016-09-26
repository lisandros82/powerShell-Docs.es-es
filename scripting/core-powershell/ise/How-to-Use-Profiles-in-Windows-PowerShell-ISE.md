---
title: "Cómo usar perfiles en ISE de Windows PowerShell"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
translationtype: Human Translation
ms.sourcegitcommit: cb3db96ff87078756166df9f90d44d88cdfd155f
ms.openlocfilehash: 3543503655cc506c4c0f8a7f3d1056c05a66ecba

---

# Cómo usar perfiles en ISE de Windows PowerShell
En este tema se explica cómo usar perfiles en el Entorno de scripting integrado (ISE) de Windows PowerShell®. Antes de realizar las tareas de esta sección, se recomienda consultar [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)). De forma alternativa, en el panel de consola, escriba `Get-Help about_Profiles` y presione **ENTRAR**.

Un perfil es un script de Windows PowerShell ISE que se ejecuta automáticamente cuando se inicia una nueva sesión.  Puede crear uno o varios perfiles de Windows PowerShell para Windows PowerShell ISE y usarlos para configurar el entorno de Windows PowerShell o Windows PowerShell ISE y prepararlo para su uso, con las variables, los alias, las funciones, y las preferencias de color y fuente que desee que estén disponibles. Un perfil afecta a todas las sesiones de Windows PowerShell ISE que inicia.

> [!NOTE]
> La directiva de ejecución de Windows PowerShell determina si puede ejecutar scripts y cargar un perfil. La directiva de ejecución predeterminada, "Restricted", impide que se ejecuten todos los scripts, incluidos los perfiles. Si usa la directiva "Restricted", no se puede cargar el perfil. Para obtener más información sobre la directiva de ejecución, consulte [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).

## Seleccionar un perfil para usarlo en Windows PowerShell ISE
Windows PowerShell ISE admite perfiles para el usuario actual y para todos los usuarios. También admite los perfiles de Windows PowerShell que se aplican a todos los hosts.

El perfil que use viene determinado por la forma en que se usa Windows PowerShell y Windows PowerShell ISE.

-   Si solo usa Windows PowerShell ISE para ejecutar Windows PowerShell, guarde todos los elementos en uno de los perfiles específicos de ISE, como el perfil CurrentUserCurrentHost de Windows PowerShell ISE o el perfil AllUsersCurrentHost de Windows PowerShell ISE.

-   Si usa varios programas host para ejecutar Windows PowerShell, guarde sus funciones, alias, variables y comandos en un perfil que afecte a todos los programas host, como el perfil CurrentUserAllHosts o AllUsersAllHosts y guarde las características específicas de ISE, como la personalización de color y fuente en el perfil CurrentUserCurrentHost de Windows PowerShell ISE o el perfil AllUsersCurrentHost de Windows PowerShell ISE.

Los siguientes son perfiles que se pueden crear y usar en Windows PowerShell ISE. Cada perfil se guarda en su propia ruta de acceso específica.

| Tipo de perfil | Ruta de acceso al perfil |
| --- | --- |
| **Usuario actual, PowerShell ISE**| `$PROFILE.CurrentUserCurrentHost`o `$PROFILE` |
| **Todos los usuarios, PowerShell ISE**| `$PROFILE.AllUsersCurrentHost` |
| **Usuario actual, todos los hosts**| `$PROFILE.CurrentUserAllHosts` |
| **Todos los usuarios, todos los hosts** | `$PROFILE.AllUsersAllHosts` |

## Para crear un nuevo perfil
Para crear un nuevo perfil "Usuario actual, Windows PowerShell ISE", ejecute este comando:

```PowerShell
if (!(Test-Path -Path $PROFILE )) 
{ New-Item -Type File -Path $PROFILE -Force }
```

Para crear un nuevo perfil "Todos los usuarios, Windows PowerShell ISE", ejecute este comando:

```PowerShell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost)) 
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Para crear un nuevo perfil "Usuario actual, todos los hosts", ejecute este comando:

```PowerShell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts)) 
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Para crear un nuevo perfil "Todos los usuarios, todos los hosts", escriba:

```PowerShell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts)) 
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## Para editar un perfil

1.  Para abrir el perfil, ejecute el comando psedit con la variable que especifica el perfil que quiere editar. Por ejemplo, para abrir el perfil "Usuario actual, Windows PowerShell ISE", escriba: `psEdit $PROFILE`

2.  Agregue algunos elementos a su perfil. Estos son algunos ejemplos para comenzar:

    -   Para cambiar el color de fondo predeterminado del panel de consola a azul, en el archivo de perfil, escriba: `$psISE.Options.OutputPaneBackground = 'blue'` . Para obtener más información acerca de la variable $psISE, consulte [Referencia del modelo de objetos de ISE de Windows PowerShell](#windows-powershell-ise-object-model-reference).

    -   Para cambiar el tamaño de la fuente a 20, en el archivo de perfil, escriba: `$psISE.Options.FontSize =20`

3.  Para guardar el archivo de perfil, en el menú **Archivo**, haga clic en **Guardar**. La próxima vez que abra Windows PowerShell ISE, se aplicarán sus opciones personalizadas.

## Véase también
- [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))
- [Usar Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)




<!--HONumber=Sep16_HO3-->


