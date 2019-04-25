---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Eliminación de paquetes
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084171"
---
# <a name="deleting-packages"></a><span data-ttu-id="d3043-103">Eliminación de paquetes</span><span class="sxs-lookup"><span data-stu-id="d3043-103">Deleting Packages</span></span>

<span data-ttu-id="d3043-104">La Galería de PowerShell no permite eliminar paquetes de forma permanente, ya que eso supondría una interrupción para cualquiera que dependa de su disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="d3043-104">The PowerShell Gallery does not support permanent deletion of packages, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="d3043-105">En su lugar, la Galería de PowerShell permite "ocultar" un paquete, lo que se puede llevar a cabo en la página de administración del paquete en el sitio web.</span><span class="sxs-lookup"><span data-stu-id="d3043-105">Instead, the PowerShell Gallery supports a way to 'unlist' a package, which can be done in the package management page on the web site.</span></span>
<span data-ttu-id="d3043-106">Cuando se oculta un paquete, ya no aparece en la búsqueda ni en ninguna lista de paquetes en la Galería de PowerShell o cuando se usan comandos PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="d3043-106">When a package is unlisted, it no longer shows up in search and in any package listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="d3043-107">A pesar de eso, es posible descargarlo si se especifica su versión exacta, que es lo que permite que los scripts automatizados sigan funcionando.</span><span class="sxs-lookup"><span data-stu-id="d3043-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="d3043-108">Si surge una situación excepcional y cree que es necesario eliminar uno de los paquetes, el equipo de la Galería de PowerShell puede encargarse de ello manualmente.</span><span class="sxs-lookup"><span data-stu-id="d3043-108">If you run into an exceptional situation where you think one of your packages must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="d3043-109">Por ejemplo, un motivo válido para eliminarlo puede ser un problema relacionado con la infracción de los derechos de autor o con contenido potencialmente dañino.</span><span class="sxs-lookup"><span data-stu-id="d3043-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="d3043-110">En ese caso, debe enviar una solicitud de soporte técnico a través de la [Galería de PowerShell](http://www.PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="d3043-110">You should submit a support request through [PowerShell Gallery](http://www.PowerShellGallery.com) in that case.</span></span>
