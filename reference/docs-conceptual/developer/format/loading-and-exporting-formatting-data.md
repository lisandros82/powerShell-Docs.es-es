---
title: Cargar y exportar datos de formato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365124"
---
# <a name="loading-and-exporting-formatting-data"></a>Carga y exportación de datos de formato

Una vez que haya creado el archivo de formato, debe actualizar los datos de formato de la sesión cargando los archivos en la sesión actual. (Los archivos de formato proporcionados por Windows PowerShell se cargan mediante complementos que se registran cuando se abre la sesión actual). Una vez que se actualizan los datos de formato de la sesión actual, Windows PowerShell usa esos datos para mostrar los objetos .NET asociados a las vistas definidas en los archivos de formato cargados. No hay ningún límite en cuanto al número de archivos de formato que se pueden cargar en la sesión actual. Además de actualizar los datos de formato, puede volver a exportar los datos de formato de la sesión actual a un archivo de formato.

## <a name="loading-format-data"></a>Cargando datos de formato

Los archivos de formato se pueden cargar en la sesión actual mediante los métodos siguientes:

- Puede importar el archivo de formato a la sesión actual desde la línea de comandos. Use el cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) como se describe en el procedimiento siguiente.

- Puede crear un manifiesto de módulo que haga referencia al archivo de formato. Los módulos le permiten empaquetar los archivos de formato para su distribución. Use el cmdlet [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) para crear el manifiesto y el cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) para cargar el módulo en la sesión actual. Para obtener más información sobre los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Puede crear un complemento que haga referencia al archivo de formato. Use [System. Management. Automation. PSSnapIn. Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) para hacer referencia a los archivos de formato. Se recomienda encarecidamente usar módulos para empaquetar los cmdlets y los archivos de formato y tipos asociados para la distribución. Para obtener más información sobre los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Si va a invocar comandos mediante programación, puede Agregar una entrada de archivo de formato al estado de sesión inicial del espacio de ejecución en el que se ejecutan los comandos. Para obtener más información sobre el tipo de .NET que se usa para agregar el archivo de formato, vea [System. Management. Automation. espacios de Sessionstateformatentry? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) (clase).

Cuando se carga un archivo de formato, se agrega a una lista interna que Windows PowerShell usa para determinar la vista que se va a usar al mostrar objetos en la línea de comandos. Puede anteponer el archivo de formato al principio de la lista, o puede anexarlo al final de la lista. Saber dónde se agrega el archivo de formato a esta lista es importante si está cargando un archivo de formato que define una vista para un objeto que tiene una vista existente definida, como cuando desea cambiar la forma en que un objeto devuelto por un cmdlet de Windows PowerShell Core es  indica. Si está cargando un archivo de formato que define la única vista para un objeto, puede usar cualquiera de los métodos descritos anteriormente.  Si está cargando un archivo de formato que define otra vista para un objeto, debe usar el cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) y anteponer el archivo al principio de la lista.

## <a name="storing-your-formatting-file"></a>Almacenar el archivo de formato

No es necesario que los archivos de formato se almacenen en disco. Sin embargo, se recomienda encarecidamente que los almacene en la siguiente carpeta: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Cargar un archivo de formato mediante Import-FormatData

1. Almacene el archivo de formato en el disco.

2. Ejecute el cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) con uno de los siguientes comandos.

   Para agregar el archivo de formato al principio de la lista, use este comando. Use este comando si va a cambiar el modo en que se muestra un objeto.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Use este comando para agregar el archivo de formato al final de la lista.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Una vez que se ha agregado un archivo mediante el cmdlet [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) , no se puede quitar el archivo de la lista mientras la sesión está abierta. Debe cerrar la sesión para quitar el archivo de formato de la lista.

## <a name="exporting-format-data"></a>Exportar datos de formato

Insertar el cuerpo de la sección aquí.
