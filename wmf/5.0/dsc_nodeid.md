---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 6c036c2d8f97e559d20dd3ac40133fa06f5dab08
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188292"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="9fc59-102">Separación de los identificadores de nodo y de configuración</span><span class="sxs-lookup"><span data-stu-id="9fc59-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="9fc59-103">Introducción</span><span class="sxs-lookup"><span data-stu-id="9fc59-103">Overview</span></span>

<span data-ttu-id="9fc59-104">Con el fin de proporcionar una experiencia más flexible y simplificada al usar DSC en modo de extracción, hemos agregado una serie de características en esta versión.</span><span class="sxs-lookup"><span data-stu-id="9fc59-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="9fc59-105">Estas características están diseñadas para que pueda tener la flexibilidad de configurar e implementar con facilidad las configuraciones en varios nodos, y seguir realizando el seguimiento de la información de estado y generación de informes de cada nodo individualmente.</span><span class="sxs-lookup"><span data-stu-id="9fc59-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="9fc59-106">Estas características son:</span><span class="sxs-lookup"><span data-stu-id="9fc59-106">These features are as follows:</span></span>

* <span data-ttu-id="9fc59-107">Un nombre de configuración que identifica la configuración de un equipo.</span><span class="sxs-lookup"><span data-stu-id="9fc59-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="9fc59-108">Este nombre pueden compartirlo varios nodos de destino.</span><span class="sxs-lookup"><span data-stu-id="9fc59-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="9fc59-109">Un identificador de agente que identifica de forma única un solo nodo.</span><span class="sxs-lookup"><span data-stu-id="9fc59-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="9fc59-110">Un paso de registro que solo se produce la primera vez que un nodo de destino se conecta a un servidor de extracción.</span><span class="sxs-lookup"><span data-stu-id="9fc59-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="9fc59-111">**Nota:** Estas características y funciones se han agregado, pero no reemplazan los conceptos ni las características de extracción existentes.</span><span class="sxs-lookup"><span data-stu-id="9fc59-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="9fc59-112">Puede usar estas nuevas características o las anteriores con el nuevo servidor de extracción que se incluye en esta versión.</span><span class="sxs-lookup"><span data-stu-id="9fc59-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="9fc59-113">Para más información, consulte [Configuración de un cliente de extracción mediante nombres de configuración](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="9fc59-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
