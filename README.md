---
ms.openlocfilehash: 84b29953f09eb62eb30f52d84b087eb4f1f90eed
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470644"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="da2ce-101">Código de conducta del código abierto de Microsoft</span><span class="sxs-lookup"><span data-stu-id="da2ce-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="da2ce-102">Este proyecto se adoptado el [código de conducta del código abierto de Microsoft](https://opensource.microsoft.com/codeofconduct/).</span><span class="sxs-lookup"><span data-stu-id="da2ce-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="da2ce-103">Para más información, consulte las [preguntas más frecuentes sobre el código de conducta](https://opensource.microsoft.com/codeofconduct/faq/) o póngase en contacto con [opencode@microsoft.com](mailto:opencode@microsoft.com) si tiene preguntas o comentarios adicionales.</span><span class="sxs-lookup"><span data-stu-id="da2ce-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a><span data-ttu-id="da2ce-106">Estado de la compilación</span><span class="sxs-lookup"><span data-stu-id="da2ce-106">Build Status</span></span>

| <span data-ttu-id="da2ce-107">Rama activa</span><span class="sxs-lookup"><span data-stu-id="da2ce-107">Live Branch</span></span> | <span data-ttu-id="da2ce-108">Rama de almacenamiento provisional</span><span class="sxs-lookup"><span data-stu-id="da2ce-108">Staging Branch</span></span> |
|:------------|:---------------|
| <span data-ttu-id="da2ce-109">[![live-badge][]][live-badge]</span><span class="sxs-lookup"><span data-stu-id="da2ce-109">[![live-badge][]][live-badge]</span></span> | <span data-ttu-id="da2ce-110">[![staging-badge][]][staging-badge]</span><span class="sxs-lookup"><span data-stu-id="da2ce-110">[![staging-badge][]][staging-badge]</span></span>

## <a name="powershell-documentation"></a><span data-ttu-id="da2ce-111">Documentación de PowerShell</span><span class="sxs-lookup"><span data-stu-id="da2ce-111">PowerShell Documentation</span></span>

<span data-ttu-id="da2ce-112">Le damos la bienvenida al repositorio PowerShell-Docs, donde se encuentra la documentación oficial de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da2ce-112">Welcome to the PowerShell-Docs repository, housing the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="da2ce-113">Estructura del repositorio</span><span class="sxs-lookup"><span data-stu-id="da2ce-113">Repository Structure</span></span>

<span data-ttu-id="da2ce-114">Cada una de las siguientes carpetas de nivel superior de este repositorio contiene un conjunto de documentos que se publica en [Microsoft Docs](https://docs.microsoft.com/powershell).</span><span class="sxs-lookup"><span data-stu-id="da2ce-114">Each of the following top-level folders in this repo contain a DocSet that is published to [Microsoft Docs](https://docs.microsoft.com/powershell).</span></span>

- <span data-ttu-id="da2ce-115">[/Developer/](https://docs.microsoft.com/powershell/developer/) es la futura página principal de la documentación del SDK de PowerShell</span><span class="sxs-lookup"><span data-stu-id="da2ce-115">[/developer/](https://docs.microsoft.com/powershell/developer/) is the future home of the PowerShell SDK documentation</span></span>
  - <span data-ttu-id="da2ce-116">Estamos en proceso de migración de este contenido desde MSDN</span><span class="sxs-lookup"><span data-stu-id="da2ce-116">We are in the process of migrating this content from MSDN</span></span>
- <span data-ttu-id="da2ce-117">[/dsc/](https://docs.microsoft.com/powershell/dsc/) es para la característica Desired State Configuration</span><span class="sxs-lookup"><span data-stu-id="da2ce-117">[/dsc/](https://docs.microsoft.com/powershell/dsc/) is for the Desired State Configuration feature</span></span>
- <span data-ttu-id="da2ce-118">[/gallery/](https://docs.microsoft.com/powershell/gallery) es para la [Galería de PowerShell](https://www.powershellgallery.com/)</span><span class="sxs-lookup"><span data-stu-id="da2ce-118">[/gallery/](https://docs.microsoft.com/powershell/gallery) is for the [PowerShell Gallery](https://www.powershellgallery.com/)</span></span>
- <span data-ttu-id="da2ce-119">[/jea/](https://docs.microsoft.com/powershell/jea/) es para la característica Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="da2ce-119">[/jea/](https://docs.microsoft.com/powershell/jea/) is for the Just Enough Administration feature</span></span>
- <span data-ttu-id="da2ce-120">[/reference/](https://docs.microsoft.com/powershell/scripting/) es para referencia de módulo y temas conceptuales de PowerShell en las versiones 3.0, 4.0, 5.0, 5.1 y 6.0</span><span class="sxs-lookup"><span data-stu-id="da2ce-120">[/reference/](https://docs.microsoft.com/powershell/scripting/) is for PowerShell conceptual topics and module reference across versions 3.0, 4.0, 5.0, 5.1, and 6.0</span></span>
  - <span data-ttu-id="da2ce-121">Este contenido también es el origen del contenido de ayuda recuperado por el cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="da2ce-121">This content is also the source of help content retrieved by the `Get-Help` cmdlet</span></span>
- <span data-ttu-id="da2ce-122">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contiene notas de la versión para Windows Management Framework, el paquete usado para distribuir nuevas versiones de PowerShell para versiones anteriores de Windows.</span><span class="sxs-lookup"><span data-stu-id="da2ce-122">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contains release notes for the Windows Management Framework, the package used to distribute new versions of PowerShell to previous versions of Windows.</span></span>

## <a name="contributing"></a><span data-ttu-id="da2ce-123">Contribución</span><span class="sxs-lookup"><span data-stu-id="da2ce-123">Contributing</span></span>

<span data-ttu-id="da2ce-124">Incorporamos las contribuciones hechas a este repositorio mediante [solicitudes de incorporación de cambios](https://help.github.com/articles/using-pull-requests/) en la rama *staging*.</span><span class="sxs-lookup"><span data-stu-id="da2ce-124">We actively merge contributions into this repository via [pull request](https://help.github.com/articles/using-pull-requests/) into the *staging* branch.</span></span>
<span data-ttu-id="da2ce-125">Tenga en cuenta que antes de enviar una solicitud de incorporación de cambios debe [firmar un contrato de licencia de contribución](https://cla.microsoft.com/) para garantizar que la comunidad pueda utilizar libremente sus aportaciones.</span><span class="sxs-lookup"><span data-stu-id="da2ce-125">Please note that before you submit a pull request you must [sign a Contribution License Agreement](https://cla.microsoft.com/) to ensure that the community is free to use your submissions.</span></span>

<span data-ttu-id="da2ce-126">Para más información sobre las colaboraciones, consulte nuestra [guía del colaborador](CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="da2ce-126">For more information on contributing, read our [contributor's guide](CONTRIBUTING.md).</span></span>
<span data-ttu-id="da2ce-127">La guía del colaborador contiene información detallada sobre cómo contribuir con documentación, herramientas sugeridas y requisitos de estilo y formato.</span><span class="sxs-lookup"><span data-stu-id="da2ce-127">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span>
<span data-ttu-id="da2ce-128">Use las plantillas de problemas y solicitud de extracción para ayudar a mantener la documentación coherente entre versiones.</span><span class="sxs-lookup"><span data-stu-id="da2ce-128">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="da2ce-129">Licencias</span><span class="sxs-lookup"><span data-stu-id="da2ce-129">Licenses</span></span>

<span data-ttu-id="da2ce-130">Hay dos archivos de licencia para este proyecto.</span><span class="sxs-lookup"><span data-stu-id="da2ce-130">There are two license files for this project.</span></span>
<span data-ttu-id="da2ce-131">La licencia de MIT se aplica al código incluido en este repositorio.</span><span class="sxs-lookup"><span data-stu-id="da2ce-131">The MIT License applies to the code contained in this repo.</span></span>
<span data-ttu-id="da2ce-132">La licencia de Creative Commons se aplica a la documentación.</span><span class="sxs-lookup"><span data-stu-id="da2ce-132">The Creative Commons license applies to the documentation.</span></span>