---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Conceptos clave usados a lo largo de esta guía"
ms.technology: powershell
ms.openlocfilehash: 873ab19fdf43ec4ac41cc546aa94b64fbc607984
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="key-concepts-used-throughout-this-guide"></a><span data-ttu-id="94f8c-103">Conceptos clave usados a lo largo de esta guía</span><span class="sxs-lookup"><span data-stu-id="94f8c-103">Key Concepts Used Throughout This Guide</span></span>
<span data-ttu-id="94f8c-104">**¿Qué es exactamente JEA?**</span><span class="sxs-lookup"><span data-stu-id="94f8c-104">**What exactly is JEA?**</span></span>

<span data-ttu-id="94f8c-105">JEA es una extensión de [puntos de conexión restringidos](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) de PowerShell que agrega definiciones de rol, cuentas virtuales y otras mejoras que ayudan a bloquear los puntos de conexión de administración.</span><span class="sxs-lookup"><span data-stu-id="94f8c-105">JEA is an extension of PowerShell [constrained endpoints](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) that adds in role definitions, virtual accounts, and several other improvements to make it even easier to lock down your management endpoints.</span></span>
<span data-ttu-id="94f8c-106">Un punto de conexión de JEA consta de un archivo de configuración de sesión de PowerShell y uno o más archivos de funcionalidad de rol.</span><span class="sxs-lookup"><span data-stu-id="94f8c-106">A JEA endpoint consists of a PowerShell Session Configuration file and one or more Role Capability files.</span></span>

<span data-ttu-id="94f8c-107">**¿Qué son los archivos de configuración de sesión y de funcionalidad de rol?**</span><span class="sxs-lookup"><span data-stu-id="94f8c-107">**What are Session Configuration and Role Capability files?**</span></span>

<span data-ttu-id="94f8c-108">Los archivos de configuración de sesión de PowerShell (.pssc) definen *quién* se puede conectar a un punto de conexión de PowerShell y *cómo* está configurado.</span><span class="sxs-lookup"><span data-stu-id="94f8c-108">PowerShell Session Configuration files (.pssc) define *who* can connect to a PowerShell endpoint and *how* it is configured.</span></span>
<span data-ttu-id="94f8c-109">Aquí es donde se asignan los usuarios y los grupos de seguridad a los roles de administración específicos y se configuran valores globales como las cuentas virtuales y las directivas de transcripción.</span><span class="sxs-lookup"><span data-stu-id="94f8c-109">This is where you would map users and security groups to specific management roles and configure global settings like virtual accounts and transcription policies.</span></span>
<span data-ttu-id="94f8c-110">Los archivos de configuración de sesión son específicos de cada máquina, lo que le permite controlar el acceso por máquina, si le interesa.</span><span class="sxs-lookup"><span data-stu-id="94f8c-110">Session configuration files are specific to each machine, which allows you to control access on a per-machine basis if desired.</span></span>

<span data-ttu-id="94f8c-111">Los archivos de funcionalidad de rol de PowerShell (.psrc) definen *qué* pueden hacer en el sistema los usuarios que pertenecen a cada rol.</span><span class="sxs-lookup"><span data-stu-id="94f8c-111">PowerShell Role Capability files (.psrc) define *what* users belonging to a role are able to do on the system.</span></span>
<span data-ttu-id="94f8c-112">Aquí puede restringir qué cmdlets, funciones, proveedores y programas externos puede usar un usuario en su sesión de JEA.</span><span class="sxs-lookup"><span data-stu-id="94f8c-112">Here, you can restrict which cmdlets, functions, providers, and external programs a user may use in their JEA session.</span></span>
<span data-ttu-id="94f8c-113">Los archivos de funcionalidad de rol suelen ser genéricos del rol al que se está atendiendo (administrador de DNS, departamento de soporte técnico de nivel 1, auditoría de inventario de solo lectura, etc.) y pertenecen a los módulos de PowerShell, lo que facilita compartirlos con el entorno y con otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="94f8c-113">Role Capability files are often generic for the role being served (DNS admin, level 1 helpdesk, read-only inventory auditing, etc.) and belong to PowerShell modules, making it easy to share them across your environment and with others.</span></span>

<span data-ttu-id="94f8c-114">**¿Cómo aprovecha JEA las cuentas virtuales?**</span><span class="sxs-lookup"><span data-stu-id="94f8c-114">**How does JEA leverage virtual accounts?**</span></span>

<span data-ttu-id="94f8c-115">En el archivo de configuración de sesión de PowerShell, puede configurar las sesiones de JEA para que usen cuentas de ejecución virtuales.</span><span class="sxs-lookup"><span data-stu-id="94f8c-115">In the PowerShell Session Configuration file, you can configure JEA sessions to use virtual "run as" accounts.</span></span>
<span data-ttu-id="94f8c-116">Las cuentas virtuales son cuentas con privilegios de un solo uso creadas para el usuario específico que se conecta en esa sesión específica en el contexto en el que se ejecutan los comandos del usuario.</span><span class="sxs-lookup"><span data-stu-id="94f8c-116">Virtual accounts are one-time privileged accounts spun up for the specific connecting user in that specific session under which context the user's commands are executed.</span></span>
<span data-ttu-id="94f8c-117">Las cuentas virtuales pertenecen de forma predeterminada al grupo de seguridad local "Administradores", pero se pueden configurar opcionalmente para que solo pertenezcan a los grupos de seguridad que especifique.</span><span class="sxs-lookup"><span data-stu-id="94f8c-117">Virtual accounts belong to the local "Administrators" security group by default, but can optionally be configured to only belong to security groups you specify.</span></span>

