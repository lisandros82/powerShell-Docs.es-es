---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Crear y publicar un elemento
ms.openlocfilehash: b6bcd3e923b77ad7d19a1d92aeb78222bff7ea7e
ms.sourcegitcommit: e08f036021e9f115dbb52c697941706cc4ee51dd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2017
---
# <a name="creating-and-publishing-an-item"></a>Crear y publicar un elemento 
La Galería de PowerShell es el lugar para publicar módulos, scripts y recursos de DSC estables de PowerShell y compartirlos con la comunidad de usuarios más amplia de PowerShell.    

En este artículo se describe la mecánica y los pasos importantes para preparar un script o un módulo y publicarlo en la Galería de PowerShell.
Se recomienda que revise el artículo de [instrucciones de publicación](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) para entender cómo garantizar que los usuarios de la Galería de PowerShell acepten ampliamente los elementos que publique. 

Los requisitos mínimos para publicar un elemento en la Galería de PowerShell son los siguientes:

* Tener una cuenta de la Galería de PowerShell y la clave de API asociada
* Asegurarse de que el elemento incluya los metadatos requeridos
* Usar las herramientas de validación previa para asegurarse de que el elemento esté listo para su publicación
* Publicar el elemento en la Galería de PowerShell con los comandos Publish-Module y Publish-Script
* Responder a preguntas o inquietudes sobre su elemento
 
La Galería de PowerShell acepta módulos y scripts de PowerShell. Cuando hablamos de scripts, nos referimos a un script de PowerShell que es un archivo único y no parte de un módulo más grande. 

## <a name="powershell-gallery-account-and-api-key"></a>Cuenta de la Galería de PowerShell y clave de API
Consulte [Creating a PowerShell Gallery Account](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery_creating_an_account) (Creación de una cuenta de la Galería de PowerShell) para saber cómo configurar una cuenta de la Galería de PowerShell. 

Una vez que cree una cuenta, puede obtener la clave de API que se necesita para publicar un elemento.
Después de iniciar sesión con la cuenta, su nombre de usuario aparecerá en la parte superior de las páginas de la Galería de PowerShell en lugar de Registrarse. Haga clic en su nombre de usuario para ir a la página Mi cuenta, donde encontrará la clave de API. 

Nota: la clave de API se debe tratar con la misma seguridad con que trata el inicio de sesión y la contraseña. Con esta clave usted mismo, o cualquier otra persona, puede actualizar el elemento de su propiedad en la Galería de PowerShell. Se recomienda que actualice la clave con regularidad, lo que puede hacer con la opción Restablecer clave en la página Mi cuenta.

## <a name="required-metadata-for-items-published-to-the-powershell-gallery"></a>Metadatos requeridos para elementos publicados en la Galería de PowerShell

La Galería de PowerShell proporciona a los usuarios de la galería información obtenida de los campos de metadatos que se incluyen en el manifiesto del script o del módulo.
Crear o modificar elementos para su publicación en la Galería de PowerShell tiene un pequeño conjunto de requisitos de información que se entrega en el manifiesto del elemento. Se recomienda revisar la sección sobre los metadatos de los elementos del artículo sobre [instrucciones de publicación](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/psgallery-PublishingGuidelines) para saber cómo entregar a los usuarios la mejor información junto con sus elementos. 

Los cmdlets [New-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/ModuleManifest-Reference) y [New-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_new-scriptfileinfo) crearán la plantilla de manifiesto para usted, con marcadores de posición para todos los elementos del manifiesto. 

Ambos manifiestos tienen dos secciones importantes para la publicación, el área Primary Key Data (Datos de clave principal) y el área PSData de PrivateData. Los datos de clave principal del manifiesto de un módulo de PowerShell son todos los elementos fuera de la sección PrivateData. El conjunto de claves principales está vinculado a la versión de PowerShell en uso y no se admiten los valores no definidos. PrivateData admite agregar nuevas claves, por lo que los elementos específicos para la Galería de PowerShell están en la sección PrivateData.


Los elementos de manifiesto más importantes de rellenar para el elemento que publica en la Galería de PowerShell son los siguientes:  

* Nombre del script o del módulo: se extraen de los nombres del archivo .PS1 en el caso de un script o de .PSD1, si se trata de un módulo.
* Versión: clave principal requerida, el formato debe seguir las instrucciones de SemVer (para detalles, consulte los procedimientos recomendados)
* Autor: clave principal requerida que contiene el nombre que se asociará al elemento (consulte Autores y propietarios, que aparece a continuación)
* Descripción: clave principal requerida que se usa para explicar brevemente qué hace este elemento y los requisitos para usarlo
* ProjectURI: campo de URI recomendado en PSData que proporciona un vínculo a un repositorio GitHub o una ubicación similar donde lleva a cabo el desarrollo del elemento

Los autores y propietarios de los elementos de la Galería de PowerShell son conceptos relacionados, pero que no siempre coinciden.  
Los propietarios de un elemento son usuarios con cuentas de la Galería de PowerShell que tienen permiso para mantener el elemento. Puede haber muchos propietarios que puedan actualizar un elemento. El propietario solo está disponible desde la Galería de PowerShell y se pierde si el elemento se copia de un sistema a otro. El autor es una cadena integrada en los datos del manifiesto, por lo que siempre forma parte del elemento. Las recomendaciones para los elementos que provienen de productos Microsoft son las siguientes:

