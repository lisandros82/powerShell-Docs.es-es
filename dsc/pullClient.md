---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "Configuración de un cliente de extracción de DSC"
ms.openlocfilehash: d2d1bab7ba2b482b2a66ce59b5f80ea32c242c47
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="setting-up-a-dsc-pull-client"></a><span data-ttu-id="b0816-103">Configuración de un cliente de extracción de DSC</span><span class="sxs-lookup"><span data-stu-id="b0816-103">Setting up a DSC pull client</span></span>

> <span data-ttu-id="b0816-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b0816-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b0816-105">Es necesario indicar a cada nodo de destino que debe usar el modo de incorporación de cambios y se le debe facilitar la dirección URL o la ubicación de archivo donde puede establecer contacto con el servidor de incorporación de cambios para obtener las configuraciones y recursos, así como la ubicación en la que se deben enviar los datos de informe.</span><span class="sxs-lookup"><span data-stu-id="b0816-105">Each target node has to be told to use pull mode and given the URL or file location where it can contact the pull server to get configurations and resources, and where it should send report data.</span></span>


<span data-ttu-id="b0816-106">En los temas siguientes se explica cómo configurar los clientes de extracción:</span><span class="sxs-lookup"><span data-stu-id="b0816-106">The following topics explain how to set up pull clients:</span></span>

* [<span data-ttu-id="b0816-107">Configuración de un cliente de extracción mediante nombres de configuración</span><span class="sxs-lookup"><span data-stu-id="b0816-107">Setting up a pull client using configuration names</span></span>](pullClientConfigNames.md)
* [<span data-ttu-id="b0816-108">Configuración de un cliente de extracción mediante id. de configuración</span><span class="sxs-lookup"><span data-stu-id="b0816-108">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)

> <span data-ttu-id="b0816-109">**Nota**: Estos temas se aplican a de PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="b0816-109">**Note**: These topics apply to PowerShell 5.0.</span></span> <span data-ttu-id="b0816-110">Para configurar un cliente de extracción en PowerShell 4.0, consulte [Configuración de un cliente de extracción con el id. de configuración de PowerShell 4.0](pullClientConfigID4.md).</span><span class="sxs-lookup"><span data-stu-id="b0816-110">To set up a pull client in PowerShell 4.0, see [Setting up a pull client using configuration ID in PowerShell 4.0](pullClientConfigID4.md).</span></span>

