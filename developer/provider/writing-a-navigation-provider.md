---
title: Escribir un proveedor de navegación | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: a789b392bddd344ad583c93a1a55302329df9917
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863541"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="d18a5-102">Escritura de un proveedor de navegación</span><span class="sxs-lookup"><span data-stu-id="d18a5-102">Writing a navigation provider</span></span>

<span data-ttu-id="d18a5-103">En este tema se describe cómo se implementan los métodos de un proveedor de Windows PowerShell que admiten los contenedores anidados (almacenes de datos de varios niveles), mover elementos y rutas de acceso relativas.</span><span class="sxs-lookup"><span data-stu-id="d18a5-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="d18a5-104">Un proveedor de navegación debe derivar de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="d18a5-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="d18a5-105">El proveedor en los ejemplos de este tema usa una base de datos de Access como su almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="d18a5-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="d18a5-106">Hay varios métodos y clases auxiliares que se usan para interactuar con la base de datos.</span><span class="sxs-lookup"><span data-stu-id="d18a5-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="d18a5-107">Para obtener el ejemplo completo que incluye los métodos auxiliares, consulte [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="d18a5-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="d18a5-108">Para obtener más información acerca de los proveedores de Windows PowerShell, consulte [Introducción al proveedor de Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d18a5-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="d18a5-109">Implementación de métodos de navegación</span><span class="sxs-lookup"><span data-stu-id="d18a5-109">Implementing navigation methods</span></span>

<span data-ttu-id="d18a5-110">El [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase implementa métodos que admiten los contenedores anidados, rutas de acceso relativas y movimiento de los elementos.</span><span class="sxs-lookup"><span data-stu-id="d18a5-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="d18a5-111">Para obtener una lista completa de estos métodos, consulte [NavigationCmdletProvider métodos](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="d18a5-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="d18a5-112">Este tema se basa en la información de [inicio rápido de proveedor de Windows PowerShell](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="d18a5-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="d18a5-113">Este tema no tratan los aspectos básicos de cómo configurar un proyecto de proveedor, o cómo se implementan los métodos heredados de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase que crear y quitar unidades.</span><span class="sxs-lookup"><span data-stu-id="d18a5-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="d18a5-114">En este tema también no cubre cómo implementar los métodos expuestos por el [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) o [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clases.</span><span class="sxs-lookup"><span data-stu-id="d18a5-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="d18a5-115">Para obtener un ejemplo que muestra cómo implementar el elemento cmdlets, consulte [escribir un proveedor de elementos](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d18a5-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="d18a5-116">Para obtener un ejemplo que muestra cómo implementar el contenedor cmdlets, consulte [escribir un proveedor de contenedor](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d18a5-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="d18a5-117">Declarar la clase de proveedor</span><span class="sxs-lookup"><span data-stu-id="d18a5-117">Declaring the provider class</span></span>

<span data-ttu-id="d18a5-118">Declare el proveedor que derive de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) y se decora con el [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="d18a5-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="d18a5-119">Implementar IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="d18a5-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="d18a5-120">El [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) método comprueba si el elemento situado en la ruta de acceso especificada es un contenedor.</span><span class="sxs-lookup"><span data-stu-id="d18a5-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a><span data-ttu-id="d18a5-121">Implementar GetChildName</span><span class="sxs-lookup"><span data-stu-id="d18a5-121">Implementing GetChildName</span></span>

<span data-ttu-id="d18a5-122">El [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) método obtiene la propiedad name del elemento secundario en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="d18a5-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="d18a5-123">Si el elemento situado en la ruta de acceso especificada no es un elemento secundario de un contenedor, este método debe devolver la ruta de acceso.</span><span class="sxs-lookup"><span data-stu-id="d18a5-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a><span data-ttu-id="d18a5-124">Implementar GetParentPath</span><span class="sxs-lookup"><span data-stu-id="d18a5-124">Implementing GetParentPath</span></span>

<span data-ttu-id="d18a5-125">El [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) método obtiene la ruta de acceso del elemento primario del elemento en la ruta de acceso especificada.</span><span class="sxs-lookup"><span data-stu-id="d18a5-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="d18a5-126">Si el elemento situado en la ruta de acceso especificada es la raíz del almacén de datos (por lo que no tiene ningún elemento primario), este método debe devolver la ruta de acceso raíz.</span><span class="sxs-lookup"><span data-stu-id="d18a5-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a><span data-ttu-id="d18a5-127">Implementar MakePath</span><span class="sxs-lookup"><span data-stu-id="d18a5-127">Implementing MakePath</span></span>

<span data-ttu-id="d18a5-128">El [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método combina una ruta de acceso del elemento primario especificado y una ruta de acceso secundaria especificada para crear una ruta de acceso interna del proveedor (para tipos de información acerca de la ruta de acceso que los proveedores pueden admitir, vea [Introducción al proveedor de Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d18a5-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="d18a5-129">El motor de PowerShell llama a este método cuando un usuario llama a la [Microsoft.Powershell.Commands.Join-Path](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d18a5-129">The PowerShell engine calls this method when a user calls the [Microsoft.Powershell.Commands.Join-Path](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.</span></span>

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="d18a5-130">Implementar NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="d18a5-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="d18a5-131">El [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) método toma `path` y `basepath` parámetros y devuelve una ruta de acceso normalizada que es equivalente a la `path`parámetro y con respecto a la `basepath` parámetro.</span><span class="sxs-lookup"><span data-stu-id="d18a5-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a><span data-ttu-id="d18a5-132">Implementar MoveItem</span><span class="sxs-lookup"><span data-stu-id="d18a5-132">Implementing MoveItem</span></span>

<span data-ttu-id="d18a5-133">El [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método mueve un elemento de la ruta de acceso especificada para la ruta de acceso de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="d18a5-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="d18a5-134">El motor de PowerShell llama a este método cuando un usuario llama a la [Microsoft.Powershell.Commands.Move elemento](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d18a5-134">The PowerShell engine calls this method when a user calls the [Microsoft.Powershell.Commands.Move-Item](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.</span></span>

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a><span data-ttu-id="d18a5-135">Véase también</span><span class="sxs-lookup"><span data-stu-id="d18a5-135">See Also</span></span>

[<span data-ttu-id="d18a5-136">Escribir un proveedor de contenedor</span><span class="sxs-lookup"><span data-stu-id="d18a5-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="d18a5-137">Información general sobre el proveedor de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="d18a5-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)