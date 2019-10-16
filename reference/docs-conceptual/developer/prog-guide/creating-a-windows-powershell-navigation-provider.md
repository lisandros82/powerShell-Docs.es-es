---
title: Crear un proveedor de navegación de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: d08e348a46b97a8b7d31f9360b29c5eedaa68ea6
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366824"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Creación de un proveedor de navegación de Windows PowerShell

En este tema se describe cómo crear un proveedor de navegación de Windows PowerShell que pueda navegar por el almacén de datos. Este tipo de proveedor admite comandos recursivos, contenedores anidados y rutas de acceso relativas.

> [!NOTE]
> Puede descargar el C# archivo de código fuente (AccessDBSampleProvider05.CS) para este proveedor mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de origen descargados están disponibles en el directorio **@no__t ejemplos de 1PowerShell >** .
>
> Para obtener más información sobre otras implementaciones del proveedor de Windows PowerShell, vea [diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

El proveedor descrito aquí permite que el usuario controle una base de datos de Access como una unidad para que el usuario pueda navegar a las tablas de datos de la base de datos. Al crear su propio proveedor de navegación, puede implementar métodos que pueden hacer que las rutas de acceso calificadas por unidad sean necesarias para la navegación, normalizar las rutas de acceso relativas, desplazar elementos del almacén de datos, así como métodos que obtienen nombres secundarios, obtienen la ruta de acceso primaria de un elemento y prueban para identificar si un elemento es un contenedor.

> [!CAUTION]
> Tenga en cuenta que este diseño supone que hay una base de datos que tiene un campo con el identificador de nombre y que el tipo del campo es LongInteger.

## <a name="define-the-windows-powershell-provider"></a>Definir el proveedor de Windows PowerShell

Un proveedor de navegación de Windows PowerShell debe crear una clase .NET que derive de la clase base [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Esta es la definición de clase del proveedor de navegación que se describe en esta sección.

[!code-csharp[AccessDBProviderSample05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Tenga en cuenta que en este proveedor, el atributo [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) incluye dos parámetros. El primer parámetro especifica un nombre descriptivo para el proveedor que usa Windows PowerShell. El segundo parámetro especifica las capacidades específicas de Windows PowerShell que el proveedor expone al tiempo de ejecución de Windows PowerShell durante el procesamiento de comandos. Para este proveedor, no hay ninguna funcionalidad específica de Windows PowerShell que se agregue.

## <a name="defining-base-functionality"></a>Definir la funcionalidad básica

Tal y como se describe en [diseñar su proveedor de PS](./designing-your-windows-powershell-provider.md), la clase base [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) deriva de otras clases que proporcionan una funcionalidad de proveedor diferente. Por lo tanto, un proveedor de navegación de Windows PowerShell debe definir toda la funcionalidad proporcionada por esas clases.

Para implementar la funcionalidad para agregar información de inicialización específica de la sesión y para liberar recursos utilizados por el proveedor, consulte [crear un proveedor de PS básico](./creating-a-basic-windows-powershell-provider.md). Sin embargo, la mayoría de los proveedores (incluido el proveedor descrito aquí) pueden usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.

Para obtener acceso al almacén de datos a través de una unidad de Windows PowerShell, debe implementar los métodos de la clase base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Para obtener más información sobre la implementación de estos métodos, vea [crear un proveedor de unidades de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular los elementos de un almacén de datos, como obtener, establecer y borrar elementos, el proveedor debe implementar los métodos proporcionados por la clase base [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Para obtener más información sobre la implementación de estos métodos, vea [crear un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Para llegar a los elementos secundarios, o sus nombres, del almacén de datos, así como a los métodos que crean, copian, cambia el nombre y quitan elementos, debe implementar los métodos proporcionados por la clase base [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Para obtener más información sobre la implementación de estos métodos, vea [crear un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Crear una ruta de acceso de Windows PowerShell

El proveedor de navegación de Windows PowerShell usa una ruta de acceso de Windows PowerShell interna del proveedor para navegar por los elementos del almacén de datos. Para crear una ruta de acceso interna del proveedor, el proveedor debe implementar el método [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) para admitir llamadas del cmdlet combine-path. Este método combina una ruta de acceso primaria y secundaria en una ruta de acceso interna del proveedor mediante un separador de ruta de acceso específico del proveedor entre las rutas de acceso primarias y secundarias.

La implementación predeterminada toma rutas de acceso con "/" o "\\" como separador de ruta de acceso, normaliza el separador de ruta de acceso a "\\", combina las partes de la ruta de acceso primaria y secundaria con el separador entre ellas y, a continuación, devuelve una cadena que contiene las rutas de acceso combinadas.

Este proveedor de navegación no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada del método [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Aspectos que se deben recordar sobre la implementación de MakePath

Se pueden aplicar las siguientes condiciones a su implementación de [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- La implementación del método [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) no debe validar la ruta de acceso como una ruta de acceso completa válida en el espacio de nombres del proveedor. Tenga en cuenta que cada parámetro solo puede representar una parte de una ruta de acceso, y es posible que los elementos combinados no generen una ruta de acceso completa. Por ejemplo, el método [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) para el proveedor filesystem podría recibir "Windows\System32" en el parámetro `parent` y "ABC. dll" en el parámetro `child`. El método combina estos valores con el separador "\\" y devuelve "windows\system32\abc.dll", que no es una ruta de acceso completa del sistema de archivos.

  > [!IMPORTANT]
  > Las partes de la ruta de acceso proporcionadas en la llamada a [System. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) pueden contener caracteres no permitidos en el espacio de nombres del proveedor. Normalmente, estos caracteres se usan para la expansión de caracteres comodín y la implementación de este método no debe quitarlos.

## <a name="retrieving-the-parent-path"></a>Recuperación de la ruta de acceso primaria

Los proveedores de navegación de Windows PowerShell implementan el método [System. Management. Automation. Provider. Navigationcmdletprovider. GetParentPath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) para recuperar la parte primaria de la ruta de acceso específica de proveedor completa o parcial indicada. El método quita la parte secundaria de la ruta de acceso y devuelve la parte de la ruta de acceso primaria. El parámetro `root` especifica la ruta de acceso completa a la raíz de una unidad. Este parámetro puede ser null o estar vacío si no se está usando una unidad montada para la operación de recuperación. Si se especifica una raíz, el método debe devolver una ruta de acceso a un contenedor en el mismo árbol que la raíz.

El proveedor de navegación de ejemplo no invalida este método, pero utiliza la implementación predeterminada. Acepta rutas de acceso que usan "/" y "\\" como separadores de ruta de acceso. Primero normaliza la ruta de acceso para que solo tenga separadores "\\" y, a continuación, divide la ruta de acceso primaria en el último "\\" y devuelve la ruta de acceso primaria.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Para recordar la implementación de GetParentPath

La implementación del método [System. Management. Automation. Provider. Navigationcmdletprovider. GetParentPath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) debe dividir la ruta de acceso léxicamente en el separador de ruta de acceso del espacio de nombres del proveedor. Por ejemplo, el proveedor filesystem usa este método para buscar el último "\\" y devuelve todo lo que queda a la izquierda del separador.

## <a name="retrieve-the-child-path-name"></a>Recuperar el nombre de la ruta de acceso secundaria

El proveedor de navegación implementa el método [System. Management. Automation. Provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) para recuperar el nombre (elemento hoja) del elemento secundario del elemento situado en la parte completa o parcial indicada. Ruta de acceso específica del proveedor.

El proveedor de navegación de ejemplo no invalida este método. A continuación se muestra la implementación predeterminada. Acepta rutas de acceso que usan "/" y "\\" como separadores de ruta de acceso. Primero normaliza la ruta de acceso para que solo tenga separadores "\\" y, a continuación, divide la ruta de acceso primaria en la última "\\" y devuelve el nombre de la parte de ruta de acceso secundaria.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Aspectos que se deben recordar sobre la implementación de GetChildName

La implementación del método [System. Management. Automation. Provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) debe dividir la ruta de acceso léxicamente en el separador de ruta de acceso. Si la ruta de acceso proporcionada no contiene separadores de ruta de acceso, el método debe devolver la ruta de acceso sin modificar.

> [!IMPORTANT]
> La ruta de acceso proporcionada en la llamada a este método podría contener caracteres que no son válidos en el espacio de nombres del proveedor. Probablemente, estos caracteres se usan para la expansión de caracteres comodín o la coincidencia de expresiones regulares, y la implementación de este método no debería quitarlos.

## <a name="determining-if-an-item-is-a-container"></a>Determinar si un elemento es un contenedor

El proveedor de navegación puede implementar el método [System. Management. Automation. Provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) para determinar si la ruta de acceso especificada indica un contenedor. Devuelve true si la ruta de acceso representa un contenedor y false en caso contrario. El usuario necesita este método para poder usar el cmdlet `Test-Path` para la ruta de acceso proporcionada.

En el código siguiente se muestra la implementación de [System. Management. Automation. Provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) en nuestro proveedor de navegación de ejemplo. El método comprueba que la ruta de acceso especificada es correcta y si la tabla existe, y devuelve true si la ruta de acceso indica un contenedor.

[!code-csharp[AccessDBProviderSample05.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Aspectos que se deben recordar sobre la implementación de IsItemContainer

La clase .NET del proveedor de navegación podría declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En este caso, la implementación de [System. Management. Automation. Provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) necesita asegurarse de que la ruta de acceso pasada cumple los requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, la propiedad [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) .

## <a name="moving-an-item"></a>Mover un elemento

En la compatibilidad del cmdlet `Move-Item`, el proveedor de navegación implementa el método [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) . Este método mueve el elemento especificado por el parámetro `path` al contenedor en la ruta de acceso proporcionada en el parámetro `destination`.

El proveedor de navegación de ejemplo no invalida el método [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) . A continuación se encuentra la implementación predeterminada.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Aspectos que se deben recordar sobre la implementación de MoveItem

La clase .NET del proveedor de navegación podría declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En este caso, la implementación de [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) debe asegurarse de que la ruta de acceso pasada cumple los requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, la propiedad **CmdletProvider. Exclude** .

De forma predeterminada, las invalidaciones de este método no deben trasladar objetos sobre objetos existentes a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Por ejemplo, el proveedor filesystem no copiará c:\temp\abc.txt sobre un archivo c:\bar.txt existente, a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Si la ruta de acceso especificada en el parámetro `destination` existe y es un contenedor, la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) no es necesaria. En este caso, [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) debe trasladar el elemento indicado por el parámetro `path` al contenedor indicado por el parámetro `destination` como un elemento secundario.

La implementación del método [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cambios en el almacén de datos. Este método se usa para confirmar la ejecución de una operación cuando se realiza un cambio en el estado del sistema, por ejemplo, la eliminación de archivos. [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envía el nombre del recurso que se va a cambiar al usuario, con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos o variables de preferencia para determinar Qué se debe mostrar al usuario.

Después de que la llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelva `true`, el método [System. Management. Automation. Provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) debe llamar a la [ Método System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Este método envía un mensaje al usuario para permitir que los comentarios indiquen si la operación debe continuar. El proveedor debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) como una comprobación adicional para las modificaciones potencialmente peligrosas del sistema.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Asociar parámetros dinámicos al cmdlet Move-Item

A veces, el cmdlet `Move-Item` requiere parámetros adicionales que se proporcionan dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de navegación debe implementar el método [System. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) para obtener los valores de parámetro necesarios del elemento en el la ruta de acceso indicada y devuelven un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .

Este proveedor de navegación no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de [System. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Normalización de una ruta de acceso relativa

El proveedor de navegación implementa el método [System. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) para normalizar la ruta de acceso completa indicada en el parámetro `path` como relativa a la ruta de acceso. especificado por el parámetro `basePath`. El método devuelve una representación de cadena de la ruta de acceso normalizada. Escribe un error si el parámetro `path` especifica una ruta de acceso inexistente.

El proveedor de navegación de ejemplo no invalida este método. A continuación se encuentra la implementación predeterminada.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Aspectos que se deben recordar sobre la implementación de NormalizeRelativePath

La implementación de [System. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) debe analizar el parámetro `path`, pero no tiene que usar el análisis puramente sintáctico. Se recomienda diseñar este método para usar la ruta de acceso para buscar la información de la ruta de acceso en el almacén de datos y crear una ruta de acceso que coincida con el uso de mayúsculas y minúsculas con la sintaxis de ruta de acceso normalizada.

## <a name="code-sample"></a>Código de ejemplo

Para obtener el código de ejemplo completo, vea el [ejemplo de código AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto y formato

Un proveedor puede Agregar miembros a objetos existentes o definir nuevos objetos. Para obtener más información, vea[extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Compilar el proveedor de Windows PowerShell

Para obtener más información, vea [Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Probar el proveedor de Windows PowerShell

Cuando el proveedor de Windows PowerShell se ha registrado con Windows PowerShell, puede probarlo mediante la ejecución de los cmdlets admitidos en la línea de comandos, incluidos los cmdlets disponibles por derivación. En este ejemplo se probará el proveedor de navegación de ejemplo.

1. Ejecute el nuevo Shell y use el cmdlet `Set-Location` para establecer la ruta de acceso que indica la base de datos de Access.

   ```powershell
   Set-Location mydb:
   ```

2. Ahora ejecute el cmdlet `Get-Childitem` para recuperar una lista de los elementos de base de datos, que son las tablas de base de datos disponibles. Para cada tabla, este cmdlet también recupera el número de filas de la tabla.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. Vuelva a usar el cmdlet `Set-Location` para establecer la ubicación de la tabla de datos de los empleados.

   ```powershell
   Set-Location Employees
   ```

4. Ahora vamos a usar el cmdlet `Get-Location` para recuperar la ruta de acceso a la tabla Employees.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. Ahora use el cmdlet `Get-Childitem` canalizado al cmdlet `Format-Table`. Este conjunto de cmdlets recupera los elementos de la tabla de datos Employees, que son las filas de la tabla. Tienen el formato especificado por el cmdlet `Format-Table`.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. Ahora puede ejecutar el cmdlet `Get-Item` para recuperar los elementos de la fila 0 de la tabla de datos Employees.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Vuelva a usar el cmdlet `Get-Item` para recuperar los datos de empleados de los elementos de la fila 0.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>Véase también

[Crear proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Diseño del proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementar un proveedor de Windows PowerShell de contenedor](./creating-a-windows-powershell-container-provider.md)

[Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
