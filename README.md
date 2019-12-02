---
ms.openlocfilehash: 034d75a84e39cb0cf88a272ca58b5ccc229c5d9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74540456"
---
# <a name="microsoft-open-source-code-of-conduct"></a>Código de conducta del código abierto de Microsoft

Este proyecto se adoptado el [código de conducta del código abierto de Microsoft](https://opensource.microsoft.com/codeofconduct/). Para más información, consulte las [preguntas más frecuentes sobre el código de conducta](https://opensource.microsoft.com/codeofconduct/faq/) o póngase en contacto con [opencode@microsoft.com](mailto:opencode@microsoft.com) si tiene preguntas o comentarios adicionales.

[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a>Estado de la compilación

| Rama activa | Rama de almacenamiento provisional |
|:------------|:---------------|
| [![live-badge][]][live-badge] | [![staging-badge][]][staging-badge]

## <a name="powershell-documentation"></a>Documentación de PowerShell

Le damos la bienvenida al repositorio PowerShell-Docs, donde se encuentra la documentación oficial de PowerShell.

## <a name="repository-structure"></a>Estructura del repositorio

Cada una de las siguientes carpetas de nivel superior de este repositorio contiene un conjunto de documentos que se publica en [Microsoft Docs](https://docs.microsoft.com/powershell).

- [/reference/](https://docs.microsoft.com/powershell/scripting/) se usa para la referencia del módulo y los temas conceptuales de PowerShell en las versiones 5.1, 6.0 y 7.0. Este contenido también es el origen del contenido de ayuda recuperado por el cmdlet `Get-Help`.
  - [docs-conceptual/](https://docs.microsoft.com/powershell): esta carpeta contiene la documentación conceptual y los siguientes conjuntos de documentos:
    - [developer/](https://docs.microsoft.com/powershell/scripting/developer/) es la documentación del SDK de PowerShell (migrada desde MSDN)
    - [/dsc/](https://docs.microsoft.com/powershell/scripting/dsc/) es para la característica Desired State Configuration.
    - [gallery/](https://docs.microsoft.com/powershell/scripting/gallery) es para la [Galería de PowerShell](https://www.powershellgallery.com/)
    - [/jea/](https://docs.microsoft.com/powershell/scripting/jea/) es para la característica Just Enough Administration.
    - [wmf/](https://docs.microsoft.com/powershell/scripting/wmf/overview) contiene notas de la versión para Windows Management Framework, el paquete usado para distribuir nuevas versiones de PowerShell a versiones anteriores de Windows.

## <a name="contributing"></a>Contribución

Incorporamos las contribuciones hechas a este repositorio mediante [solicitudes de incorporación de cambios](https://help.github.com/articles/using-pull-requests/) en la rama *staging*.
Tenga en cuenta que antes de enviar una solicitud de incorporación de cambios debe [firmar un contrato de licencia de contribución](https://cla.microsoft.com/) para garantizar que la comunidad pueda utilizar libremente sus aportaciones.

Para más información sobre las colaboraciones, consulte nuestra [guía del colaborador](https://docs.microsoft.com/contribute/powershell/powershell-contribute). La guía del colaborador contiene información detallada sobre cómo contribuir con documentación, herramientas sugeridas y requisitos de estilo y formato. Use las plantillas de problemas y solicitud de extracción para ayudar a mantener la documentación coherente entre versiones.

## <a name="licenses"></a>Licencias

Hay dos archivos de licencia para este proyecto. La licencia de MIT se aplica al código incluido en este repositorio. La licencia de Creative Commons se aplica a la documentación.