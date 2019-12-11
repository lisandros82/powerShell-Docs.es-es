---
ms.date: 09/06/2019
keywords: powershell, cmdlet
title: Novedades de PowerShell 5.0 ISE
ms.openlocfilehash: 8f15e99c5a6ae33aeae9bd33eb0cf58fb27e3b90
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416632"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a>Novedades de Windows PowerShell 5.0 ISE

En este tema se explican las características nuevas y actualizadas que se introdujeron en la versión 5.0 del Entorno de scripting integrado (ISE) de Windows PowerShell.

> [!NOTE]
> PowerShell ISE ya no se incluye en el desarrollo activo de características. Como componente que se envía con Windows, sigue siendo compatible oficialmente con las correcciones de servicios de seguridad y alta prioridad.
> Aunque actualmente no está previsto quitar el ISE de Windows,
>
> no existe ninguna compatibilidad con él a partir de PowerShell v6. Los usuarios que quieran reemplazar el ISE deben usar [Visual Studio Code](https://code.visualstudio.com/) con la [extensión de PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).

## <a name="feature-description"></a>Descripción de la característica

Windows PowerShell ISE es una aplicación host que permite escribir, ejecutar y probar scripts y módulos en un entorno gráfico e intuitivo. Las características principales, como el coloreado de la sintaxis, el procedimiento para completar con el tabulador, la depuración visual, la compatibilidad con Unicode y la Ayuda contextual, proporcionan una rica experiencia de scripting.

Para obtener más información, consulte [Introducción a Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).

En la tabla siguiente se enumeran las características nuevas y modificadas de esta versión de Windows PowerShell ISE en Windows PowerShell.

## <a name="intellisense"></a>Intellisense

> Agregado en ISE 3.0

IntelliSense es una característica de asistencia de finalización automática que forma parte de Windows PowerShell ISE.
Intellisense muestra menús en los que se pueden hacer clic de los cmdlets, parámetros, valores de parámetros, archivos o carpetas potencialmente coincidentes a medida que escribe.

**¿Qué valor aporta este cambio?**

Con la adición de IntelliSense, es más fácil detectar cmdlets y la sintaxis cuando se usa Windows PowerShell ISE para crear scripts. También puede usar Windows PowerShell ISE para obtener información sobre Windows PowerShell al crear nuevos scripts.

**¿Qué funciona de manera diferente?**

Si escribe cmdlets en Windows PowerShell ISE, se muestra un menú desplazable en el que puede realizar sus selecciones, que permite examinar y seleccionar los comandos adecuados.

## <a name="snippets"></a>Fragmentos de código

> Agregado en ISE 3.0

Los *fragmentos de código* son secciones de código de Windows PowerShell breves que puede insertar fácilmente en los scripts que crea en Windows PowerShell ISE. Windows PowerShell ISE incluye un conjunto predeterminado de fragmentos de código. Los fragmentos de código se pueden agregar mediante el cmdlet `New-Snippet` mientras se trabaja en Windows PowerShell ISE.

**¿Qué valor aporta este cambio?**

El uso de fragmentos de código permite ensamblar y crear rápidamente scripts para automatizar el entorno.

**¿Qué funciona de manera diferente?**

Para usar fragmentos de código en Windows PowerShell 3.0, o cualquier versión posterior, en el menú **Edición**, haga clic en **Iniciar fragmentos de código** o presione <kbd>Ctrl</kbd>+<kbd>J</kbd>.

## <a name="add-on-tools"></a>Herramientas de complemento

> Agregado en PowerShell 3.0

Windows PowerShell ISE ahora admite herramientas de complemento mediante el modelo de objetos. Estos complementos son controles de Windows Presentation Foundation (WPF) que se muestran como un panel vertical u horizontal en la consola. Si hay varias herramientas de complemento en un panel, se mostrarán como un control de pestaña. También puede agregar o quitar herramientas de complemento no producidas por Microsoft. Para obtener más información, consulte [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).

**¿Qué valor aporta este cambio?**

Los complementos permiten ampliar y personalizar Windows PowerShell ISE con herramientas que agregan funcionalidad y mejoran su experiencia de scripting.

**¿Qué funciona de manera diferente?**

Windows PowerShell ISE 3.0 y versiones posteriores incluyen el complemento **Commands**. El complemento **Commands** permite examinar cmdlets y acceder a la ayuda sobre los cmdlets en paralelo con los paneles de **scripts** y de **consola**.

Puede encontrar complementos adicionales mediante el comando **Abrir sitio web de herramientas de complemento** del menú **Complementos**.

## <a name="restart-manager-and-auto-save"></a>Administrador de reinicio y Autoguardar

> Agregado en PowerShell 3.0

Windows PowerShell ISE ahora guarda automáticamente los scripts abiertos cada dos minutos en una ubicación aparte. Al reiniciarse Windows PowerShell ISE tras un bloqueo o reinicio inesperado, recupera scripts que se abrieron en la última sesión, incluso si estos no se guardaron.

Para cambiar el intervalo de guardado automático, ejecute el siguiente comando en el panel de consola: `$psise.Options.AutoSaveMinuteInterval`.

**¿Qué valor aporta este cambio?**

Ahora puede trabajar en Windows PowerShell ISE con la tranquilidad de saber que los scripts abiertos se guardan automáticamente.

**¿Qué funciona de manera diferente?**

Windows PowerShell ISE 2.0 no guarda los scripts automáticamente.

## <a name="most-recently-used-list"></a>Lista Usados más recientemente

> Agregado en PowerShell 3.0

Windows PowerShell ISE tiene ahora una lista Usados más recientemente para los archivos. Cuando se abre un archivo en Windows PowerShell ISE, este se agrega a la lista Usados más recientemente en el menú **Archivo**.

Para cambiar el número predeterminado de archivos en la lista Usados más recientemente, ejecute el siguiente comando en el panel de consola: `$psise.Options.MruCount`.

**¿Qué valor aporta este cambio?**

Ahora puede usar la lista Usados más recientemente para acceder fácilmente a los archivos que usa con frecuencia.

**¿Qué funciona de manera diferente?**

Windows PowerShell ISE 2.0 no tiene una lista Usados más recientemente.

## <a name="console-pane"></a>Panel de consola

> Agregado en PowerShell 3.0

Los paneles de comandos y de salida separados que estaban disponibles en la primera versión de Windows PowerShell ISE se combinaron en un solo panel de consola. El panel de consola es similar en funciones y apariencia a una consola típica de Windows PowerShell, pero incluye las siguientes mejoras:

- El color de la sintaxis del texto de entrada (no texto de salida), incluida la sintaxis XML
- Intellisense
- Coincidencia de llaves
- Indicación de errores
- Compatibilidad total con Unicode
- <kbd>F1</kbd>: ayuda contextual
- <kbd>Ctrl</kbd>+<kbd>F1</kbd>: cmdlet Show-Command contextual
- Compatibilidad con scripts complejos y de derecha a izquierda
- Compatibilidad con fuentes
- Zoom
- Modos de selección de líneas y bloques
- Conservación del contenido escrito en la línea de comandos cuando presiona la <kbd>Flecha arriba</kbd> para ver el historial en la consola

**¿Qué valor aporta este cambio?**

La adición de estos cambios del panel de consola proporciona una experiencia de scripting más coherente con la interfaz de la consola.

**¿Qué funciona de manera diferente?**

Windows PowerShell ISE 2.0 presenta paneles de comandos y de salida independientes.

## <a name="command-line-switches"></a>Modificadores de línea de comandos

> Agregado en PowerShell 3.0

Si inicia Windows PowerShell ISE desde la línea de comandos (escribiendo **Powershell_ise.exe**), puede agregar los siguientes modificadores de línea de comandos nuevos.

- `-NoProfile`: inicia Windows PowerShell ISE sin ejecutar `$profile`
- `-Help`: muestra una ventana de Ayuda
- `-mta`: inicia Windows PowerShell ISE en modo de contenedor multiproceso. El modo de operación predeterminado de Windows PowerShell ISE es el modo de contenedor uniproceso o `-sta`.

**¿Qué valor aporta este cambio?**

La adición de estos modificadores de línea de comandos permite controlar el entorno en el que se ejecuta Windows PowerShell ISE.

**¿Qué funciona de manera diferente?**

Windows PowerShell ISE 2.0 no reconoce estos modificadores de línea de comandos.

## <a name="new-editor-features"></a>Nuevas características del editor

> Agregado en PowerShell 3.0

Otras características de edición de Windows PowerShell ISE son:

- **Color de la sintaxis XML**: Windows PowerShell ISE ahora colorea la sintaxis XML de la misma manera que la sintaxis de Windows PowerShell.
- **Coincidencia de llaves**: Windows PowerShell ISE incluye la coincidencia de llaves y el resaltado, y se pueden usar de las siguientes maneras: (por ejemplo, con el comando **Ir a Igualar** o <kbd>Ctrl</kbd>+<kbd>]</kbd> se localiza la llave de cierre, si hay alguna llave de apertura seleccionada).
- **Vista Esquema**: el panel de scripts admite la esquematización, que permite expandir y contraer secciones de código al hacer clic en los signos más o menos en el margen izquierdo. Puede usar llaves o las etiquetas `#region` y `#endregion` para marcar el inicio o el final de una sección contraíble. Para expandir o contraer todas las regiones, presione <kbd>Ctrl</kbd>+<kbd>M</kbd>.
- **Edición de texto con arrastrar y colocar**: Windows PowerShell ISE permite ahora la edición de texto con arrastrar y colocar. Puede seleccionar cualquier bloque de texto y arrastrar el texto a otra ubicación en el editor o la consola para mover el texto. Si mantiene presionada la tecla <kbd>Ctrl</kbd> mientras arrastra el texto seleccionado, al soltar el botón del mouse, el texto se copiará en la nueva ubicación. En esta versión de Windows PowerShell ISE, al arrastrar y colocar archivos en Windows PowerShell ISE, el archivo se abre.
- **Presentación de errores de análisis**: los errores de análisis se indican con un subrayado rojo. Cuando desplaza el cursor sobre un error indicado, el texto de información sobre herramientas muestra el problema que se encontró en el código.
- **Zoom**: el porcentaje de zoom del contenido de la consola puede establecerse mediante el control deslizante del zoom (en la esquina inferior derecha de la ventana de Windows PowerShell ISE) o escribiendo el comando `$psise.options.Zoom` en el panel de consola.
- **Copiar y pegar texto enriquecido**: la copia en el Portapapeles de Windows PowerShell ISE conserva la información de fuente, tamaño y color de la selección original.
- **Selección de bloques**: para seleccionar un bloque de texto puede mantener presionada la tecla <kbd>ALT</kbd> y seleccionar texto en el panel de scripts con el mouse, o bien presionar <kbd>Alt</kbd>+<kbd>Mayús</kbd>+<kbd>Flecha</kbd>.

