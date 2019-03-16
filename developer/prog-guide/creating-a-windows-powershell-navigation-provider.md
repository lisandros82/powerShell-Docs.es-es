---
title: Creación de un proveedor de navegación de Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: 40454f880b57d5b3a8a8ded21c8c97aebba027fe
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055077"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Creación de un proveedor de navegación de Windows PowerShell

Este tema describe cómo crear un proveedor de navegación de Windows PowerShell que puede navegar por el almacén de datos. Este tipo de proveedor es compatible con comandos recursivos, los contenedores anidados y rutas de acceso relativas.

> [!NOTE]
> Puede descargar el C# (AccessDBSampleProvider05.cs) de archivo de código fuente para este proveedor mediante el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components. Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.
>
> Para obtener más información acerca de otras implementaciones del proveedor de Windows PowerShell, consulte [diseñar su proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

El proveedor que se describe aquí permite el identificador de usuario de una base de datos de Access como una unidad para que el usuario pueda ir a las tablas de datos en la base de datos. Al crear su propio proveedor de navegación, puede implementar los métodos que pueden hacer rutas de acceso completa a la unidad necesarios para la navegación, normalizar rutas de acceso relativas, mover los elementos de almacén de datos, además de los métodos que obtención los nombres de elemento secundario, probar y obtención la ruta de acceso primaria de un elemento para identificar si un elemento es un contenedor.

> [!CAUTION]
> Tenga en cuenta que este diseño considera una base de datos que tiene un campo con el identificador de nombre y que el tipo del campo es LongInteger.

En la lista siguiente incluye las secciones de este tema. Si no está familiarizado con la escritura de un proveedor de navegación de Windows PowerShell, lea esta información en el orden en que aparece. Sin embargo, si está familiarizado con la escritura de un proveedor de navegación de Windows PowerShell, vaya directamente a la información que necesita.

- [Definir una clase de proveedor de navegación de PS](#Define-the-Windows-PowerShell-provider)

- [Definir la funcionalidad de Base](#Defining-Base-Functionality)

- [Creación de una ruta de acceso PS](#Creating-a-Windows-PowerShell-Path)

- [Recuperar la ruta de acceso primaria](#Retrieving-the-Parent-Path)

- [Recuperar el nombre de ruta de acceso secundaria](#Retrieve-the-Child-Path-Name)

- [Determinar si un elemento es un contenedor](#Determining-if-an-Item-is-a-Container)

- [Mover un elemento](#Moving-an-Item)

- [Asociar los parámetros dinámicos a la `Move-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [La normalización de una ruta de acceso relativa](#Normalizing-a-Relative-Path)

- [Ejemplo de código](#Code-Sample)

- [Definir los tipos de objeto y el formato](#Defining-Object-Types-and-Formatting)

- [Creación del proveedor de Windows PowerShell](#Building-the-Windows-PowerShell-provider)

- [Probar el proveedor de Windows PowerShell](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a>Defina el proveedor de Windows PowerShell

Un proveedor de navegación de Windows PowerShell debe crear una clase .NET que se deriva de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase base. Esta es la definición de clase para el proveedor de navegación que se describe en esta sección.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Tenga en cuenta que en este proveedor, el [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo incluye dos parámetros. El primer parámetro especifica un nombre descriptivo para el proveedor que está usando Windows PowerShell. El segundo parámetro especifica las capacidades específicas de Windows PowerShell que expone el proveedor para el tiempo de ejecución de Windows PowerShell durante el procesamiento de comandos. Para este proveedor, no hay ningún funcionalidades específicas de Windows PowerShell que se agregan.

## <a name="defining-base-functionality"></a>Definir la funcionalidad de Base

Como se describe en [diseño PS proveedor](./designing-your-windows-powershell-provider.md), el [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase base que se deriva de varias clases que proporcionan otro proveedor funcionalidad. Un proveedor de navegación de Windows PowerShell, por lo tanto, debe definir toda la funcionalidad proporcionada por esas clases.

Para implementar la funcionalidad para agregar información de inicialización específicas de la sesión y para liberar los recursos utilizados por el proveedor, consulte [creación de un proveedor básico de PS](./creating-a-basic-windows-powershell-provider.md). Sin embargo, la mayoría de proveedores (incluido el proveedor que se describe aquí) puede usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.

Para obtener acceso al almacén de datos a través de una unidad de Windows PowerShell, debe implementar los métodos de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase base. Para obtener más información acerca de cómo implementar estos métodos, consulte [creación de un proveedor de la unidad de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular los elementos de un almacén de datos, como introducción, configuración y elementos de compensación, el proveedor debe implementar los métodos proporcionados por el [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase base. Para obtener más información acerca de cómo implementar estos métodos, consulte [creación de un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Para obtener los elementos secundarios o sus nombres, de que el almacén de datos, así como los métodos que crean, copiarán, cambiar el nombre y eliminar elementos, debe implementar los métodos proporcionados por el [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)clase base. Para obtener más información acerca de cómo implementar estos métodos, consulte [creación de un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Creación de una ruta de acceso de Windows PowerShell

Proveedor de navegación de Windows PowerShell usa una ruta de acceso interna del proveedor de Windows PowerShell para navegar por los elementos del almacén de datos. Para crear una ruta de acceso interna del proveedor en el proveedor debe implementar la [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) llamadas al método que admite del cmdlet Combine-Path. Este método combina una ruta de acceso primaria y secundaria en una ruta de acceso interna del proveedor, con un separador de ruta de acceso específica del proveedor entre las rutas de acceso primarias y secundarias.

La implementación predeterminada toma rutas de acceso con "/" o "\\"como separador de ruta de acceso, normaliza el separador de ruta de acceso a"\\", combina los elementos primarios y secundarios de la ruta con el separador entre ellas y, a continuación, devuelve una cadena que contiene el rutas de acceso combinadas.

Este proveedor de navegación no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de la [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Cosas que recordar acerca de cómo implementar MakePath

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- La implementación de la [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método no debe validar la ruta de acceso como una ruta legal completo en el espacio de nombres del proveedor. Tenga en cuenta que cada parámetro sólo pueden representar una parte de una ruta de acceso y los elementos combinados no podrían generar una ruta de acceso completa. Por ejemplo, el [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) método para el proveedor filesystem podría recibir "windows\system32" en el `parent` parámetro y "abc.dll" en el `child` parámetro. El método combina estos valores con el "\\" separador y devuelve "windows\system32\abc.dll", que no es una ruta de acceso de archivo completo del sistema.

  > [!IMPORTANT]
  > Los elementos de la ruta de acceso proporcionados en la llamada a [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) podría contener caracteres no permitidos en el espacio de nombres del proveedor. Estos caracteres más probable es que se usan para la expansión de caracteres comodín y la implementación de este método no debería quitar.

## <a name="retrieving-the-parent-path"></a>Recuperar la ruta de acceso primaria

Los proveedores de exploración de Windows PowerShell implementan el [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) método para recuperar la parte principal del completa o parcial ruta de acceso específica del proveedor. El método quita la parte secundaria de la ruta de acceso y devuelve al elemento primario de parte de la ruta de acceso. El `root` parámetro especifica la ruta de acceso completa a la raíz de una unidad. Este parámetro puede ser nulo ni estar vacío si no se usa para la operación de recuperación de una unidad montada. Si se especifica una raíz, el método debe devolver una ruta de acceso a un contenedor en el mismo árbol de la raíz.

El proveedor de navegación no invalida este método, pero utiliza la implementación predeterminada. Acepta las rutas de acceso que se usan "/" y "\\" como separadores de ruta de acceso. En primer lugar normaliza la ruta de acceso para que solo se "\\" separadores, a continuación, divide la ruta de acceso primaria desactivado en el último "\\" y devuelve la ruta de acceso primaria.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Recordar acerca de cómo implementar GetParentPath

La implementación de la [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) método debe dividir la ruta de acceso léxicamente en el separador de ruta de acceso del espacio de nombres del proveedor. Por ejemplo, el proveedor filesystem utiliza este método para buscar la última "\\" y todo lo devuelve a la izquierda del separador.

## <a name="retrieve-the-child-path-name"></a>Recuperar el nombre de ruta de acceso secundaria

El proveedor de navegación implementa el [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) método para recuperar el nombre (elemento de hoja) del elemento secundario del elemento situado en el completo indicado o ruta de acceso parcial específica del proveedor.

El proveedor de navegación no invalida este método. La implementación predeterminada se muestra a continuación. Acepta las rutas de acceso que se usan "/" y "\\" como separadores de ruta de acceso. En primer lugar normaliza la ruta de acceso para que solo se "\\" separadores, a continuación, divide la ruta de acceso primaria desactivado en el último "\\" y devuelve el nombre del elemento secundario de parte de la ruta de acceso.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Cosas que recordar acerca de cómo implementar GetChildName

La implementación de la [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) método debe dividir la ruta de acceso léxicamente en el separador de ruta de acceso. Si la ruta de acceso proporcionada no contiene separadores de ruta de acceso, el método debe devolver la ruta de acceso sin modificar.

> [!IMPORTANT]
> La ruta de acceso proporcionada en la llamada a este método podría contener caracteres que no son válidos en el espacio de nombres del proveedor. Estos caracteres son probablemente usa para la expansión de caracteres comodín o coincidencia de expresión regular y la implementación de este método no debería quitar.

## <a name="determining-if-an-item-is-a-container"></a>Determinar si un elemento es un contenedor

Puede implementar el proveedor de navegación de la [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) método para determinar si la ruta de acceso especificada indica un contenedor. Devuelve true si la ruta de acceso representa un contenedor y false en caso contrario. El usuario necesita este método para que pueda usar el `Test-Path` cmdlet para la ruta de acceso proporcionada.

El siguiente código muestra la [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementación en nuestro proveedor de navegación de ejemplo. El método comprueba que la ruta de acceso especificada sea correcta y si la tabla existe y devuelve true si la ruta de acceso indica un contenedor.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Cosas que recordar acerca de cómo implementar IsItemContainer

El clase .NET del proveedor de navegación puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. En este caso, la implementación de [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) debe asegurarse de que la ruta de acceso pasa cumple los requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) propiedad.

## <a name="moving-an-item"></a>Mover un elemento

Soporte del `Move-Item` implementa el proveedor de navegación de cmdlet, el [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método. Este método mueve el elemento especificado por el `path` parámetro en el contenedor en la ruta de acceso proporcionada en el `destination` parámetro.

El proveedor de navegación no invalida el [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) método. La siguiente es la implementación predeterminada.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Cosas que recordar acerca de cómo implementar MoveItem

El clase .NET del proveedor de navegación puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. En este caso, la implementación de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) debe asegurarse de que la ruta de acceso pasa cumple los requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el **CmdletProvider.Exclude** propiedad.

De forma predeterminada, las invalidaciones de este método no deben mover los objetos a través de los objetos existentes a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Por ejemplo, el proveedor filesystem no copiará c:\temp\abc.txt a través de un archivo c:\bar.txt existente a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Si la ruta de acceso especificada en el `destination` parámetro existe y es un contenedor, el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad no es necesaria. En este caso, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) debe mover el elemento indicado por el `path` parámetro en el contenedor indicado por el `destination` parámetro como un elemento secundario.

La implementación de la [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) debe llamar al método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cualquier cambio en el almacén de datos. Este método se utiliza para confirmar la ejecución de una operación cuando se modifica el estado del sistema, por ejemplo, eliminar archivos. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envía el nombre del recurso que se puede cambiar para el usuario, con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos o variables de preferencia en determinar lo que debe mostrarse al usuario.

Después de llamar a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve `true`, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) debe llamar al método el [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envía un mensaje al usuario para que los comentarios que decir si debe continuarse la operación. El proveedor debe llamar a [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) como una comprobación adicional para las modificaciones del sistema potencialmente peligrosos.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Asociar los parámetros dinámicos para el Cmdlet Move-Item

A veces la `Move-Item` cmdlet requiere parámetros adicionales que se proporcionan de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de navegación debe implementar la [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) método para obtener los valores de parámetro necesarios desde el elemento situado en la ruta de acceso indicada y devolver un objeto que tiene las propiedades y campos con el análisis de atributos similar a una clase de cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto.

Este proveedor de navegación no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>La normalización de una ruta de acceso relativa

El proveedor de navegación implementa el [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) indica el método para normalizar la ruta de acceso completa en el `path` parámetro como en relación con la ruta de acceso especificada por el `basePath` parámetro. El método devuelve una representación de cadena de la ruta de acceso normalizada. Escribe un error si el `path` parámetro especifica una ruta de acceso que no existe.

El proveedor de navegación no invalida este método. La siguiente es la implementación predeterminada.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Cosas que recordar acerca de cómo implementar NormalizeRelativePath

La implementación de [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) debe analizar el `path` parámetro, pero no tiene que utilizar el análisis sintácticas. Se recomienda este método para utilizar la ruta de acceso para buscar la información de ruta de acceso del almacén de datos y crear una ruta de acceso que coincide con las mayúsculas y minúsculas de diseño y estandarizado de sintaxis de ruta de acceso.

## <a name="code-sample"></a>Ejemplo de código

Para el código de ejemplo completo, vea [AccessDbProviderSample05 código de ejemplo](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir los tipos de objeto y el formato

Es posible que un proveedor para agregar a miembros a los objetos existentes o defina nuevos objetos. Para obtener más información, consulte[extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Creación del proveedor de Windows PowerShell

Para obtener más información, consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Probar el proveedor de Windows PowerShell

Cuando se ha registrado el proveedor de Windows PowerShell con Windows PowerShell, puede probarla mediante la ejecución de los cmdlets compatibles en la línea de comandos, incluidos los cmdlets facilitados por derivación. En este ejemplo se probará el proveedor de navegación.

1. Ejecute el nuevo shell y use el `Set-Location` cmdlet para establecer la ruta de acceso para indicar la base de datos de Access.

   ```powershell
   Set-Location mydb:
   ```

2. Ahora ejecute el `Get-Childitem` para recuperar una lista de los elementos de la base de datos, que son las tablas de base de datos disponibles. Para cada tabla, este cmdlet también recupera el número de filas de tabla.

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

3. Use el `Set-Location` cmdlet nuevo para establecer la ubicación de la tabla de datos de empleados.

   ```powershell
   Set-Location Employees
   ```

4. Ahora vamos a usar el `Get-Location` para recuperar la ruta de acceso a la tabla Employees.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. Ahora utilice el `Get-Childitem` se canaliza al cmdlet la `Format-Table` cmdlet. Este conjunto de cmdlets recupera los elementos de la tabla de datos de empleados, que son las filas de tabla. Se les aplica formato según lo especificado por el `Format-Table` cmdlet.

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

6. Ahora puede ejecutar el `Get-Item` cmdlet para recuperar los elementos de la fila 0 de la tabla de datos de empleados.

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

7. Use el `Get-Item` cmdlet nuevo para recuperar los datos del empleado para los elementos en la fila 0.

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

[Proveedor de PowerShell de Windows de su diseño](./designing-your-windows-powershell-provider.md)

[Extensión de tipos de objeto y el formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementar un proveedor de contenedor Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)