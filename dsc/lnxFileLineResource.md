---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Recurso nxFileLine de DSC para Linux
ms.openlocfilehash: 798bfa4150996622c33c77d6a5aa3be4af342f1b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxfileline-resource"></a><span data-ttu-id="c6c0b-103">Recurso nxFileLine de DSC para Linux</span><span class="sxs-lookup"><span data-stu-id="c6c0b-103">DSC for Linux nxFileLine Resource</span></span>

<span data-ttu-id="c6c0b-104">El recurso **nxFileLine** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para administrar líneas dentro de un archivo de configuración en un nodo de Linux.</span><span class="sxs-lookup"><span data-stu-id="c6c0b-104">The **nxFileLine** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to to manage lines within a configuration file on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="c6c0b-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c6c0b-105">Syntax</span></span>

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="c6c0b-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="c6c0b-106">Properties</span></span>

|  <span data-ttu-id="c6c0b-107">Propiedad</span><span class="sxs-lookup"><span data-stu-id="c6c0b-107">Property</span></span> |  <span data-ttu-id="c6c0b-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="c6c0b-108">Description</span></span> |
|---|---|
| <span data-ttu-id="c6c0b-109">FilePath</span><span class="sxs-lookup"><span data-stu-id="c6c0b-109">FilePath</span></span>| <span data-ttu-id="c6c0b-110">La ruta de acceso completa al archivo para administrar las líneas en el nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="c6c0b-110">The full path to the file to manage lines in on the target node.</span></span>|
| <span data-ttu-id="c6c0b-111">ContainsLine</span><span class="sxs-lookup"><span data-stu-id="c6c0b-111">ContainsLine</span></span>| <span data-ttu-id="c6c0b-112">Una línea que debe asegurarse que exista en el archivo.</span><span class="sxs-lookup"><span data-stu-id="c6c0b-112">A line to ensure exists in the file.</span></span> <span data-ttu-id="c6c0b-113">Esta línea se anexará al archivo si no existe en él.</span><span class="sxs-lookup"><span data-stu-id="c6c0b-113">This line will be appended to the file if it does not exist in the file.</span></span> <span data-ttu-id="c6c0b-114">**ContainsLine** es una propiedad obligatoria, pero se puede establecer en una cadena vacía (\`ContainsLine = ‘’\`\`) si no se necesita.</span><span class="sxs-lookup"><span data-stu-id="c6c0b-114">**ContainsLine** is mandatory, but can be set to an empty string (\`ContainsLine = ‘’\`\`) if it is not needed.</span></span>|
| <span data-ttu-id="c6c0b-115">DoesNotContainPattern</span><span class="sxs-lookup"><span data-stu-id="c6c0b-115">DoesNotContainPattern</span></span>| <span data-ttu-id="c6c0b-116">Un patrón de expresiones regulares para las líneas que no deben existir en el archivo.</span><span class="sxs-lookup"><span data-stu-id="c6c0b-116">A regular expression pattern for lines that should not exist in the file.</span></span> <span data-ttu-id="c6c0b-117">Para todas las líneas que existan en el archivo y coincidan con esta expresión regular, se quitará la línea del archivo.</span><span class="sxs-lookup"><span data-stu-id="c6c0b-117">For any lines that exist in the file that match this regular expression, the line will be removed from the file.</span></span>|
| <span data-ttu-id="c6c0b-118">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c6c0b-118">DependsOn</span></span> | <span data-ttu-id="c6c0b-119">Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso.</span><span class="sxs-lookup"><span data-stu-id="c6c0b-119">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c6c0b-120">Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c6c0b-120">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="c6c0b-121">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="c6c0b-121">Example</span></span>

<span data-ttu-id="c6c0b-122">En este ejemplo se muestra cómo utilizar el recurso **nxFileLine** para configurar el archivo `/etc/sudoers`, asegurándose de que el usuario monuser esté configurado como not requiretty.</span><span class="sxs-lookup"><span data-stu-id="c6c0b-122">This example demonstrates using the **nxFileLine** resource to configure the `/etc/sudoers` file, ensuring that the user: monuser is configured to not requiretty.</span></span>

```
Import-DSCResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```