---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso nxFileLine de DSC para Linux
ms.openlocfilehash: 2e94bab318b5db65df88d268a88585079bab89bf
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953222"
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="ffb84-103">Recurso nxFileLine de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="ffb84-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="ffb84-104">El recurso **nxFileLine** de Desired State Configuration (DSC) de PowerShell ofrece un mecanismo para administrar líneas dentro de un archivo de configuración en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="ffb84-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="ffb84-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ffb84-105">Syntax</span></span>

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="ffb84-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ffb84-106">Properties</span></span>

|<span data-ttu-id="ffb84-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ffb84-107">Property</span></span> |<span data-ttu-id="ffb84-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="ffb84-108">Description</span></span> |
|---|---|
|<span data-ttu-id="ffb84-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="ffb84-109">FilePath</span></span> |<span data-ttu-id="ffb84-110">La ruta de acceso completa al archivo para administrar las líneas en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="ffb84-110">The full path to the file to manage lines in on the target node.</span></span> |
|<span data-ttu-id="ffb84-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="ffb84-111">ContainsLine</span></span> |<span data-ttu-id="ffb84-112">Una línea que debe asegurarse que exista en el archivo.</span><span class="sxs-lookup"><span data-stu-id="ffb84-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="ffb84-113">Esta línea se anexará al archivo si no existe en él.</span><span class="sxs-lookup"><span data-stu-id="ffb84-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="ffb84-114">**ContainsLine** es una propiedad obligatoria, pero se puede establecer en una cadena vacía (`ContainsLine = ""`) si no se necesita.</span><span class="sxs-lookup"><span data-stu-id="ffb84-114">**ContainsLine** is mandatory, but can be set to an empty string (`ContainsLine = ""`) if it is not needed.</span></span> |
|<span data-ttu-id="ffb84-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="ffb84-115">DoesNotContainPattern</span></span> |<span data-ttu-id="ffb84-116">Un patrón de expresiones regulares para las líneas que no deben existir en el archivo.</span><span class="sxs-lookup"><span data-stu-id="ffb84-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="ffb84-117">Para todas las líneas que existan en el archivo y coincidan con esta expresión regular, se quitará la línea del archivo.</span><span class="sxs-lookup"><span data-stu-id="ffb84-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="ffb84-118">Propiedades comunes</span><span class="sxs-lookup"><span data-stu-id="ffb84-118">Common properties</span></span>

|<span data-ttu-id="ffb84-119">Propiedad</span><span class="sxs-lookup"><span data-stu-id="ffb84-119">Property</span></span> |<span data-ttu-id="ffb84-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="ffb84-120">Description</span></span> |
|---|---|
|<span data-ttu-id="ffb84-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="ffb84-121">DependsOn</span></span> |<span data-ttu-id="ffb84-122">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="ffb84-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="ffb84-123">Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="ffb84-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="ffb84-124">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="ffb84-124">Example</span></span>

<span data-ttu-id="ffb84-125">En este ejemplo se muestra cómo utilizar el recurso **nxFileLine** para configurar el archivo `/etc/sudoers`, asegurándose de que el usuario monuser esté configurado como not requiretty.</span><span class="sxs-lookup"><span data-stu-id="ffb84-125">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```