* Deben tener varios propietarios, donde al menos uno de ellos debe ser el nombre del equipo que genera el elemento 
* El autor debe ser un nombre de equipo conocido (como Equipo de SDK de Azure) o Microsoft Corporation.


## <a name="pre-validate-your-item"></a>Validación previa del elemento

Existen algunas herramientas que debe ejecutar en el código antes de publicar el elemento en la Galería de PowerShell:

* [PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/), que se encuentra en la Galería de PowerShell
* En el caso de los módulos, Test-ModuleManifest, que forma parte de PowerShell
* En el caso de los script, Test-ScriptFileInfo, que se incluye con PowerShell Get

[PowerShell Script Analyzer](https://www.powershellgallery.com/packages/PSScriptAnalyzer/) es una herramienta de análisis de código estático que examinará el código para asegurarse de que cumple con las instrucciones de codificación básica de PowerShell. Esta herramienta identificará problemas comunes y críticos que pueda tener el código y se debe ejecutar de manera regular durante el desarrollo para ayudarlo a preparar el elemento para su publicación. PowerShell Script Analyzer brindará una lista de los problemas, identificándolos como Errores, Advertencia e Información. Todos los errores se deben solucionar antes de publicar el elemento en la Galería de PowerShell. Las advertencias se deben revisar y se debe solucionar la mayoría.
PowerShell Script Analyzer se ejecuta cada vez que un elemento se publica o actualiza en la Galería de PowerShell. El equipo de operaciones de la galería se pondrá en contacto con los propietarios del elemento para solucionar los errores que se encuentren. 

Si la infraestructura de la Galería de PowerShell no puede leer la información del manifiesto del elemento, no se podrá publicar. 
[Test-ModuleManifest](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/test-modulemanifest) detectará los problemas comunes que podrían hacer que no se pueda usar el módulo una vez instalado. Se debe ejecutar para cada módulo antes de publicarlo en la Galería de PowerShell. 

Del mismo modo, [Test-ScriptFileInfo](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_test-scriptfileinfo) valida los metadatos de un script y se debe ejecutar en cada script (publicado por separado de un módulo) antes de publicarlo en la Galería de PowerShell. 


## <a name="publishing-items"></a>Publicación de elementos

Debe usar [Publish-Script](https://msdn.microsoft.com/en-us/powershell/gallery/psget/script/psget_publish-script) o [Publish-Module](https://msdn.microsoft.com/en-us/powershell/gallery/psget/module/psget_publish-module) para publicar elementos en la Galería de PowerShell.
Ambos comandos requieren lo siguiente 

* La ruta de acceso al elemento que se publicará. Si es un módulo, use la carpeta con el nombre del módulo. Si especifica una carpeta con varias versiones del mismo módulo, debe especificar el valor RequiredVersion.
* Una clave de API de NuGet. La clave de API que se encuentra en la página Mi cuenta de la Galería de PowerShell.

La mayor parte de las otras opciones de la línea de comandos debe estar en los datos del manifiesto del elemento que se publica, para que no tenga que especificarlos en el comando. 

Para evitar errores, se recomienda que pruebe los comandos con -Whatif -Verbose antes de la publicación. Esto permitirá ahorrar bastante tiempo, porque cada vez que publique en la Galería de PowerShell, debe actualizar el número de versión en la sección de manifiesto del elemento. 

Algunos ejemplos podrían ser los siguientes: 'Publish-Module -Path ".\MyModule" -RequiredVersion "0.0.1" -NugetAPIKey "GUID" -Whatif -Verbose' 'Publish-Script -Path ".\MyScriptFile.PS1" -NugetAPIKey "GUID" -Whatif -Verbose'

Revise cuidadosamente los resultados y, si no ve errores ni advertencias, repita el comando sin -Whatif.

Todos los elementos que se publican en la Galería de PowerShell se examinarán para ver si tienen virus y se analizarán con PowerShell Script Analyzer. Todos los problemas que surjan en ese momento se enviarán al publicador para que los solucione.  

Una vez que se publica un elemento en la Galería de PowerShell, deberá estar atento a cualquier comentario que aparezca sobre el elemento.

* Asegúrese de supervisar la dirección de correo electrónico asociada con la cuenta que usó para publicar.
Los usuarios y el equipo de operaciones de la Galería de PowerShell harán llegar sus comentarios a través de esa cuenta, incluidos los problema que surjan cuando se ejecute el antivirus o PSSA.
Si la cuenta de correo electrónico no es válida o se notifican problemas graves a la cuenta y no se resuelven durante mucho tiempo, los elementos se considerarán abandonados y se quitarán de la Galería de PowerShell, tal como se indica en los [Términos de uso](https://www.powershellgallery.com/policies/Terms).  
* Se recomienda que se suscriba a la opción Comentarios de cada elemento de la Galería de PowerShell que publique. Esto le permitirá recibir notificaciones si algún usuario comenta sobre alguno de sus elementos en la Galería de PowerShell. Esta acción es opcional y requiere crear una cuenta con LiveFyre.     

