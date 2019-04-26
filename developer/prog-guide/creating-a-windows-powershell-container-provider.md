---
title: Creación de un proveedor de contenedores de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: 33effed9a96cf1b9ee5f1a50b60a1937526db9d1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081910"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Creación de un proveedor de contenedores de Windows PowerShell

Este tema describe cómo crear un proveedor de Windows PowerShell que puede trabajar en almacenes de datos de varias capas. Para este tipo de almacén de datos, el nivel superior de la tienda contiene los elementos raíz y cada nivel posterior se conoce como un nodo de elementos secundarios. Al permitir al usuario que funcionan en los siguientes nodos secundarios, un usuario puede interactuar de forma jerárquica a través del almacén de datos.

Los proveedores que pueden trabajar en los almacenes de datos de varios niveles se conocen como proveedores de contenedor de Windows PowerShell. Sin embargo, tenga en cuenta que un proveedor de contenedores de Windows PowerShell puede usarse solo cuando hay un contenedor (no hay contenedores anidados) con los elementos en ella. Si no hay contenedores anidados, a continuación, debe implementar un proveedor de navegación de Windows PowerShell. Para obtener más información sobre la implementación de proveedor de navegación de Windows PowerShell, consulte [creación de un proveedor de navegación de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> Puede descargar el C# (AccessDBSampleProvider04.cs) de archivo de código fuente para este proveedor mediante el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components. Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.
>
> Para obtener más información acerca de otras implementaciones del proveedor de Windows PowerShell, consulte [diseñar su proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

El proveedor de contenedores de Windows PowerShell que se describe aquí, define la base de datos como su contenedor único, con las tablas y filas de la base de datos que se definen como elementos del contenedor.

> [!CAUTION]
> Tenga en cuenta que este diseño considera una base de datos que tiene un campo con el identificador de nombre y que el tipo del campo es LongInteger.

Esta es una lista de las secciones de este tema. Si no está familiarizado con la escritura de un proveedor de contenedores de Windows PowerShell, lea esta información en el orden en que aparece. Sin embargo, si está familiarizado con la escritura de un proveedor de contenedores de Windows PowerShell, vaya directamente a la información que necesita.

- [Definir una clase de proveedor de contenedor de Windows PowerShell](#Defining-a-Windows-PowerShell-Container-Provider-Class)

- [Definir la funcionalidad de Base](#defining-base-functionality)

- [Recuperar elementos secundarios](#Retrieving-Child-Items)

- [Asociar los parámetros dinámicos a la `Get-ChildItem` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet)

- [Al recuperar los nombres de elementos secundarios](#Retrieving-Child-Item-Names)

- [Asociar los parámetros dinámicos a la `Get-ChildItem` Cmdlet (nombre)](#Attaching-Dynamic-Parameters-to-the-Get-ChildItem-Cmdlet-(Name))

- [Cambiar nombre de elementos](#Renaming-Items)

- [Asociar los parámetros dinámicos a la `Rename-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Rename-Item-Cmdlet)

- [Crear nuevos elementos](#Creating-New-Items)

- [Asociar los parámetros dinámicos a la `New-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-New-Item-Cmdlet)

- [Quitar elementos de un](#Removing-Items)

- [Asociar los parámetros dinámicos a la `Remove-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Remove-Item-Cmdlet)

- [Consulta de elementos secundarios](#Querying-for-Child-Items)

- [Copiar elementos](#Copying-Items)

- [Asociar los parámetros dinámicos a la `Copy-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Copy-Item-Cmdlet)

- [Ejemplo de código](#Code-Sample)

- [Creación del proveedor de Windows PowerShell](#Building-the-Windows-PowerShell-Provider)

- [Probar el proveedor de Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-a-windows-powershell-container-provider-class"></a>Definir una clase de proveedor de contenedor de Windows PowerShell

Un proveedor de contenedores de Windows PowerShell debe definir una clase .NET que se deriva de la [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase base. Esta es la definición de clase para el proveedor de contenedores de Windows PowerShell descrito en esta sección.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Tenga en cuenta que en esta definición, de la clase el [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo incluye dos parámetros. El primer parámetro especifica un nombre descriptivo para el proveedor que está usando Windows PowerShell. El segundo parámetro especifica las capacidades específicas de Windows PowerShell que expone el proveedor para el tiempo de ejecución de Windows PowerShell durante el procesamiento de comandos. Para este proveedor, no hay ningún funcionalidades específicas de Windows PowerShell que se agregan.

## <a name="defining-base-functionality"></a>Definir la funcionalidad de Base

Como se describe en [diseñar su proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase se deriva de varias clases que proporcionan funcionalidad proveedor diferente. Un proveedor de contenedor de Windows PowerShell, por lo tanto, tiene que definir toda la funcionalidad proporcionada por esas clases.

Para implementar la funcionalidad para agregar información de inicialización específicas de la sesión y para liberar los recursos utilizados por el proveedor, consulte [creación de un proveedor de PowerShell de Windows básico](./creating-a-basic-windows-powershell-provider.md). Sin embargo, la mayoría de proveedores (incluido el proveedor que se describe aquí) puede usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.

Para obtener acceso al almacén de datos, el proveedor debe implementar los métodos de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase base. Para obtener más información acerca de cómo implementar estos métodos, consulte [creación de un proveedor de la unidad de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular los elementos de un almacén de datos, como introducción, configuración y elementos de compensación, el proveedor debe implementar los métodos proporcionados por el [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase base. Para obtener más información acerca de cómo implementar estos métodos, consulte [creación de un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Recuperar elementos secundarios

Para recuperar un elemento secundario, debe invalidar el proveedor de contenedores de Windows PowerShell la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método para admitir llamadas desde el `Get-ChildItem` cmdlet. Este método recupera los elementos secundarios del almacén de datos y los escribe en la canalización como objetos. Si el `recurse` se especifica el parámetro del cmdlet, el método recupera todos los elementos secundarios, independientemente de qué nivel se encuentran en. Si el `recurse` parámetro no se especifica, el método recupera sólo un único nivel de elementos secundarios.

Esta es la implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método para este proveedor. Tenga en cuenta que este método recupera los elementos secundarios de todas las tablas de base de datos cuando la ruta de acceso indica la base de datos de Access y recupera los elementos secundarios de las filas de la tabla si la ruta de acceso indica una tabla de datos.

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
} // GetChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Cosas que recordar acerca de cómo implementar GetChildItems

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Al definir la clase de proveedor, un proveedor de contenedores de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos del elemento especificado (método) capacidades. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- La implementación de este método debe tener en cuenta cualquier forma de acceso al elemento que podría hacer que el elemento visible para el usuario. Por ejemplo, si un usuario tiene acceso de escritura a un archivo mediante el proveedor FileSystem (proporcionado por Windows PowerShell), pero no el acceso de lectura, el archivo sigue existiendo y [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) devuelve `true`. Su implementación podría requerir la comprobación de un elemento primario para ver si se puede enumerar el elemento secundario.

- Al escribir varios elementos, el [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) método puede tardar algún tiempo. Puede diseñar su proveedor para escribir los elementos mediante el [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método a la vez. Con esta técnica se presentan los elementos al usuario en una secuencia.

- La implementación de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) es responsable de evitar una recursión infinita cuando hay vínculos circulares y similares. Debe iniciará una excepción de terminación adecuada para reflejar una condición de ese tipo.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Asociar los parámetros dinámicos al Cmdlet Get-ChildItem

A veces la `Get-ChildItem` cmdlet que llama a [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) requiere parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, debe implementar el proveedor de contenedores de Windows PowerShell la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) método. Este método recupera los parámetros dinámicos para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros para el `Get-ChildItem` cmdlet.

Este proveedor de contenedores de Windows PowerShell no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Al recuperar los nombres de elementos secundarios

Para recuperar los nombres de elementos secundarios, debe invalidar el proveedor de contenedores de Windows PowerShell la [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método para admitir llamadas desde el `Get-ChildItem`cmdlet cuando su `Name` se especifica el parámetro. Este método recupera los nombres de los elementos secundarios de los nombres de elemento secundario o de ruta de acceso especificados para todos los contenedores si el `returnAllContainers` se especifica el parámetro del cmdlet. Un nombre de elemento secundario es la parte de la hoja de una ruta de acceso. Por ejemplo, el nombre de elemento secundario para la ruta de acceso de c:\windows\system32\abc.dll es "abc.dll". El nombre de elemento secundario para el directorio de c:\windows\system32 es "system32".

Esta es la implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) método para este proveedor. Tenga en cuenta que el método recupera los nombres de tabla si la ruta de acceso especificada indica la base de datos de Access (unidad) y los números de fila si la ruta de acceso indica una tabla.

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
} // GetChildNames
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Cosas que recordar acerca de cómo implementar GetChildNames

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Al definir la clase de proveedor, un proveedor de contenedores de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos del elemento especificado (método) capacidades. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

  > [!NOTE]
  > Se produce una excepción a esta regla cuando el `returnAllContainers` se especifica el parámetro del cmdlet. En este caso, el método debe recuperar cualquier nombre de elemento secundario de un contenedor, incluso si no coincide con los valores de la [System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), o [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben recuperar los nombres de objetos que se ocultan generalmente el usuario a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) se especifica la propiedad. Si la ruta de acceso especificada indica un contenedor, el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad no es necesaria.

- La implementación de [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) es responsable de evitar una recursión infinita cuando hay vínculos circulares y similares. Debe iniciará una excepción de terminación adecuada para reflejar una condición de ese tipo.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Asociar los parámetros dinámicos al Cmdlet Get-ChildItem (nombre)

A veces la `Get-ChildItem` cmdlet (con el `Name` parámetro) requiere parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, debe implementar el proveedor de contenedores de Windows PowerShell la [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) método. Este método recupera los parámetros dinámicos para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros para el `Get-ChildItem` cmdlet.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Cambiar nombre de elementos

Para cambiar el nombre de un elemento, un proveedor de contenedores de Windows PowerShell debe invalidar el [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método para admitir llamadas desde el `Rename-Item` cmdlet. Este método cambia el nombre del elemento en la ruta de acceso especificada para el nuevo nombre proporcionado. Siempre debe ser el nuevo nombre en relación con el elemento primario (contenedor).

Este proveedor no invalida el [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método. Sin embargo, la siguiente es la implementación predeterminada.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Cosas que recordar acerca de cómo implementar RenameItem

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Al definir la clase de proveedor, un proveedor de contenedores de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos del elemento especificado (método) capacidades. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- El [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) método está pensado para la modificación del nombre de un solo producto y no para las operaciones de movimiento. La implementación del método debe escribir un error si el `newName` parámetro contiene separadores de ruta de acceso, o pueden provocar el elemento para cambiar su ubicación principal.

- De forma predeterminada, las invalidaciones de este método deben no cambiar el nombre de los objetos a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) se especifica la propiedad. Si la ruta de acceso especificada indica un contenedor, el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad no es necesaria.

- La implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) debe llamar al método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cualquier cambio en el almacén de datos. Este método se utiliza para confirmar la ejecución de una operación cuando se modifica el estado del sistema, por ejemplo, cambiar el nombre de archivos. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envía el nombre del recurso que se puede cambiar para el usuario, con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos o variables de preferencia en determinar lo que debe mostrarse.

  Después de llamar a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve `true`, [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) debe llamar al método el [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envía un mensaje en un mensaje de confirmación al usuario para que los comentarios adicionales que decir si debe continuarse la operación. Debe llamar un proveedor [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) como una comprobación adicional para las modificaciones del sistema potencialmente peligrosos.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Asociar los parámetros dinámicos para el Cmdlet Rename-Item

A veces la `Rename-Item` cmdlet requiere parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, debe implementar el proveedor de contenedores de Windows PowerShell la [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) método. Este método recupera los parámetros para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros para el `Rename-Item` cmdlet.

Este proveedor de contenedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Crear nuevos elementos

Para crear nuevos elementos, debe implementar un proveedor de contenedores de la [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método para admitir llamadas desde el `New-Item` cmdlet. Este método crea un elemento de datos ubicado en la ruta de acceso especificada. El `type` parámetro del cmdlet contiene el tipo definido por el proveedor para el nuevo elemento. Por ejemplo, el proveedor de sistema de archivos usa un `type` parámetro con un valor "file" o "directory". El `newItemValue` parámetro del cmdlet especifica un valor específico del proveedor para el nuevo elemento.

Esta es la implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método para este proveedor.

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Cosas que recordar acerca de cómo implementar el nuevo elemento

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- El [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método debe realizar una comparación entre mayúsculas y minúsculas de la cadena pasada en el `type` parámetro. También debe permitir coincidencias menos ambiguo. Por ejemplo, para los tipos "file" y "Active", solo la primera letra es necesario para eliminar la ambigüedad. Si el `type` parámetro indica un tipo no se puede crear el proveedor, el [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método debe escribir una excepción ArgumentException con un mensaje que indica los tipos puede crear el proveedor.

- Para el `newItemValue` parámetro, la implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método se recomienda que acepte las cadenas como mínimo. También debe aceptar el tipo de objeto que se recupera mediante la [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para la misma ruta de acceso. El [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) método puede utilizar el [System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) método para convertir tipos el tipo deseado.

- La implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) debe llamar al método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cualquier cambio en el almacén de datos. Después de llamar a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve true, el [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) debe llamar al método el [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método como una comprobación adicional para las modificaciones del sistema potencialmente peligrosos.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Asociar los parámetros dinámicos al Cmdlet New-Item

A veces la `New-Item` cmdlet requiere parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenedor debe implementar la [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) método. Este método recupera los parámetros para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros para el `New-Item` cmdlet.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Quitar elementos

Para quitar elementos, debe invalidar el proveedor de Windows PowerShell la [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) método para admitir llamadas desde el `Remove-Item` cmdlet. Este método elimina un elemento del almacén de datos en la ruta especificada. Si el `recurse` parámetro de la `Remove-Item` cmdlet está establecido en `true`, el método quita todos los elementos secundarios, independientemente de su nivel. Si el parámetro se establece en `false`, el método quita solo de un solo elemento en la ruta de acceso especificada.

Este proveedor no admite la eliminación de elementos. Sin embargo, el código siguiente es la implementación predeterminada de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Cosas que recordar acerca de cómo implementar RemoveItem

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Al definir la clase de proveedor, un proveedor de contenedores de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos del elemento especificado (método) capacidades. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deberían quitar objetos a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en true. Si la ruta de acceso especificada indica un contenedor, el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad no es necesaria.

- La implementación de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) es responsable de evitar una recursión infinita cuando hay vínculos circulares y similares. Debe iniciará una excepción de terminación adecuada para reflejar una condición de ese tipo.

- La implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) debe llamar al método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cualquier cambio en el almacén de datos. Después de llamar a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve `true`, [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) debe llamar al método el [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método como una comprobación adicional para las modificaciones del sistema potencialmente peligrosos.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Asociar los parámetros dinámicos al Cmdlet Remove-Item

A veces la `Remove-Item` cmdlet requiere parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenedor debe implementar la [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) método para controlar estos parámetros. Este método recupera los parámetros dinámicos para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros para el `Remove-Item` cmdlet.

Este proveedor de contenedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Consulta de elementos secundarios

Para comprobar si existen elementos secundarios en la ruta de acceso especificada, el proveedor de contenedores de Windows PowerShell debe invalidar el [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método. Este método devuelve `true` si el elemento tiene elementos secundarios, y `false` en caso contrario. Para una ruta de acceso null o está vacío, el método tiene en cuenta los elementos en el almacén de datos para ser elementos secundarios y devuelve `true`.

Aquí está la invalidación para el [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método. Si hay más de dos partes de ruta de acceso creadas por el método de aplicación auxiliar ChunkPath, el método devuelve `false`, ya que sólo un contenedor de la base de datos y un contenedor de la tabla se definen. Para obtener más información acerca de este método auxiliar, vea el método ChunkPath se describe en [creación de un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Cosas que recordar acerca de cómo implementar HasChildItems

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Si el proveedor de contenedor expone una raíz que contiene los puntos de montaje interesantes, la implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) método debe devolver `true`cuando un valor null o una cadena vacía se pasa en la ruta de acceso.

## <a name="copying-items"></a>Copiar elementos

Para copiar elementos, el proveedor de contenedor debe implementar la [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) método para admitir llamadas desde el `Copy-Item` cmdlet. Este método copia un elemento de datos desde la ubicación indicada por el `path` parámetro del cmdlet para la ubicación indicada por el `copyPath` parámetro. Si el `recurse` parámetro se especifica, el método de copia de todos los subcontenedores. Si no se especifica el parámetro, el método de copia únicamente un solo nivel de elementos.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Cosas que recordar sobre la implementación de CopyItem

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Al definir la clase de proveedor, un proveedor de contenedores de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos del elemento especificado (método) capacidades. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben copiar los objetos a través de los objetos existentes a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Por ejemplo, el proveedor FileSystem no copiará c:\temp\abc.txt a través de un archivo c:\abc.txt existente a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Si la ruta de acceso especificada en el `copyPath` parámetro existe y que un contenedor, el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad no es necesaria. En este caso, [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) debe copiar el elemento indicado por el `path` parámetro en el contenedor indicado por el `copyPath` parámetro como un elemento secundario.

- La implementación de [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) es responsable de evitar una recursión infinita cuando hay vínculos circulares y similares. Debe iniciará una excepción de terminación adecuada para reflejar una condición de ese tipo.

- La implementación de la [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) debe llamar al método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cualquier cambio en el almacén de datos. Después de llamar a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve true, el [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) debe llamar al método el [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método como una comprobación adicional para las modificaciones del sistema potencialmente peligrosos. Para obtener más información sobre cómo llamar a estos métodos, consulte [cambiar el nombre de elementos](#Renaming-Items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Asociar los parámetros dinámicos para el Cmdlet Copy-Item

A veces la `Copy-Item` cmdlet requiere parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, debe implementar el proveedor de contenedores de Windows PowerShell la [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) método para controlar estos parámetros. Este método recupera los parámetros para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros para el `Copy-Item` cmdlet.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Ejemplo de código

Para el código de ejemplo completo, vea [AccessDbProviderSample04 código de ejemplo](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Creación del proveedor de Windows PowerShell

Consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Probar el proveedor de Windows PowerShell

Cuando se ha registrado el proveedor de Windows PowerShell con Windows PowerShell, puede probarla mediante la ejecución de los cmdlets compatibles en la línea de comandos. Tenga en cuenta que la salida del ejemplo siguiente utiliza una base de datos de Access ficticia.

1. Ejecute el `Get-ChildItem` cmdlet para recuperar la lista de elementos secundarios de una tabla Customers de la base de datos de Access.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   Aparece el siguiente resultado.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Ejecute el `Get-ChildItem` cmdlet nuevo para recuperar los datos de una tabla.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   Aparece el siguiente resultado.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. Ahora utilice el `Get-Item` cmdlet para recuperar los elementos de la fila 0 en la tabla de datos.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   Aparece el siguiente resultado.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. Reutilizar `Get-Item` para recuperar los datos para los elementos en la fila 0.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   Aparece el siguiente resultado.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. Ahora utilice el `New-Item` cmdlet para agregar una fila a una tabla existente. El `Path` parámetro especifica la ruta de acceso completa a la fila y debe indicar un número de fila que es mayor que el número de filas de la tabla existente. El `Type` parámetro indica "row" para especificar ese tipo de elemento se va a agregar. Por último, el `Value` parámetro especifica una lista delimitada por comas de valores de columna para la fila.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Compruebe la exactitud de la nueva operación de elemento como sigue.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   Aparece el siguiente resultado.

   ```output
   ID        : 3
   FirstName : Eric
   LastName  : Gruber
   Email     : ericgruber@fabrikam.com
   Title     : President
   Company   : Fabrikam
   WorkPhone : (425) 555-0100
   Address   : 4567 Main Street
   City      : Buffalo
   State     : NY
   Zip       : 98052
   Country   : USA
   ```

## <a name="see-also"></a>Véase también

[Creación de proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Implementar un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md)

[Implementar un proveedor de navegación de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)