**¿Qué valor aporta este cambio?**

Las características de edición adicionales proporcionan un entorno de edición más coherente y eficaz.

**¿Qué funciona de manera diferente?**

Estas mejoras de edición no estaban presentes en Windows PowerShell ISE 2.0.

## <a name="new-help-viewer-window"></a>Ventana del nuevo visor de Ayuda

> Agregado en PowerShell 3.0

Si presiona <kbd>F1</kbd> cuando el cursor está en un cmdlet, o si tiene parte de un cmdlet resaltado, el nuevo visor de Ayuda abre la ayuda contextual sobre el cmdlet resaltado. Para ver la Ayuda **acerca de** Windows PowerShell, escriba `operators` en el panel de consola y, después, presione <kbd>F1</kbd>.

Antes de usar esta característica, descargue la versión más actual de los temas de Ayuda de Windows PowerShell desde el sitio web de Microsoft. El método más sencillo para la descarga de los temas de la Ayuda es ejecutar el cmdlet `Update-Help` en el panel de consola al ejecutar Windows PowerShell ISE como administrador.

Puede modificar donde busca ayuda la tecla <kbd>F1</kbd>. En el menú **Herramientas**/**Opciones**, en la pestaña **Configuración general**, debajo de **Otra configuración**, puede activar o desactivar la casilla **Usar Ayuda local en lugar de contenido en línea**. Al activarla, el cliente busca la Ayuda del cmdlet en la Ayuda descargada en la carpeta de módulos. Si la casilla está desactivada, el cliente busca ayuda en línea.

**¿Qué valor aporta este cambio?**

La ayuda contextual sin salir del cmdlet o script actual proporciona una experiencia de aprendizaje integrada.

**¿Qué funciona de manera diferente?**

Al presionar <kbd>F1</kbd> en versiones anteriores de Windows PowerShell ISE, se abría el archivo de Ayuda en el equipo local. En Windows PowerShell ISE 3.0 y versiones posteriores, se abre una ventana que contiene la Ayuda del cmdlet, que es configurable y permite realizar búsquedas. Esta experiencia de la Ayuda es una novedad de Windows PowerShell ISE 3.0 y la ayuda actualizable es una novedad de Windows PowerShell 3.0.

## <a name="show-command-cmdlet"></a>Cmdlet Show-Command

> Agregado en PowerShell 3.0

El cmdlet `Show-Command` permite componer o ejecutar un cmdlet o una función rellenando un formulario gráfico. El formato permite a los usuarios trabajar con Windows PowerShell en un entorno gráfico.
`Show-Command` también permite a los generadores de scripts avanzados crear una GUI rápida basada en Windows PowerShell.

**¿Qué valor aporta este cambio?**

Si usa `Show-Command` en sus scripts de Windows PowerShell, puede proporcionar a los usuarios el entorno gráfico con el que están familiarizados. `Show-Command` también puede ayudar a los nuevos usuarios a aprender Windows PowerShell.

**¿Qué funciona de manera diferente?**

`Show-Command` es el nuevo Windows PowerShell ISE 3.0.

## <a name="see-also"></a>Vea también

Para obtener más información sobre cómo usar Windows PowerShell ISE, consulte [Exploración del Entorno de scripting integrado de Windows PowerShell](../components/ise/exploring-the-windows-powershell-ise.md).
