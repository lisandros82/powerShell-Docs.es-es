---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Cmdlets de Web Access
ms.technology: powershell
ms.openlocfilehash: ac8717c2aa97d0482b4d88f1b57d621d7ff47535
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2017
---
#  <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="e6040-103">Cmdlets de Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="e6040-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="e6040-104">Este tema de referencia ofrece descripciones y sintaxis de todos los cmdlets específicos de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="e6040-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="e6040-105">Enumera los cmdlets por orden alfabético según el verbo que aparece al principio del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e6040-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="e6040-106">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e6040-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="e6040-107">Agrega una nueva regla de autorización al conjunto de reglas de autorización de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="e6040-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="e6040-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e6040-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="e6040-109">Devuelve un conjunto de las reglas de autorización de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="e6040-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="e6040-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="e6040-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="e6040-111">Configura en IIS la aplicación web de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="e6040-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="e6040-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e6040-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="e6040-113">Quita una regla de autorización especificada de Windows PowerShell Web Access.</span><span class="sxs-lookup"><span data-stu-id="e6040-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="e6040-114">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e6040-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="e6040-115">Comprueba las reglas de autorización para validar que se ha autorizado una solicitud de acceso de punto de conexión, equipo o usuario en concreto.</span><span class="sxs-lookup"><span data-stu-id="e6040-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="e6040-116">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="e6040-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="e6040-117">Desinstala de IIS la aplicación web de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6040-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="e6040-118">**Nota**:</span><span class="sxs-lookup"><span data-stu-id="e6040-118">**Note**:</span></span>
>
><span data-ttu-id="e6040-119">Para enumerar todos los cmdlets disponibles, use el</span><span class="sxs-lookup"><span data-stu-id="e6040-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="e6040-120">cmdlet `Get-Command –Module PowerShellWebAccess`.</span><span class="sxs-lookup"><span data-stu-id="e6040-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="e6040-121">Para más información sobre cualquiera de los cmdlets o su sintaxis, use el cmdlet</span><span class="sxs-lookup"><span data-stu-id="e6040-121">For more information about, or for the syntax of, any of the cmdlets, use:</span></span>  
<span data-ttu-id="e6040-122">`Get-Help `*&lt;nombre del cmdlet&gt;*,</span><span class="sxs-lookup"><span data-stu-id="e6040-122">`Get-Help `*&lt;cmdlet name&gt;*</span></span>  
<span data-ttu-id="e6040-123">donde *&lt;nombre del cmdlet&gt;* es el nombre del cmdlet que quiere investigar.</span><span class="sxs-lookup"><span data-stu-id="e6040-123">where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="e6040-124">Para obtener información más detallada, puede ejecutar cualquiera de los siguientes cmdlets:</span><span class="sxs-lookup"><span data-stu-id="e6040-124">For more detailed information, you can run any of the following cmdlets:</span></span>

-  <span data-ttu-id="e6040-125">`Get-Help `*&lt;nombre del cmdlet&gt;*` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="e6040-125">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
-  <span data-ttu-id="e6040-126">`Get-Help `*&lt;nombre del cmdlet&gt;*` -Examples`</span><span class="sxs-lookup"><span data-stu-id="e6040-126">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
-  <span data-ttu-id="e6040-127">`Get-Help `*&lt;nombre del cmdlet&gt;*` -Full`</span><span class="sxs-lookup"><span data-stu-id="e6040-127">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="e6040-128">Más información</span><span class="sxs-lookup"><span data-stu-id="e6040-128">More Information</span></span>

<span data-ttu-id="e6040-129">Para más información sobre PowerShell Web Access, vea lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e6040-129">For more information about PowerShell Web Access, see the following:</span></span>

-   [<span data-ttu-id="e6040-130">Instalación y uso de Windows PowerShell Web Access</span><span class="sxs-lookup"><span data-stu-id="e6040-130">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)

