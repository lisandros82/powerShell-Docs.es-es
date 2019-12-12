---
title: Escribir un proveedor de elementos | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 12d2cb8c40c9fd6278bb964a6259d03167536195
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359884"
---
# <a name="writing-an-item-provider"></a>Escritura de un proveedor de elementos

En este tema se describe cómo implementar los métodos de un proveedor de Windows PowerShell que tienen acceso a los elementos del almacén de datos y los manipulan. Para poder tener acceso a los elementos, un proveedor debe derivar de la clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

El proveedor de los ejemplos de este tema utiliza una base de datos de Access como almacén de datos. Hay varios métodos y clases auxiliares que se usan para interactuar con la base de datos. Para obtener el ejemplo completo que incluye los métodos auxiliares, vea [AccessDBProviderSample03](./accessdbprovidersample03.md)

Para obtener más información sobre los proveedores de Windows PowerShell, consulte [información general del proveedor de Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementar métodos de elemento

La clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) expone varios métodos que se pueden usar para obtener acceso a los elementos de un almacén de datos y manipularlos. Para obtener una lista completa de estos métodos, consulte [métodos de ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods). En este ejemplo, se implementarán cuatro de estos métodos. [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) obtiene un elemento en una ruta de acceso especificada. [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) establece el valor del elemento especificado. [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) comprueba si existe un elemento en la ruta de acceso especificada. [System. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) comprueba una ruta de acceso para ver si se asigna a una ubicación en el almacén de datos.

> [!NOTE]
> Este tema se basa en la información del [Inicio rápido del proveedor de Windows PowerShell](./windows-powershell-provider-quickstart.md). En este tema no se tratan los aspectos básicos de cómo configurar un proyecto de proveedor o cómo implementar los métodos heredados de la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) que crean y quitan unidades.

### <a name="declaring-the-provider-class"></a>Declarar la clase de proveedor

Declare el proveedor para que derive de la clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) y decorarlo con [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implementar GetItem

El motor de PowerShell llama a [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) en el proveedor. El método devuelve el elemento en la ruta de acceso especificada. En el ejemplo de base de datos de Access, el método comprueba si el elemento es la propia unidad, una tabla de la base de datos o una fila de la base de datos. El método envía el elemento al motor de PowerShell llamando al método [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>Implementación de SetItem

El método [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) lo llama el motor de PowerShell llama a cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) . Establece el valor del elemento en la ruta de acceso especificada.

En el ejemplo de base de datos de Access, tiene sentido establecer el valor de un elemento solo si ese elemento es una fila, por lo que el método produce [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) cuando el elemento no es una fila.

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>Implementación de ItemExists

El método [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) lo llama el motor de PowerShell cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) . El método determina si hay un elemento en la ruta de acceso especificada. Si el elemento existe, el método lo devuelve al motor de PowerShell mediante una llamada a [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>Implementación de IsValidPath

El método [System. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) comprueba si la ruta de acceso especificada es sintácticamente válida para el proveedor actual. No comprueba si existe un elemento en la ruta de acceso.

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>Pasos siguientes

Un proveedor típico del mundo real es capaz de admitir elementos que contienen otros elementos y de mover elementos de una ruta de acceso a otra dentro de la unidad. Para obtener un ejemplo de un proveedor que admite contenedores, vea [escribir un proveedor de contenedores](./writing-a-container-provider.md). Para obtener un ejemplo de un proveedor que admite mover elementos, consulte [escribir un proveedor de navegación](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Véase también

[Escribir un proveedor de contenedores](./writing-a-container-provider.md)

[Escribir un proveedor de navegación](./writing-a-navigation-provider.md)

[Información general del proveedor de Windows PowerShell](./windows-powershell-provider-overview.md)
