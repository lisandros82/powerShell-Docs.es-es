---
title: Escribir un proveedor de contenedores | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 524fd900-c0fe-4d13-87f2-14903a8fd5a4
caps.latest.revision: 5
ms.openlocfilehash: 48ab9102e8f1b17b3b533cc3b0aa1dacef0e2076
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366244"
---
# <a name="writing-a-container-provider"></a><span data-ttu-id="88353-102">Escritura de un proveedor de contenedores</span><span class="sxs-lookup"><span data-stu-id="88353-102">Writing a container provider</span></span>

<span data-ttu-id="88353-103">En este tema se describe cómo implementar los métodos de un proveedor de Windows PowerShell que admiten elementos que contienen otros elementos, como carpetas en el proveedor del sistema de archivos.</span><span class="sxs-lookup"><span data-stu-id="88353-103">This topic describes how to implement the methods of a Windows PowerShell provider that support items that contain other items, such as folders in the file system provider.</span></span> <span data-ttu-id="88353-104">Para poder admitir contenedores, un proveedor debe derivar de la clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="88353-104">To be able to support containers, a provider must derive from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

<span data-ttu-id="88353-105">El proveedor de los ejemplos de este tema utiliza una base de datos de Access como almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="88353-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="88353-106">Hay varios métodos y clases auxiliares que se usan para interactuar con la base de datos.</span><span class="sxs-lookup"><span data-stu-id="88353-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="88353-107">Para obtener el ejemplo completo que incluye los métodos auxiliares, vea [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="88353-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>

<span data-ttu-id="88353-108">Para obtener más información sobre los proveedores de Windows PowerShell, consulte [información general del proveedor de Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="88353-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-container-methods"></a><span data-ttu-id="88353-109">Implementar métodos de contenedor</span><span class="sxs-lookup"><span data-stu-id="88353-109">Implementing container methods</span></span>

<span data-ttu-id="88353-110">La clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) implementa métodos que admiten contenedores y crean, copian y quitan elementos.</span><span class="sxs-lookup"><span data-stu-id="88353-110">The [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class implements methods that support containers, and create, copy, and remove items.</span></span> <span data-ttu-id="88353-111">Para obtener una lista completa de estos métodos, vea [System. Management. Automation. Provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider?view=pscore-6.2.0#methods).</span><span class="sxs-lookup"><span data-stu-id="88353-111">For a complete list of these methods, see [System.Management.Automation.Provider.ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider?view=pscore-6.2.0#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="88353-112">Este tema se basa en la información del [Inicio rápido del proveedor de Windows PowerShell](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="88353-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="88353-113">En este tema no se tratan los aspectos básicos de cómo configurar un proyecto de proveedor o cómo implementar los métodos heredados de la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) que crean y quitan unidades.</span><span class="sxs-lookup"><span data-stu-id="88353-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="88353-114">En este tema tampoco se explica cómo implementar los métodos expuestos por la clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="88353-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="88353-115">Para ver un ejemplo en el que se muestra cómo implementar cmdlets de elementos, consulte [Writing a item Provider](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="88353-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="88353-116">Declarar la clase de proveedor</span><span class="sxs-lookup"><span data-stu-id="88353-116">Declaring the provider class</span></span>

<span data-ttu-id="88353-117">Declare el proveedor para que derive de la clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) y decorarlo con [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="88353-117">Declare the provider to derive from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
   {

   }
```

### <a name="implementing-getchilditems"></a><span data-ttu-id="88353-118">Implementación de GetChildItems</span><span class="sxs-lookup"><span data-stu-id="88353-118">Implementing GetChildItems</span></span>

<span data-ttu-id="88353-119">El motor de PowerShell llama al método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. GetChildItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.Getchilditemcommand) .</span><span class="sxs-lookup"><span data-stu-id="88353-119">The PowerShell engine calls the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method when a user calls the [Microsoft.PowerShell.Commands.GetChildItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.Getchilditemcommand) cmdlet.</span></span> <span data-ttu-id="88353-120">Este método obtiene los elementos que son elementos secundarios del elemento en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="88353-120">This method gets the items that are the children of the item at the specified path.</span></span>

<span data-ttu-id="88353-121">En el ejemplo de base de datos de Access, el comportamiento del método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) depende del tipo del elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="88353-121">In the Access database example, the behavior of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method depends on the type of the specified item.</span></span> <span data-ttu-id="88353-122">Si el elemento es la unidad, los elementos secundarios son tablas y el método devuelve el conjunto de tablas de la base de datos.</span><span class="sxs-lookup"><span data-stu-id="88353-122">If the item is the drive, then the children are tables, and the method returns the set of tables from the database.</span></span> <span data-ttu-id="88353-123">Si el elemento especificado es una tabla, los elementos secundarios son las filas de esa tabla.</span><span class="sxs-lookup"><span data-stu-id="88353-123">If the specified item is a table, then the children are the rows of that table.</span></span> <span data-ttu-id="88353-124">Si el elemento es una fila, no tiene elementos secundarios y el método solo devuelve esa fila.</span><span class="sxs-lookup"><span data-stu-id="88353-124">If the item is a row, then it  has no children, and the method returns that row only.</span></span> <span data-ttu-id="88353-125">El método [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) devuelve todos los elementos secundarios al motor de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="88353-125">All child items are sent back to the PowerShell engine by the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

```csharp
protected override void GetChildItems(string path, bool recurse)
       {
           // If path represented is a drive then the children in the path are
           // tables. Hence all tables in the drive represented will have to be
           // returned
           if (PathIsDrive(path))
           {
               foreach (DatabaseTableInfo table in GetTables())
               {
                   WriteItemObject(table, path, true);

                   // if the specified item exists and recurse has been set then
                   // all child items within it have to be obtained as well
                   if (ItemExists(path) && recurse)
                   {
                       GetChildItems(path + pathSeparator + table.Name, recurse);
                   }
               } // foreach (DatabaseTableInfo...
           } // if (PathIsDrive...
           else
           {
               // Get the table name, row number and type of path from the
               // path specified
               string tableName;
               int rowNumber;

               PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

               if (type == PathType.Table)
               {
                   // Obtain all the rows within the table
                   foreach (DatabaseRowInfo row in GetRows(tableName))
                   {
                       WriteItemObject(row, path + pathSeparator + row.RowNumber,
                               false);
                   } // foreach (DatabaseRowInfo...
               }
               else if (type == PathType.Row)
               {
                   // In this case the user has directly specified a row, hence
                   // just give that particular row
                   DatabaseRowInfo row = GetRow(tableName, rowNumber);
                   WriteItemObject(row, path + pathSeparator + row.RowNumber,
                               false);
               }
               else
               {
                   // In this case, the path specified is not valid
                   ThrowTerminatingInvalidPathException(path);
               }
           } // else
       }
```

### <a name="implementing-getchildnames"></a><span data-ttu-id="88353-126">Implementación de GetChildNames</span><span class="sxs-lookup"><span data-stu-id="88353-126">Implementing GetChildNames</span></span>

<span data-ttu-id="88353-127">El método [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) es similar al método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) , con la salvedad de que solo devuelve la propiedad Name de los elementos, y no los propios elementos.</span><span class="sxs-lookup"><span data-stu-id="88353-127">The [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method is similar to the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method, except that it returns only the name property of the items, and not the items themselves.</span></span>

```csharp
protected override void GetChildNames(string path,
                                     ReturnContainers returnContainers)
       {
           // If the path represented is a drive, then the child items are
           // tables. get the names of all the tables in the drive.
           if (PathIsDrive(path))
           {
               foreach (DatabaseTableInfo table in GetTables())
               {
                   WriteItemObject(table.Name, path, true);
               } // foreach (DatabaseTableInfo...
           } // if (PathIsDrive...
           else
           {
               // Get type, table name and row number from path specified
               string tableName;
               int rowNumber;

               PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

               if (type == PathType.Table)
               {
                   // Get all the rows in the table and then write out the
                   // row numbers.
                   foreach (DatabaseRowInfo row in GetRows(tableName))
                   {
                       WriteItemObject(row.RowNumber, path, false);
                   } // foreach (DatabaseRowInfo...
               }
               else if (type == PathType.Row)
               {
                   // In this case the user has directly specified a row, hence
                   // just give that particular row
                   DatabaseRowInfo row = GetRow(tableName, rowNumber);

                   WriteItemObject(row.RowNumber, path, false);
               }
               else
               {
                   ThrowTerminatingInvalidPathException(path);
               }
           } // else
       }
```

### <a name="implementing-newitem"></a><span data-ttu-id="88353-128">Implementar NewItem</span><span class="sxs-lookup"><span data-stu-id="88353-128">Implementing NewItem</span></span>

<span data-ttu-id="88353-129">El método [System. Management. Automation. Provider. Containercmdletprovider. newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) crea un nuevo elemento del tipo especificado en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="88353-129">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method creates a new item of the specified type at the specified path.</span></span> <span data-ttu-id="88353-130">El motor de PowerShell llama a este método cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. NewItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.newitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="88353-130">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.NewItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.newitemcommand) cmdlet.</span></span>

<span data-ttu-id="88353-131">En este ejemplo, el método implementa la lógica para determinar que la ruta de acceso y el tipo coinciden.</span><span class="sxs-lookup"><span data-stu-id="88353-131">In this example, the method implements logic to determine that the path and type match.</span></span> <span data-ttu-id="88353-132">Es decir, solo se puede crear una tabla directamente en la unidad (la base de datos) y solo se puede crear una fila en una tabla.</span><span class="sxs-lookup"><span data-stu-id="88353-132">That is, only a table can be created directly under the drive (the database), and only a row can be created under a table.</span></span> <span data-ttu-id="88353-133">Si la ruta de acceso y el tipo de elemento especificados no coinciden de esta manera, el método produce una excepción.</span><span class="sxs-lookup"><span data-stu-id="88353-133">If the specified path and item type don't match in this way, the method throws an exception.</span></span>

```csharp
protected override void NewItem(string path, string type,
                                   object newItemValue)
       {
           string tableName;
           int rowNumber;

           PathType pt = GetNamesFromPath(path, out tableName, out rowNumber);

           if (pt == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           // Check if type is either "table" or "row", if not throw an
           // exception
           if (!String.Equals(type, "table", StringComparison.OrdinalIgnoreCase)
               && !String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
           {
               WriteError(new ErrorRecord
                                 (new ArgumentException("Type must be either a table or row"),
                                     "CannotCreateSpecifiedObject",
                                        ErrorCategory.InvalidArgument,
                                             path
                                  )
                         );

               throw new ArgumentException("This provider can only create items of type \"table\" or \"row\"");
           }

           // Path type is the type of path of the container. So if a drive
           // is specified, then a table can be created under it and if a table
           // is specified, then a row can be created under it. For the sake of
           // completeness, if a row is specified, then if the row specified by
           // the path does not exist, a new row is created. However, the row
           // number may not match as the row numbers only get incremented based
           // on the number of rows

           if (PathIsDrive(path))
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   // Execute command using ODBC connection to create a table
                   try
                   {
                       // create the table using an sql statement
                       string newTableName = newItemValue.ToString();

                       if (!TableNameIsValid(newTableName))
                       {
                           return;
                       }
                       string sql = "create table " + newTableName
                                            + " (ID INT)";

                       // Create the table using the Odbc connection from the
                       // drive.
                       AccessDBPSDriveInfo di = this.PSDriveInfo as AccessDBPSDriveInfo;

                       if (di == null)
                       {
                           return;
                       }
                       OdbcConnection connection = di.Connection;

                       if (ShouldProcess(newTableName, "create"))
                       {
                           OdbcCommand cmd = new OdbcCommand(sql, connection);
                           cmd.ExecuteScalar();
                       }
                   }
                   catch (Exception ex)
                   {
                       WriteError(new ErrorRecord(ex, "CannotCreateSpecifiedTable",
                                 ErrorCategory.InvalidOperation, path)
                                 );
                   }
               } // if (String...
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   throw new
                       ArgumentException("A row cannot be created under a database, specify a path that represents a Table");
               }
           }// if (PathIsDrive...
           else
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   if (rowNumber < 0)
                   {
                       throw new
                           ArgumentException("A table cannot be created within another table, specify a path that represents a database");
                   }
                   else
                   {
                       throw new
                           ArgumentException("A table cannot be created inside a row, specify a path that represents a database");
                   }
               } //if (String.Equals....
               // if path specified is a row, create a new row
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   // The user is required to specify the values to be inserted
                   // into the table in a single string separated by commas
                   string value = newItemValue as string;

                   if (String.IsNullOrEmpty(value))
                   {
                       throw new
                           ArgumentException("Value argument must have comma separated values of each column in a row");
                   }
                   string[] rowValues = value.Split(',');

                   OdbcDataAdapter da = GetAdapterForTable(tableName);

                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   if (rowValues.Length != table.Columns.Count)
                   {
                       string message =
                            String.Format(CultureInfo.CurrentCulture,
                                            "The table has {0} columns and the value specified must have so many comma separated values",
                                                table.Columns.Count);

                       throw new ArgumentException(message);
                   }

                   if (!Force && (rowNumber >=0 && rowNumber < table.Rows.Count))
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                                        "The row {0} already exists. To create a new row specify row number as {1}, or specify path to a table, or use the -Force parameter",
                                                            rowNumber, table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   if (rowNumber > table.Rows.Count)
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                            "To create a new row specify row number as {0}, or specify path to a table",
                                                table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   // Create a new row and update the row with the input
                   // provided by the user
                   DataRow row = table.NewRow();
                   for (int i = 0; i < rowValues.Length; i++)
                   {
                       row[i] = rowValues[i];
                   }
                   table.Rows.Add(row);

                   if (ShouldProcess(tableName, "update rows"))
                   {
                       // Update the table from memory back to the data source
                       da.Update(ds, tableName);
                   }

               }// else if (String...
           }// else ...

       }
