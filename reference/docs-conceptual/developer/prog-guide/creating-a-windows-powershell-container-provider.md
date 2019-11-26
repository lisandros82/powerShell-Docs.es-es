---
title: Crear un proveedor de contenedores de Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: fcb03d4021f00837095ce703beb0d841233391d6
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416217"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Creación de un proveedor de contenedores de Windows PowerShell

En este tema se describe cómo crear un proveedor de Windows PowerShell que pueda trabajar en almacenes de datos de varias capas. Para este tipo de almacén de datos, el nivel superior del almacén contiene los elementos raíz y cada nivel subsiguiente se denomina nodo de los elementos secundarios. Al permitir que el usuario trabaje en estos nodos secundarios, un usuario puede interactuar jerárquicamente a través del almacén de datos.

Los proveedores que pueden trabajar en almacenes de datos de varios niveles se conocen como proveedores de contenedores de Windows PowerShell. Sin embargo, tenga en cuenta que solo se puede usar un proveedor de contenedores de Windows PowerShell cuando hay un contenedor (sin contenedores anidados) con elementos contenidos en él. Si hay contenedores anidados, debe implementar un proveedor de navegación de Windows PowerShell. Para obtener más información sobre cómo implementar el proveedor de navegación de Windows PowerShell, consulte [crear un proveedor de navegación de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> Puede descargar el C# archivo de código fuente (AccessDBSampleProvider04.CS) para este proveedor mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .
>
> Para obtener más información sobre otras implementaciones del proveedor de Windows PowerShell, vea [diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

El proveedor de contenedores de Windows PowerShell que se describe aquí define la base de datos como su contenedor único, con las tablas y filas de la base de datos definidas como elementos del contenedor.

> [!CAUTION]
> Tenga en cuenta que este diseño supone que hay una base de datos que tiene un campo con el identificador de nombre y que el tipo del campo es LongInteger.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Definir una clase de proveedor de contenedores de Windows PowerShell

Un proveedor de contenedores de Windows PowerShell debe definir una clase .NET que derive de la clase base [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Esta es la definición de clase del proveedor de contenedores de Windows PowerShell que se describe en esta sección.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Observe que en esta definición de clase, el atributo [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) incluye dos parámetros. El primer parámetro especifica un nombre descriptivo para el proveedor que usa Windows PowerShell. El segundo parámetro especifica las capacidades específicas de Windows PowerShell que el proveedor expone al tiempo de ejecución de Windows PowerShell durante el procesamiento de comandos. Para este proveedor, no hay ninguna funcionalidad específica de Windows PowerShell que se agregue.

## <a name="defining-base-functionality"></a>Definir la funcionalidad básica

Como se describe en [diseñar un proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md), la clase [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) se deriva de otras clases que proporcionan una funcionalidad de proveedor diferente. Por lo tanto, un proveedor de contenedores de Windows PowerShell debe definir toda la funcionalidad proporcionada por esas clases.

Para implementar la funcionalidad para agregar información de inicialización específica de la sesión y liberar recursos utilizados por el proveedor, consulte [crear un proveedor de Windows PowerShell básico](./creating-a-basic-windows-powershell-provider.md). Sin embargo, la mayoría de los proveedores (incluido el proveedor descrito aquí) pueden usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.

Para obtener acceso al almacén de datos, el proveedor debe implementar los métodos de la clase base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Para obtener más información sobre la implementación de estos métodos, vea [crear un proveedor de unidades de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular los elementos de un almacén de datos, como obtener, establecer y borrar elementos, el proveedor debe implementar los métodos proporcionados por la clase base [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Para obtener más información sobre la implementación de estos métodos, vea [crear un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Recuperar elementos secundarios

Para recuperar un elemento secundario, el proveedor de contenedores de Windows PowerShell debe invalidar el método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) para admitir llamadas del cmdlet `Get-ChildItem`. Este método recupera los elementos secundarios del almacén de datos y los escribe en la canalización como objetos. Si se especifica el parámetro `recurse` del cmdlet, el método recupera todos los elementos secundarios sin tener en consideración el nivel en el que se encuentran. Si no se especifica el parámetro `recurse`, el método recupera solo un único nivel de elementos secundarios.

Esta es la implementación del método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) para este proveedor. Tenga en cuenta que este método recupera los elementos secundarios en todas las tablas de base de datos cuando la ruta de acceso indica la base de datos de Access y recupera los elementos secundarios de las filas de esa tabla si la ruta de acceso indica una tabla de datos.

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

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Aspectos que se deben recordar sobre la implementación de GetChildItems

Se pueden aplicar las siguientes condiciones a su implementación de [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Al definir la clase de proveedor, un proveedor de contenedores de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- La implementación de este método debe tener en cuenta cualquier forma de acceso al elemento que pueda hacer que el elemento sea visible para el usuario. Por ejemplo, si un usuario tiene acceso de escritura a un archivo a través del proveedor FileSystem (proporcionado por Windows PowerShell), pero no de acceso de lectura, el archivo sigue existiendo y [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) devuelve `true`. La implementación de puede requerir la comprobación de un elemento primario para ver si se puede enumerar el elemento secundario.

- Al escribir varios elementos, el método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) puede tardar algún tiempo. Puede diseñar su proveedor para escribir los elementos mediante el método [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) de uno en uno. El uso de esta técnica presentará los elementos al usuario en una secuencia.

- La implementación de [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) es responsable de evitar la recursividad infinita cuando hay vínculos circulares y similares. Se debe iniciar una excepción de terminación adecuada para reflejar este tipo de condición.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Adjuntar parámetros dinámicos al cmdlet Get-ChildItem

A veces, el cmdlet `Get-ChildItem` que llama a [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) requiere parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenedores de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) . Este método recupera los parámetros dinámicos para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con los atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet `Get-ChildItem`.

Este proveedor de contenedores de Windows PowerShell no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Recuperar nombres de elementos secundarios

Para recuperar los nombres de los elementos secundarios, el proveedor de contenedores de Windows PowerShell debe invalidar el método [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) para admitir llamadas del cmdlet `Get-ChildItem` cuando se especifica su parámetro `Name`. Este método recupera los nombres de los elementos secundarios de la ruta de acceso especificada o los nombres de los elementos secundarios de todos los contenedores si se especifica el parámetro `returnAllContainers` del cmdlet. Un nombre secundario es la parte hoja de una ruta de acceso. Por ejemplo, el nombre secundario de la ruta de acceso c:\windows\system32\abc.dll es "ABC. dll". El nombre secundario para el directorio c:\windows\system32 es "system32".

Esta es la implementación del método [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) para este proveedor. Tenga en cuenta que el método recupera los nombres de tabla si la ruta de acceso especificada indica la base de datos de Access (unidad) y los números de fila si la ruta de acceso indica una tabla.

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

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Aspectos que se deben recordar sobre la implementación de GetChildNames

Se pueden aplicar las siguientes condiciones a su implementación de [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- Al definir la clase de proveedor, un proveedor de contenedores de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

  > [!NOTE]
  > Una excepción a esta regla se produce cuando se especifica el parámetro `returnAllContainers` del cmdlet. En este caso, el método debe recuperar cualquier nombre secundario de un contenedor, incluso si no coincide con los valores de las propiedades [System. Management. Automation. Provider. Cmdletprovider. Filter *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)o [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) .

- De forma predeterminada, las invalidaciones de este método no deben recuperar los nombres de los objetos que normalmente están ocultos del usuario a menos que se especifique la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) . Si la ruta de acceso especificada indica un contenedor, la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) no es necesaria.

- La implementación de [System. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) es responsable de evitar la recursividad infinita cuando hay vínculos circulares y similares. Se debe iniciar una excepción de terminación adecuada para reflejar este tipo de condición.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Adjuntando parámetros dinámicos al cmdlet Get-ChildItem (Name)

A veces, el cmdlet `Get-ChildItem` (con el parámetro `Name`) requiere parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenedores de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) . Este método recupera los parámetros dinámicos para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet `Get-ChildItem`.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Cambiar el nombre de los elementos

Para cambiar el nombre de un elemento, un proveedor de contenedores de Windows PowerShell debe invalidar el método [System. Management. Automation. Provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) para admitir llamadas del cmdlet `Rename-Item`. Este método cambia el nombre del elemento en la ruta de acceso especificada al nuevo nombre proporcionado. El nuevo nombre siempre debe ser relativo al elemento primario (contenedor).

Este proveedor no invalida el método [System. Management. Automation. Provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) . Sin embargo, la implementación predeterminada es la siguiente.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Aspectos que se deben recordar sobre la implementación de RenameItem

Se pueden aplicar las siguientes condiciones a su implementación de [System. Management. Automation. Provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- Al definir la clase de proveedor, un proveedor de contenedores de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- El método [System. Management. Automation. Provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) está pensado para la modificación del nombre de un solo elemento, y no para las operaciones de movimiento. La implementación del método debe escribir un error si el parámetro `newName` contiene separadores de ruta de acceso o puede hacer que el elemento cambie su ubicación primaria.

- De forma predeterminada, las invalidaciones de este método no deben cambiar el nombre de los objetos a menos que se especifique la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) . Si la ruta de acceso especificada indica un contenedor, la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) no es necesaria.

