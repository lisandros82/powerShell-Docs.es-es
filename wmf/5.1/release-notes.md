---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: "Notas de la versión de WMF 5.1"
ms.openlocfilehash: f80c1ec5886578e3e43f2c96981f40152db000d1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="windows-management-framework-wmf-51-release-notes"></a><span data-ttu-id="4e0fe-103">Notas de la versión de Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="4e0fe-103">Windows Management Framework (WMF) 5.1 Release Notes</span></span> #

<span data-ttu-id="4e0fe-104">WMF 5.1 incluye los componentes de PowerShell, WMI, WinRM e inventario y licencias de software (SIL) que se lanzaron con Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="4e0fe-104">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory and Licensing (SIL) components that were released with Windows Server 2016.</span></span>
<span data-ttu-id="4e0fe-105">WMF 5.1 puede instalarse en Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 y 2012 R2 y proporciona una serie de mejoras con respecto a WMF 5.0 RTM, incluidos:</span><span class="sxs-lookup"><span data-stu-id="4e0fe-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="4e0fe-106">Nuevos cmdlets: usuarios locales y grupos; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="4e0fe-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="4e0fe-107">En las mejoras de PowerShellGet se incluyen la aplicación de módulos firmados y la instalación de módulos JEA</span><span class="sxs-lookup"><span data-stu-id="4e0fe-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="4e0fe-108">PackageManagement ha agregado compatibilidad con contenedores, configuración de CBS, configuración basada en EXE y paquetes de CAB</span><span class="sxs-lookup"><span data-stu-id="4e0fe-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="4e0fe-109">Mejoras de depuración para las clases DSC y PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e0fe-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="4e0fe-110">Mejoras de seguridad, incluido el cumplimiento de módulos firmados por catálogos procedentes del servidor de extracción y al usar cmdlets de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="4e0fe-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="4e0fe-111">Respuestas a varios problemas y varias solicitudes de usuarios</span><span class="sxs-lookup"><span data-stu-id="4e0fe-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="4e0fe-112">**Notas importantes:**</span><span class="sxs-lookup"><span data-stu-id="4e0fe-112">**Important notes:**</span></span>

- <span data-ttu-id="4e0fe-113">**WMF 5.1 necesita .NET Framework 4.5.2**.</span><span class="sxs-lookup"><span data-stu-id="4e0fe-113">**WMF 5.1 requires the .NET Framework 4.5.2**.</span></span> <span data-ttu-id="4e0fe-114">La instalación se realizará correctamente, pero se producirá un error en las características clave si .NET 4.5.2 no está instalado.</span><span class="sxs-lookup"><span data-stu-id="4e0fe-114">Installation will succeed, but key features will fail if .NET 4.5.2 is not installed.</span></span> <span data-ttu-id="4e0fe-115">Las instrucciones están disponibles en el tema [Instalación y configuración de WMF 5.1](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure).</span><span class="sxs-lookup"><span data-stu-id="4e0fe-115">Instructions are available in the [Install and Configure WMF 5.1 ](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/install-configure) topic.</span></span>
- <span data-ttu-id="4e0fe-116">Hay que desinstalar la versión preliminar de WMF 5.1 antes de instalar WMF 5.1 RTM.</span><span class="sxs-lookup"><span data-stu-id="4e0fe-116">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="4e0fe-117">WMF 5.1 puede instalarse directamente sobre WMF 5.0 o WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="4e0fe-117">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="4e0fe-118">__No es necesario__ instalar WMF 4.0 antes de instalar WMF 5.1 en Windows 7 y Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="4e0fe-118">It is __not required__ to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="4e0fe-119">Este era un problema de la versión preliminar de WMF 5.1 y ya se ha resuelto.</span><span class="sxs-lookup"><span data-stu-id="4e0fe-119">That was an issue for the WMF 5.1 Preview release, and has been resolved.</span></span>  


