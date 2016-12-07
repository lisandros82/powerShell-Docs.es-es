---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: dificultades comunes de las funcionalidades de rol
ms.technology: powershell
ms.openlocfilehash: 8e928ec07ef98b2ec8186a27d3aefa1450a3a424
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="common-role-capability-pitfalls"></a>Dificultades comunes de las funcionalidades de rol
Es posible que se encuentre con algunas dificultades comunes si realiza este proceso usted mismo.
A continuación se incluye una guía rápida en la que se explica cómo identificar y corregir estos problemas al modificar o crear un punto de conexión nuevo:

#### <a name="functions-vs-cmdlets"></a>Funciones frente a Cmdlets
Los comandos de PowerShell escritos en PowerShell son funciones de PowerShell.
Los comandos de PowerShell escritos como clases .NET especializadas son cmdlets de PowerShell.
Para comprobar el tipo de comando, ejecute `Get-Command`.

#### <a name="visibleproviders"></a>VisibleProviders
Deberá exponer los proveedores que necesiten sus comandos.
El más común es el proveedor FileSystem, pero puede que también necesite exponer otros, como el proveedor del Registro.
Para obtener una introducción a los proveedores, consulte esta [entrada del blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).
Tenga cuidado al exponer los proveedores: a menudo es mejor definir una función propia que funcione con los proveedores subyacentes que exponer directamente el proveedor en una sesión de JEA.
De este modo, puede permitir que los usuarios sigan trabajando con archivos, claves del Registro, etc., pero mantiene el control sobre **los** archivos y claves del Registro con los que pueden trabajar mediante una lógica de validación personalizada.

