---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Entorno de scripting integrado (ISE) de Windows PowerShell
ms.assetid: f156b92d-0203-46d2-89c7-b4989d32e3d2
ms.openlocfilehash: a5fcc8c813349d0b85cc3af29047424fe787d168
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320523"
---
# <a name="windows-powershell-integrated-scripting-environment-ise"></a>Entorno de scripting integrado (ISE) de Windows PowerShell

El Entorno de scripting integrado (ISE ) de Windows PowerShell es uno de los dos hosts para el motor y el lenguaje de Windows PowerShell. Puede escribir, ejecutar y probar scripts de maneras que no están disponibles en la consola de Windows PowerShell. El ISE agrega color de sintaxis, finalización con tabulación, IntelliSense, depuración visual y ayuda contextual.

El ISE permite ejecutar comandos en un panel de consola, pero también admite paneles que se pueden usar para ver simultáneamente el código fuente del script y otras herramientas que pueden conectarse al ISE. También puede abrir varias ventanas de script al mismo tiempo, lo cual es especialmente útil cuando se depura un script que usa las funciones definidas en otros scripts o módulos.

## <a name="whats-new"></a>Novedades

Estas son algunas de las características que se agregaron al ISE en las versiones más recientes de PowerShell.

### <a name="added-in-powershell-30-windows-server-2012-windows-8"></a>Agregado en PowerShell 3.0 (Windows Server 2012, Windows 8)

**Intellisense** completa automáticamente sus comandos mostrando menús de cmdlets, parámetros, valores de parámetros, archivos o carpetas coincidentes a medida que escribe.

**Fragmentos de código** son secciones de código breves que puede insertar fácilmente en los scripts que escribe. Una colección de fragmentos de código útiles se incluye en el cuadro y puede agregar más mediante el cmdlet **New-Snippet**.

Se pueden crear **herramientas de complemento** que agreguen características al ISE mediante la escritura de código que interactúe con el [modelo de objetos de scripting de Windows PowerShell ISE](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

Estas herramientas pueden mostrar controles en un panel con fichas o funcionar de manera invisible en segundo plano. El complemento **Comandos** es un buen ejemplo. Se incluye con la versión 3.0 y posteriores, que muestra una lista de los comandos disponibles y su ayuda.

**Administrador de reinicio y Autoguardar** permite guardar automáticamente los scripts cada dos minutos para ayudar a evitar la pérdida del trabajo en caso de un bloqueo o reinicio inesperado.

Ahora, la **lista Usados más recientemente** forma parte del menú Abrir archivo para que sea más fácil obtener acceso a los archivos que se usan con mayor frecuencia.

**Panel de consola combinado**. En versiones anteriores del ISE, los paneles de comandos y salida eran independientes. Ahora se combinan en un solo panel que representa más directamente lo que se ve en la consola de Windows Powershell.

**Modificadores de la línea de comandos**. Varios modificadores de la línea de comandos nuevos ofrecen un mayor control sobre el funcionamiento del ISE. -NoProfile inicia el ISE sin ejecutar un script de perfil. -Help abre una ventana de ayuda con el ISE. -mta inicia el ISE en "modo de contenedor multiproceso". El modo predeterminado es el de uniproceso.

Las **nuevas características del editor** facilitan la creación y lectura del código:

- **Color de la sintaxis XML**. El editor de ISE colorea ahora la sintaxis XML de la misma manera que la sintaxis de código de Windows PowerShell.

- **Coincidencia de llaves**. Windows PowerShell ISE resalta las llaves coincidentes para que pueda asegurarse de tener la cantidad correcta de llaves de cierre según la cantidad de llaves de apertura. Use CTRL-\[ para ubicar la llave de cierre que coincida con la llave de apertura en la que se encuentra en cursor.

- **Vista Esquema**. Puede contraer o expandir las secciones del código haciendo clic en los signos más y menos del margen izquierdo. De este modo, podrá encontrar fácilmente el código que busca en un script largo.

- **Editar texto con arrastrar y colocar**. Puede seleccionar un bloque de texto y arrastrarlo a otra ubicación para moverlo. Si mantiene presionada la tecla Ctrl mientras arrastra el texto seleccionado, lo copiará en lugar de moverlo.

- **Presentación de errores de análisis**. Windows PowerShell examina el script a medida que escribe. Si detecta un error, muestra un zigzag rojo bajo el código incorrecto. Al mantener el puntero sobre el error indicado, la información sobre herramientas muestra el problema encontrado.

- **Zoom**. Puede acercar el texto para que resulte más fácil de leer o alejarlo para ver la imagen más grande mediante el control deslizante de la esquina inferior derecha de la ventana del ISE.

- **Copia y pegado de texto enriquecido**. Al copia texto del ISE en el Portapapeles, se incluye la información de fuente, tamaño y de color del texto seleccionado.

- **Selección de bloques**. Para seleccionar un fragmento de texto en forma de bloque, puede mantener presionada la tecla ALT y seleccionar texto en el panel de scripts con el ratón, o bien presionar **Alt+Mayús+Flecha**.

### <a name="added-in-powershell-20-windows-server-2008-r2-windows-7"></a>Agregado en PowerShell 2.0 (Windows Server 2008 R2, Windows 7)

El ISE se introdujo con PowerShell 2.0.

## <a name="requirements-for-running-the-windows-powershell-ise"></a>Requisitos para ejecutar Windows PowerShell ISE

El ISE está disponible en cualquier equipo Windows que puede ejecutar Windows PowerShell 2.0 o una versión posterior. Cada versión de Windows y Windows Server incluye una versión de Windows PowerShell y el ISE, pero se puede actualizar a la versión más reciente disponible mediante la instalación de Windows Management Framework (WMF). Consulte la documentación del [WMF](/powershell/wmf) para obtener más información.

> [!NOTE]
> Dado que Windows PowerShell ISE requiere una interfaz gráfica de usuario, no puede ejecutar la opción Server Core de Windows Server.

## <a name="see-also"></a>Vea también

[Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)