<span data-ttu-id="94f8c-118">**Comunicación remota de PowerShell**: permite ejecutar comandos de PowerShell en máquinas remotas.</span><span class="sxs-lookup"><span data-stu-id="94f8c-118">**PowerShell Remoting**: PowerShell remoting allows you to run PowerShell commands against remote machines.</span></span>
<span data-ttu-id="94f8c-119">Puede operar en uno o varios equipos y usar conexiones temporales o permanentes.</span><span class="sxs-lookup"><span data-stu-id="94f8c-119">You can operate against one or many computers, and use either temporary or persistent connections.</span></span>
<span data-ttu-id="94f8c-120">En esta demostración, obtuvo acceso de manera remota a la máquina local con una sesión interactiva.</span><span class="sxs-lookup"><span data-stu-id="94f8c-120">In this demo, you remoted into your local machine with an interactive session.</span></span>
<span data-ttu-id="94f8c-121">JEA restringe la funcionalidad disponible a través de Comunicación remota de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94f8c-121">JEA restricts the functionality available through PowerShell remoting.</span></span>
<span data-ttu-id="94f8c-122">Para obtener más información sobre Comunicación remota de PowerShell, ejecute `Get-Help about_Remote`.</span><span class="sxs-lookup"><span data-stu-id="94f8c-122">For more information about PowerShell remoting, run `Get-Help about_Remote`.</span></span>

<span data-ttu-id="94f8c-123">**Usuario de ejecución**: en JEA, un usuario sin privilegios de administrador se ejecuta como una cuenta virtual con privilegios.</span><span class="sxs-lookup"><span data-stu-id="94f8c-123">**"RunAs" User**: When using JEA, a non-administrator "runs as" a privileged "Virtual Account."</span></span>
<span data-ttu-id="94f8c-124">La cuenta virtual solo dura mientras se produzca la sesión remota.</span><span class="sxs-lookup"><span data-stu-id="94f8c-124">The Virtual Account only lasts the duration of the remote session.</span></span>
<span data-ttu-id="94f8c-125">Es decir, se crea cuando un usuario se conecta al punto de conexión y se destruye cuando el usuario finaliza la sesión.</span><span class="sxs-lookup"><span data-stu-id="94f8c-125">That is to say, it is created when a user connects to the endpoint, and destroyed when the user ends the session.</span></span>
<span data-ttu-id="94f8c-126">De forma predeterminada, la cuenta virtual es miembro del grupo de administradores local.</span><span class="sxs-lookup"><span data-stu-id="94f8c-126">By default, the Virtual Account is a member of the local Administrators group.</span></span>
<span data-ttu-id="94f8c-127">En un controlador de dominio, es miembro de los administradores de dominio.</span><span class="sxs-lookup"><span data-stu-id="94f8c-127">On a domain controller, it is a member of Domain Admins.</span></span>
<span data-ttu-id="94f8c-128">Las cuentas virtuales son locales en la máquina en la que se crean y no tienen permisos fuera de esa máquina.</span><span class="sxs-lookup"><span data-stu-id="94f8c-128">Virtual Accounts are local to the machine on which they are created, and do not have permissions outside of that machine.</span></span>
<span data-ttu-id="94f8c-129">Esto significa que no están registradas en Active Directory (no se les ha asignado ningún RID).</span><span class="sxs-lookup"><span data-stu-id="94f8c-129">This means that they are not registered in Active Directory (no RID is assigned).</span></span>
<span data-ttu-id="94f8c-130">Además, si un comando o script permitido intenta obtener acceso a recursos fuera de la máquina local, obtendrá acceso a esos recursos con la identidad de la máquina, no con la identidad de la cuenta virtual.</span><span class="sxs-lookup"><span data-stu-id="94f8c-130">Additionally, if an allowed command/script tries to access resources outside of the local machine, it will be accessing those resources under the machine's identity, not the Virtual Account identity.</span></span>

<span data-ttu-id="94f8c-131">**Usuario conectado**: usuario sin privilegios de administrador que se conecta al punto de conexión de JEA y al que se asignan roles.</span><span class="sxs-lookup"><span data-stu-id="94f8c-131">**"Connected" User**: The non-administrator user who connects to the JEA endpoint and to whom roles are assigned.</span></span>
<span data-ttu-id="94f8c-132">Los comandos que ejecute este usuario se ejecutan en el contexto del usuario de ejecución o de la cuenta virtual.</span><span class="sxs-lookup"><span data-stu-id="94f8c-132">Any commands this user runs are run under the context of the RunAs User or virtual account.</span></span>

