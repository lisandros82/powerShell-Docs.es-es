---
title: Crear un proveedor de contenido de Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: 4afe0370f7a2c5b17826544e94e76650611c9d68
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417509"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Creación de un proveedor de contenido de Windows PowerShell

En este tema se describe cómo crear un proveedor de Windows PowerShell que permita al usuario manipular el contenido de los elementos de un almacén de datos. Como consecuencia, un proveedor que puede manipular el contenido de los elementos se conoce como proveedor de contenido de Windows PowerShell.

> [!NOTE]
> Puede descargar el C# archivo de código fuente (AccessDBSampleProvider06.CS) para este proveedor mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de código fuente descargados están disponibles en el directorio **\<ejemplos de PowerShell >** .
>
> Para obtener más información sobre otras implementaciones del proveedor de Windows PowerShell, vea [diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="define-the-windows-powershell-content-provider-class"></a>Definición de la clase de proveedor de contenido de Windows PowerShell

Un proveedor de contenido de Windows PowerShell debe crear una clase .NET que admita la interfaz [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) . Esta es la definición de clase para el proveedor de elementos que se describe en esta sección.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Tenga en cuenta que en esta definición de clase, el atributo [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) incluye dos parámetros. El primer parámetro especifica un nombre descriptivo para el proveedor que usa Windows PowerShell. El segundo parámetro especifica las capacidades específicas de Windows PowerShell que el proveedor expone al tiempo de ejecución de Windows PowerShell durante el procesamiento de comandos. Para este proveedor, no hay ninguna funcionalidad específica de Windows PowerShell adicional.

## <a name="define-functionality-of-base-class"></a>Definir la funcionalidad de la clase base

Como se describe en [diseñar un proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md), la clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) se deriva de otras clases que proporcionan una funcionalidad de proveedor diferente. Por lo tanto, un proveedor de contenido de Windows PowerShell suele definir toda la funcionalidad proporcionada por esas clases.

Para obtener más información sobre cómo implementar la funcionalidad para agregar información de inicialización específica de la sesión y para liberar los recursos utilizados por el proveedor, consulte [crear un proveedor básico de Windows PowerShell](./creating-a-basic-windows-powershell-provider.md). Sin embargo, la mayoría de los proveedores, incluido el proveedor descrito aquí, pueden usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.

