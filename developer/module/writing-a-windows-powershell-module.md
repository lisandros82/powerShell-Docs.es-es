---
title: Escribir un módulo de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082063"
---
# <a name="writing-a-windows-powershell-module"></a>Escritura de un módulo de Windows PowerShell

Este documento está dirigido a administradores, desarrolladores de la secuencia de comandos y los desarrolladores de cmdlets que necesitan para empaquetar y distribuir sus cmdlets de Windows PowerShell. Mediante el uso de módulos de Windows PowerShell, puede empaquetar y distribuir sus soluciones de Windows PowerShell sin usar un lenguaje compilado.

Módulos de Windows PowerShell permiten a la partición, organizar y abstraer el código de Windows PowerShell en unidades independientes y reutilizables. Con estas unidades reutilizables, pueden compartir fácilmente los módulos directamente con otros usuarios. Si es un desarrollador de script, también puede volver a empaquetar los módulos de terceros para crear aplicaciones personalizadas basadas en la secuencia de comandos. Los módulos, similares a los módulos en otros lenguajes de secuencias de comandos como Perl y Python, habilitar soluciones de scripting para entornos de producción que usan componentes reutilizables, redistribuibles, con la ventaja añadida de que le permite volver a empaquetar y abstraer varios componentes a crear soluciones personalizadas.

En su más básica, Windows PowerShell tratará cualquier código válido de secuencia de comandos Windows PowerShell guarda en un archivo. psm1 como un módulo. PowerShell también automáticamente tratará a cualquier ensamblado cmdlet binario como un módulo. Sin embargo, también puede usar un módulo (o más específicamente, un manifiesto de módulo) para agrupar una solución completa. Los escenarios siguientes describen los usos típicos de módulos de Windows PowerShell.

### <a name="libraries"></a>Bibliotecas

Módulos pueden utilizarse para empaquetar y distribuir cohesivas bibliotecas de funciones que realizan tareas comunes. Normalmente, los nombres de estas funciones comparten uno o varios nombres que reflejan la tarea habitual que se usan para. Estas funciones también pueden ser similares a las clases de .NET Framework en que pueden tener miembros públicos y privados. Por ejemplo, una biblioteca puede contener un conjunto de funciones para las transferencias de archivos. En este caso, el nombre que refleje la tarea habitual podría ser "file".

### <a name="configuration"></a>Configuración

Los módulos se pueden usar para personalizar su entorno mediante la adición de variables, proveedores, funciones y cmdlets específicos.

### <a name="compiled-code-development-and-distribution"></a>Desarrollo de código compilado y distribución

Los desarrolladores de cmdlet y proveedor pueden utilizar módulos para probar y distribuir su código compilado sin necesidad de crear complementos. Puede importar el ensamblado que contiene el código compilado como un módulo (un módulo binario) sin necesidad de crear y registrar complementos.

## <a name="see-also"></a>Véase también

[Descripción de un módulo de Windows PowerShell](./understanding-a-windows-powershell-module.md)

[Cómo escribir un módulo de Script de PowerShell](./how-to-write-a-powershell-script-module.md)

[Cómo escribir un módulo binario de PowerShell](./how-to-write-a-powershell-binary-module.md)

[Cómo escribir un manifiesto de módulo de PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[Modificar la ruta de instalación PSModulePath](./modifying-the-psmodulepath-installation-path.md)

[Importar un módulo de PowerShell](./importing-a-powershell-module.md)

[Instalación de un módulo de PowerShell](./installing-a-powershell-module.md)
