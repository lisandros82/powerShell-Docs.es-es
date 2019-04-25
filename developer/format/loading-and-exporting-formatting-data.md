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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065213"
---
# <a name="loading-and-exporting-formatting-data"></a>Carga y exportación de datos de formato

Una vez haya creado el archivo de formato, deberá actualizar los datos de formato de la sesión al cargar los archivos en la sesión actual. (Los archivos de formato proporcionados por Windows PowerShell se cargan los complementos que se registran cuando se abre la sesión actual). Una vez que se actualiza el formato de datos de la sesión actual, Windows PowerShell usa esos datos para mostrar los objetos de .NET asociados con las vistas definidas en los archivos de formato de cargados. No hay ningún límite al número de archivos de formato que pueden cargar en la sesión actual. Además de actualizar los datos de formato, puede exportar los datos de formato en la sesión actual a un archivo de formato.

## <a name="loading-format-data"></a>Carga de datos de formato

Archivos de formato se pueden cargar en la sesión actual mediante los métodos siguientes:

- Puede importar el archivo de formato en la sesión actual de la línea de comandos. Use la [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet tal y como se describe en el siguiente procedimiento.

- Puede crear un manifiesto de módulo que hace referencia a su archivo de formato. Los módulos le permiten empaquetar archivos para la distribución de formato. Use la [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) para crear el manifiesto y el [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet para cargar el módulo en la sesión actual. Para obtener más información acerca de los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Puede crear un complemento que hace referencia a su archivo de formato. Use la [System.Management.Automation.PSSnapIn.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) para hacer referencia a los archivos de formato. Se recomienda encarecidamente usar módulos de cmdlets de paquete y cualquier formato asociadas y archivos de tipos para la distribución. Para obtener más información acerca de los módulos, consulte [escribir un módulo de Windows PowerShell](../module/writing-a-windows-powershell-module.md).

- Si los comandos que se están invocando mediante programación, puede agregar una entrada del archivo de formato para el estado de sesión inicial del espacio de ejecución que se ejecutan los comandos. ¿Para obtener más información sobre el tipo de .NET que se usa para agregar el archivo de formato, vea el [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) clase.

Cuando se carga un archivo de formato, se agrega a una lista interna que usa Windows PowerShell para determinar qué vista se debe para usar al mostrar los objetos en la línea de comandos. Puede anteponer el archivo de formato para el principio de la lista, o se puede anexar al final de la lista. Es importante saber dónde se agrega el archivo de formato a esta lista si va a cargar el archivo de formato que define una vista para un objeto que tiene una vista existente definida, por ejemplo, cuando desee cambiar cómo un objeto devuelto por un cmdlet de Windows PowerShell core se  muestra. Si está cargando un archivo de formato que define la vista única de un objeto, puede usar cualquiera de los métodos descritos anteriormente.  Si está cargando un archivo de formato que define otra vista para un objeto, se debe utilizar el [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet y anteponer el archivo al principio de la lista.

## <a name="storing-your-formatting-file"></a>Almacenar el archivo de formato

No hay ningún requisito para los archivos de formato que se almacenan en el disco. Sin embargo, se recomienda almacenarlas en la siguiente carpeta: `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>Cargar un archivo de formato mediante Import-FormatData

1. Store su archivo de formato en el disco.

2. Ejecute el [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet mediante uno de los siguientes comandos.

   Para agregar su formato de archivo a la parte delantera de la lista de utilizar este comando. Use este comando si va a cambiar cómo se muestra un objeto.

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   Para agregar su formato de archivo al final de la lista de utilizar este comando.

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   Una vez haya agregado un archivo mediante el [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, no se puede quitar el archivo de la lista mientras la sesión está abierta. Debe cerrar la sesión para quitar el archivo de formato de la lista.

## <a name="exporting-format-data"></a>Exportación de datos de formato

Inserte aquí el cuerpo de sección.
