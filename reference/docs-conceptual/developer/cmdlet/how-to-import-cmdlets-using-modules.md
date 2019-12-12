---
title: Cómo importar cmdlets mediante módulos | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364464"
---
# <a name="how-to-import-cmdlets-using-modules"></a>Cómo importar cmdlets mediante módulos

En este artículo se describe cómo importar cmdlets en una sesión de PowerShell con un módulo binario.

> [!NOTE]
> Los miembros de los módulos pueden incluir cmdlets, proveedores, funciones, variables, alias y mucho más. Los complementos solo pueden contener cmdlets y proveedores.

## <a name="how-to-load-cmdlets-using-a-module"></a>Cómo cargar cmdlets mediante un módulo

1. Cree una carpeta de módulo que tenga el mismo nombre que el archivo de ensamblado en el que se implementan los cmdlets. En este procedimiento, se crea la carpeta del módulo en la carpeta Windows `system32`.

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. Asegúrese de que la variable de entorno `PSModulePath` incluya la ruta de acceso a la nueva carpeta del módulo. De forma predeterminada, la carpeta del sistema ya está agregada a la variable de entorno `PSModulePath`. Para ver el `PSModulePath`, escriba: `$env:PSModulePath`.

1. Copie el ensamblado del cmdlet en la carpeta del módulo.

1. Agregue un archivo de manifiesto del módulo (`.psd1`) en la carpeta raíz del módulo. PowerShell usa el manifiesto del módulo para importar el módulo. Para obtener más información, vea [Cómo escribir un manifiesto del módulo de PowerShell](../module/how-to-write-a-powershell-module-manifest.md).

1. Ejecute el siguiente comando para agregar los cmdlets a la sesión:

   `Import-Module [Module_Name]`

   Este procedimiento se puede usar para probar los cmdlets. Agrega todos los cmdlets del ensamblado a la sesión. Para obtener más información sobre los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).

## <a name="see-also"></a>Consulta también

[Cómo escribir un manifiesto de módulo de PowerShell](../module/how-to-write-a-powershell-module-manifest.md)

[Importar un módulo de PowerShell](../module/importing-a-powershell-module.md)

[Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[Instalación de módulos](../module/installing-a-powershell-module.md)

[Modificación de la ruta de instalación de PSModulePath](../module/modifying-the-psmodulepath-installation-path.md)

[Escribir un cmdlet de Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
