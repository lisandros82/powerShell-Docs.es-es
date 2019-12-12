---
title: Escribir un módulo de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360624"
---
# <a name="writing-a-windows-powershell-module"></a>Escritura de un módulo de Windows PowerShell

Este documento está escrito para administradores, desarrolladores de scripts y desarrolladores de cmdlets que necesitan empaquetar y distribuir sus cmdlets de Windows PowerShell. Mediante el uso de módulos de Windows PowerShell, puede empaquetar y distribuir sus soluciones de Windows PowerShell sin usar un lenguaje compilado.

Los módulos de Windows PowerShell le permiten particionar, organizar y abstraer su código de Windows PowerShell en unidades reutilizables independientes. Con estas unidades reutilizables, puede compartir fácilmente sus módulos directamente con otros. Si es desarrollador de script, también puede volver a empaquetar módulos de terceros para crear aplicaciones personalizadas basadas en scripts. Los módulos, similares a los módulos de otros lenguajes de scripting, como Perl y Python, habilitan soluciones de scripting listas para producción que usan componentes redistribuibles reutilizables, con la ventaja adicional de permitirle volver a empaquetar y abstraer varios componentes en crear soluciones personalizadas.

En su mayor parte, Windows PowerShell tratará cualquier código de script válido de Windows PowerShell guardado en un archivo. psm1 como módulo. PowerShell también tratará automáticamente cualquier ensamblado de cmdlet binario como módulo. Sin embargo, también puede usar un módulo (o más concretamente, un manifiesto de módulo) para agrupar una solución completa. En los siguientes escenarios se describen los usos típicos de los módulos de Windows PowerShell.

### <a name="libraries"></a>Bibliotecas

Los módulos se pueden usar para empaquetar y distribuir bibliotecas coherentes de funciones que realizan tareas comunes. Normalmente, los nombres de estas funciones comparten uno o más sustantivos que reflejan la tarea común para la que se usan. Estas funciones también pueden ser similares a las clases de .NET Framework en que pueden tener miembros públicos y privados. Por ejemplo, una biblioteca puede contener un conjunto de funciones para las transferencias de archivos. En este caso, el sustantivo que refleja la tarea común podría ser "File".

### <a name="configuration"></a>Configuración

Los módulos se pueden usar para personalizar el entorno mediante la adición de cmdlets, proveedores, funciones y variables específicos.

### <a name="compiled-code-development-and-distribution"></a>Desarrollo y distribución de código compilado

Los desarrolladores de cmdlets y proveedores pueden usar módulos para probar y distribuir su código compilado sin necesidad de crear complementos. Pueden importar el ensamblado que contiene el código compilado como un módulo (un módulo binario) sin necesidad de crear y registrar complementos.

## <a name="see-also"></a>Véase también

[Descripción de un módulo de Windows PowerShell](./understanding-a-windows-powershell-module.md)

[Cómo escribir un módulo de script de PowerShell](./how-to-write-a-powershell-script-module.md)

[Cómo escribir un módulo binario de PowerShell](./how-to-write-a-powershell-binary-module.md)

[Cómo escribir un manifiesto de módulo de PowerShell](how-to-write-a-powershell-module-manifest.md)

[Modificación de la ruta de instalación de PSModulePath](./modifying-the-psmodulepath-installation-path.md)

[Importar un módulo de PowerShell](./importing-a-powershell-module.md)

[Instalación de un módulo de PowerShell](./installing-a-powershell-module.md)