- La implementación del método [System. Management. Automation. Provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cambios en el almacén de datos. Este método se usa para confirmar la ejecución de una operación cuando se realiza un cambio en el estado del sistema, por ejemplo, cambiar el nombre de los archivos. [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envía el nombre del recurso que se va a cambiar al usuario, con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos o variables de preferencia para determinar lo que se debe mostrar.

  Después de que la llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelva `true`, el método [System. Management. Automation. Provider. Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) debe llamar al método [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Este método envía un mensaje de confirmación al usuario para permitir comentarios adicionales para indicar si la operación debe continuar. Un proveedor debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) como una comprobación adicional para las modificaciones potencialmente peligrosas del sistema.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Asociar los parámetros dinámicos al cmdlet Rename-Item

A veces, el cmdlet `Rename-Item` requiere parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenedores de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) . Este método recupera los parámetros para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con los atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet `Rename-Item`.

Este proveedor de contenedores no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Crear nuevos elementos

Para crear nuevos elementos, un proveedor de contenedores debe implementar el método [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) para admitir llamadas del cmdlet `New-Item`. Este método crea un elemento de datos ubicado en la ruta de acceso especificada. El parámetro `type` del cmdlet contiene el tipo definido por el proveedor para el nuevo elemento. Por ejemplo, el proveedor FileSystem usa un parámetro `type` con un valor "File" o "Directory". El parámetro `newItemValue` del cmdlet especifica un valor específico del proveedor para el nuevo elemento.

Esta es la implementación del método [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) para este proveedor.

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

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Aspectos que se deben recordar sobre la implementación de NewItem

Las condiciones siguientes pueden aplicarse a su implementación de [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- El método [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) debe realizar una comparación sin distinción entre mayúsculas y minúsculas de la cadena pasada en el parámetro `type`. También debe permitir una coincidencia menos ambigua. Por ejemplo, para los tipos "File" y "Directory", solo se necesita la primera letra para eliminar la ambigüedad. Si el parámetro `type` indica un tipo que el proveedor no puede crear, el método [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) debe escribir una excepción ArgumentException con un mensaje que indique los tipos que el proveedor puede crear.

- En el caso del parámetro `newItemValue`, se recomienda que la implementación del método [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) acepte cadenas como mínimo. También debe aceptar el tipo de objeto recuperado por el método [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) para la misma ruta de acceso. El método [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) puede usar el método [System. Management. Automation. LanguagePrimitives. ConvertTo *](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) para convertir tipos en el tipo deseado.

- La implementación del método [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cambios en el almacén de datos. Después de que la llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelva true, el método [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) debe llamar al método [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) como una comprobación adicional para las modificaciones potencialmente peligrosas del sistema.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Adjuntar parámetros dinámicos al cmdlet New-Item

A veces, el cmdlet `New-Item` requiere parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenedores debe implementar el método [System. Management. Automation. Provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) . Este método recupera los parámetros para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con los atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet `New-Item`.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Quitar elementos

Para quitar elementos, el proveedor de Windows PowerShell debe invalidar el método [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) para admitir llamadas del cmdlet `Remove-Item`. Este método elimina un elemento del almacén de datos en la ruta de acceso especificada. Si el parámetro `recurse` del cmdlet `Remove-Item` está establecido en `true`, el método quita todos los elementos secundarios independientemente de su nivel. Si el parámetro se establece en `false`, el método solo quita un elemento de la ruta de acceso especificada.

Este proveedor no admite la eliminación de elementos. Sin embargo, el código siguiente es la implementación predeterminada de [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Aspectos que se deben recordar sobre la implementación de RemoveItem

Las condiciones siguientes pueden aplicarse a su implementación de [System. Management. Automation. Provider. Containercmdletprovider. newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Al definir la clase de proveedor, un proveedor de contenedores de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben quitar objetos a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en true. Si la ruta de acceso especificada indica un contenedor, la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) no es necesaria.

- La implementación de [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) es responsable de evitar la recursividad infinita cuando hay vínculos circulares y similares. Se debe iniciar una excepción de terminación adecuada para reflejar este tipo de condición.

- La implementación del método [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cambios en el almacén de datos. Después de que la llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelva `true`, el método [System. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) debe llamar al método [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) como una comprobación adicional para las modificaciones potencialmente peligrosas del sistema.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Adjuntar parámetros dinámicos al cmdlet Remove-item

A veces, el cmdlet `Remove-Item` requiere parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenedores debe implementar el método [System. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) para controlar estos parámetros. Este método recupera los parámetros dinámicos para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet `Remove-Item`.

Este proveedor de contenedores no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de [System. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Consulta de elementos secundarios

Para comprobar si existen elementos secundarios en la ruta de acceso especificada, el proveedor de contenedores de Windows PowerShell debe invalidar el método [System. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) . Este método devuelve `true` si el elemento tiene elementos secundarios y `false` de lo contrario. En el caso de una ruta de acceso nula o vacía, el método considera que los elementos del almacén de datos son secundarios y devuelven `true`.

Esta es la invalidación del método [System. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) . Si hay más de dos partes de la ruta de acceso creadas por el método auxiliar ChunkPath, el método devuelve `false`, ya que solo se definen un contenedor de base de datos y un contenedor de tabla. Para obtener más información sobre este método auxiliar, vea el método ChunkPath que se describe en [crear un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Aspectos que se deben recordar sobre la implementación de HasChildItems

Se pueden aplicar las siguientes condiciones a su implementación de [System. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Si el proveedor de contenedores expone una raíz que contiene puntos de montaje interesantes, la implementación del método [System. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) debe devolver `true` cuando se pasa un valor null o una cadena vacía para la ruta de acceso.

## <a name="copying-items"></a>Copiar elementos

Para copiar elementos, el proveedor de contenedores debe implementar el método [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) para admitir llamadas del cmdlet `Copy-Item`. Este método copia un elemento de datos de la ubicación indicada por el parámetro `path` del cmdlet en la ubicación indicada por el parámetro `copyPath`. Si se especifica el parámetro `recurse`, el método copia todos los subcontenedores. Si no se especifica el parámetro, el método copia solo un único nivel de elementos.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Aspectos que se deben recordar sobre la implementación de CopyItem

Las condiciones siguientes pueden aplicarse a su implementación de [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- Al definir la clase de proveedor, un proveedor de contenedores de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben copiar objetos sobre objetos existentes a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Por ejemplo, el proveedor FileSystem no copiará c:\temp\abc.txt sobre un archivo c:\abc.txt existente, a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Si la ruta de acceso especificada en el parámetro `copyPath` existe e indica un contenedor, la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) no es necesaria. En este caso, [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) debe copiar el elemento indicado por el parámetro `path` en el contenedor indicado por el parámetro `copyPath` como un elemento secundario.

- La implementación de [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) es responsable de evitar la recursividad infinita cuando hay vínculos circulares y similares. Se debe iniciar una excepción de terminación adecuada para reflejar este tipo de condición.

- La implementación del método [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cambios en el almacén de datos. Después de que la llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelva true, el método [System. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) debe llamar al método [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) como una comprobación adicional para las modificaciones de sistema potencialmente peligrosas. Para obtener más información sobre cómo llamar a estos métodos, vea [cambiar el nombre de los elementos](#renaming-items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Adjuntar parámetros dinámicos al cmdlet Copy-Item

A veces, el cmdlet `Copy-Item` requiere parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenedores de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) para administrar estos parámetros. Este método recupera los parámetros para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con los atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet `Copy-Item`.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de [System. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Código de ejemplo

Para obtener el código de ejemplo completo, vea el [ejemplo de código AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Compilar el proveedor de Windows PowerShell

Vea [Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Probar el proveedor de Windows PowerShell

Cuando el proveedor de Windows PowerShell se ha registrado con Windows PowerShell, puede probarlo mediante la ejecución de los cmdlets admitidos en la línea de comandos. Tenga en cuenta que en la siguiente salida de ejemplo se utiliza una base de datos de Access ficticia.

1. Ejecute el cmdlet `Get-ChildItem` para recuperar la lista de elementos secundarios de una tabla Customers de la base de datos de Access.

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

2. Vuelva a ejecutar el cmdlet `Get-ChildItem` para recuperar los datos de una tabla.

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

3. Ahora use el cmdlet `Get-Item` para recuperar los elementos de la fila 0 de la tabla de datos.

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

4. Reutilice `Get-Item` para recuperar los datos de los elementos de la fila 0.

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

5. Ahora use el cmdlet `New-Item` para agregar una fila a una tabla existente. El parámetro `Path` especifica la ruta de acceso completa a la fila y debe indicar un número de fila mayor que el número de filas existente en la tabla. El parámetro `Type` indica "Row" para especificar el tipo de elemento que se va a agregar. Por último, el parámetro `Value` especifica una lista delimitada por comas de valores de columna de la fila.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Compruebe la corrección de la operación del nuevo elemento como se indica a continuación.

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

## <a name="see-also"></a>Vea también

[Crear proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Diseño del proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Implementar un elemento proveedor de Windows PowerShell](./creating-a-windows-powershell-item-provider.md)

[Implementar un proveedor de navegación de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)
