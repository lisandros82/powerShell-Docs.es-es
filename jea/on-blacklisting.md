---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: Acerca de la lista negra
ms.technology: powershell
ms.openlocfilehash: e823cc0b130500fb7ea60e65acf27f90ad3f3802
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
### <a name="on-blacklisting"></a><span data-ttu-id="eb987-103">Acerca de la lista negra</span><span class="sxs-lookup"><span data-stu-id="eb987-103">On Blacklisting</span></span>
<span data-ttu-id="eb987-104">Ahora que se ha familiarizado con JEA, probablemente se pregunte si es posible incluir comandos en una lista negra.</span><span class="sxs-lookup"><span data-stu-id="eb987-104">After playing around with JEA, you may be wondering if it is possible to blacklist commands.</span></span>
<span data-ttu-id="eb987-105">Se trata de una solicitud comprensible, pero actualmente no está previsto para JEA por las razones siguientes:</span><span class="sxs-lookup"><span data-stu-id="eb987-105">This is an understandable request, but it is not currently planned for JEA for the following reasons:</span></span>

1.  <span data-ttu-id="eb987-106">Hemos diseñado JEA para limitar a los operadores a las acciones que necesitan realizar.</span><span class="sxs-lookup"><span data-stu-id="eb987-106">We designed JEA to limit operators to only the actions they need to do.</span></span>
<span data-ttu-id="eb987-107">Una lista negra es lo contrario a esto.</span><span class="sxs-lookup"><span data-stu-id="eb987-107">A blacklist is the opposite.</span></span>

2.  <span data-ttu-id="eb987-108">Los autores de los comandos de PowerShell no diseñaron dichos comandos con JEA en mente.</span><span class="sxs-lookup"><span data-stu-id="eb987-108">PowerShell command authors did not design PowerShell commands with the JEA in mind.</span></span>
<span data-ttu-id="eb987-109">En una instalación nueva de Windows Server 2016, existen aproximadamente 1520 comandos disponibles de inmediato.</span><span class="sxs-lookup"><span data-stu-id="eb987-109">On a fresh install of Windows Server 2016, there are about 1520 commands immediately available.</span></span>
<span data-ttu-id="eb987-110">Los modelos de riesgos para estos comandos no incluían la posibilidad de que un usuario pudiese ejecutar comandos como una cuenta con más privilegios.</span><span class="sxs-lookup"><span data-stu-id="eb987-110">The threat models for these commands did not include the possibility that a user would be running commands as a more privileged account.</span></span>
<span data-ttu-id="eb987-111">Por ejemplo, determinados comandos permiten la inserción de código por diseño (por ejemplo, Invoke-Command y Add-Type en el módulo principal de PowerShell).</span><span class="sxs-lookup"><span data-stu-id="eb987-111">For example, certain commands allow for code injection by design (e.g. Add-Type and Invoke-Command in the core PowerShell module).</span></span>
<span data-ttu-id="eb987-112">JEA puede avisarle cuando exponga los comandos específicos que conocemos, pero no hemos vuelto a evaluar todos los demás comandos de Windows en función del nuevo modelo de riesgos.</span><span class="sxs-lookup"><span data-stu-id="eb987-112">JEA can warn you when you expose the specific commands we know about, but we have not re-assessed every other command in Windows based on the new threat model.</span></span>
<span data-ttu-id="eb987-113">Debe comprender las funcionalidades de los comandos que exponga a través de JEA.</span><span class="sxs-lookup"><span data-stu-id="eb987-113">You must understand the capabilities of the commands you exposing through JEA.</span></span>  

3.  <span data-ttu-id="eb987-114">Además, incluso aunque JEA bloquease todos los comandos con vulnerabilidades de inserción de código, no hay ninguna garantía de que un usuario malintencionado no pueda llevar a cabo una acción incluida en la lista negra con otro comando relacionado.</span><span class="sxs-lookup"><span data-stu-id="eb987-114">Furthermore, even if JEA blocked all commands with code-injection vulnerabilities, there is no guarantee that a malicious user would not be able to carry out a blacklisted action with another related command.</span></span>
<span data-ttu-id="eb987-115">A menos que comprenda todos los comandos que expone, es imposible garantizar que una acción determinada no es posible.</span><span class="sxs-lookup"><span data-stu-id="eb987-115">Unless you understand all of the commands that you are exposing, it is impossible for you to guarantee that a certain action is not possible.</span></span>
<span data-ttu-id="eb987-116">Usted tiene la responsabilidad de comprender qué comandos expone, tanto si se incluyen en una lista blanca como en una lista negra.</span><span class="sxs-lookup"><span data-stu-id="eb987-116">The burden is on you to understand what commands you are exposing, whether they are using a whitelist or a blacklist.</span></span>
<span data-ttu-id="eb987-117">El número de comandos que expondría una lista negra sería imposible de administrar, por lo que JEA se implementa mediante listas blancas.</span><span class="sxs-lookup"><span data-stu-id="eb987-117">The number of commands a blacklist would expose is unmanageable, so JEA is implemented using whitelists instead.</span></span>

