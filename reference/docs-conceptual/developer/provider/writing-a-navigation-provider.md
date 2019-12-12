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
ms.openlocfilehash: edb4d9944a527391983e068ddf07f4fac415c3f9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359874"
---
# <a name="writing-a-navigation-provider"></a>Escritura de un proveedor de navegación

En este tema se describe cómo implementar los métodos de un proveedor de Windows PowerShell que admiten contenedores anidados (almacenes de datos de varios niveles), mover elementos y rutas de acceso relativas. Un proveedor de navegación debe derivar de la clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

El proveedor de los ejemplos de este tema utiliza una base de datos de Access como almacén de datos. Hay varios métodos y clases auxiliares que se usan para interactuar con la base de datos. Para obtener el ejemplo completo que incluye los métodos auxiliares, vea [AccessDBProviderSample05](./accessdbprovidersample05.md).

Para obtener más información sobre los proveedores de Windows PowerShell, consulte [información general del proveedor de Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-navigation-methods"></a>Implementar métodos de navegación

La clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) implementa métodos que admiten contenedores anidados, rutas de acceso relativas y elementos móviles. Para obtener una lista completa de estos métodos, consulte [métodos de NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).

> [!NOTE]
> Este tema se basa en la información del [Inicio rápido del proveedor de Windows PowerShell](./windows-powershell-provider-quickstart.md). En este tema no se tratan los aspectos básicos de cómo configurar un proyecto de proveedor o cómo implementar los métodos heredados de la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) que crean y quitan unidades. En este tema tampoco se trata cómo implementar métodos expuestos por las clases [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) o [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Para ver un ejemplo en el que se muestra cómo implementar cmdlets de elementos, consulte [Writing a item Provider](./writing-an-item-provider.md). Para ver un ejemplo que muestra cómo implementar cmdlets de contenedor, consulte [escribir un proveedor de contenedores](./writing-a-container-provider.md).

### <a name="declaring-the-provider-class"></a>Declarar la clase de proveedor

Declare el proveedor para que derive de la clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) y decorarlo con [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a>Implementación de IsItemContainer

El método [System. Management. Automation. Provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) comprueba si el elemento de la ruta de acceso especificada es un contenedor.

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

### <a name="implementing-getchildname"></a>Implementación de GetChildName

El método [System. Management. Automation. Provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) obtiene la propiedad Name del elemento secundario en la ruta de acceso especificada. Si el elemento de la ruta de acceso especificada no es un elemento secundario de un contenedor, este método debe devolver la ruta de acceso.

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

### <a name="implementing-getparentpath"></a>Implementación de GetParentPath

El método [System. Management. Automation. Provider. Navigationcmdletprovider. GetParentPath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) obtiene la ruta de acceso del elemento primario del elemento en la ruta de acceso especificada. Si el elemento de la ruta de acceso especificada es la raíz del almacén de datos (por lo que no tiene ningún elemento primario), este método debe devolver la ruta de acceso raíz.

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

### <a name="implementing-makepath"></a>Implementación de MakePath

El método [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) combina una ruta de acceso primaria especificada y una ruta de acceso secundaria especificada para crear una ruta de acceso interna del proveedor (para obtener información sobre los tipos de ruta de acceso que los proveedores pueden admitir, consulte [información general del proveedor de Windows PowerShell](./windows-powershell-provider-overview.md). El motor de PowerShell llama a este método cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) .

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

### <a name="implementing-normalizerelativepath"></a>Implementación de NormalizeRelativePath

El método [System. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) toma `path` y `basepath` parámetros y devuelve una ruta de acceso normalizada equivalente al parámetro `path` y relativo al parámetro `basepath`.

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

### <a name="implementing-moveitem"></a>Implementación de MoveItem

El método [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) mueve un elemento de la ruta de acceso especificada a la ruta de acceso de destino especificada. El motor de PowerShell llama a este método cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) .

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

## <a name="see-also"></a>Véase también

[Escribir un proveedor de contenedores](./writing-a-container-provider.md)

[Información general del proveedor de Windows PowerShell](./windows-powershell-provider-overview.md)