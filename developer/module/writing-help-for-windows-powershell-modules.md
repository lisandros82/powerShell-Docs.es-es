---
title: Escribir la Ayuda de módulos de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854071"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Escritura de la Ayuda de los módulos de Windows PowerShell

Módulos de Windows PowerShell pueden incluir temas de ayuda sobre el módulo y los miembros de módulo, como cmdlets, proveedores, funciones y scripts. El `Get-Help` cmdlet muestra los temas de Ayuda del módulo en el mismo formato, tal como muestra la Ayuda de otros elementos de Windows PowerShell y los usuarios usar estándar `Get-Help` comandos para obtener los temas de ayuda.

Este documento explica el formato y la ubicación correcta de temas de Ayuda del módulo, y recomienda las directrices para el contenido de Ayuda del módulo.

## <a name="types-of-module-help"></a>Tipos de Ayuda del módulo

Un módulo puede incluir los siguientes tipos de ayuda.

- **Ayuda de cmdlet**. Los temas de ayuda que describen los cmdlets en un módulo son archivos XML que use el comando ayudarán esquema

- **Ayuda del proveedor**. Los temas de ayuda que describen los proveedores en un módulo son archivos XML que utilizan el proveedor de ayudarán de esquema.

- **Funciones**. Los temas de ayuda que describen las funciones de un módulo puede ser archivos XML que use el comando Ayuda basada en comentarios de los temas de Ayuda de la función, o el script o un módulo de script o de esquema

- **Ayuda de script**. Los temas de ayuda que describen las secuencias de comandos en un módulo puede ayudar a los archivos XML que utilizan el comando esquema o basada en comentarios de los temas de ayuda en la secuencia de comandos o el módulo de script.

- **Conceptual ("About"), ayuda**. Puede usar un conceptual ("about"), el tema de ayuda para describir el módulo y sus miembros y explicar cómo se pueden usar conjuntamente para realizar tareas de los miembros. Temas de ayuda conceptual son archivos de texto con codificación Unicode (UTF-8). El nombre de archivo debe usar el `about_<name>.help.txt` formato, como about_MyModule.help.txt. De forma predeterminada, Windows PowerShell incluye más de 100 de estos temas de Ayuda conceptuales y se les aplica formato similar al ejemplo siguiente.

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a>Selección de ubicación de la Ayuda del módulo

El `Get-Help` cmdlet busca los archivos de tema de Ayuda del módulo en subdirectorios específicos del lenguaje del directorio de módulo.

Por ejemplo, el diagrama de estructura de directorios siguiente muestra la ubicación de los temas de ayuda para el módulo SampleModule.

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> En el ejemplo, el  *\<ModulePath >* marcador de posición representa una de las rutas de acceso en el `PSModulePath` variable de entorno, como home\Documents\Modules $, $pshome\Modules o una ruta de acceso personalizada que especifica el usuario.

## <a name="getting-module-help"></a>Obtención de Ayuda del módulo

Cuando un usuario importa un módulo en una sesión, los temas de ayuda para dicho módulo se importan en la sesión junto con el módulo. Puede enumerar los archivos de tema de ayuda en el valor de la clave de la lista de archivos en el manifiesto del módulo, pero los temas de ayuda no se ven afectados por la `Export-ModuleMember` cmdlet.

Puede proporcionar temas de Ayuda de módulos en diferentes idiomas. El `Get-Help` cmdlet muestra automáticamente los temas de Ayuda del módulo en el idioma que se especifica para el usuario actual en el elemento de configuración Regional y de idioma en el Panel de Control. En Windows Vista y versiones posteriores de Windows, `Get-Help` busca en subdirectorios específicos del lenguaje del directorio de módulo según los estándares de reserva de idioma establecidas para Windows de los temas de ayuda.

A partir de Windows PowerShell 3.0, ejecutando un `Get-Help` comando de un cmdlet o función desencadena la importación automática del módulo. El `Get-Help` cmdlet muestra inmediatamente el contenido de los temas de Ayuda del módulo.

Si el módulo no contiene los temas de ayuda y hay no hay temas de ayuda para los comandos en el módulo en el equipo del usuario, `Get-Help` muestra ayuda generada automáticamente. La Ayuda generada automáticamente incluye la sintaxis de comandos, parámetros y tipos de entrada y salida, pero no incluye las descripciones. La Ayuda generada automáticamente incluye el texto que se dirige al usuario al intentar usar el `Update-Help` para descargar la Ayuda de comandos de Internet o de un recurso compartido de archivos. También recomienda el uso de la **Online** parámetro de la `Get-Help` para obtener la versión en línea del tema de ayuda.

## <a name="supporting-updatable-help"></a>Compatibilidad con la ayuda actualizable

Los usuarios de Windows PowerShell 3.0 y versiones posteriores de Windows PowerShell pueden descargar e instalar archivos de Ayuda actualizados para un módulo desde Internet o desde un recurso compartido de archivos local. El `Update-Help` y `Save-Help` cmdlets ocultar los detalles de administración del usuario. Los usuarios ejecuten el `Update-Help` cmdlet y, a continuación, utilice el `Get-Help` cmdlet para leer los archivos de ayuda más recientes para el módulo en el símbolo del sistema de Windows PowerShell. Los usuarios no es necesario reiniciar Windows o Windows PowerShell.

Los usuarios detrás de firewalls y los que no tienen acceso a Internet pueden usar la Ayuda actualizable, también. Los administradores con Internet acceso utilizan el `Save-Help` cmdlet para descargar e instalar los archivos de ayuda más recientes para un recurso compartido de archivos. A continuación, los usuarios utilizar el **ruta de acceso** parámetro de la `Update-Help` para obtener los archivos de ayuda más recientes desde el recurso compartido de archivos.

Los autores de módulos pueden incluir los archivos de ayuda en el módulo y usar la Ayuda actualizable para actualizar los archivos de ayuda, u omitir los archivos de Ayuda del módulo y usar la Ayuda actualizable para instalar y actualizarlos.

Para obtener más información sobre la Ayuda actualizable, consulte [compatibilidad con la Ayuda actualizable](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Compatibilidad con la ayuda en línea

Los usuarios que no se pueden o no instalen actualizan ayuda archivos en sus equipos a menudo dependen de la versión en línea de temas de Ayuda del módulo. El **Online** parámetro de la `Get-Help` cmdlet abre la versión en línea de un cmdlet o una función avanzada de tema de ayuda para el usuario en su explorador de Internet predeterminado.

El `Get-Help` cmdlet usa el valor de la **HelpUri** propiedad del cmdlet o función para buscar la versión en línea del tema de ayuda.

A partir de Windows PowerShell 3.0, puede ayudar a los usuarios encontrar la versión en línea de los temas de Ayuda de cmdlet y función definiendo el atributo HelpUri en la clase del cmdlet o **HelpUri** propiedad de la **CmdletBinding** atributo. El valor del atributo es el valor de la **HelpUri** propiedad del cmdlet o función.

Para obtener más información, consulte [compatibilidad con la Ayuda en línea](./supporting-online-help.md).

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)

[Compatibilidad con la Ayuda actualizable](./supporting-updatable-help.md)

[Compatibilidad con la Ayuda en línea](./supporting-online-help.md)