Para tener acceso al almacén de datos, el proveedor debe implementar los métodos de la clase base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Para obtener más información sobre la implementación de estos métodos, vea [crear un proveedor de unidades de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Para manipular los elementos de un almacén de datos, como obtener, establecer y borrar elementos, el proveedor debe implementar los métodos proporcionados por la clase base [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Para obtener más información sobre la implementación de estos métodos, vea [crear un proveedor de elementos de Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Para trabajar en almacenes de datos de varias capas, el proveedor debe implementar los métodos proporcionados por la clase base [System. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Para obtener más información sobre la implementación de estos métodos, vea [crear un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

Para admitir comandos recursivos, contenedores anidados y rutas de acceso relativas, el proveedor debe implementar la clase base [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Además, este proveedor de contenido de Windows PowerShell puede asociar la interfaz [System. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) a la clase base [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) y, por tanto, debe implementar los métodos proporcionados por esa clase. Para obtener más información, vea implementar estos métodos, vea [implementar un proveedor de navegación de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementar un lector de contenido

Para leer el contenido de un elemento, un proveedor debe implementar una clase de lector de contenido que derive de [System. Management. Automation. Provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader). El lector de contenido para este proveedor permite el acceso al contenido de una fila de una tabla de datos. La clase de lector de contenido define un método de **lectura** que recupera los datos de la fila indicada y devuelve una lista que representa los datos, un método de **búsqueda** que mueve el lector de contenido, un método de **cierre** que cierra el lector de contenido y un método **Dispose** .

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implementar un escritor de contenido

Para escribir contenido en un elemento, un proveedor debe implementar una clase de escritor de contenido que derive de [System. Management. Automation. Provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter). La clase de escritor de contenido define un método de **escritura** que escribe el contenido de fila especificado, un método de **búsqueda** que mueve el escritor de contenido, un método de **cierre** que cierra el escritor de contenido y un método **Dispose** .

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Recuperación del lector de contenido

Para obtener contenido de un elemento, el proveedor debe implementar [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) para admitir el cmdlet `Get-Content`. Este método devuelve el lector de contenido para el elemento situado en la ruta de acceso especificada. A continuación, se puede abrir el objeto lector para leer el contenido.

Esta es la implementación de [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) para este método para este proveedor.

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

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Aspectos que se deben recordar sobre la implementación de GetContentReader

Las condiciones siguientes pueden aplicarse a una implementación de [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Al definir la clase de proveedor, un proveedor de contenido de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben recuperar un lector para objetos ocultos del usuario a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que está oculto para el usuario y [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Adjuntar parámetros dinámicos al cmdlet Get-Content

El cmdlet `Get-Content` podría requerir parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenido de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) . Este método recupera los parámetros dinámicos para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con los atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet.

Este proveedor de contenedores de Windows PowerShell no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Recuperación del escritor de contenido

Para escribir contenido en un elemento, el proveedor debe implementar [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) para admitir los cmdlets `Set-Content` y `Add-Content`. Este método devuelve el escritor de contenido para el elemento situado en la ruta de acceso especificada.

Esta es la implementación de [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) para este método.

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

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Aspectos que se deben recordar sobre la implementación de GetContentWriter

Se pueden aplicar las siguientes condiciones a su implementación de [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Al definir la clase de proveedor, un proveedor de contenido de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben recuperar un sistema de escritura para los objetos que están ocultos del usuario a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que está oculto para el usuario y [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Adjuntar parámetros dinámicos a los cmdlets Add-Content y set-Content

Los cmdlets `Add-Content` y `Set-Content` pueden requerir parámetros dinámicos adicionales que se agregan en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenido de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) para administrar estos parámetros. Este método recupera los parámetros dinámicos para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con los atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros a los cmdlets.

Este proveedor de contenedores de Windows PowerShell no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Borrar contenido

El proveedor de contenido implementa el método [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) para admitir el cmdlet `Clear-Content`. Este método quita el contenido del elemento en la ruta de acceso especificada, pero deja el elemento intacto.

Esta es la implementación del método [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) para este proveedor.

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Aspectos que se deben recordar sobre la implementación de ClearContent

Las condiciones siguientes pueden aplicarse a una implementación de [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Al definir la clase de proveedor, un proveedor de contenido de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben borrar el contenido de los objetos que se ocultan al usuario a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que está oculto para el usuario y [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

- La implementación del método [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cambios en el almacén de datos. Este método se usa para confirmar la ejecución de una operación cuando se realiza un cambio en el almacén de datos, como borrar el contenido. El método [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envía el nombre del recurso que se va a cambiar al usuario, con el tiempo de ejecución de Windows PowerShell que controla cualquier configuración de línea de comandos o variables de preferencia para determinar lo que se debe mostrar.

  Después de que la llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelva `true`, el método [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) debe llamar al método [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Este método envía un mensaje al usuario para permitir que los comentarios comprueben si la operación debe continuar. La llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite realizar una comprobación adicional de las modificaciones del sistema potencialmente peligrosas.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Adjuntar parámetros dinámicos al cmdlet Clear-Content

El cmdlet `Clear-Content` puede requerir parámetros dinámicos adicionales que se agregan en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de contenido de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) para administrar estos parámetros. Este método recupera los parámetros para el elemento en la ruta de acceso indicada. Este método recupera los parámetros dinámicos para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con los atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet.

Este proveedor de contenedores de Windows PowerShell no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Código de ejemplo

Para obtener el código de ejemplo completo, vea el [ejemplo de código AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto y formato

Al escribir un proveedor, puede ser necesario agregar miembros a los objetos existentes o definir nuevos objetos. Una vez hecho esto, debe crear un archivo de tipos que Windows PowerShell pueda usar para identificar a los miembros del objeto y un archivo de formato que define cómo se muestra el objeto. Para obtener más información, vea [extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Compilar el proveedor de Windows PowerShell

Vea [Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Probar el proveedor de Windows PowerShell

Cuando el proveedor de Windows PowerShell se ha registrado con Windows PowerShell, puede probarlo mediante la ejecución de los cmdlets admitidos en la línea de comandos. Por ejemplo, pruebe el proveedor de contenido de ejemplo.

Use el cmdlet `Get-Content` para recuperar el contenido del elemento especificado en la tabla de la base de datos en la ruta de acceso especificada por el parámetro `Path`. El parámetro `ReadCount` especifica el número de elementos que el lector de contenido definido debe leer (el valor predeterminado es 1). Con la siguiente entrada de comando, el cmdlet recupera dos filas (elementos) de la tabla y muestra su contenido. Tenga en cuenta que en la siguiente salida de ejemplo se utiliza una base de datos de Access ficticia.

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

## <a name="see-also"></a>Vea también

[Crear proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Diseño del proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementar un proveedor de navegación de Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md)

[Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)
