---
title: Creación de un proveedor de contenido de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: 35c68a2b0f8c9bd1ed4fc54c41aa427ddd75907c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081927"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Creación de un proveedor de contenido de Windows PowerShell

Este tema describe cómo crear un proveedor de Windows PowerShell que permite al usuario manipular el contenido de los elementos de un almacén de datos. Como consecuencia, un proveedor que puede manipular el contenido de los elementos se conoce como un proveedor de contenido de Windows PowerShell.

> [!NOTE]
> Puede descargar el C# (AccessDBSampleProvider06.cs) de archivo de código fuente para este proveedor mediante el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components. Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Están disponibles en los archivos de origen descargado el  **\<ejemplos de PowerShell >** directory.
>
> Para obtener más información acerca de otras implementaciones del proveedor de Windows PowerShell, consulte [diseñar su proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

En la lista siguiente contiene las secciones de este tema. Si no está familiarizado con la escritura de un proveedor de contenido de Windows PowerShell, lea estas secciones en el orden en que aparecen. Sin embargo, si está familiarizado con la escritura de un proveedor de contenido de Windows PowerShell, vaya directamente a la información que necesita.

- [Definición de la clase de proveedor de contenido de PowerShell de Windows](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [Definir la funcionalidad de Base](#Define-Functionality-of-Base-Class)

- [Implementación de un lector de contenido](#Implementing-a-Content-Reader)

- [Implementar un sistema de escritura de contenido](#Implementing-a-Content-Writer)

- [Recuperando el lector de contenido](#Retrieving-the-Content-Reader)

- [Asociar los parámetros dinámicos a la `Get-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [Recuperar el sistema de escritura de contenido](#Retrieving-the-Content-Writer)

- [Asociar los parámetros dinámicos a la Add_Content y `Set-Content` Cmdlets](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [Borrar contenido](#Clearing-Content)

- [Asociar los parámetros dinámicos a la `Clear-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [Ejemplo de código](#Code-Sample)

- [Definir los tipos de objeto y el formato](#defining-object-types-and-formatting)

- [Creación del proveedor de Windows PowerShell](#Building-the-Windows-PowerShell-Provider)

- [Probar el proveedor de Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a>Definir la clase de proveedor de contenido de PowerShell de Windows

Un proveedor de contenido de Windows PowerShell debe crear una clase .NET que admita la [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaz. Esta es la definición de clase para el proveedor de elementos que se describen en esta sección.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Tenga en cuenta que en esta definición, de la clase el [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo incluye dos parámetros. El primer parámetro especifica un nombre descriptivo para el proveedor que está usando Windows PowerShell. El segundo parámetro especifica las capacidades específicas de Windows PowerShell que expone el proveedor para el tiempo de ejecución de Windows PowerShell durante el procesamiento de comandos. Para este proveedor, no hay ningún agregadas capacidades específicas de Windows PowerShell.

## <a name="define-functionality-of-base-class"></a>Definir la funcionalidad de la clase Base

Como se describe en [proveedor de diseño de Windows PowerShell](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase se deriva de varias clases que proporcionan funcionalidad proveedor diferente. Un proveedor de contenido de Windows PowerShell, por lo tanto, normalmente define toda la funcionalidad proporcionada por esas clases.

Para obtener más información acerca de cómo implementar la funcionalidad para agregar información de inicialización específicas de la sesión y para liberar los recursos utilizados por el proveedor, consulte [creación de un proveedor de PowerShell de Windows básico](./creating-a-basic-windows-powershell-provider.md). Sin embargo, la mayoría proveedores, incluidos el proveedor que se describe aquí, pueden usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.

Para obtener acceso al almacén de datos, el proveedor debe implementar los métodos de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase base. Para obtener más información acerca de cómo implementar estos métodos, consulte [creación de un proveedor de la unidad de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular los elementos de un almacén de datos, como introducción, configuración y elementos de compensación, el proveedor debe implementar los métodos proporcionados por el [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) clase base. Para obtener más información acerca de cómo implementar estos métodos, consulte [creación de un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Para trabajar en almacenes de datos de varias capas, el proveedor debe implementar los métodos proporcionados por el [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) clase base. Para obtener más información acerca de cómo implementar estos métodos, consulte [creación de un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

Para admitir comandos recursivos, los contenedores anidados y las rutas de acceso relativas, el proveedor debe implementar la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase base. Además, este proveedor de contenido de Windows PowerShell puede adjunta [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interfaz para el [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase base y, por lo tanto, debe implementar los métodos proporcionados por esa clase. Para obtener más información, vea implementar esos métodos, consulte [implementar un proveedor de navegación de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementación de un lector de contenido

Para leer el contenido de un elemento, un proveedor debe implementa una clase de lector del contenido que se derive de [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader). El lector de contenido para este proveedor permite el acceso al contenido de una fila en una tabla de datos. Define la clase de lector contenido un **lectura** método que recupera los datos de las filas indicadas y devuelve una lista que representa los datos, un **Seek** método que se mueve el lector de contenido, un  **Cerrar** método que cierra el lector de contenido, y un **Dispose** método.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implementar un sistema de escritura de contenido

Para escribir contenido en un elemento, un proveedor debe implementar un contenido deriva de la clase del escritor [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter). Define la clase del escritor contenido un **escribir** método que escribe el contenido de la fila especificada, un **Seek** método que el sistema de escritura de contenido, se mueve un **cerrar** método que se cierra el sistema de escritura de contenido y un **Dispose** método.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Recuperando el lector de contenido

Para obtener el contenido de un elemento, el proveedor debe implementar la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) para admitir la `Get-Content` cmdlet. Este método devuelve el lector de contenido para el elemento situado en la ruta de acceso especificada. A continuación, se puede abrir el objeto de lector para leer el contenido.

Esta es la implementación de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) para este método para este proveedor.

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Cosas que recordar acerca de cómo implementar GetContentReader

Las siguientes condiciones pueden aplicarse a una implementación de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Al definir la clase de proveedor, un proveedor de contenido de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) método debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos del elemento especificado capacidades. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben recuperar un lector para los objetos que se ocultan al usuario a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que se oculta al usuario y [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Asociar los parámetros dinámicos al Cmdlet Get-Content

El `Get-Content` cmdlet podría requerir parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenido de Windows PowerShell debe implementar la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) método. Este método recupera los parámetros dinámicos para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet.

Este proveedor de contenedores de Windows PowerShell no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Recuperar el sistema de escritura de contenido

Para escribir contenido en un elemento, el proveedor debe implementar la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) para admitir la `Set-Content` y `Add-Content` cmdlets. Este método devuelve el escritor de contenido para el elemento situado en la ruta de acceso especificada.

Esta es la implementación de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) para este método.

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Cosas que recordar acerca de cómo implementar GetContentWriter

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Al definir la clase de proveedor, un proveedor de contenido de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) método debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos del elemento especificado capacidades. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben recuperar un sistema de escritura para los objetos que se ocultan al usuario a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que se oculta al usuario y [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Asociar los parámetros dinámicos a los Cmdlets Add-Content y Set-Content

El `Add-Content` y `Set-Content` cmdlets podría requerir parámetros dinámicos adicionales que se agregan a un tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenido de Windows PowerShell debe implementar la [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) método para controlar estos parámetros. Este método recupera los parámetros dinámicos para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros a los cmdlets.

Este proveedor de contenedores de Windows PowerShell no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Borrar contenido

El proveedor de contenido implementa el [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método de apoyo el `Clear-Content` cmdlet. Este método quita el contenido del elemento en la ruta de acceso especificada, pero deja intacto el elemento.

Esta es la implementación de la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método para este proveedor.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Cosas que recordar acerca de cómo implementar ClearContent

Las siguientes condiciones pueden aplicarse a una implementación de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Al definir la clase de proveedor, un proveedor de contenido de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) método debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos del elemento especificado capacidades. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben borrar el contenido de los objetos que se ocultan al usuario a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que se oculta al usuario y [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

- La implementación de la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) debe llamar al método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cualquier cambio en el almacén de datos. Este método se utiliza para confirmar la ejecución de una operación cuando se realiza un cambio en el almacén de datos, como borrar el contenido. El [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) método envía el nombre del recurso que se puede cambiar para el usuario, con el tiempo de ejecución de Windows PowerShell que cualquier configuración de línea de comandos o la preferencia de control variables de determinar lo que debe mostrarse.

  Después de llamar a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve `true`, [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) debe llamar al método el [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envía un mensaje al usuario para que los comentarios comprobar si debe continuarse la operación. La llamada a [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite una comprobación adicional para las modificaciones del sistema potencialmente peligrosos.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Asociar los parámetros dinámicos para el Cmdlet Clear-Content

El `Clear-Content` cmdlet podría requerir parámetros dinámicos adicionales que se agregan en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenido de Windows PowerShell debe implementar la [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) método para controlar estos parámetros. Este método recupera los parámetros para el elemento situado en la ruta de acceso indicada. Este método recupera los parámetros dinámicos para el elemento situado en la ruta de acceso indicada y devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet.

Este proveedor de contenedores de Windows PowerShell no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Ejemplo de código

Para el código de ejemplo completo, vea [AccessDbProviderSample06 código de ejemplo](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir los tipos de objeto y el formato

Al escribir un proveedor, puede ser necesario agregar a miembros a los objetos existentes o defina nuevos objetos. Al hacerlo, debe crear un archivo de tipos que puede usar Windows PowerShell para identificar a los miembros del objeto y un archivo de formato que define cómo se muestra el objeto. Para obtener más información, consulte [extender los tipos de objeto y formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Creación del proveedor de Windows PowerShell

Consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Probar el proveedor de Windows PowerShell

Cuando se ha registrado el proveedor de Windows PowerShell con Windows PowerShell, puede probarla mediante la ejecución de los cmdlets compatibles en la línea de comandos. Por ejemplo, probar el proveedor de contenido de ejemplo.

Use la `Get-Content` cmdlet para recuperar el contenido del elemento especificado en la tabla de base de datos en la ruta de acceso especificada por el `Path` parámetro. El `ReadCount` parámetro especifica el número de elementos para el lector de contenido definido leer (el valor predeterminado es 1). Con la siguiente entrada de comando, el cmdlet recupera dos filas (elementos) de la tabla y muestra su contenido. Tenga en cuenta que la salida del ejemplo siguiente utiliza una base de datos de Access ficticia.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
ID        : 1
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
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>Véase también

[Crear proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Proveedor de PowerShell de Windows de su diseño](./designing-your-windows-powershell-provider.md)

[Extensión de tipos de objeto y el formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementar un proveedor de navegación Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)
