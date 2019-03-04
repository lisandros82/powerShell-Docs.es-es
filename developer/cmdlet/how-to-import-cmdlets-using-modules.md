---
title: Uso de módulos de Cmdlets de importación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859151"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Cómo importar cmdlets mediante módulos

Este tema describe cómo importar los cmdlets en una sesión de Windows PowerShell mediante el uso de un módulo binario.

> [!NOTE]
> Pueden incluir los miembros de los módulos de cmdlets, proveedores, funciones, variables, alias y mucho más. Complementos solo pueden contener cmdlets y proveedores.

## <a name="how-to-load-cmdlets-using-a-module"></a>Cómo cargar mediante un módulo de cmdlets

1. Cree una carpeta de módulo que tiene el mismo nombre que el archivo de ensamblado en el que se implementan los cmdlets. En este procedimiento, se crea la carpeta del módulo en el `system32` carpeta.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. Asegúrese de que el `PSModulePath` variable de entorno incluye la ruta de acceso a la nueva carpeta de módulo. De forma predeterminada, la carpeta del sistema se ha agregado a la `PSModulePath` variable de entorno.

3. Copie el ensamblado de cmdlet en la carpeta del módulo.

4. Ejecute el siguiente comando para agregar los cmdlets a la sesión:

   `import-module [Module_Name]`

   Este procedimiento puede usarse para probar sus cmdlets. Agrega todos los cmdlets en el ensamblado a la sesión. Para obtener más información acerca de los módulos, vea los distintos tipos de módulos, las distintas formas de cargar los módulos y cómo restringir los elementos de un módulo que se exportan, [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Instalación de módulos](../module/installing-a-powershell-module.md)