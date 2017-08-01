---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "ARCHIVO LÉAME"
ms.technology: powershell
ms.openlocfilehash: b0ef4ff685b82e1a4e9ab83a45736720df7b39a2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="just-enough-administration"></a><span data-ttu-id="25c3b-103">Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="25c3b-103">Just Enough Administration</span></span>
<span data-ttu-id="25c3b-104">Just Enough Administration (JEA) es una tecnología de seguridad que permite la administración delegada de todo lo que se puede administrar con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="25c3b-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything that can be managed with PowerShell.</span></span>
<span data-ttu-id="25c3b-105">Con JEA, se puede hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="25c3b-105">With JEA, you can:</span></span>
- <span data-ttu-id="25c3b-106">**Reducir el número de administradores de las máquinas** aprovechando las cuentas virtuales que realizan acciones con privilegios en nombre de usuarios normales.</span><span class="sxs-lookup"><span data-stu-id="25c3b-106">**Reduce the number of administrators on your machines** by leveraging virtual accounts that perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="25c3b-107">**Limitar lo que pueden hacer los usuarios** especificando qué cmdlets, funciones y comandos externos pueden ejecutar.</span><span class="sxs-lookup"><span data-stu-id="25c3b-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="25c3b-108">**Entender mejor lo que hacen los usuarios** con transcripciones "con consentimiento temporal" que muestran exactamente qué comandos ejecutó un usuario durante una sesión.</span><span class="sxs-lookup"><span data-stu-id="25c3b-108">**Better understand what your users are doing** with "over the shoulder" transcriptions that show you exactly what commands a user executed during a session.</span></span>

<span data-ttu-id="25c3b-109">**¿Por qué es importante?**</span><span class="sxs-lookup"><span data-stu-id="25c3b-109">**Why is this important?**</span></span>  
<span data-ttu-id="25c3b-110">Considere el escenario común en el que los servidores DNS coexisten con los controladores de dominio de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="25c3b-110">Consider the common scenario where your DNS servers are co-located with your Active Directory Domain Controllers.</span></span>
<span data-ttu-id="25c3b-111">Los administradores DNS necesitan tener privilegios de administrador local para solucionar problemas con el servidor DNS, pero para ello tiene que hacerlos miembros del grupo de seguridad "Administradores de dominio" con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="25c3b-111">Your DNS administrators need to have local administrator privileges to fix issues with the DNS server, but in order to do so you have to make them members of the highly privileged "Domain Admins" security group.</span></span>
<span data-ttu-id="25c3b-112">Este enfoque proporciona a los administradores de DNS el control sobre todo el dominio y les permite acceder a todos los recursos de la máquina.</span><span class="sxs-lookup"><span data-stu-id="25c3b-112">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="25c3b-113">Con JEA, puede configurar un rol para los administradores DNS que les proporcione acceso a todos los comandos que necesitan para realizar su trabajo, pero a nada más.</span><span class="sxs-lookup"><span data-stu-id="25c3b-113">With JEA in place, you can configure a role for your DNS administrators that gives them access to all the commands they need to get their job done, but nothing more.</span></span>
<span data-ttu-id="25c3b-114">Esto significa que puede proporcionar el acceso adecuado para reparar una caché DNS dudosa sin concederles involuntariamente derechos en Active Directory, para examinar el sistema de archivos o para ejecutar scripts potencialmente peligrosos.</span><span class="sxs-lookup"><span data-stu-id="25c3b-114">This means you can provide the appropriate access to repair a poisoned DNS cache without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span>
<span data-ttu-id="25c3b-115">Y lo que es mejor, cuando la sesión de JEA está configurada para usar cuentas virtuales con privilegios de un solo uso, los administradores de DNS pueden conectarse al servidor mediante credenciales *sin privilegios* y seguir siendo capaces de ejecutar comandos con privilegios.</span><span class="sxs-lookup"><span data-stu-id="25c3b-115">Better yet, when the JEA session is configured to use one-time privileged virtual accounts, your DNS administrators can connect to the server using *unprivileged* credentials and still be able to run privileged commands.</span></span>

## <a name="availability"></a><span data-ttu-id="25c3b-116">Disponibilidad</span><span class="sxs-lookup"><span data-stu-id="25c3b-116">Availability</span></span>
<span data-ttu-id="25c3b-117">JEA se está desarrollando en paralelo a Windows Server 2016, y está disponible en versiones anteriores de Windows mediante actualizaciones de Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="25c3b-117">JEA is being developed in parallel to Windows Server 2016, and is available on older versions of Windows through Windows Management Framework updates.</span></span>
<span data-ttu-id="25c3b-118">La versión actual de JEA está disponible en las siguientes plataformas:</span><span class="sxs-lookup"><span data-stu-id="25c3b-118">The current release of JEA is available on the following platforms:</span></span>

