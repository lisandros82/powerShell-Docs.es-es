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
ms.translationtype: HT
ms.contentlocale: es-ES
---
### <a name="common-role-capability-pitfalls"></a><span data-ttu-id="94e5f-103">Dificultades comunes de las funcionalidades de rol</span><span class="sxs-lookup"><span data-stu-id="94e5f-103">Common Role Capability Pitfalls</span></span>
<span data-ttu-id="94e5f-104">Es posible que se encuentre con algunas dificultades comunes si realiza este proceso usted mismo.</span><span class="sxs-lookup"><span data-stu-id="94e5f-104">You may run into a few common pitfalls if you go through this process yourself.</span></span>
<span data-ttu-id="94e5f-105">A continuación se incluye una guía rápida en la que se explica cómo identificar y corregir estos problemas al modificar o crear un punto de conexión nuevo:</span><span class="sxs-lookup"><span data-stu-id="94e5f-105">Here is a quick guide explaining how to identify and remediate these issues when modifying or creating a new endpoint:</span></span>

#### <a name="functions-vs-cmdlets"></a><span data-ttu-id="94e5f-106">Funciones frente a Cmdlets</span><span class="sxs-lookup"><span data-stu-id="94e5f-106">Functions vs. Cmdlets</span></span>
<span data-ttu-id="94e5f-107">Los comandos de PowerShell escritos en PowerShell son funciones de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94e5f-107">PowerShell commands written in PowerShell are PowerShell functions.</span></span>
<span data-ttu-id="94e5f-108">Los comandos de PowerShell escritos como clases .NET especializadas son cmdlets de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94e5f-108">PowerShell commands written as specialized .NET classes are PowerShell cmdlets.</span></span>
<span data-ttu-id="94e5f-109">Para comprobar el tipo de comando, ejecute `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="94e5f-109">You can check the command type by running `Get-Command`.</span></span>

#### <a name="visibleproviders"></a><span data-ttu-id="94e5f-110">VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="94e5f-110">VisibleProviders</span></span>
<span data-ttu-id="94e5f-111">Deberá exponer los proveedores que necesiten sus comandos.</span><span class="sxs-lookup"><span data-stu-id="94e5f-111">You will need to expose any providers your commands need.</span></span>
<span data-ttu-id="94e5f-112">El más común es el proveedor FileSystem, pero puede que también necesite exponer otros, como el proveedor del Registro.</span><span class="sxs-lookup"><span data-stu-id="94e5f-112">The most common is the FileSystem provider, but you may also need to expose others, like the Registry provider.</span></span>
<span data-ttu-id="94e5f-113">Para obtener una introducción a los proveedores, consulte esta [entrada del blog Hey, Scripting Guy](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span><span class="sxs-lookup"><span data-stu-id="94e5f-113">For an introduction to providers, check out this [Hey, Scripting Guy blog post](http://blogs.technet.com/b/heyscriptingguy/archive/2015/04/20/find-and-use-windows-powershell-providers.aspx).</span></span>
<span data-ttu-id="94e5f-114">Tenga cuidado al exponer los proveedores: a menudo es mejor definir una función propia que funcione con los proveedores subyacentes que exponer directamente el proveedor en una sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="94e5f-114">Be careful when exposing providers -- often, it is better to define your own function that works with the underlying providers than to directly expose the provider in a JEA session.</span></span>
<span data-ttu-id="94e5f-115">De este modo, puede permitir que los usuarios sigan trabajando con archivos, claves del Registro, etc., pero mantiene el control sobre **los** archivos y claves del Registro con los que pueden trabajar mediante una lógica de validación personalizada.</span><span class="sxs-lookup"><span data-stu-id="94e5f-115">This way, you can still allow users to work with files, registry keys, etc. but retain control over **which** files and registry keys they can work with using custom validation logic.</span></span>

