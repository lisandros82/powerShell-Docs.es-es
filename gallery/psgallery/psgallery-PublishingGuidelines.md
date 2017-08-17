---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
description: Instrucciones para publicadores
title: "Instrucciones y procedimientos recomendados para publicar en la Galería de PowerShell"
ms.openlocfilehash: 394e69e189761f3c5a4bb54dfa8df15c4ab240d6
ms.sourcegitcommit: e63f09c005b6bbf39c3c001944f307c2b155765b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/11/2017
---
# <a name="powershellgallery-publishing-guidelines-and-best-practices"></a>Instrucciones y procedimientos recomendados para publicar en PowerShellGallery

En este tema se describen los pasos recomendados que los equipos de Microsoft usan para garantizar que los elementos que se publiquen en la Galería de PowerShell se adopten ampliamente y proporcionen gran valor a los usuarios, en virtud de cómo la Galería de PowerShell administra los datos de manifiesto y según los comentarios de gran cantidad de usuarios de la Galería de PowerShell.
Los elementos que se publican según estas instrucciones tendrán más probabilidades de atraer a más usuarios que los instalen y confíen en ellos.

A continuación, se incluyen instrucciones sobre cómo debe ser un elemento de la Galería de PowerShell, cuál es la configuración de manifiesto opcional más importante, cómo mejorar el código con los comentarios de los revisores iniciales y [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer), cómo crear la versión del módulo, la documentación, pruebas y ejemplos de cómo usar el contenido que compartió.
Gran parte de esta documentación sigue las instrucciones para la publicación de los [módulos de recursos DSC de alta calidad](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md).

Si desea conocer los mecanismos para publicar un elemento en la Galería de PowerShell, consulte [Crear y publicar un elemento](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/creating-and-publishing-an-item).

