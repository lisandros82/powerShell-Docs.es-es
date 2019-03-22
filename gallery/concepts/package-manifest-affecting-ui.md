---
ms.date: 06/09/2017
schema: 2.0.0
keywords: powershell
title: Valores de los archivos de manifiesto de los paquetes que afectan a la interfaz de usuario de la Galería de PowerShell
ms.openlocfilehash: cedf81df8de29c54ef559a800d654305029491ec
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2019
ms.locfileid: "58058222"
---
# <a name="package-manifest-values-that-impact-the-powershell-gallery-ui"></a>Valores de los archivos de manifiesto de los paquetes que afectan a la interfaz de usuario de la Galería de PowerShell

Este tema proporciona a los editores información resumida sobre cómo modificar el manifiesto para sus publicaciones de Galería de PowerShell de modo que las características de los cmdlets de PowerShellGet y la interfaz de usuario de Galería de PowerShell se vean afectadas. Este contenido está organizado por donde aparecerá el cambio, primero por la sección central y después por el área de navegación a la izquierda. Hay una sección detallada que cubre las etiquetas, que identifica las etiquetas importantes, así como algunas de las etiquetas más utilizadas. Hay dos temas que proporcionan ejemplos de manifiestos:

- Para los módulos, consulte el artículo para [actualizar un archivo de manifiesto de módulo](/powershell/module/powershellget/Update-ModuleManifest).
- Para los scripts, consulte el artículo para [crear un archivo de script con metadatos](/powershell/module/powershellget/New-ScriptFileInfo).

## <a name="powershell-gallery-feature-elements-controlled-by-the-manifest"></a>Elementos de la característica Galería de PowerShell controlados por el manifiesto

En la tabla siguiente se muestran los paquetes de la interfaz de usuario de la Galería de PowerShell que controla el editor. Cada elemento indica si se puede controlar por el manifiesto del módulo o del script.