<span data-ttu-id="25c3b-119">**Windows Server**</span><span class="sxs-lookup"><span data-stu-id="25c3b-119">**Windows Server**</span></span>
- <span data-ttu-id="25c3b-120">Windows Server 2016 Technical Preview 4 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="25c3b-120">Windows Server 2016 Technical Preview 4 and higher</span></span>
- <span data-ttu-id="25c3b-121">Windows Server 2012 R2, 2012 y 2008 R2\* con [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) instalado</span><span class="sxs-lookup"><span data-stu-id="25c3b-121">Windows Server 2012 R2, 2012, and 2008 R2\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="25c3b-122">**Cliente de Windows**</span><span class="sxs-lookup"><span data-stu-id="25c3b-122">**Windows Client**</span></span>
- <span data-ttu-id="25c3b-123">Windows 10 con la actualización de noviembre (1511) instalada</span><span class="sxs-lookup"><span data-stu-id="25c3b-123">Windows 10 with the November Update (1511) installed</span></span>
- <span data-ttu-id="25c3b-124">Windows 8.1, 8 y 7\* con [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) instalado</span><span class="sxs-lookup"><span data-stu-id="25c3b-124">Windows 8.1, 8, and 7\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="25c3b-125">\* La compatibilidad con cuentas virtuales en sesiones de JEA no está disponible en Windows Server 2008 R2 o Windows 7.</span><span class="sxs-lookup"><span data-stu-id="25c3b-125">\* Support for virtual accounts in JEA sessions is currently not available on Windows Server 2008 R2 or Windows 7.</span></span>


## <a name="explore-the-experience-guide"></a><span data-ttu-id="25c3b-126">Explorar la guía de la experiencia</span><span class="sxs-lookup"><span data-stu-id="25c3b-126">Explore the experience guide</span></span>
<span data-ttu-id="25c3b-127">¿Listo para aprender a crear, implementar y utilizar su propio punto de conexión JEA?</span><span class="sxs-lookup"><span data-stu-id="25c3b-127">Ready to learn how to author, deploy, and use your own JEA endpoint?</span></span>

<span data-ttu-id="25c3b-128">Esta guía incluye una rápida introducción con un punto de conexión de JEA predefinido para que se haga una idea de cómo es la experiencia del usuario final y, después, describe el proceso de crear un punto de conexión desde cero para demostrar conceptos como las configuraciones de sesión y las funcionalidades de rol.</span><span class="sxs-lookup"><span data-stu-id="25c3b-128">This guide gets you started quickly with a pre-built JEA endpoint to get an idea of what the end-user experience is like, then walks you through recreating an endpoint from scratch to help demonstrate concepts like session configurations and Role Capabilities.</span></span>

1.  <span data-ttu-id="25c3b-129">[Introducción](introduction.md) </span><span class="sxs-lookup"><span data-stu-id="25c3b-129">[Introduction](introduction.md) </span></span>  
<span data-ttu-id="25c3b-130">Revise brevemente por qué debería interesarle JEA.</span><span class="sxs-lookup"><span data-stu-id="25c3b-130">Briefly review why you should care about JEA</span></span>

2.  [<span data-ttu-id="25c3b-131">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="25c3b-131">Prerequisites</span></span>](prerequisites.md)  
<span data-ttu-id="25c3b-132">Explica cómo configurar su entorno</span><span class="sxs-lookup"><span data-stu-id="25c3b-132">Explains how to set up your environment</span></span>

3.  [<span data-ttu-id="25c3b-133">Uso de JEA</span><span class="sxs-lookup"><span data-stu-id="25c3b-133">Using JEA</span></span>](using-jea.md)  
<span data-ttu-id="25c3b-134">Ayuda a entender la experiencia de usuario de JEA.</span><span class="sxs-lookup"><span data-stu-id="25c3b-134">Helps you start by understanding the operator experience of using JEA</span></span>

4.  [<span data-ttu-id="25c3b-135">Recreación de la demostración</span><span class="sxs-lookup"><span data-stu-id="25c3b-135">Remake the Demo</span></span>](remake-the-demo-endpoint.md)  
<span data-ttu-id="25c3b-136">Cree una configuración de sesión de JEA desde cero.</span><span class="sxs-lookup"><span data-stu-id="25c3b-136">Create a JEA Session Configuration from scratch</span></span>

5.  [<span data-ttu-id="25c3b-137">Funcionalidades de rol</span><span class="sxs-lookup"><span data-stu-id="25c3b-137">Role Capabilities</span></span>](role-capabilities.md)  
<span data-ttu-id="25c3b-138">Aprenda cómo personalizar las funcionalidades JEA con archivos de funcionalidad de rol.</span><span class="sxs-lookup"><span data-stu-id="25c3b-138">Learn about how to customize JEA capabilities with Role Capability Files</span></span>

