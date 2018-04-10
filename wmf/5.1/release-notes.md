---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Notas de la versión de WMF 5.1
ms.openlocfilehash: eb22267c1af28a9fcdd049c76d363fff687f6167
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="windows-management-framework-wmf-51-release-notes"></a>Notas de la versión de Windows Management Framework (WMF) 5.1 #

WMF 5.1 incluye los componentes de PowerShell, WMI, WinRM y Registro de inventario de software (SIL) que se lanzaron con Windows Server 2016.
WMF 5.1 puede instalarse en Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 y 2012 R2 y proporciona una serie de mejoras con respecto a WMF 5.0 RTM, incluidos:

- Nuevos cmdlets: usuarios locales y grupos; Get-ComputerInfo
- En las mejoras de PowerShellGet se incluyen la aplicación de módulos firmados y la instalación de módulos JEA
- PackageManagement ha agregado compatibilidad con contenedores, configuración de CBS, configuración basada en EXE y paquetes de CAB
- Mejoras de depuración para las clases DSC y PowerShell
- Mejoras de seguridad, incluido el cumplimiento de módulos firmados por catálogos procedentes del servidor de extracción y al usar cmdlets de PowerShellGet
- Respuestas a varios problemas y varias solicitudes de usuarios

**Notas importantes:**

- **WMF 5.1 necesita .NET Framework 4.5.2** (o una versión superior). La instalación se realizará correctamente, pero se producirá un error en las características clave si .NET 4.5.2 (o una versión superior) no está instalado. Las instrucciones están disponibles en el tema [Instalación y configuración de WMF 5.1](https://msdn.microsoft.com/powershell/wmf/5.1/install-configure).
- Hay que desinstalar la versión preliminar de WMF 5.1 antes de instalar WMF 5.1 RTM.
- WMF 5.1 puede instalarse directamente sobre WMF 5.0 o WMF 4.0.
- __No es necesario__ instalar WMF 4.0 antes de instalar WMF 5.1 en Windows 7 y Windows Server 2008 R2. Este era un problema de la versión preliminar de WMF 5.1 y ya se ha resuelto.