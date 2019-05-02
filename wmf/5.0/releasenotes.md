---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 07ebcfd37cc3e1f38a9434ffa8d86f479b89ee0f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085225"
---
# <a name="windows-management-framework-wmf-50-rtm-release-notes-overview"></a><span data-ttu-id="17477-102">Introducción a las notas de la versión de Windows Management Framework (WMF) 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="17477-102">Windows Management Framework (WMF) 5.0 RTM Release Notes Overview</span></span>

<span data-ttu-id="17477-103">**WMF 5.0 se ha reemplazado por WMF 5.1. Los usuarios que tengan WMF 5.0 deben actualizarlo a WMF 5.1 para poder recibir soporte técnico. Siga las [instrucciones de instalación de WMF 5.1](../5.1/install-configure.md)**.</span><span class="sxs-lookup"><span data-stu-id="17477-103">**WMF 5.0 is superseded by WMF 5.1. Users with WMF 5.0 must upgrade to WMF 5.1 to receive support. Please follow the [installation intructions of WMF 5.1](../5.1/install-configure.md)**</span></span>

<span data-ttu-id="17477-104">Windows Management Framework (WMF) 5.0 RTM ofrece funcionalidad actualizada de WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="17477-104">Windows Management Framework (WMF) 5.0 RTM brings functionality that has been updated from WMF 4.0.</span></span> <span data-ttu-id="17477-105">WMF 5.0 RTM está disponible solo para la instalación en **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1** y **Windows 7 SP1**, y contiene las versiones actualizadas o la introducción de las características siguientes:</span><span class="sxs-lookup"><span data-stu-id="17477-105">WMF 5.0 RTM is available for installation only on **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1**, and **Windows 7 SP1** and contains updated versions or introduction of the following features:</span></span>

- <span data-ttu-id="17477-106">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="17477-106">Windows PowerShell</span></span>
- <span data-ttu-id="17477-107">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="17477-107">Just Enough Administration (JEA)</span></span>
- <span data-ttu-id="17477-108">Configuración de estado deseado (DSC) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="17477-108">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="17477-109">Entorno de scripting integrado (ISE) de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="17477-109">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>
- <span data-ttu-id="17477-110">Windows PowerShell Web Services (Extensión IIS Management OData)</span><span class="sxs-lookup"><span data-stu-id="17477-110">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="17477-111">Administración remota de Windows (WinRM)</span><span class="sxs-lookup"><span data-stu-id="17477-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="17477-112">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="17477-112">Windows Management Instrumentation (WMI)</span></span>

<span data-ttu-id="17477-113">WMF 5.0 RTM reemplaza a [WMF 5.0 Production Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span><span class="sxs-lookup"><span data-stu-id="17477-113">WMF 5.0 RTM replaces the [WMF 5.0 Production Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span></span> <span data-ttu-id="17477-114">Puede instalar WMF 5.0 RTM sin desinstalar WMF 5.0 Production Preview, pero debe desinstalar todas las demás versiones anteriores de WMF 5.0 Preview antes de instalar WMF 5.0 RTM.</span><span class="sxs-lookup"><span data-stu-id="17477-114">You can install WMF 5.0 RTM without uninstalling WMF 5.0 Production Preview, but you must uninstall all other older releases of WMF 5.0 previews before installing the WMF 5.0 RTM.</span></span>

<span data-ttu-id="17477-115">*Nota:* Si está ejecutando Windows 10, puede obtener el mismo conjunto de funciones disponibles en WMF 5.0 RTM mediante la actualización de noviembre de Windows 10 (versión 1511).</span><span class="sxs-lookup"><span data-stu-id="17477-115">*Note:* If you are running Windows 10, you can get the same set of functionality available in WMF 5.0 RTM by updating to the November update of Windows 10 (Version 1511).</span></span> <span data-ttu-id="17477-116">Si aún no actualizó su sistema con Windows 10, seleccione el botón Inicio y, después, Configuración > Actualización y seguridad > Windows Update > Buscar actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="17477-116">If you have not already updated your Windows 10 system, select the Start button, then select Settings > Update & security > Windows Update > Check for updates.</span></span>