```

### <a name="implementing-copyitem"></a><span data-ttu-id="88353-134">Implementar CopyItem</span><span class="sxs-lookup"><span data-stu-id="88353-134">Implementing CopyItem</span></span>

<span data-ttu-id="88353-135">[System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) copia el elemento especificado en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="88353-135">The [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) copies the specified item to the specified path.</span></span> <span data-ttu-id="88353-136">El motor de PowerShell llama a este método cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. CopyItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.copyitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="88353-136">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.CopyItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.copyitemcommand) cmdlet.</span></span> <span data-ttu-id="88353-137">Este método también puede ser recursivo, copiando todos los elementos secundarios además del propio elemento.</span><span class="sxs-lookup"><span data-stu-id="88353-137">This method can also be recursive, copying all of the items children in addition to the item itself.</span></span>

<span data-ttu-id="88353-138">Del mismo modo que el método [System. Management. Automation. Provider. Containercmdletprovider. newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) , este método realiza la lógica para asegurarse de que el elemento especificado es del tipo correcto para la ruta de acceso en la que se copia.</span><span class="sxs-lookup"><span data-stu-id="88353-138">Similarly to the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method, this method performs logic to make sure that the specified item is of the correct type for the path to which it is being copied.</span></span> <span data-ttu-id="88353-139">Por ejemplo, si la ruta de acceso de destino es una tabla, el elemento que se va a copiar debe ser una fila.</span><span class="sxs-lookup"><span data-stu-id="88353-139">For example, if the destination path is a table, the item to be copied must be a row.</span></span>

```csharp
protected override void CopyItem(string path, string copyPath, bool recurse)
       {
           string tableName, copyTableName;
           int rowNumber, copyRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);
           PathType copyType = GetNamesFromPath(copyPath, out copyTableName, out copyRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(copyPath);
           }

           // Get the table and the table to copy to
           OdbcDataAdapter da = GetAdapterForTable(tableName);
           if (da == null)
           {
               return;
           }

           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           OdbcDataAdapter cda = GetAdapterForTable(copyTableName);
           if (cda == null)
           {
               return;
           }

           DataSet cds = GetDataSetForTable(cda, copyTableName);
           DataTable copyTable = GetDataTable(cds, copyTableName);

           // if source represents a table
           if (type == PathType.Table)
           {
               // if copyPath does not represent a table
               if (copyType != PathType.Table)
               {
                   ArgumentException e = new ArgumentException("Table can only be copied on to another table location");

                   WriteError(new ErrorRecord(e, "PathNotValid",
                       ErrorCategory.InvalidArgument, copyPath));

                   throw e;
               }

               // if table already exists then force parameter should be set
               // to force a copy
               if (!Force && GetTable(copyTableName) != null)
               {
                   throw new ArgumentException("Specified path already exists");
               }

               for (int i = 0; i < table.Rows.Count; i++)
               {
                   DataRow row = table.Rows[i];
                   DataRow copyRow = copyTable.NewRow();

                   copyRow.ItemArray = row.ItemArray;
                   copyTable.Rows.Add(copyRow);
               }
           } // if (type == ...
           // if source represents a row
           else
           {
               if (copyType == PathType.Row)
               {
                   if (!Force && (copyRowNumber < copyTable.Rows.Count))
                   {
                       throw new ArgumentException("Specified path already exists.");
                   }

                   DataRow row = table.Rows[rowNumber];
                   DataRow copyRow = null;

                   if (copyRowNumber < copyTable.Rows.Count)
                   {
                       // copy to an existing row
                       copyRow = copyTable.Rows[copyRowNumber];
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                   }
                   else if (copyRowNumber == copyTable.Rows.Count)
                   {
                       // copy to the next row in the table that will
                       // be created
                       copyRow = copyTable.NewRow();
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                       copyTable.Rows.Add(copyRow);
                   }
                   else
                   {
                       // attempting to copy to a nonexistent row or a row
                       // that cannot be created now - throw an exception
                       string message = String.Format(CultureInfo.CurrentCulture,
                                             "The item cannot be specified to the copied row. Specify row number as {0}, or specify a path to the table.",
                                                    table.Rows.Count);

                       throw new ArgumentException(message);
                   }
               }
               else
               {
                   // destination path specified represents a table,
                   // create a new row and copy the item
                   DataRow copyRow = copyTable.NewRow();
                   copyRow.ItemArray = table.Rows[rowNumber].ItemArray;
                   copyRow[0] = GetNextID(copyTable);
                   copyTable.Rows.Add(copyRow);
               }
           }

           if (ShouldProcess(copyTableName, "CopyItems"))
           {
               cda.Update(cds, copyTableName);
           }

       } //CopyItem