| Elemento de UI | Descripción | Módulo | Script |
| --- | --- | --- | --- |
| **Título** | Este es el nombre del paquete que se publica en la galería  | No | No |
| **Versión** | La versión que se muestra es la cadena de versión de los metadatos y una versión preliminar si está especificada. La parte principal de la versión en un manifiesto de módulo es ModuleVersion. Para un script, se identifica como .VERSION. Si se especifica una cadena de versión preliminar, se anexará a ModuleVersion para los módulos, o se especificará como parte de .VERSION para los scripts. Hay documentación para especificar las cadenas de versión preliminar en los [módulos](module-prerelease-support.md) y en los [scripts](script-prerelease-support.md). | Sí | Sí |
| **Descripción** | Esta es la descripción del manifiesto de módulo y en un manifiesto del archivo de script es .DESCRIPTION. | Sí | Sí |
| **Requerir aceptación de licencia** | Un módulo puede requerir que el usuario acepte una licencia modificando el manifiesto del módulo con RequireLicenseAcceptance = $true, suministrando un LicenseURI y proporcionando un archivo license.txt en la raíz de la carpeta del módulo. Está disponible información adicional en el tema [Requerir la aceptación de la licencia](../how-to/working-with-packages/packages-that-require-license-acceptance.md). | Sí | No |
| **Notas de la versión** | En los módulos, esta información se extrae de la sección ReleaseNotes, en PSData\PrivateData. En los manifiestos de scripts, es el elemento .RELEASENOTES. | Sí | Sí |
| **Propietarios** | Los propietarios son la lista de usuarios en Galería de PowerShell que pueden actualizar un paquete. La lista de propietarios no se incluye en el manifiesto del paquete. Hay documentación adicional que describe cómo [administrar propietarios de elementos](../how-to/publishing-packages/managing-package-owners.md). | No | No |
| **Autor** | Se incluye en el manifiesto del módulo como Author y en un manifiesto del script como .AUTHOR. El campo Autor a menudo se usa para especificar una empresa u organización asociada a un paquete. | Sí | Sí |
| **Copyright** | Este es el campo Copyright del manifiesto del módulo y .COPYRIGHT en un manifiesto del script. | Sí | Sí |
| **Lista de archivos** | La lista de archivos se extrae desde el paquete cuando se publica en Galería de PowerShell. No se puede controlar mediante la información del manifiesto. Nota: Hay un archivo .nuspec adicional enumerado con cada paquete de la Galería de PowerShell que no está presente después de instalar el paquete en un sistema. Es el manifiesto del paquete Nuget para el paquete y puede omitirse. | No | No |
| **Etiquetas** | En los módulos, las etiquetas se incluyen en PSData\PrivateData. En los scripts, la sección está etiquetada como .TAGS. Tenga en cuenta que las etiquetas no pueden contener espacios, aunque estén entre comillas. Las etiquetas tienen requisitos y significados adicionales, que se describen más adelante en este tema en la sección Detalles de las etiquetas. | Sí | Sí |
| **Cmdlets** | Se proporcionan en el manifiesto del módulo con CmdletsToExport. Tenga en cuenta que el procedimiento recomendado consiste en enumerar explícitamente los elementos, en lugar de utilizar el carácter comodín "*", ya que se mejorará el rendimiento del módulo de carga para los usuarios. | Sí | No |
| **Funciones** | Se proporcionan en el manifiesto del módulo con FunctionsToExport. Tenga en cuenta que el procedimiento recomendado consiste en enumerar explícitamente los elementos, en lugar de utilizar el carácter comodín "*", ya que se mejorará el rendimiento del módulo de carga para los usuarios. | Sí | No |
| **Recursos de DSC** | En los módulos que se usarán en PowerShell versión 5.0 y versiones posteriores, se proporciona en el manifiesto mediante DscResourcesToExport. Si el módulo se va a usar en PowerShell 4, no debe usarse DSCResourcesToExport ya que no es una clave de manifiestos compatible. (DSC no estaba disponible antes de PowerShell 4). | Sí | No |
| **Flujos de trabajo** | Los flujos de trabajo se publican en Galería de PowerShell como scripts y se identifican como flujos de trabajo en el código (consulte [Connect-AzureVM](https://www.powershellgallery.com/packages/Connect-AzureVM/1.0/Content/Connect-AzureVM.ps1) para obtener un ejemplo). Esto no lo controla el manifiesto. | No | No |
| **Funcionalidades de rol** | Esto se mostrará cuando el módulo publicado en Galería de PowerShell contiene uno o más archivos de función de funcionalidad de rol (.psrc) que utilice JEA. Consulte la documentación de JEA para más información sobre [las funcionalidades de rol](/powershell/jea/role-capabilities). | Sí | No |
| **Ediciones de PowerShell** | Esto se especifica en el manifiesto del script o del módulo. Para los módulos diseñados para usarse con PowerShell 5.0 y versiones anteriores, esto se controlaba mediante etiquetas. Para equipos de escritorio, utilice la etiqueta PSEdition_Desktop y para núcleos, utilice la etiqueta PSEdition_Core. En el caso de los módulos que se van a usar solo en PowerShell 5.1 y versiones posteriores, hay una clave CompatiblePSEditions en el manifiesto principal. Para más detalles, consulte la característica de PS Edition en [la documentación de PowerShell Get](module-psedition-support.md). | Sí | Sí |
| **Dependencias** | Las dependencias son los módulos de Galería de PowerShell que se declaran bien en el módulo como RequiredModules o en el manifiesto del script como #Requires -Module (nombre). | Sí | Sí |
| **Versión mínima de PowerShell** | Se puede especificar en un manifiesto de módulo como PowerShellVersion | Sí | No |
| **Historial de versiones** | El historial de versiones refleja las actualizaciones realizadas en un módulo en Galería de PowerShell. Si una versión de un paquete está oculta por la característica de eliminación, no se mostrará en el historial de versiones, excepto a los propietarios del paquete. | No | No |
| **Sitio del proyecto** | El sitio del proyecto se proporciona para los módulos en la sección Privatedata\PSData del manifiesto del módulo al especificar un valor de ProjectURI. En el manifiesto del script, se controla al especificar .PROJECTURI. | Sí | Sí |
| **Licencia** | Se proporciona un vínculo de licencia para los módulos en la sección Privatedata\PSData del manifiesto del módulo al especificar un valor de LicenseURI. En el manifiesto del script, se controla al especificar .LICENSEURI. Es importante tener en cuenta que si no se proporciona una licencia mediante LicenseURI o dentro de un módulo, los términos de uso de la Galería de PowerShell especifican los términos de uso del paquete. Consulte los términos de uso para obtener más información. | Sí | Sí |
| **Icono** | Puede especificarse un icono para cualquier paquete de la Galería de PowerShell proporcionando la marca IconURI en el manifiesto del script o en la sección PSData de Privatedata del manifiesto del módulo. La IconURI debe apuntar a una imagen de 32 x 32 con fondo transparente. El URI **debe** ser una dirección URL de imagen directa y **no debe** ir a una página web que contenga la imagen o un archivo en el paquete de Galería de PowerShell. | Sí | Sí |


## <a name="editing-package-details"></a>Edición de los detalles del paquete

La página Editar paquete de la Galería de PowerShell permite a los editores cambiar algunos de los campos que se muestran para un paquete, en concreto:

- Title
- Descripción
- Resumen
- URL del icono
- URL de la página principal de proyecto
- Autores
- Copyright
- Etiquetas
- Notas de la versión
- Se requiere licencia

No se suele recomendar este enfoque, excepto cuando es necesario corregir lo que se muestra para una versión anterior de un módulo. Los usuarios que adquieren el módulo verán que los metadatos no coinciden con lo que se muestra en la Galería de PowerShell, lo que plantea preocupaciones sobre el paquete. Esto provocará con frecuencia consultas dirigidas a los propietarios de los paquetes para confirmar el cambio. Se recomienda encarecidamente que cada vez que se utilice este enfoque, se publique una nueva versión del paquete con los mismos cambios.

## <a name="tag-details"></a>Detalles de las etiquetas

Las etiquetas son cadenas simples que se utilizan los consumidores para buscar paquetes. Las etiquetas son más útiles cuando se utilizan de forma coherente en muchos paquetes relacionados con el mismo tema. El uso de varias versiones de la misma palabra (por ejemplo, base de datos y bases de datos, o prueba y pruebas) suele ofrecer muchas ventajas. Las etiquetas son cadenas de palabras únicas que no distinguen entre mayúsculas y minúsculas y que no pueden incluir espacios en blanco. Si hay una frase que cree que los usuarios van a buscar, agréguela a la descripción del paquete y se encontrará en los resultados de la búsqueda. Utilice mayúsculas y minúsculas como en Pascal, guiones, subrayados o puntos si desea mejorar la legibilidad.
Tenga cuidado al crear etiquetas largas, complejas y poco habituales, ya que frecuentemente se suelen escribir mal.

Hay determinadas etiquetas que hay que tener en cuenta, ya que Galería de PowerShell y los cmdlets de PowerShellGet las tratan de forma única. PSEdition_Desktop y PSEdition_Core son ejemplos específicos y se han descrito más arriba.

Tal y como se mencionó antes, las etiquetas proporcionan el máximo valor cuando son específicas y muchos paquetes las usan de forma coherente. Como el editor siempre busca las mejores etiquetas para utilizar, el enfoque más sencillo es buscar en Galería de PowerShell las etiquetas que está considerando. Idealmente, habrá muchos paquetes devueltos, y las descripciones de los mismos se alinearán con el uso que se haga de esa palabra clave.

Como referencia, estas son algunas etiquetas más utilizadas desde el 14/12/2017. En algunos casos, hay opciones similares pero quizá menos adecuadas que se muestran al lado de la etiqueta. Es un procedimiento recomendado usar la etiqueta preferida, ya que producirá menos ruido y mejorará los resultados de búsqueda para los consumidores.

| Etiqueta preferida | Alternativas y notas |
| --- | --- |
| Azure |  |
| DSC | DesiredStateConfiguration es menos deseable, es demasiado largo |
| ResourceManager | ARM se utiliza para describir el grupo de procesadores y no debe usarse para Azure Resource Manager |
| DSCResourceKit |  |
| SQL |  |
| AWS |  |
| DSCResource |  |
| Automatización |  |
| REST |  |
| ActiveDirectory | AD no se utiliza por sí solo  |
| SQLServer |  |
| DBA |  |
| Seguridad | Defense es menos preciso |
| Base de datos | Databases (en plural) es menos deseable |
| DevOps |  |
| Windows |  |
| Build |  |
| Implementación | Deploy se utiliza con menos frecuencia |
| Nube |  |
| GIT |  |
| Test | Testing es menos deseable |
| VersionControl | Version es menos preciso, aunque se utiliza con más frecuencia  |
| Registro | Uso preferido de logging como acción |
| Registro | Uso preferido de log como hecho |
| Copias de seguridad |  |
| IaaS |  |
| Linux |  |
| IIS |  |
| AzureAutomation |  |
| Almacenamiento |  |
| Github |  |
| Json |  |
| Exchange |  |
| Red | Networking es similar, menos frecuente |
| SharePoint |  |
| Informes | Reporting es una acción, report es un objeto |
| Informe | Report es un objeto |
| WinRM |  |
| Supervisión |  |
| VSTS |  |
| Excel |  |
| Google |  |
| Color |  |
| DNS |  |
| Office365 | Es preferible escribir Office completo. O365 es menos frecuente, aunque es más corto |
| Gitlab |  |
| Pester |  |
| AzureAD |  |
| HTML |  |
| Hyper-V | HyperV es menos común como etiqueta |
| Configuración |  |
| ChatOps |  |
| PackageManagement |  |
| WMI |  |
| Firewall |  |
| Docker |  |
| Appveyor |  |
| AzureRm | Se utiliza principalmente para los módulos de AzureRM |
| Zip |  |
| MSI |  |
| MacOS |  |
| PoshBot |  |
