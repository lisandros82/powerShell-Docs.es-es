---
ms.date: 08/24/2018
keywords: powershell, cmdlet
title: Descripción de los nombres de comandos de PowerShell
ms.openlocfilehash: a65ffcdca6510093b0a77234e20546b6cc1f02bf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030421"
---
# <a name="learning-powershell-command-names"></a>Descripción de los nombres de comandos de PowerShell

El aprendizaje de nombres de comandos y parámetros supone una inversión de tiempo considerable con la mayoría de las interfaces de la línea de comandos. El problema es que hay algunos patrones. La memorización es la única manera de aprender los comandos y parámetros que necesita utilizar regularmente.

Cuando se trabaja con un nuevo comando o parámetro, no siempre se puede utilizar lo que ya se conoce. Tiene que buscar y aprender un nuevo nombre. Tradicionalmente, las interfaces de la línea de comandos comienzan con un pequeño conjunto de herramientas y crecen con adiciones incrementales. Es fácil ver por qué no hay una estructura estándar.
Esto parece lógico para los nombres de comandos ya que cada comando es una herramienta independiente. PowerShell tiene una mejor manera de controlar los nombres de comandos.

## <a name="learning-command-names-in-traditional-shells"></a>Aprendizaje de nombres de comandos en shells tradicionales

La mayoría de los comandos se crea para administrar elementos del sistema operativo o las aplicaciones, como los servicios o los procesos. Los comandos tienen nombres que pueden o no encajar en una familia. Por ejemplo, en sistemas Windows, puede usar los comandos `net start` y `net stop` para iniciar y detener un servicio. **SC.exe** es otra herramienta de control de servicios de Windows. Ese nombre no encaja en el patrón de nomenclatura de los comandos de servicio **net.exe**. Para la administración del proceso, Windows tiene el comando **tasklist.exe** para enumerar los procesos y el comando **taskkill.exe** para eliminarlos.

Además, estos comandos tienen especificaciones de parámetro irregulares. No se puede usar el comando `net start` para iniciar un servicio en un equipo remoto. El comando **sc.exe** puede iniciar un servicio en un equipo remoto. Pero para especificar el equipo remoto, debe anteponer el nombre con una barra invertida doble. Para iniciar el servicio de cola de impresión en un equipo remoto llamado DC01, escriba `sc.exe \\DC01 start spooler`.
Para enumerar las tareas que se ejecutan en DC01, utilice el parámetro **/S** y el nombre del equipo sin barras invertidas. Por ejemplo, `tasklist /S DC01`.

> [!NOTE]
> Antes de PowerShell v6, `sc` era un alias para el cmdlet `Set-Content`. Por lo tanto, para ejecutar el comando **sc.exe** en una versión de PowerShell anterior a la versión 6, debe incluir el nombre de archivo completo **sc.exe**, incluida la extensión de archivo **exe**.

Los servicios y procesos son ejemplos de elementos manejables en un equipo que tienen ciclos de vida bien definidos. Puede iniciar o detener servicios o procesos, u obtener una lista de todos los servicios o procesos que se están ejecutando actualmente. Aunque existen importantes distinciones técnicas entre ellos, las acciones que se realizan en los servicios y procesos son conceptualmente las mismas. Además, las selecciones que realizamos para personalizar una acción mediante la especificación de parámetros también pueden ser conceptualmente similares.

PowerShell aprovecha estas similitudes para reducir el número de nombres distintos que debe saber para entender y usar los cmdlets.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Los cmdlets usan nombres verbo-sustantivo para reducir la memorización de comandos.

PowerShell usa un sistema de nomenclatura de "verbo-sustantivo". Cada nombre de cmdlet consiste en un verbo estándar con un guión y un sustantivo específico. Los verbos de PowerShell no son siempre verbos ingleses, pero expresan acciones específicas en PowerShell. Los sustantivos son muy similares a los de cualquier idioma. Describen tipos específicos de objetos que son importantes para la administración del sistema. Es fácil demostrar cómo estos nombres de dos componentes reducen el esfuerzo de aprendizaje examinando algunos ejemplos.

PowerShell tiene un conjunto recomendado de verbos estándar. Los sustantivos tienen menos restricciones, pero siempre describen sobre qué elemento actúa el verbo. PowerShell tiene comandos, como `Get-Process`, `Stop-Process`, `Get-Service` y `Stop-Service`.

En este ejemplo de dos sustantivos y verbos, la coherencia no simplifica tanto el aprendizaje. Extienda esa lista a un conjunto estandarizado de 10 verbos y 10 sustantivos. Ahora solo tiene que comprender 20 palabras.
Pero esas palabras se pueden combinar para formar 100 nombres de comando distintos.

Es fácil entender lo que hace un comando de PowerShell leyendo su nombre. El comando para apagar el equipo es `Stop-Computer`. El comando para enumerar todos los equipos en una red es `Get-Computer`. El comando para obtener la fecha del sistema es `Get-Date`.

Puede enumerar todos los comandos que incluyan un verbo determinado con el parámetro **Verb** para `Get-Command`. Por ejemplo, para ver todos los cmdlets que usan el verbo `Get`, escriba:

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

Utilice el parámetro **Noun** para ver una familia de comandos que afectan al mismo tipo de objeto. Por ejemplo, ejecute el siguiente comando para ver los comandos disponibles para la administración de servicios:

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>Los cmdlets usan parámetros estándar.

Como hemos indicado anteriormente, los comandos usados en las interfaces de línea de comandos tradicionales no siempre tienen nombres de parámetro coherentes. Los parámetros suelen tener un único carácter o palabras abreviadas que sean fáciles de escribir, pero que los nuevos usuarios no puedan comprender fácilmente.

A diferencia de la mayoría de interfaces de línea de comandos tradicionales, PowerShell procesa los parámetros directamente y usa este acceso directo a los parámetros junto con instrucciones para desarrolladores para estandarizar los nombres de parámetro. Esta guía anima pero no garantiza que cada cmdlet cumpla con el estándar.

PowerShell también normaliza el separador de parámetro. Los nombres de parámetro siempre tienen un '-' antepuesto con un comando de PowerShell. Considere el ejemplo siguiente:

```powershell
Get-Command -Name Clear-Host
```

El nombre del parámetro es **Name**, pero se escribe como `-Name` cuando se usa en la línea de comandos como parámetro.

Estas son algunas de las características generales de los nombres y usos de los parámetros estándar.

### <a name="the-help-parameter-"></a>Parámetro de ayuda (?)

Cuando se especifica el parámetro `-?` en cualquier cmdlet, PowerShell muestra la ayuda para el cmdlet.
El cmdlet no se ejecuta.

### <a name="common-parameters"></a>Parámetros comunes

PowerShell tiene varios *parámetros comunes*. Estos parámetros se controlan mediante el motor de PowerShell. Los parámetros comunes siempre se comportan del mismo modo. Los parámetros comunes son **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable** y **OutBuffer**.

### <a name="recommended-parameter-names"></a>Nombres de parámetro recomendados

Los cmdlets principales de PowerShell usan nombres estándar para parámetros similares. No se exige el uso de nombres de parámetro estándares, pero existen instrucciones explícitas a fin de promover la estandarización.

Por ejemplo, el nombre recomendado para un parámetro que hace referencia a un equipo, como **nombreDeEquipo**, en lugar de servidor, host, sistema, nodo u otras alternativas comunes. Otros nombres de parámetro importantes recomendados son **Force**, **Exclude**, **Include**, **PassThru**, **Path** y **CaseSensitive**.