```

### <a name="implementing-removeitem"></a><span data-ttu-id="88353-140">Implementar RemoveItem</span><span class="sxs-lookup"><span data-stu-id="88353-140">Implementing RemoveItem</span></span>

<span data-ttu-id="88353-141">El método [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) quita el elemento en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="88353-141">The [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method removes the item at the specified path.</span></span> <span data-ttu-id="88353-142">El motor de PowerShell llama a este método cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. RemoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.removeitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="88353-142">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.RemoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.removeitemcommand) cmdlet.</span></span>

```csharp
protected override void RemoveItem(string path, bool recurse)
       {
           string tableName;
           int rowNumber = 0;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               // if recurse flag has been specified, delete all the rows as well
               if (recurse)
               {
                   OdbcDataAdapter da = GetAdapterForTable(tableName);
                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   for (int i = 0; i < table.Rows.Count; i++)
                   {
                       table.Rows[i].Delete();
                   }

                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       da.Update(ds, tableName);
                       RemoveTable(tableName);
                   }
               }//if (recurse...
               else
               {
                   // Remove the table
                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       RemoveTable(tableName);
                   }
               }
           }
           else if (type == PathType.Row)
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               table.Rows[rowNumber].Delete();

               if (ShouldProcess(path, "RemoveItem"))
               {
                   da.Update(ds, tableName);
               }
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

## <a name="next-steps"></a><span data-ttu-id="88353-143">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="88353-143">Next steps</span></span>

<span data-ttu-id="88353-144">Un proveedor típico del mundo real es capaz de mover elementos de una ruta de acceso a otra dentro de la unidad.</span><span class="sxs-lookup"><span data-stu-id="88353-144">A typical real-world provider is capable of moving items from one path to another within the drive.</span></span> <span data-ttu-id="88353-145">Para obtener un ejemplo de un proveedor que admite mover elementos, consulte [escribir un proveedor de navegación](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="88353-145">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88353-146">Véase también</span><span class="sxs-lookup"><span data-stu-id="88353-146">See Also</span></span>

[<span data-ttu-id="88353-147">Escribir un proveedor de navegación</span><span class="sxs-lookup"><span data-stu-id="88353-147">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="88353-148">Información general del proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="88353-148">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
