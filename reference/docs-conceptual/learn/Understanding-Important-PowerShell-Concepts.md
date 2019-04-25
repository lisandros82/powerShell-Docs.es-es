---
ms.date: 08/23/2018
keywords: powershell, cmdlet
title: Descripción de los conceptos importantes de PowerShell
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: fad64563d1a7a6abd4f0e430331f81f91f43d312
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058597"
---
# <a name="understanding-important-powershell-concepts"></a>Descripción de los conceptos importantes de PowerShell

El diseño de PowerShell integra los conceptos de numerosos entornos diferentes. Varios de los conceptos serán familiares para personas con experiencia en shells o entornos de programación. Sin embargo, pocas personas los conocerán todos. Observar algunos de estos conceptos nos proporcionará una práctica introducción del shell.

## <a name="output-is-object-based"></a>La salida está basada en objetos

A diferencia de las interfaces tradicionales de la línea de comandos, los cmdlets de PowerShell están diseñados para tratar con objetos.
Un objeto es información estructurada que es algo más que la cadena de caracteres que aparece en la pantalla. La salida del comando siempre incluye información adicional que puede usarse si es necesaria.

Si ha utilizado herramientas de procesamiento de texto para procesar datos en el pasado, verá que se comportan de forma diferente cuando se utilizan en PowerShell. En la mayoría de los casos, no necesita herramientas de procesamiento de texto para extraer información específica. Se accede directamente a partes de los datos mediante la sintaxis de objetos estándar de PowerShell.

## <a name="the-command-family-is-extensible"></a>La familia de comandos es extensible

Las interfaces como **cmd.exe** no proporcionan una manera de extender directamente el conjunto de comandos integrado. Puede crear herramientas externas de línea de comandos que se ejecuten en **cmd.exe**. Pero estas herramientas externas no tienen servicios, como la integración de la ayuda. **cmd.exe** no sabe automáticamente que estas herramientas externas son comandos válidos.

Los comandos nativos de PowerShell nativos se conocen como *cmdlets*. Puede crear sus propios módulos y funciones de cmdlets mediante el código compilado o scripts. Los módulos pueden agregar cmdlets y proveedores al shell. PowerShell también admite scripts que son análogos a los scripts de shell de UNIX y los archivos por lotes de **cmd.exe**.

## <a name="powershell-handles-console-input-and-display"></a>PowerShell controla la entrada y la presentación de la consola

Cuando se escribe un comando, PowerShell siempre procesa la entrada directamente de línea de comandos directamente. PowerShell también formatea la salida que se ve en la pantalla. Esta diferencia es significativa porque reduce el trabajo requerido de cada cmdlet. Esto asegura que siempre se pueden hacer las cosas de la misma manera con cualquier cmdlet. Los desarrolladores de cmdlets no necesitan escribir código para analizar los argumentos de línea de comandos o formatear la salida.

Las herramientas de línea de comandos tradicionales tienen sus propios esquemas para solicitar y mostrar la Ayuda. Algunas herramientas de línea de comandos usan **/?** para desencadenar la presentación de la Ayuda; otras usan **-?**, **/H** o incluso **//**. Algunas mostrarán la Ayuda en una ventana de interfaz gráfica de usuario, en lugar de hacerlo en la pantalla de la consola. Si usa un parámetro equivocado, la herramienta podría omitir la entrada y empezar a ejecutar una tarea automáticamente.
Dado que PowerShell analiza y procesa automáticamente la línea de comandos, el parámetro **-?** siempre significa "mostrar la Ayuda para este comando".

> [!NOTE]
> Si se ejecuta una aplicación de gráficos en PowerShell, se abre la ventana de la aplicación.
> PowerShell interviene solo al procesar la entrada de línea de comandos que proporciona o la salida de la aplicación devuelta a la ventana de la consola. No afecta al funcionamiento interno de la aplicación.

## <a name="powershell-uses-some-c-syntax"></a>PowerShell usa la sintaxis de C#

PowerShell se basa en .NET Framework. Comparte algunas características de sintaxis y palabras clave con el lenguaje de programación C#. Aprender PowerShell puede hacer que sea mucho más fácil conocer C#. Para aquellos que ya estén familiarizados con C#, las similitudes pueden facilitar el aprendizaje de PowerShell.
