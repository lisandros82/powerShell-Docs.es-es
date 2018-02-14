---
ms.date: 2017-06-05
keywords: powershell, cmdlet
title: Scripting de PowerShell
ms.openlocfilehash: 9214b9e40ff6c181f921f89ef78406af20c30e5f
ms.sourcegitcommit: 755d7bc0740573d73613cedcf79981ca3dc81c5e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="powershell"></a>PowerShell

PowerShell, basado en .NET Framework, es un lenguaje de scripting y shell de línea de comandos basado en tareas. Está diseñado específicamente para que los administradores del sistema y los usuarios avanzados automaticen rápidamente la administración de varios sistemas operativos (Linux, macOS, Unix y Windows) y los procesos relacionados con las aplicaciones que se ejecutan en dichos sistemas operativos.

## <a name="powershell-is-open-source"></a>PowerShell es de código abierto

El código fuente base de PowerShell ahora está disponible en GitHub y admite las contribuciones de la comunidad. Vea el [código de PowerShell en GitHub](https://github.com/powershell/powershell).

Puede empezar con los fragmentos que necesita en [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) (Obtener PowerShell)
o, si lo prefiere, con el paseo introductorio incluido en esta [introducción](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).

## <a name="powershell-design-goals"></a>Objetivos de diseño de PowerShell
Windows PowerShell está diseñado para mejorar el entorno de scripting y línea de comandos mediante la eliminación de antiguos problemas y la adición de nuevas características.

### <a name="discoverability"></a>Detectabilidad
Windows PowerShell facilita la detección de sus características. Por ejemplo, para buscar una lista de cmdlets con la finalidad de ver y cambiar los servicios de Windows, escriba:

```
Get-Command *-Service
```

Después de detectar qué cmdlet lleva a cabo una tarea, puede obtener más información sobre este mediante el cmdlet Get-Help. Por ejemplo, para mostrar la ayuda sobre el cmdlet Get-Service, escriba:

```
Get-Help Get-Service
```
La mayoría de los cmdlets emiten objetos que se pueden manipular y después representar en texto para mostrar. Para comprender la salida de ese cmdlet, canalice su salida al cmdlet Get-Member. Por ejemplo, el siguiente comando muestra información sobre los miembros de la salida del objeto mediante el cmdlet Get-Service.

```
Get-Service | Get-Member
```

### <a name="consistency"></a>Consistency
La administración de sistemas puede ser una tarea muy compleja y las herramientas con una interfaz coherente ayudan a controlar esa complejidad inherente. Lamentablemente, ni las herramientas de línea de comandos ni los objetos COM que permiten ejecutar scripts son famosos por su coherencia.

La coherencia de Windows PowerShell es uno de sus activos principales. Por ejemplo, si sabe cómo usar el cmdlet Sort-Object, puede usar ese conocimiento para ordenar la salida de cualquier cmdlet. No es necesario obtener información sobre las distintas rutinas de ordenación de cada cmdlet.

Además, los desarrolladores de cmdlets no tienen que diseñar características de ordenación para sus cmdlets. Windows PowerShell les proporciona un marco que proporciona las características básicas y les obliga a ser coherentes en muchos aspectos de la interfaz. El marco elimina algunas de las opciones que se suelen dejar al desarrollador, pero a cambio simplifica el desarrollo de cmdlets sólidos y fáciles de usar.

### <a name="interactive-and-scripting-environments"></a>Entornos interactivo y de scripting
Windows PowerShell es un entorno interactivo y de scripting combinado que ofrece acceso a las herramientas de línea de comandos y a los objetos COM, y que permite aprovechar la eficacia de la biblioteca de clases .NET Framework (FCL).

Este entorno mejora en el Símbolo del sistema de Windows, que proporciona un entorno interactivo con varias herramientas de línea de comandos. También mejora en los scripts de Windows Script Host (WSH), que permiten usar varias herramientas de línea de comandos y objetos de automatización COM, pero no proporcionan un entorno interactivo.

Al combinar el acceso a todas estas características, Windows PowerShell amplía la capacidad del usuario interactivo y el escritor de scripts, y facilita la administración del sistema.

### <a name="object-orientation"></a>Orientación a objetos
Aunque interactúa con Windows PowerShell escribiendo comandos de texto, Windows PowerShell se basa en objetos, no en texto. La salida de un comando es un objeto. Puede enviar el objeto de salida a otro comando como entrada. Como resultado, Windows PowerShell proporciona una interfaz conocida a usuarios que tienen experiencia con otros shells, a la vez que introduce un paradigma de línea de comandos nuevo y eficaz. Amplía el concepto de envío de datos entre comandos, ya que permite enviar objetos, en lugar de texto.

### <a name="easy-transition-to-scripting"></a>Transición sencilla al scripting
Windows PowerShell facilita la transición de la escritura interactiva de comandos a la creación y ejecución de scripts. Puede escribir comandos en el símbolo del sistema de Windows PowerShell para detectar los comandos que realizan una tarea. A continuación, puede guardar esos comandos en una transcripción o un historial antes de copiarlos en un archivo para su uso como un script.