6.  [<span data-ttu-id="25c3b-139">De un extremo a otro: Active Directory</span><span class="sxs-lookup"><span data-stu-id="25c3b-139">End to End - Active Directory</span></span>](end-to-end---active-directory.md)  
<span data-ttu-id="25c3b-140">Cree un punto de conexión completamente nuevo para administrar Active Directory.</span><span class="sxs-lookup"><span data-stu-id="25c3b-140">Make a whole new endpoint for managing Active Directory</span></span>

7.  [<span data-ttu-id="25c3b-141">Implementación y mantenimiento de varias máquinas</span><span class="sxs-lookup"><span data-stu-id="25c3b-141">Multi-machine Deployment and Maintenance</span></span>](multi-machine-deployment-and-maintenance.md)  
<span data-ttu-id="25c3b-142">Descubra cómo cambia la implementación y la creación según la escala.</span><span class="sxs-lookup"><span data-stu-id="25c3b-142">Discover how deployment and authoring changes with scale</span></span>

8.  [<span data-ttu-id="25c3b-143">Generación de informes en JEA</span><span class="sxs-lookup"><span data-stu-id="25c3b-143">Reporting on JEA</span></span>](reporting-on-jea.md)  
<span data-ttu-id="25c3b-144">Descubra cómo auditar e informar sobre todas las acciones y la infraestructura de JEA.</span><span class="sxs-lookup"><span data-stu-id="25c3b-144">Discover how to audit and report on all JEA actions and infrastructure</span></span>

9.  <span data-ttu-id="25c3b-145">Apéndices</span><span class="sxs-lookup"><span data-stu-id="25c3b-145">Appendixes</span></span>
  - [<span data-ttu-id="25c3b-146">Conceptos clave usados a lo largo de esta guía</span><span class="sxs-lookup"><span data-stu-id="25c3b-146">Key Concepts Used Throughout This Guide</span></span>](key-concepts-used-throughout-this-guide.md)  
  -  [<span data-ttu-id="25c3b-147">Creación de un controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="25c3b-147">Creating a Domain Controller</span></span>](creating-a-domain-controller.md)  
  -  [<span data-ttu-id="25c3b-148">Acerca de la lista negra</span><span class="sxs-lookup"><span data-stu-id="25c3b-148">On Blacklisting</span></span>](on-blacklisting.md)  
  -  [<span data-ttu-id="25c3b-149">Consideraciones al limitar comandos</span><span class="sxs-lookup"><span data-stu-id="25c3b-149">Considerations When Limiting Commands</span></span>](considerations-when-limiting-commands.md)  
  -  [<span data-ttu-id="25c3b-150">Dificultades comunes de las funcionalidades de rol</span><span class="sxs-lookup"><span data-stu-id="25c3b-150">Common Role Capability Pitfalls</span></span>](common-role-capability-pitfalls.md)

## <a name="start-authoring-your-own-jea-endpoints"></a><span data-ttu-id="25c3b-151">Empiece a crear sus propios puntos de conexión de JEA</span><span class="sxs-lookup"><span data-stu-id="25c3b-151">Start authoring your own JEA endpoints</span></span>
<span data-ttu-id="25c3b-152">Es fácil crear un punto de conexión de JEA: lo único que necesita es un sistema habilitado para JEA y un editor de texto (como PowerShell ISE).</span><span class="sxs-lookup"><span data-stu-id="25c3b-152">It's easy to author a JEA endpoint -- all you need is a JEA-enabled system and a text editor (like PowerShell ISE).</span></span>
<span data-ttu-id="25c3b-153">Se recomienda que, para empezar, cree archivos esqueleto mediante [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx)y [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx) sin ningún otro argumento.</span><span class="sxs-lookup"><span data-stu-id="25c3b-153">One helpful tip to get started is to create skeleton files using [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) and [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx) without any other arguments.</span></span>
<span data-ttu-id="25c3b-154">Estos archivos esqueleto contienen todos los campos de configuración aplicables, junto con comentarios útiles que explican para qué puede usarse cada campo.</span><span class="sxs-lookup"><span data-stu-id="25c3b-154">These skeleton files contain all of the applicable configuration fields along with helpful comments to explain what each field can be used for.</span></span>

<span data-ttu-id="25c3b-155">Para facilitar la creación de puntos de conexión de JEA, consulte el [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) (Asistente para el kit de herramientas de JEA), que proporciona una GUI con la que puede crear archivos de configuración de sesión y funcionalidad de rol.</span><span class="sxs-lookup"><span data-stu-id="25c3b-155">To make authoring JEA endpoints even easier, check out the [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) which provides a GUI with which you can author Session Configuration and Role Capability files.</span></span>
<span data-ttu-id="25c3b-156">Incluso permite generar funcionalidades de rol basadas en los registros de PowerShell para que tome como punto de partida los comandos que los usuarios ejecutan habitualmente para realizar su trabajo.</span><span class="sxs-lookup"><span data-stu-id="25c3b-156">It even supports generating Role Capabilities based on PowerShell logs to start you off with the commands your users regularly run to get their jobs done.</span></span>

