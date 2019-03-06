---
title: Creación de un proveedor de elementos de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: be1446dbd2b244f4752e55c8137433edee8427b0
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429999"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Creación de un proveedor de elementos de Windows PowerShell

Este tema describe cómo crear un proveedor de Windows PowerShell que puede manipular los datos en un almacén de datos. En este tema, se conocen como "elementos" de los datos de almacén de los elementos de datos en el almacén. Como consecuencia, un proveedor que puede manipular los datos en el almacén se conoce como un proveedor de elementos de Windows PowerShell.

> [!NOTE]
> Puede descargar el C# (AccessDBSampleProvider03.cs) de archivo de código fuente para este proveedor mediante el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components. Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.
>
> Para obtener más información acerca de otras implementaciones del proveedor de Windows PowerShell, consulte [diseñar su proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

El proveedor de elementos de Windows PowerShell que se describe en este tema obtiene los elementos de datos de una base de datos de Access. En este caso, un "elemento" es una tabla en la base de datos de Access o una fila en una tabla.

En la lista siguiente contiene las secciones de este tema. Si no está familiarizado con la escritura de un proveedor de elementos de Windows PowerShell, lea estas secciones en el orden en que aparecen. Sin embargo, si está familiarizado con la escritura de un proveedor de elementos de Windows PowerShell, vaya directamente a la información que necesita:

- [Definición de la clase de proveedor de Windows PowerShell elemento](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [Definir la funcionalidad de Base](#Defining-Base-Functionality)

- [Comprobación de validez de la ruta de acceso](#Checking-for-Path-Validity)

- [Determinar si existe un elemento](#Determining-if-an-Item-Exists)

- [Asociar los parámetros dinámicos a la `Test-Path` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [Recuperación de un elemento](#Retrieving-an-Item)

- [Asociar los parámetros dinámicos a la `Get-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [Definición de un elemento](#Setting-an-Item)

- [Asociar los parámetros dinámicos a la `Set-Item` Cmdlet](#Retrieving-Dynamic-Parameters-for-SetItem)

- [Borrar un elemento](#Clearing-an-Item)

- [Asociar los parámetros dinámicos al Cmdlet Cler Item](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [Llevar a cabo una acción predeterminada para un elemento](#Performing-a-Default-Action-for-an-Item)

- [Recuperar los parámetros dinámicos para InvokeDefaultAction](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [Implementación de métodos y clases auxiliares](#Implementing-Helper-Methods-and-Classes)

- [Ejemplo de código](#Code-Sample)

- [Definir los tipos de objeto y el formato](#Defining-Object-Types-and-Formatting)

- [Creación del proveedor de Windows PowerShell](#Building-the-Windows-PowerShell-provider)

- [Probar el proveedor de Windows PowerShell](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>Definición de la clase de proveedor de Windows PowerShell elemento

Un proveedor de elementos de Windows PowerShell debe definir una clase .NET que se deriva de la [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase base. La siguiente es la definición de clase para el proveedor de elementos que se describen en esta sección.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Tenga en cuenta que en esta definición, de la clase el [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo incluye dos parámetros. El primer parámetro especifica un nombre descriptivo para el proveedor que está usando Windows PowerShell. El segundo parámetro especifica las capacidades específicas de Windows PowerShell que expone el proveedor para el tiempo de ejecución de Windows PowerShell durante el procesamiento de comandos. Para este proveedor, no hay ningún agregadas capacidades específicas de Windows PowerShell.

## <a name="defining-base-functionality"></a>Definir la funcionalidad de Base

Como se describe en [proveedor de diseño de Windows PowerShell](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase se deriva de varias clases que proporcionan diferentes funcionalidad de proveedor. Un proveedor de elementos de Windows PowerShell, por lo tanto, debe definir toda la funcionalidad proporcionada por esas clases.

Para obtener más información acerca de cómo implementar la funcionalidad para agregar información de inicialización específicas de la sesión y para liberar los recursos utilizados por el proveedor, consulte [creación de un proveedor de PowerShell de Windows básico](./creating-a-basic-windows-powershell-provider.md). Sin embargo, la mayoría proveedores, incluidos el proveedor que se describe aquí, pueden usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.

Antes de que el proveedor de elementos de Windows PowerShell puede manipular los elementos en el almacén, debe implementar los métodos de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basar la clase para tener acceso al almacén de datos. Para obtener más información sobre la implementación de esta clase, vea [creación de un proveedor de la unidad de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Comprobación de validez de la ruta de acceso

Cuando se busca un elemento de datos, el tiempo de ejecución de Windows PowerShell proporciona una ruta de acceso de Windows PowerShell para el proveedor, tal como se define en la sección "Conceptos de PSPath" de [cómo Windows PowerShell funciona](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Un proveedor de elementos de Windows PowerShell debe comprobar la validez sintáctica y semántica de cualquier ruta de acceso pasado a él mediante la implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método. Este método devuelve `true` si la ruta de acceso es válido, y `false` en caso contrario. Ser consciente de que la implementación de este método no debe comprobar la existencia del elemento en la ruta de acceso, pero solo que la ruta de acceso es sintácticamente y correctos semánticamente.

Esta es la implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) método para este proveedor. Tenga en cuenta que esta implementación llama a un método de aplicación auxiliar de NormalizePath para convertir todos los separadores en la ruta de acceso a una uniforme.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Determinar si existe un elemento

Después de comprobar la ruta de acceso, el tiempo de ejecución de Windows PowerShell debe determinar si existe un elemento de datos en esa ruta de acceso. Para admitir este tipo de consulta, el proveedor de elementos de Windows PowerShell implementa la [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método. Este método devuelve `true` un elemento se encuentra en la ruta de acceso especificada y `false` (predeterminado) en caso contrario.

Esta es la implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método para este proveedor. Tenga en cuenta que este método llama a los métodos auxiliares PathIsDrive ChunkPath y GetTable y DatabaseTableInfo objeto definido por el usa un proveedor.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Cosas que recordar acerca de cómo implementar ItemExists

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Al definir la clase de proveedor, un proveedor de elementos de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) método debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las funciones especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- La implementación de este método debe controlar cualquier forma de acceso al elemento que podría hacer que el elemento visible para el usuario. Por ejemplo, si un usuario tiene acceso de escritura a un archivo mediante el proveedor FileSystem (proporcionado por Windows PowerShell), pero no el acceso de lectura, el archivo sigue existiendo y [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) devuelve `true`. Su implementación podría requerir la comprobación de un elemento primario para ver si el elemento secundario se puede enumerar.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Asociar los parámetros dinámicos para el Cmdlet Test-Path

A veces la `Test-Path` cmdlet que llama a [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) requiere parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos de Windows PowerShell debe implementar el proveedor de elementos de la [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) método. Este método recupera los parámetros dinámicos para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros para el `Test-Path` cmdlet.

Este proveedor de elementos de Windows PowerShell no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Recuperación de un elemento

Para recuperar un elemento, debe invalidar el proveedor de elementos de Windows PowerShell [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para admitir llamadas desde el `Get-Item` cmdlet. Este método escribe el elemento con el [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) método.

Esta es la implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para este proveedor. Tenga en cuenta que este método utiliza los métodos auxiliares GetTable y GetRow para recuperar los elementos que son las filas de una tabla de datos o tablas en la base de datos de Access.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Cosas que recordar acerca de cómo implementar GetItem

Las siguientes condiciones pueden aplicarse a una implementación de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Al definir la clase de proveedor, un proveedor de elementos de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeración. En estos casos, la implementación de [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) debe asegurarse de que la ruta de acceso que se pasa al método cumple esos requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben recuperar los objetos que se ocultan generalmente el usuario a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Por ejemplo, el [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método para las comprobaciones de proveedor del sistema de archivos la [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad antes de intentar llamar a [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) ocultos o archivos del sistema.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Asociar los parámetros dinámicos al Cmdlet Get-Item

A veces la `Get-Item` cmdlet requiere parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos de Windows PowerShell debe implementar el proveedor de elementos de la [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) método. Este método recupera los parámetros dinámicos para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros para el `Get-Item` cmdlet.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Definición de un elemento

Para establecer un elemento, debe invalidar el proveedor de elementos de Windows PowerShell la [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método para admitir llamadas desde el `Set-Item` cmdlet. Este método establece el valor del elemento en la ruta de acceso especificada.

Este proveedor no proporciona una invalidación para el [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) método. Sin embargo, la siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Cosas que recordar acerca de cómo implementar SetItem

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Al definir la clase de proveedor, un proveedor de elementos de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeración. En estos casos, la implementación de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) debe asegurarse de que la ruta de acceso que se pasa al método cumple esos requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben establecer o escribir en objetos que se ocultan al usuario a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Se debe enviar un error en la [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método si la ruta de acceso representa un elemento oculto y [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

- La implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) debe llamar al método [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)y comprobar su valor devuelto antes de realizar cualquier cambio en el almacén de datos. Este método se utiliza para confirmar la ejecución de una operación cuando se realiza un cambio en el almacén de datos, por ejemplo, eliminar archivos. El [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) método envía el nombre del recurso que se puede cambiar con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos para el usuario, o variables de preferencia de determinar lo que debe mostrarse.

  Después de llamar a [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve `true`, [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)debe llamar al método el [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envía un mensaje al usuario para que los comentarios comprobar si debe continuarse la operación. La llamada a [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite una comprobación adicional para las modificaciones del sistema potencialmente peligrosos.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Recuperar los parámetros dinámicos para SetItem

A veces la `Set-Item` cmdlet requiere parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos de Windows PowerShell debe implementar el proveedor de elementos de la [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) método. Este método recupera los parámetros dinámicos para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros para el `Set-Item` cmdlet.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Borrar un elemento

Para borrar un elemento, el proveedor de elementos de Windows PowerShell implementa la [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) método para admitir llamadas desde el `Clear-Item` cmdlet. Este método borra el elemento de datos en la ruta especificada.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Cosas que recordar acerca de cómo implementar ClearItem

Las siguientes condiciones pueden aplicarse a una implementación de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Al definir la clase de proveedor, un proveedor de elementos de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeración. En estos casos, la implementación de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) debe asegurarse de que la ruta de acceso que se pasa al método cumple esos requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben establecer o escribir en objetos que se ocultan al usuario a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Se debe enviar un error en la [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método si la ruta de acceso representa un elemento que se oculta al usuario y [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

- La implementación de la [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) debe llamar al método [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)y comprobar su valor devuelto antes de realizar cualquier cambio en el almacén de datos. Este método se utiliza para confirmar la ejecución de una operación cuando se realiza un cambio en el almacén de datos, por ejemplo, eliminar archivos. El [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) método envía el nombre del recurso que se puede cambiar para el usuario, con el tiempo de ejecución de Windows PowerShell y controlar cualquier configuración de línea de comandos o la preferencia variables de determinar lo que debe mostrarse.

  Después de llamar a [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve `true`, [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)debe llamar al método el [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envía un mensaje al usuario para que los comentarios comprobar si debe continuarse la operación. La llamada a [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite una comprobación adicional para las modificaciones del sistema potencialmente peligrosos.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Recuperar los parámetros dinámicos para ClearItem

A veces la `Clear-Item` cmdlet requiere parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos de Windows PowerShell debe implementar el proveedor de elementos de la [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) método. Este método recupera los parámetros dinámicos para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros para el `Clear-Item` cmdlet.

Este proveedor de elementos no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Llevar a cabo una acción predeterminada para un elemento

Puede implementar un proveedor de elementos de Windows PowerShell la [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) método para admitir llamadas desde el `Invoke-Item` cmdlet, que permite al proveedor a realizar una acción predeterminada para el elemento situado en la ruta de acceso especificada. Por ejemplo, el proveedor FileSystem podría usar este método para llamar a ShellExecute para un elemento específico.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Cosas que recordar acerca de cómo implementar InvokeDefaultAction

Las siguientes condiciones pueden aplicarse a una implementación de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Al definir la clase de proveedor, un proveedor de elementos de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeración. En estos casos, la implementación de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) debe asegurarse de que la ruta de acceso que se pasa al método cumple esos requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben establecer o escribir objetos ocultos al usuario a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Se debe enviar un error en la [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método si la ruta de acceso representa un elemento que se oculta al usuario y [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Recuperar los parámetros dinámicos para InvokeDefaultAction

A veces la `Invoke-Item` cmdlet requiere parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos de Windows PowerShell debe implementar el proveedor de elementos de la [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) método. Este método recupera los parámetros dinámicos para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros dinámicos a la `Invoke-Item` cmdlet.

Este proveedor de elementos no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementación de métodos y clases auxiliares

Este proveedor de elementos implementa varios métodos auxiliares y las clases que son utilizadas por el público reemplazar métodos definidos por Windows PowerShell. El código para estas clases y métodos auxiliares se muestran en el [código de ejemplo](#Code-Sample) sección.

### <a name="normalizepath-method"></a>Método NormalizePath

Este proveedor de elementos implementa un método de aplicación auxiliar de NormalizePath para asegurarse de que la ruta de acceso tiene un formato coherente. El formato especificado usa una barra diagonal inversa (\\) como separador.

### <a name="pathisdrive-method"></a>Método PathIsDrive

Este proveedor de elementos implementa un método de aplicación auxiliar de PathIsDrive para determinar si la ruta de acceso especificada es realmente el nombre de la unidad.

### <a name="chunkpath-method"></a>Método ChunkPath

Este proveedor de elementos implementa un método auxiliar ChunkPath que interrumpe la ruta de acceso especificada para que el proveedor pueda identificar sus elementos individuales. Devuelve una matriz que se compone de los elementos de la ruta de acceso.

### <a name="gettable-method"></a>Método getTable

Este proveedor de elementos implementa el método auxiliar GetTables que devuelve un objeto DatabaseTableInfo que representa información acerca de la tabla especificada en la llamada.

### <a name="getrow-method"></a>GetRow (método)

El [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) método del proveedor de este elemento llama al método de aplicación auxiliar de GetRows. Este método auxiliar recupera un objeto DatabaseRowInfo que representa información acerca de la fila especificada en la tabla.

### <a name="databasetableinfo-class"></a>Clase DatabaseTableInfo

El proveedor de este elemento define una clase de DatabaseTableInfo que representa una colección de información en una tabla de datos en la base de datos. Esta clase es similar a la [System.IO.Directoryinfo](/dotnet/api/System.IO.DirectoryInfo) clase.

El proveedor de elementos de ejemplo define un método de DatabaseTableInfo.GetTables que devuelve una colección de objetos de información de tabla define las tablas en la base de datos. Este método incluye un bloque try/catch para asegurarse de que cualquier error de base de datos se muestra como una fila con las entradas de cero.

### <a name="databaserowinfo-class"></a>DatabaseRowInfo Class

El proveedor de este elemento define la clase auxiliar DatabaseRowInfo que representa una fila en una tabla de la base de datos. Esta clase es similar a la [System.IO.Fileinfo](/dotnet/api/System.IO.FileInfo) clase.

El proveedor de ejemplo define un método DatabaseRowInfo.GetRows para devolver una colección de objetos de información de la fila de la tabla especificada. Este método incluye un bloque try/catch para capturar excepciones. No hay información de fila producirá errores.

## <a name="code-sample"></a>Ejemplo de código

Para el código de ejemplo completo, vea [AccessDbProviderSample03 código de ejemplo](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir los tipos de objeto y el formato

Al escribir un proveedor, puede ser necesario agregar a miembros a los objetos existentes o defina nuevos objetos. Cuando termine, cree un archivo de tipos que puede usar Windows PowerShell para identificar a los miembros del objeto y un archivo de formato que define cómo se muestra el objeto. Para obtener más información, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Creación del proveedor de Windows PowerShell

Consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Probar el proveedor de Windows PowerShell

Cuando se registra este proveedor de elementos de Windows PowerShell con Windows PowerShell, sólo puede probar las opciones básicas y funcionalidad del proveedor de la unidad. Para probar la manipulación de los elementos, también debe implementar funcionalidad del contenedor se describe en [implementar un proveedor de contenedor de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Véase también

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Creación de proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Proveedor de PowerShell de Windows de su diseño](./designing-your-windows-powershell-provider.md)

[Extensión de tipos de objeto y el formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo funciona Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Creación de un proveedor de contenedor Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Creación de un proveedor de la unidad de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)