---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ec4ae8e4b2ef0ec226cb75607f7aaf34b48f6b76
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085650"
---
# <a name="authoring-improvements-using-powershell-ise"></a><span data-ttu-id="6d589-102">Mejoras de creación mediante PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="6d589-102">Authoring Improvements using PowerShell ISE</span></span>

<span data-ttu-id="6d589-103">La creación de configuraciones de DSC en Windows PowerShell ISE es mucho más fácil gracias a las siguientes mejoras:</span><span class="sxs-lookup"><span data-stu-id="6d589-103">Authoring DSC configurations in Windows PowerShell ISE is much easier, thanks to the following improvements:</span></span>

- <span data-ttu-id="6d589-104">Para enumerar todos los recursos de DSC en un bloque de **configuración** o un bloque de **nodo**, escriba **Ctrl+Space** en una línea en blanco dentro de él.</span><span class="sxs-lookup"><span data-stu-id="6d589-104">List all DSC resources within a **configuration** block or **node** block by entering **Ctrl+Space** on a blank line within it.</span></span>
- <span data-ttu-id="6d589-105">Finalización automática de propiedades de recurso de tipo **enumeración**.</span><span class="sxs-lookup"><span data-stu-id="6d589-105">Automatic completion on resource properties that are of the **enumeration** type.</span></span>
- <span data-ttu-id="6d589-106">Finalización automática de la propiedad **DependsOn** de los recursos de DSC, en función de otras instancias de recurso de la configuración.</span><span class="sxs-lookup"><span data-stu-id="6d589-106">Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.</span></span>
- <span data-ttu-id="6d589-107">Mejor finalización con tabulación de los valores de propiedad de recurso.</span><span class="sxs-lookup"><span data-stu-id="6d589-107">Better tab completion of resource property values.</span></span>

<span data-ttu-id="6d589-108">**Nota:** Debe tener una cadena vacía para los valores de propiedad de recurso para poder usar Ctrl+Space para mostrar las opciones.</span><span class="sxs-lookup"><span data-stu-id="6d589-108">**Note:** You must have an empty string for resource property values before you can use Ctrl+Space to list the options.</span></span> <span data-ttu-id="6d589-109">Presione **Tabulador** para recorrer las opciones.</span><span class="sxs-lookup"><span data-stu-id="6d589-109">Pressing **Tab** cycles through options.</span></span>
