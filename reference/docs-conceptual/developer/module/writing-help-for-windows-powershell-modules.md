---
title: Escribir ayuda para módulos de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360564"
---
# <a name="writing-help-for-windows-powershell-modules"></a>Escritura de la Ayuda de los módulos de Windows PowerShell

Los módulos de Windows PowerShell pueden incluir temas de ayuda sobre el módulo y los miembros del módulo, como cmdlets, proveedores, funciones y scripts. El cmdlet `Get-Help` muestra los temas de ayuda del módulo en el mismo formato que muestra la ayuda para otros elementos de Windows PowerShell y los usuarios usan los comandos `Get-Help` estándar para obtener los temas de ayuda.

En este documento se explica el formato y la ubicación correcta de los temas de ayuda del módulo, y se sugieren instrucciones para el contenido de la ayuda del módulo.

## <a name="types-of-module-help"></a>Tipos de ayuda de módulo

Un módulo puede incluir los siguientes tipos de ayuda.

- **Ayuda del cmdlet**. Los temas de ayuda que describen los cmdlets de un módulo son archivos XML que usan el esquema de ayuda de comandos.

- **Ayuda del proveedor**. Los temas de ayuda que describen los proveedores de un módulo son archivos XML que usan el esquema de ayuda del proveedor.

- **Ayuda**de la función. Los temas de ayuda que describen las funciones de un módulo pueden ser archivos XML que usan el esquema de ayuda del comando o los temas de ayuda basados en comentarios dentro de la función, o el módulo de script o script.

- **Ayuda del script**. Los temas de ayuda que describen los scripts de un módulo pueden ser archivos XML que usan el esquema de ayuda del comando o los temas de ayuda basados en comentarios del módulo script o script.

- **Ayuda conceptual ("About")** . Puede usar un tema de ayuda conceptual ("About") para describir el módulo y sus miembros, así como explicar cómo se pueden usar los miembros conjuntamente para realizar tareas. Los temas de ayuda conceptual son archivos de texto con codificación Unicode (UTF-8). El nombre de archivo debe usar el formato `about_<name>.help.txt`, como about_MyModule. help. txt. De forma predeterminada, Windows PowerShell incluye más de 100 de estos temas conceptuales sobre los temas de ayuda y tienen el formato del siguiente ejemplo.

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

## <a name="placement-of-module-help"></a>Ubicación de la ayuda del módulo

El cmdlet `Get-Help` busca archivos de tema de ayuda del módulo en subdirectorios específicos del lenguaje del directorio del módulo.

Por ejemplo, en el diagrama de la estructura de directorios siguiente se muestra la ubicación de los temas de ayuda para el módulo SampleModule.

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
> En el ejemplo, el marcador de posición *\<ModulePath >* representa una de las rutas de acceso de la variable de entorno `PSModulePath`, como $Home \documents\modules, $pshome nueva \modules. o una ruta de acceso personalizada que el usuario especifica.

## <a name="getting-module-help"></a>Obtener ayuda de módulo

Cuando un usuario importa un módulo en una sesión, los temas de ayuda de ese módulo se importan en la sesión junto con el módulo. Puede enumerar los archivos de tema de ayuda en el valor de la clave FileList en el manifiesto del módulo, pero los temas de ayuda no se ven afectados por el cmdlet `Export-ModuleMember`.

Puede proporcionar temas de ayuda de módulo en distintos idiomas. El cmdlet `Get-Help` muestra automáticamente los temas de ayuda del módulo en el idioma especificado para el usuario actual en el elemento configuración regional y de idioma del panel de control. En Windows Vista y versiones posteriores de Windows, `Get-Help` busca los temas de ayuda en subdirectorios específicos del lenguaje del directorio del módulo de acuerdo con los estándares de reserva del lenguaje establecidos para Windows.

A partir de Windows PowerShell 3,0, la ejecución de un comando `Get-Help` para un cmdlet o una función desencadena la importación automática del módulo. El cmdlet `Get-Help` muestra inmediatamente el contenido de los temas de ayuda en el módulo.

Si el módulo no contiene temas de ayuda y no hay ningún tema de ayuda para los comandos del módulo en el equipo del usuario, `Get-Help` muestra la ayuda generada automáticamente. La ayuda generada automáticamente incluye la sintaxis de comandos, los parámetros y los tipos de entrada y salida, pero no incluye ninguna descripción. La ayuda generada automáticamente incluye texto que indica al usuario que intente usar el cmdlet `Update-Help` para descargar la ayuda del comando desde Internet o desde un recurso compartido de archivos. También recomienda usar el parámetro **online** del cmdlet `Get-Help` para obtener la versión en línea del tema de ayuda.

## <a name="supporting-updatable-help"></a>Compatibilidad con la ayuda actualizable

Los usuarios de Windows PowerShell 3,0 y versiones posteriores de Windows PowerShell pueden descargar e instalar archivos de ayuda actualizados para un módulo desde Internet o desde un recurso compartido de archivos local. Los cmdlets `Update-Help` y `Save-Help` ocultan los detalles de administración del usuario. Los usuarios ejecutan el cmdlet `Update-Help` y, a continuación, usan el cmdlet `Get-Help` para leer los archivos de ayuda más recientes para el módulo en el símbolo del sistema de Windows PowerShell. Los usuarios no necesitan reiniciar Windows ni Windows PowerShell.

Los usuarios detrás de firewalls y aquellos que no tienen acceso a Internet también pueden usar la ayuda actualizable. Los administradores con acceso a Internet usan el cmdlet `Save-Help` para descargar e instalar los archivos de ayuda más recientes en un recurso compartido de archivos. A continuación, los usuarios usan el parámetro **path** del cmdlet `Update-Help` para obtener los archivos de ayuda más recientes del recurso compartido de archivos.

Los autores de módulos pueden incluir archivos de ayuda en el módulo y usar la ayuda actualizable para actualizar los archivos de ayuda, u omitir los archivos de ayuda del módulo y usar la ayuda actualizable para instalarlos y actualizarlos.

Para obtener más información acerca de la ayuda actualizable, consulte compatibilidad con la [ayuda actualizable](./supporting-updatable-help.md).

## <a name="supporting-online-help"></a>Compatibilidad con la ayuda en línea

Los usuarios que no pueden instalar archivos de ayuda actualizados en sus equipos suelen basarse en la versión en línea de los temas de ayuda de los módulos. El parámetro **online** del cmdlet `Get-Help` abre la versión en línea del tema de ayuda de un cmdlet o una función avanzada para el usuario en su explorador de Internet predeterminado.

El cmdlet `Get-Help` usa el valor de la propiedad **HelpUri** del cmdlet o la función para encontrar la versión en línea del tema de ayuda.

A partir de Windows PowerShell 3,0, puede ayudar a los usuarios a encontrar la versión en línea de los temas de ayuda de cmdlets y funciones definiendo el atributo HelpUri en la clase de cmdlet o la propiedad **HelpUri** del atributo **CmdletBinding** . El valor del atributo es el valor de la propiedad **HelpUri** del cmdlet o la función.

Para obtener más información, consulte compatibilidad con la [ayuda en línea](./supporting-online-help.md).

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)

[Compatibilidad con la ayuda actualizable](./supporting-updatable-help.md)

[Compatibilidad con la ayuda en línea](./supporting-online-help.md)