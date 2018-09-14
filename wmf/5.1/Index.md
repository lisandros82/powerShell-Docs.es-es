---
ms.date: 08/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Notas de la versión de WMF 5.1
ms.openlocfilehash: 3081d200f0c6aac6074719bb1c204900aabf96c2
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522912"
---
# <a name="windows-management-framework-wmf-51"></a><span data-ttu-id="e15c1-103">Windows Management Framework (WMF) 5.1</span><span class="sxs-lookup"><span data-stu-id="e15c1-103">Windows Management Framework (WMF) 5.1</span></span> #

<span data-ttu-id="e15c1-104">WMF proporciona a los usuarios la capacidad de actualizar los sistemas de Windows existentes a las versiones de los componentes de PowerShell, WMI, WinRM y Registro de inventario de software (SIL) que se publicaron con Windows Server 2016.</span><span class="sxs-lookup"><span data-stu-id="e15c1-104">WMF provides users with the ability to update existing Windows systems to the versions of PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span>

<span data-ttu-id="e15c1-105">WMF 5.1 puede instalarse en Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 y 2012 R2 y proporciona una serie de mejoras con respecto a WMF 5.0 RTM, incluidos:</span><span class="sxs-lookup"><span data-stu-id="e15c1-105">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides a number of improvements over WMF 5.0 RTM including:</span></span>

- <span data-ttu-id="e15c1-106">Nuevos cmdlets: usuarios locales y grupos; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="e15c1-106">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="e15c1-107">En las mejoras de PowerShellGet se incluyen la aplicación de módulos firmados y la instalación de módulos JEA</span><span class="sxs-lookup"><span data-stu-id="e15c1-107">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="e15c1-108">PackageManagement ha agregado compatibilidad con contenedores, configuración de CBS, configuración basada en EXE y paquetes de CAB</span><span class="sxs-lookup"><span data-stu-id="e15c1-108">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="e15c1-109">Mejoras de depuración para las clases DSC y PowerShell</span><span class="sxs-lookup"><span data-stu-id="e15c1-109">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="e15c1-110">Mejoras de seguridad, incluido el cumplimiento de módulos firmados por catálogos procedentes del servidor de extracción y al usar cmdlets de PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e15c1-110">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="e15c1-111">Respuestas a varios problemas y varias solicitudes de usuarios</span><span class="sxs-lookup"><span data-stu-id="e15c1-111">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="e15c1-112">Para conocer las novedades de esta versión, examine los temas enumerados en [Características y escenarios nuevos](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features).</span><span class="sxs-lookup"><span data-stu-id="e15c1-112">To learn about what is new in this release, browse the topics listed under [New Scenarios and Features](https://docs.microsoft.com/powershell/wmf/5.1/scenarios-features).</span></span>

<span data-ttu-id="e15c1-113">En el tema [Instalación y configuración](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) se enumeran los requisitos y se proporcionan instrucciones para la instalación de WMF.</span><span class="sxs-lookup"><span data-stu-id="e15c1-113">The [Install and Configure](https://docs.microsoft.com/powershell/wmf/5.1/install-configure) topic lists the requirements and provides installation instructions for WMF.</span></span>

<span data-ttu-id="e15c1-114">En el tema [Compatibilidad](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) se enumeran las versiones de WMF que pueden instalarse en cada edición de Windows.</span><span class="sxs-lookup"><span data-stu-id="e15c1-114">The [Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/compatibility) topic lists which versions of WMF may be installed on which Windows releases.</span></span>

<span data-ttu-id="e15c1-115">En [Compatibilidad de productos](https://docs.microsoft.com/powershell/wmf/5.1/productincompat) se enumeran las aplicaciones de Microsoft para las que no se ha aprobado el uso de WMF 5.1 en este momento.</span><span class="sxs-lookup"><span data-stu-id="e15c1-115">[Product Compatibility](https://docs.microsoft.com/powershell/wmf/5.1/productincompat) lists the Microsoft applications that have not approved WMF 5.1 for use at this time.</span></span>

<span data-ttu-id="e15c1-116">La documentación de MSDN incluye detalles sobre los componentes de WMF:</span><span class="sxs-lookup"><span data-stu-id="e15c1-116">Details for the components of WMF will be found in MSDN documentation:</span></span>

- [<span data-ttu-id="e15c1-117">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="e15c1-117">PowerShell 5.1</span></span>](https://docs.microsoft.com/powershell/)
- <span data-ttu-id="e15c1-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="e15c1-118">[WMI](https://msdn.microsoft.com/library/jj152383(v=vs.85).aspx)</span></span>
- <span data-ttu-id="e15c1-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="e15c1-119">[WinRM](https://msdn.microsoft.com/library/aa384426(v=vs.85).aspx)</span></span>
- <span data-ttu-id="e15c1-120">[Registro de inventario de software](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="e15c1-120">[Software Inventory Logging](https://technet.microsoft.com/library/dn383584(v=ws.11).aspx)</span></span>
