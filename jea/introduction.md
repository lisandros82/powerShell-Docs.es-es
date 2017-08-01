---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Introducción"
ms.technology: powershell
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="introduction"></a><span data-ttu-id="161ca-103">Introducción</span><span class="sxs-lookup"><span data-stu-id="161ca-103">Introduction</span></span>

##  <a name="motivation"></a><span data-ttu-id="161ca-104">**Motivaciones**</span><span class="sxs-lookup"><span data-stu-id="161ca-104">**Motivation**</span></span>  
<span data-ttu-id="161ca-105">Cuando le concede a alguien el acceso con privilegios a los sistemas, está ampliando el límite de confianza a esa persona.</span><span class="sxs-lookup"><span data-stu-id="161ca-105">When you grant someone privileged access to your systems, you extend your trust boundary to that person.</span></span>
<span data-ttu-id="161ca-106">Esto es un riesgo, ya que los administradores son una superficie expuesta a ataques.</span><span class="sxs-lookup"><span data-stu-id="161ca-106">This is a risk -- administrators are an attack surface.</span></span>
<span data-ttu-id="161ca-107">Los ataques internos y las credenciales robadas son una realidad habitual.</span><span class="sxs-lookup"><span data-stu-id="161ca-107">Insider attacks and stolen credentials are both real and common.</span></span>

##  <a name="not-a-new-problem"></a><span data-ttu-id="161ca-108">**No es un problema nuevo**</span><span class="sxs-lookup"><span data-stu-id="161ca-108">**Not a new problem**</span></span>  
<span data-ttu-id="161ca-109">Es probable que esté muy familiarizado con el principio del privilegio mínimo y que use algún tipo de control de acceso basado en rol (RBAC) con aplicaciones que lo proporcionan.</span><span class="sxs-lookup"><span data-stu-id="161ca-109">You are probably very familiar with the principle of least privilege, and you might use some form of role-based access control (RBAC) with applications that provide it.</span></span>
<span data-ttu-id="161ca-110">Pero la eficacia y la facilidad de uso de estas soluciones suelen verse limitadas por su amplio alcance y su imprecisión.</span><span class="sxs-lookup"><span data-stu-id="161ca-110">However, the effectiveness and manageability of these solutions are often limited by their broad scope and imprecision.</span></span>
<span data-ttu-id="161ca-111">Además, existen lagunas en la cobertura de RBAC.</span><span class="sxs-lookup"><span data-stu-id="161ca-111">Furthermore, there are gaps in RBAC coverage.</span></span>
<span data-ttu-id="161ca-112">Por ejemplo, en Windows, el acceso privilegiado es en gran medida un conmutador binario, que le obliga a conceder permisos innecesarios al agregar usuarios al grupo de administradores.</span><span class="sxs-lookup"><span data-stu-id="161ca-112">For example, in Windows, privileged access is largely a binary switch, forcing you to give unnecessary permissions when adding users to the Administrators group.</span></span>

##  <a name="just-enough-administration-jea"></a><span data-ttu-id="161ca-113">**Just Enough Administration (JEA)**</span><span class="sxs-lookup"><span data-stu-id="161ca-113">**Just Enough Administration (JEA)**</span></span> 
<span data-ttu-id="161ca-114">Proporciona una plataforma de control de acceso basado en rol, RBAC, mediante el acceso remoto a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="161ca-114">Provides a role-based access control (RBAC) platform through PowerShell Remoting.</span></span>
<span data-ttu-id="161ca-115">*Permite a usuarios específicos realizar tareas administrativas específicas en servidores sin concederles derechos de administrador.*</span><span class="sxs-lookup"><span data-stu-id="161ca-115">*It allows specific users to perform specific administrative tasks on servers without giving them administrator rights.*</span></span>
<span data-ttu-id="161ca-116">Esto permite llenar el vacío de las soluciones de RBAC existentes y simplifica la administración de las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="161ca-116">This allows you to fill in the gaps between your existing RBAC solutions, and simplifies management of those settings.</span></span>

