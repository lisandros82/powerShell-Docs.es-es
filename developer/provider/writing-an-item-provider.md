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
ms.openlocfilehash: 9285a2f0e673de8b86084157423512bdeeda109d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058203"
---
# <a name="writing-an-item-provider"></a>Escritura de un proveedor de elementos

En este tema se describe cómo se implementan los métodos de un proveedor de Windows PowerShell que obtener acceso y manipulan los elementos en el almacén de datos. Para poder tener acceso a elementos, un proveedor debe derivar de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase.

El proveedor en los ejemplos de este tema usa una base de datos de Access como su almacén de datos. Hay varios métodos y clases auxiliares que se usan para interactuar con la base de datos. Para obtener el ejemplo completo que incluye los métodos auxiliares, consulte [AccessDBProviderSample03](./accessdbprovidersample03.md)

Para obtener más información acerca de los proveedores de Windows PowerShell, consulte [Introducción al proveedor de Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementación de métodos de elemento

El [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase expone varios métodos que pueden utilizarse para tener acceso y manipular los elementos de un almacén de datos. Para obtener una lista completa de estos métodos, consulte [ItemCmdletProvider métodos](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx). En este ejemplo, implementaremos cuatro de estos métodos. [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Obtiene un elemento en una ruta de acceso especificada. [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) establece el valor del elemento especificado. [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) comprueba si existe un elemento en la ruta especificada. [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) comprueba una ruta de acceso para ver si se asigna a una ubicación en el almacén de datos.

> [!NOTE]
> Este tema se basa en la información de [inicio rápido de proveedor de Windows PowerShell](./windows-powershell-provider-quickstart.md). Este tema no tratan los aspectos básicos de cómo configurar un proyecto de proveedor, o cómo se implementan los métodos heredados de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase que crear y quitar unidades.

### <a name="declaring-the-provider-class"></a>Declarar la clase de proveedor

Declare el proveedor que derive de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) y se decora con el [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implementar GetItem

El [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) llama el motor de PowerShell cuando un usuario llama a la [Microsoft.PowerShell.Commands.Get elemento](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet en el proveedor. El método devuelve el elemento situado en la ruta de acceso especificada. En el ejemplo de base de datos de Access, el método comprueba si el elemento es la unidad, una tabla en la base de datos o una fila en la base de datos. El método envía el elemento para el motor de PowerShell mediante una llamada a la [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.

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

### <a name="implementing-setitem"></a>Implementar SetItem

El [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método se llama por el motor de PowerShell llama cuando un usuario llama a la [Microsoft.PowerShell.Commands.Set elemento](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet . Establece el valor del elemento en la ruta especificada.

En el ejemplo de base de datos de acceso, tiene sentido para establecer el valor de un elemento únicamente si dicho elemento es una fila, por lo que produce el método [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) cuando el elemento no es una fila.

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

### <a name="implementing-itemexists"></a>Implementar ItemExists

El [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método se llama el motor de PowerShell cuando un usuario llama a la [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet. El método determina si hay un elemento en la ruta de acceso especificada. Si el elemento existe, el método lo pasa al motor de PowerShell mediante una llamada a [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

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

### <a name="implementing-isvalidpath"></a>Implementar IsValidPath

El [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método comprueba si la ruta de acceso especificada es sintácticamente válido para el proveedor actual. No comprueba si existe un elemento en la ruta de acceso.

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

Un proveedor de reales típico es capaz de admitir los elementos que contienen otros elementos y de mover elementos desde una ruta de acceso a otro dentro de la unidad. Para obtener un ejemplo de un proveedor que admita contenedores, consulte [escribir un proveedor de contenedor](./writing-a-container-provider.md). Para obtener un ejemplo de un proveedor que admite el movimiento de los elementos, vea [escribir un proveedor de navegación](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Véase también

[Escribir un proveedor de contenedor](./writing-a-container-provider.md)

[Escribir un proveedor de navegación](./writing-a-navigation-provider.md)

[Información general sobre el proveedor de PowerShell de Windows](./windows-powershell-provider-overview.md)