Se aceptan y valoran comentarios sobre estas instrucciones. Si tiene algún comentario, abra los temas que aparecen en el [repositorio de documentación de GitHub](https://github.com/powershell/powershell-docs/).

## <a name="best-practices-for-publishing-items"></a>Procedimientos recomendados para los elementos publicados

Los procedimientos recomendados siguientes son importantes para los usuarios de los elementos de la Galería de PowerShell y están ordenados según prioridad nominal.
Es mucho más probable que otros usuarios descarguen y adopten los elementos que siguen estas instrucciones.

* Usar PSScriptAnalyzer
* Incluir documentación y ejemplos
* Responder a los comentarios
* Proporcionar módulos, no scripts
* Seguir las instrucciones de [SemVer] para el control de versiones
* Proporcionar vínculos a un sitio de proyecto
* Incluir pruebas en los módulos
* Incluir los términos de licencia o un vínculo a ellos
* Firmar el código
* Seguir las instrucciones de SemVer para el control de versiones
* Usar etiquetas comunes, tal como se documenta en Etiquetas comunes de la Galería de PowerShell
* Publicación de prueba mediante un repositorio local

Cada uno de estos puntos se analiza brevemente en las secciones siguientes.

## <a name="use-psscriptanalyzer"></a>Usar PSScriptAnalyzer

[PSScriptAnalyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer) es una herramienta de análisis de código estático gratis que funciona en el código de PowerShell.
PSScriptAnalyzer identificará los problemas más comunes que se encuentran en el código de PowerShell y, por lo general, una recomendación para corregirlos.
Se trata de una herramienta fácil de usar, que clasifica los problemas como Errores (graves, que se deben solucionar), Advertencia (se debe revisar y solucionar) e Información (vale la pena revisarlo para cumplir con los procedimientos recomendados).
Todos los elementos que se publiquen en la Galería de PowerShell se examinarán con PSScriptAnalyzer y todos los errores se informarán al propietario, el que deberá solucionarlos.

El procedimiento recomendado es ejecutar `Invoke-ScriptAnalyzer` con Advertencia `-Recurse` y `-Severity`.

Revise los resultados y asegúrese de lo siguiente:

* Se corrigen todos los errores o se solucionan en la documentación
* Se revisan todas las advertencias y se solucionan donde corresponda

Se recomienda que los usuarios que adquieren elementos en la Galería de PowerShell ejecuten PSScriptAnalyzer y evalúen todos los errores y las advertencias.
Es muy probable que los usuarios se pongan en contacto con los propietarios de los distintos contenidos si ven que PSScriptAnalyzer informa algún error.
Si hay una razón de peso para que el elemento conserve el código que se marca como error, agregue dicha información a la documentación para que no tenga que responder la misma pregunta muchas veces.

## <a name="include-documentation-and-examples"></a>Incluir documentación y ejemplos

La documentación y los ejemplos son la mejor manera de asegurarse de que los usuarios puedan aprovechar todo código compartido.

La documentación es el aspecto más útil que se debe incluir en los elementos que se publican en la Galería de PowerShell.
Por lo general, los usuarios omitirán los elementos que no incluyan documentación, dado que la alternativa es leer el código para entender de qué se trata el elemento y cómo usarlo.
En MSDN hay varios artículos disponibles sobre cómo proporcionar documentación con los elementos de PowerShell, entre los que se incluyen los siguientes:

* Instrucciones sobre cómo prestar ayuda, en el artículo sobre [cómo escribir ayuda para cmdlet](https://msdn.microsoft.com/en-us/library/aa965353(VS.85).aspx)
* Cómo crear ayuda para cmdlet, que es el mejor enfoque para cualquier script, función o cmdlet de PowerShell.
  Para información sobre cómo crear ayuda para cmdlet, comience con [este artículo](http://go.microsoft.com/fwlink/?LinkID=123415) de la biblioteca de MSDN (Microsoft Developer Network).
  Para agregar ayuda dentro de un script, consulte el artículo sobre [la ayuda basada en comentarios](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_comment_based_help).
* Muchos módulos también incluyen documentación en formato de texto, como archivos Markdown.
  Esto puede resultar especialmente útil cuando hay un sitio de proyecto en GitHub, donde el formato Markdown se usa mucho.
  El procedimiento recomendado es usar [Markdown característico de GitHub](https://help.github.com/categories/writing-on-github/)

Los ejemplos muestran a los usuarios cómo está pensado usarse el elemento.
Muchos desarrolladores dirían que primero ven los ejemplos antes que la documentación para saber cómo usar el contenido.
El mejor tipo de ejemplo muestra el uso básico, además de un caso de uso realista simulado, y un código bien comentado.
Los ejemplos de los módulos publicados en la Galería de PowerShell deben estar en una carpeta Examples en la raíz del módulo.

Encontrará un buen patrón de ejemplos en el [módulo PSDscResource](https://www.powershellgallery.com/packages/PSDscResources), en la carpeta Examples\RegistryResource.
Hay cuatro casos de uso de ejemplo con una breve descripción en la parte superior de cada archivo que documenta lo que se demuestra.

## <a name="respond-to-feedback"></a>Responder a los comentarios

La comunidad valora enormemente a los propietarios de elementos que responden de forma adecuada a los comentarios.
Es importante responder a los usuarios que brindan comentarios constructivos, dado que esto significa que el elemento les interesa lo suficiente como para tratar de ayudar a mejorarlo.

Existen dos métodos de comentarios disponibles en la Galería de PowerShell:

* Ponerse en contacto con el propietario: esta opción permite que un usuario envíe un correo electrónico al propietario de un elemento. Como propietario de un elemento, es importante supervisar la dirección de correo electrónico que se usa con los elementos de la Galería de PowerShell y responder a los problemas que surgen. La desventaja de este método es que solo el usuario y el propietario verán la comunicación, por lo que el propietario podría tener que responder la misma pregunta varias veces.
* Comentarios: en la parte inferior de la página de un elemento aparece el campo Comentario.
  La ventaja de este sistema es que los demás usuarios podrán ver los comentarios y las respuestas, lo que disminuye la cantidad de veces que se debe responder una misma pregunta.
  Como propietario de un elemento, se recomienda que siga los comentarios que se han hecho para cada elemento.
Consulte [Envío de comentarios a través de medios sociales o comentarios](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-SocialMediaFeedback) para conocer detalles sobre cómo hacerlo.

La comunidad valora a los propietarios que responden de forma constructiva a los comentarios.
Use la oportunidad que ofrece el informe para solicitar más información si la necesita, proporcione una solución alternativa o identifique si una actualización corrige un problema.

Si en cualquiera de estos canales de comunicación se observa un comportamiento inadecuado, use la característica Notificar abuso de la Galería de PowerShell para ponerse en contacto con los administradores de la galería.

## <a name="modules-versus-scripts"></a>Comparación entre módulos y scripts

El uso compartido de un script con otros usuarios es genial y proporciona a los demás usuarios ejemplos de cómo solucionar problemas que puedan tener.
El problema es que los scripts de la Galería de PowerShell son archivos únicos sin documentación, ejemplos y pruebas por separado.

Los módulos de PowerShell tienen una estructura de carpetas que permite incluir varias carpetas y archivos en el paquete.
La estructura del módulo permite incluir los otros elementos que indicamos como procedimientos recomendados: ayuda de cmdlet, documentación, ejemplos y pruebas.
La principal desventaja es que un script dentro de un módulo se debe exponer y usar como función.
Para información sobre cómo crear un módulo, consulte [Escribir un módulo de Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=144916).

Hay situaciones en las que un script brinda una mejor experiencia para el usuario, especialmente con configuraciones de DSC.
El procedimiento recomendado para las configuraciones de DSC es publicar la configuración como script acompañado de un módulo que contiene los documentos, los ejemplos y las pruebas.
El script muestra el módulo que lo acompaña usando RequiredModules = @(nombre del módulo).
Este enfoque se puede usar con cualquier script.

Los scripts independientes que siguen los otros procedimientos recomendados proporcionan valor real a los demás usuarios.
Es muy recomendable proporcionar documentación basada en los comentarios y un vínculo a un sitio de proyecto cuando se publica un script en la Galería de PowerShell.

## <a name="provide-a-link-to-a-project-site"></a>Proporcionar un vínculo a un sitio de proyecto

Un sitio de proyecto es donde un publicador puede interactuar directamente con los usuarios de sus elementos de la Galería de PowerShell.
Los usuarios prefieren los elementos que brindan esta opción, porque les permite obtener más fácilmente información sobre el elemento.
Muchos de los elementos que se encuentran en la Galería de PowerShell se desarrollan en GitHub, mientras que otros los proporcionan organizaciones con una presencia web dedicada.
Cada una de estas se pueden considerar como un sitio de proyecto.

Para agregar un vínculo, se incluye un elemento ProjectURI en la sección PSData del manifiesto, de la siguiente manera:

        # A URL to the main website for this project.
        ProjectUri = 'https://github.com/powershell/powershell'

Si se proporciona ProjectURI, la Galería de PowerShell incluirá un vínculo al sitio de proyecto en el lado izquierdo de la página del elemento.

## <a name="include-tests"></a>Incluir pruebas

Incluir pruebas con código abierto es importante para los usuarios, porque les brinda garantías sobre lo que se valida y proporciona información sobre cómo funciona el código. También permite que los usuarios se aseguren de no romper la funcionalidad original si modifican el código para adaptarlo a su entorno.

Es muy recomendable que las pruebas se escriban para aprovechar el marco de prueba Pester, diseñado específicamente para PowerShell.
Pester está disponible en [GitHub](https://github.com/Pester/Pester), la [Galería de PowerShell](https://www.powershellgallery.com/packages/Pester/) y se incluye en Windows 10, Windows Server 2016, WMF 5.0 y WMF 5.1.

El [sitio del proyecto Pester en GitHub](https://github.com/Pester/Pester) incluye una excelente documentación sobre cómo escribir pruebas de Pester, desde la introducción hasta los procedimientos recomendados.

Los objetivos de la cobertura de las pruebas se mencionan en la [documentación del módulo de recursos de alta calidad](https://github.com/PowerShell/DscResources/blob/master/HighQualityModuleGuidelines.md), con una cobertura de código de pruebas unitarias recomendada de 70%.

## <a name="include-andor-link-to-license-terms"></a>Incluir los términos de licencia o un vínculo a ellos

Todos los elementos que se publican en la Galería de PowerShell deben especificar los términos de licencia o estar vinculados a la licencia que se incluye en los [Términos de uso](https://www.powershellgallery.com/policies/Terms) en "Anexo A".
El mejor enfoque para especificar una licencia distinta es proporcionar un vínculo a la licencia con el elemento LicenseURI en PSData.
Puede encontrar un ejemplo en el tema Campos recomendados del manifiesto.

```powershell
PrivateData = @{
    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        Tags = @('.net','acl','active-directory')

        # A URL to the license for this module.
        LicenseUri = 'http://www.apache.org/licenses/LICENSE-2.0'
```

## <a name="sign-your-code"></a>Firmar el código

La firma de código permite que los usuarios tengan el mayor nivel de seguridad con respecto a quién publicó el elemento y que la copia del código que adquieren es exactamente lo que publicó el publicador.
Para más información sobre la firma de código en términos generales, consulte [Introducción a la firma de código](http://go.microsoft.com/fwlink/?LinkId=106296).
PowerShell admite la validación de la firma de código mediante dos enfoques principales:

* Firma de archivos de script
* Firma de catálogo de un módulo

Firmar archivos de PowerShell es un enfoque establecido para garantizar que el código que se ejecuta proviene de un origen de confianza y que no se ha modificado.
El tema [Información sobre la firma](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_signing) muestra detalles sobre cómo firmar los archivos de script de PowerShell.
Como información general, se puede agregar una firma a cualquier archivo .PS1 que PowerShell valida cuando se carga el script.
Es posible restringir a PowerShell si se usan los cmdlets de [directiva de ejecución](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_execution_policies) para garantizar que se usen scripts firmados.

La firma de catálogo de módulos es una característica que se agregó a PowerShell en la versión 5.1.
En el tema [Cmdlets del catálogo](https://msdn.microsoft.com/en-us/powershell/wmf/5.1/catalog-cmdlets) puede encontrar información sobre cómo firmar un módulo.
Como información general, la firma de catálogo se hace mediante la creación de un archivo de catálogo, el que contiene un valor hash para cada archivo del módulo y, luego, se firma ese archivo.
Los cmdlets publish-module, install-module, save-module y update-module de PowerShellGet comprobarán si la firma es válida y, luego, confirmarán si el valor hash de cada elemento coincide con lo que aparece en el catálogo.
Si hay instalada una versión anterior del módulo en el sistema, install-module confirmará si la autoridad de firma de la versión nueva coincide con la instalada anteriormente.
La firma de catálogo funciona en conjunto con la firma de archivos de script, pero no la reemplaza. PowerShell no valida las firmas de catálogo en el momento de cargar módulos.

## <a name="follow-semver-guidelines-for-versioning"></a>Seguir las instrucciones de SemVer para el control de versiones

[SemVer](http://semver.org/) es una convención pública que describe cómo estructurar y cambiar una versión para permitir una interpretación sencilla de los cambios.
La versión del elemento se debe incluir en los datos de manifiesto.

* La versión debe tener una estructura de tres bloques numéricos separados por puntos, como en 0.1.1 o 4.11.192
* Las versiones que comienzan con "0" indican que el elemento todavía no está listo para el entorno de producción y el primer número solo debe empezar por "0" si es el único número que se usa
* Los cambios en el primer número (1.9.9999 a 2.0.0) indican cambios importantes y disruptivos entre las distintas versiones
* Los cambios en el segundo número (1.01 a 1.02) indican cambios en el nivel de característica, como agregar cmdlets nuevos a un módulo
* Los cambios en el tercer número indican cambios no disruptivos, como nuevos parámetros, ejemplos actualizados o pruebas nuevas
* Cuando se enumeren las versiones, PowerShell las ordenará como cadenas, por lo que 1.01.0 se considerará mayor que 1.001.0

PowerShell se creó antes de que se publicara SemVer, por lo que admite la mayoría pero no la totalidad de los elementos de SemVer, específicamente:

* No admite cadenas de versión preliminar en los números de versión. Esto resulta útil si un publicador desea brindar una versión preliminar de una nueva versión principal después de brindar una versión 1.0.0. Esto se admitirá en una futura versión de los cmdlets de PowerShellGet y la Galería de PowerShell.
* PowerShell y la Galería de PowerShell permiten cadenas de versión con 1, 2 y 4 segmentos. Al comienzo, muchos de los módulos no seguían las instrucciones y las versiones de producto de Microsoft incluyen información de compilación como un cuarto bloque de números (por ejemplo, 5.1.14393.1066). Estas diferencias se omiten desde la perspectiva del control de versiones.

## <a name="test-using-a-local-repository"></a>Prueba mediante un repositorio local

La Galería de PowerShell no está diseñada para utilizarse como destino en las pruebas del proceso de publicación.
La mejor manera de probar el proceso completo de publicación en la Galería de PowerShell es configurar y usar un repositorio local propio.
Esto puede hacerse de las siguientes maneras:

* Configurar una instancia local de la Galería de PowerShell, usando para ello el [proyecto Galería privada de PS](https://github.com/PowerShell/PSPrivateGallery) en GitHub. Este proyecto de vista previa permite configurar una instancia de la Galería de PowerShell que se puede controlar y usar en las pruebas.
* Configurar un [repositorio interno de NuGet](https://blogs.msdn.microsoft.com/powershell/2014/05/20/setting-up-an-internal-powershellget-repository/). Esto requerirá un mayor trabajo de configuración, pero tiene la ventaja de que se validan algunos requisitos más, en particular el uso de una clave de API, y si las dependencias están presentes o no en el destino al publicar.
* Configurar un recurso compartido de archivos como “repositorio” de pruebas. Su configuración es muy sencilla, pero puesto que se trata de un recurso compartido de archivos, las validaciones que se han mencionado anteriormente no se llevarán a cabo. En este caso, una de las posibles ventajas es que el recurso compartido de archivos no comprueba la clave de API (obligatoria), por lo que se puede usar la misma clave que se utilizaría para publicar en la Galería de PowerShell.

Con cualquiera de estas soluciones, hay que usar Register-PSRepository para definir un nuevo “repositorio”. Este repositorio se utilizará en la propiedad -Repository para Publish-Module.

Un aspecto adicional sobre la publicación de prueba: para eliminar cualquier elemento publicado en la Galería de PowerShell, es necesario contar con la ayuda del equipo de operaciones, que confirmará la ausencia de dependencias en el elemento que se quiere publicar.
Por esa razón, no somos partidarios de usar la Galería de PowerShell como destino de prueba, y nos pondremos en contacto con los publicadores que así lo hagan.

## <a name="recommended-workflow"></a>Flujo de trabajo recomendado

El enfoque que se considera más adecuado para los elementos que se publican en la Galería de PowerShell es el siguiente:

* Haga el desarrollo inicial en un sitio de proyecto de código abierto. El equipo de PowerShell usa GitHub.
* Use los comentarios de los revisores y [Powershell Script Analyzer](https://aka.ms/psscriptanalyzer) para que el código tenga un estado estable
* Incluya documentación para que otros usuarios sepan cómo usar su trabajo
* Pruebe la acción de publicación con un repositorio local.
* Publique una versión estable o alfa en la Galería de PowerShell y asegúrese de incluir la documentación y el vínculo al sitio del proyecto
* Recopile comentarios y establezca una iteración en el código del sitio del proyecto y, luego, publique actualizaciones estables en la Galería de PowerShell
* Agregue ejemplos y pruebas Pester en el proyecto y el módulo
* Decida si desea firmar su elemento
* Cuando considere que el proyecto está listo para usarlo en un entorno de producción, publique una versión 1.0.0 en la Galería de PowerShell
* Siga recopilando comentarios y estableciendo iteraciones en el código según las contribuciones de los usuarios
