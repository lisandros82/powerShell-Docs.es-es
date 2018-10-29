# <a name="microsoft-open-source-code-of-conduct"></a>Código de conducta del código abierto de Microsoft

Este proyecto se adoptado el [código de conducta del código abierto de Microsoft](https://opensource.microsoft.com/codeofconduct/).
Para más información, consulte las [preguntas más frecuentes sobre el código de conducta](https://opensource.microsoft.com/codeofconduct/faq/) o póngase en contacto con [opencode@microsoft.com](mailto:opencode@microsoft.com) si tiene preguntas o comentarios adicionales.

[![Estado de la compilación](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

## <a name="powershell-documentation"></a>Documentación de PowerShell

Le damos la bienvenida al repositorio PowerShell-Docs, donde se encuentra la documentación oficial de PowerShell.

## <a name="repository-structure"></a>Estructura del repositorio

Cada una de las siguientes carpetas de nivel superior de este repositorio contiene un conjunto de documentos que se publica en [Microsoft Docs](https://docs.microsoft.com/powershell).

- [/Developer/](https://docs.microsoft.com/powershell/developer/) es la futura página principal de la documentación del SDK de PowerShell
  - Estamos en proceso de migración de este contenido desde MSDN
- [/dsc/](https://docs.microsoft.com/powershell/dsc/) es para la característica Desired State Configuration
- [/gallery/](https://docs.microsoft.com/powershell/gallery) es para la [Galería de PowerShell](https://www.powershellgallery.com/)
- [/jea/](https://docs.microsoft.com/powershell/jea/) es para la característica Just Enough Administration
- [/reference/](https://docs.microsoft.com/powershell/scripting/) es para referencia de módulo y temas conceptuales de PowerShell en las versiones 3.0, 4.0, 5.0, 5.1 y 6.0
  - Este contenido también es el origen del contenido de ayuda recuperado por el cmdlet `Get-Help`.
- [/wmf](https://docs.microsoft.com/powershell/wmf/readme) contiene notas de la versión para Windows Management Framework, el paquete usado para distribuir nuevas versiones de PowerShell para versiones anteriores de Windows.

## <a name="contributing"></a>Contribución

Incorporamos las contribuciones hechas a este repositorio mediante [solicitudes de incorporación de cambios](https://help.github.com/articles/using-pull-requests/) en la rama *staging*.
Tenga en cuenta que antes de enviar una solicitud de incorporación de cambios debe [firmar un contrato de licencia de contribución](https://cla.microsoft.com/) para garantizar que la comunidad pueda utilizar libremente sus aportaciones.

Para más información sobre las colaboraciones, consulte nuestra [guía del colaborador](CONTRIBUTING.md).
La guía del colaborador contiene información detallada sobre cómo contribuir con documentación, herramientas sugeridas y requisitos de estilo y formato.
Use las plantillas de problemas y solicitud de extracción para ayudar a mantener la documentación coherente entre versiones.

## <a name="licenses"></a>Licencias

Hay dos archivos de licencia para este proyecto.
La licencia de MIT se aplica al código incluido en este repositorio.
La licencia de Creative Commons se aplica a la documentación.