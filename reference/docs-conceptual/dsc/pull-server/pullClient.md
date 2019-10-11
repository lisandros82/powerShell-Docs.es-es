---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Configuración de un cliente de extracción de DSC
ms.openlocfilehash: 54c68ac26e5388260e252ce01418170e26ddecde
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955172"
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="b4fde-103">Configuración de un cliente de extracción de DSC</span><span class="sxs-lookup"><span data-stu-id="b4fde-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="b4fde-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b4fde-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4fde-105">El servidor de extracción (característica de Windows *DSC-Service*) es un componente de Windows Server admitido, si bien no está previsto ofrecer nuevas características o funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="b4fde-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="b4fde-106">Se recomienda empezar a realizar la transición de los clientes administrados a [DSC de Azure Automation](/azure/automation/automation-dsc-getting-started) (incluye características más allá del servidor de extracción de Windows Server) o a una de las soluciones de la comunidad que figuran [aquí](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="b4fde-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="b4fde-107">Es necesario indicar a cada nodo de destino que debe usar el modo de incorporación de cambios y se le debe facilitar la dirección URL o la ubicación de archivo donde puede establecer contacto con el servidor de incorporación de cambios para obtener las configuraciones y recursos, así como la ubicación en la que se deben enviar los datos de informe.</span><span class="sxs-lookup"><span data-stu-id="b4fde-107">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>

<span data-ttu-id="b4fde-108">En los temas siguientes se explica cómo configurar los clientes de extracción:</span><span class="sxs-lookup"><span data-stu-id="b4fde-108">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="b4fde-109">Configuración de un cliente de extracción mediante nombres de configuración</span><span class="sxs-lookup"><span data-stu-id="b4fde-109">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="b4fde-110">Configuración de un cliente de extracción mediante id. de configuración</span><span class="sxs-lookup"><span data-stu-id="b4fde-110">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> [!NOTE]
> <span data-ttu-id="b4fde-111">Estos temas se aplican a PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="b4fde-111">These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="b4fde-112">Para configurar un cliente de extracción en PowerShell 4.0, consulte [Configuración de un cliente de extracción con el id. de configuración de PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="b4fde-112">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>