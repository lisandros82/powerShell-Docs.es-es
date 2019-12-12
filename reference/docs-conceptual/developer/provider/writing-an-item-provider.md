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
# <a name="writing-an-item-provider"></a><span data-ttu-id="c2fc7-102">Escritura de un proveedor de elementos</span><span class="sxs-lookup"><span data-stu-id="c2fc7-102">Writing an item provider</span></span>

<span data-ttu-id="c2fc7-103">En este tema se describe cómo implementar los métodos de un proveedor de Windows PowerShell que tienen acceso a los elementos del almacén de datos y los manipulan.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="c2fc7-104">Para poder tener acceso a los elementos, un proveedor debe derivar de la clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="c2fc7-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="c2fc7-105">El proveedor de los ejemplos de este tema utiliza una base de datos de Access como almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="c2fc7-106">Hay varios métodos y clases auxiliares que se usan para interactuar con la base de datos.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="c2fc7-107">Para obtener el ejemplo completo que incluye los métodos auxiliares, vea [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="c2fc7-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="c2fc7-108">Para obtener más información sobre los proveedores de Windows PowerShell, consulte [información general del proveedor de Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c2fc7-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="c2fc7-109">Implementar métodos de elemento</span><span class="sxs-lookup"><span data-stu-id="c2fc7-109">Implementing item methods</span></span>

<span data-ttu-id="c2fc7-110">La clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) expone varios métodos que se pueden usar para obtener acceso a los elementos de un almacén de datos y manipularlos.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="c2fc7-111">Para obtener una lista completa de estos métodos, consulte [métodos de ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods).</span><span class="sxs-lookup"><span data-stu-id="c2fc7-111">For a complete list of these methods, see [ItemCmdletProvider Methods](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods).</span></span> <span data-ttu-id="c2fc7-112">En este ejemplo, se implementarán cuatro de estos métodos.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="c2fc7-113">[System. Management. Automation. Provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) obtiene un elemento en una ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="c2fc7-114">[System. Management. Automation. Provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) establece el valor del elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="c2fc7-115">[System. Management. Automation. Provider. Itemcmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) comprueba si existe un elemento en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="c2fc7-116">[System. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) comprueba una ruta de acceso para ver si se asigna a una ubicación en el almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="c2fc7-117">Este tema se basa en la información del [Inicio rápido del proveedor de Windows PowerShell](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="c2fc7-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="c2fc7-118">En este tema no se tratan los aspectos básicos de cómo configurar un proyecto de proveedor o cómo implementar los métodos heredados de la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) que crean y quitan unidades.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="c2fc7-119">Declarar la clase de proveedor</span><span class="sxs-lookup"><span data-stu-id="c2fc7-119">Declaring the provider class</span></span>

<span data-ttu-id="c2fc7-120">Declare el proveedor para que derive de la clase [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) y decorarlo con [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="c2fc7-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="c2fc7-121">Implementar GetItem</span><span class="sxs-lookup"><span data-stu-id="c2fc7-121">Implementing GetItem</span></span>

<span data-ttu-id="c2fc7-122">El motor de PowerShell llama a [System. Management. Automation. Provider. Itemcmdletprovider. GetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) en el proveedor.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) cmdlet on your provider.</span></span> <span data-ttu-id="c2fc7-123">El método devuelve el elemento en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="c2fc7-124">En el ejemplo de base de datos de Access, el método comprueba si el elemento es la propia unidad, una tabla de la base de datos o una fila de la base de datos.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="c2fc7-125">El método envía el elemento al motor de PowerShell llamando al método [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .</span><span class="sxs-lookup"><span data-stu-id="c2fc7-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="c2fc7-126">Implementación de SetItem</span><span class="sxs-lookup"><span data-stu-id="c2fc7-126">Implementing SetItem</span></span>

<span data-ttu-id="c2fc7-127">El método [System. Management. Automation. Provider. Itemcmdletprovider. SetItem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) lo llama el motor de PowerShell llama a cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="c2fc7-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) cmdlet.</span></span> <span data-ttu-id="c2fc7-128">Establece el valor del elemento en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="c2fc7-129">En el ejemplo de base de datos de Access, tiene sentido establecer el valor de un elemento solo si ese elemento es una fila, por lo que el método produce [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) cuando el elemento no es una fila.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="c2fc7-130">Implementación de ItemExists</span><span class="sxs-lookup"><span data-stu-id="c2fc7-130">Implementing ItemExists</span></span>

<span data-ttu-id="c2fc7-131">El método [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) lo llama el motor de PowerShell cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) .</span><span class="sxs-lookup"><span data-stu-id="c2fc7-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) cmdlet.</span></span> <span data-ttu-id="c2fc7-132">El método determina si hay un elemento en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="c2fc7-133">Si el elemento existe, el método lo devuelve al motor de PowerShell mediante una llamada a [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="c2fc7-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="c2fc7-134">Implementación de IsValidPath</span><span class="sxs-lookup"><span data-stu-id="c2fc7-134">Implementing IsValidPath</span></span>

<span data-ttu-id="c2fc7-135">El método [System. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) comprueba si la ruta de acceso especificada es sintácticamente válida para el proveedor actual.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="c2fc7-136">No comprueba si existe un elemento en la ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="c2fc7-137">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="c2fc7-137">Next steps</span></span>

<span data-ttu-id="c2fc7-138">Un proveedor típico del mundo real es capaz de admitir elementos que contienen otros elementos y de mover elementos de una ruta de acceso a otra dentro de la unidad.</span><span class="sxs-lookup"><span data-stu-id="c2fc7-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="c2fc7-139">Para obtener un ejemplo de un proveedor que admite contenedores, vea [escribir un proveedor de contenedores](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c2fc7-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="c2fc7-140">Para obtener un ejemplo de un proveedor que admite mover elementos, consulte [escribir un proveedor de navegación](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="c2fc7-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2fc7-141">Véase también</span><span class="sxs-lookup"><span data-stu-id="c2fc7-141">See Also</span></span>

[<span data-ttu-id="c2fc7-142">Escribir un proveedor de contenedores</span><span class="sxs-lookup"><span data-stu-id="c2fc7-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="c2fc7-143">Escribir un proveedor de navegación</span><span class="sxs-lookup"><span data-stu-id="c2fc7-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="c2fc7-144">Información general del proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2fc7-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
