---
title: Crear un proveedor de elementos de Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: c60da62a06fcb40b6970d4209e991e57af733f33
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323190"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Creación de un proveedor de elementos de Windows PowerShell

En este tema se describe cómo crear un proveedor de Windows PowerShell que pueda manipular los datos de un almacén de datos. En este tema, se hace referencia a los elementos de datos del almacén como "elementos" del almacén de datos. Como consecuencia, se hace referencia a un proveedor que puede manipular los datos del almacén como un proveedor de elementos de Windows PowerShell.

> [!NOTE]
> Puede descargar el C# archivo de código fuente (AccessDBSampleProvider03.CS) para este proveedor mediante el kit de desarrollo de software de Microsoft Windows para Windows Vista y los componentes de tiempo de ejecución de .NET Framework 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Los archivos de código fuente descargados  **\<** están disponibles en el directorio de ejemplos de PowerShell >.
>
> Para obtener más información sobre otras implementaciones del proveedor de Windows PowerShell, vea [diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

El proveedor de elementos de Windows PowerShell que se describe en este tema obtiene elementos de datos de una base de datos de Access. En este caso, un "elemento" es una tabla de la base de datos de Access o una fila de una tabla.

## <a name="defining-the-windows-powershell-item-provider-class"></a>Definir la clase de proveedor de elementos de Windows PowerShell

Un proveedor de elementos de Windows PowerShell debe definir una clase .NET que derive de la clase base [System. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . A continuación se indica la definición de clase para el proveedor de elementos descrito en esta sección.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Tenga en cuenta que en esta definición de clase, el atributo [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) incluye dos parámetros. El primer parámetro especifica un nombre descriptivo para el proveedor que usa Windows PowerShell. El segundo parámetro especifica las capacidades específicas de Windows PowerShell que el proveedor expone al tiempo de ejecución de Windows PowerShell durante el procesamiento de comandos. Para este proveedor, no hay ninguna funcionalidad específica de Windows PowerShell adicional.

## <a name="defining-base-functionality"></a>Definir la funcionalidad básica

Como se describe en [diseñar un proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md), la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) se deriva de otras clases que proporcionan una funcionalidad de proveedor diferente. Por lo tanto, un proveedor de elementos de Windows PowerShell debe definir toda la funcionalidad proporcionada por esas clases.

Para obtener más información sobre cómo implementar la funcionalidad para agregar información de inicialización específica de la sesión y para liberar los recursos utilizados por el proveedor, consulte [crear un proveedor básico de Windows PowerShell](./creating-a-basic-windows-powershell-provider.md). Sin embargo, la mayoría de los proveedores, incluido el proveedor descrito aquí, pueden usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.

Antes de que el proveedor de elementos de Windows PowerShell pueda manipular los elementos del almacén, debe implementar los métodos de la clase base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) para tener acceso al almacén de datos. Para obtener más información sobre la implementación de esta clase, vea [crear un proveedor de unidades de Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Comprobando la validez de la ruta de acceso

Al buscar un elemento de datos, el tiempo de ejecución de Windows PowerShell suministra una ruta de acceso de Windows PowerShell al proveedor, tal como se define en la sección "conceptos de PSPath" de [Cómo funciona Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). Un proveedor de elementos de Windows PowerShell debe comprobar la validez sintáctica y semántica de cualquier ruta de acceso que se le haya pasado implementando el método [System. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) . Este método devuelve `true` si la ruta de acceso es válida `false` y, de lo contrario,. Tenga en cuenta que la implementación de este método no debe comprobar la existencia del elemento en la ruta de acceso, pero solo la ruta de acceso es sintácticamente correcta y semánticamente.

Esta es la implementación del método [System. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) para este proveedor. Tenga en cuenta que esta implementación llama a un método auxiliar de NormalizePath para convertir todos los separadores de la ruta de acceso en una uniforme.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Determinar si existe un elemento

Después de comprobar la ruta de acceso, el tiempo de ejecución de Windows PowerShell debe determinar si un elemento de datos existe en esa ruta de acceso. Para admitir este tipo de consulta, el proveedor de elementos de Windows PowerShell implementa el método [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) . Este método devuelve `true` un elemento que se encuentra en la ruta de `false` acceso especificada y, de lo contrario, es (valor predeterminado).

Esta es la implementación del método [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) para este proveedor. Tenga en cuenta que este método llama a los métodos auxiliares PathIsDrive, ChunkPath y GetTable, y usa un objeto DatabaseTableInfo definido por el proveedor.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Aspectos que se deben recordar sobre la implementación de ItemExists

Se pueden aplicar las siguientes condiciones a su implementación de [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- Al definir la clase de proveedor, un proveedor de elementos de Windows PowerShell podría declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- La implementación de este método debe controlar cualquier forma de acceso al elemento que pueda hacer que el elemento sea visible para el usuario. Por ejemplo, si un usuario tiene acceso de escritura a un archivo a través del proveedor FileSystem (proporcionado por Windows PowerShell), pero no de acceso de lectura, el archivo sigue existiendo y [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) devuelve `true`. La implementación puede requerir la comprobación de un elemento primario para ver si el elemento secundario se puede enumerar.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Adjuntar parámetros dinámicos al cmdlet Test-path

A veces `Test-Path` , el cmdlet que llama a [System. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) requiere parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de elementos de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Itemcmdletprovider. Itemexistsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) . Este método recupera los parámetros dinámicos para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o [System. Management. Automation. Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar `Test-Path` los parámetros al cmdlet.

Este proveedor de elementos de Windows PowerShell no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Recuperar un elemento

Para recuperar un elemento, el proveedor de elementos de Windows PowerShell debe invalidar el método [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) para admitir llamadas del `Get-Item` cmdlet. Este método escribe el elemento mediante el método [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .

Esta es la implementación del método [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) para este proveedor. Tenga en cuenta que este método usa los métodos de aplicación auxiliar GetTable y GetRow para recuperar elementos que son tablas en la base de datos de Access o en filas de una tabla de datos.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Aspectos que se deben recordar sobre la implementación de GetItem

Las condiciones siguientes pueden aplicarse a una implementación de [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- Al definir la clase de proveedor, un proveedor de elementos de Windows PowerShell podría declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación de [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) debe asegurarse de que la ruta de acceso que se pasa al método cumple esos requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben recuperar objetos que normalmente están ocultos del usuario a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Por ejemplo, el método [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) para el proveedor filesystem comprueba la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) antes de intentar llamar a. [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) para los archivos ocultos o del sistema.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Adjuntar parámetros dinámicos al cmdlet Get-Item

A veces `Get-Item` , el cmdlet requiere parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de elementos de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) . Este método recupera los parámetros dinámicos para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o [System. Management. Automation. Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar `Get-Item` los parámetros al cmdlet.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Establecer un elemento

Para establecer un elemento, el proveedor de elementos de Windows PowerShell debe invalidar el método [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) para `Set-Item` admitir llamadas del cmdlet. Este método establece el valor del elemento en la ruta de acceso especificada.

Este proveedor no proporciona una invalidación para el método [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) . Sin embargo, la siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Aspectos que se deben recordar sobre la implementación de SetItem

Se pueden aplicar las siguientes condiciones a su implementación de [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- Al definir la clase de proveedor, un proveedor de elementos de Windows PowerShell podría declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación de [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) debe asegurarse de que la ruta de acceso que se pasa al método cumple esos requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben establecer ni escribir objetos que estén ocultos para el usuario a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Se debe enviar un error al método [System. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) si la ruta de acceso representa un elemento oculto y [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

- La implementación del método [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de efectuar cualquier cambio en el almacén de datos. Este método se utiliza para confirmar la ejecución de una operación cuando se realiza un cambio en el almacén de datos, por ejemplo, la eliminación de archivos. El método [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envía el nombre del recurso que se va a cambiar al usuario, con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos o variables de preferencia en determinar lo que se debe mostrar.

  Después de que se devuelva `true`la llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) , el método [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) debe llamar a la [ Método System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Este método envía un mensaje al usuario para permitir que los comentarios comprueben si la operación debe continuar. La llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite realizar una comprobación adicional de las modificaciones del sistema potencialmente peligrosas.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Recuperando parámetros dinámicos para SetItem

A veces `Set-Item` , el cmdlet requiere parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de elementos de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) . Este método recupera los parámetros dinámicos para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o [System. Management. Automation. Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar `Set-Item` los parámetros al cmdlet.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Borrar un elemento

Para borrar un elemento, el proveedor de elementos de Windows PowerShell implementa el método [System. Management. Automation. Provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) para admitir llamadas `Clear-Item` del cmdlet. Este método borra el elemento de datos en la ruta de acceso especificada.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Aspectos que se deben recordar sobre la implementación de ClearItem

Las condiciones siguientes pueden aplicarse a una implementación de [System. Management. Automation. Provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- Al definir la clase de proveedor, un proveedor de elementos de Windows PowerShell podría declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación de [System. Management. Automation. Provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) debe asegurarse de que la ruta de acceso que se pasa al método cumple esos requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben establecer ni escribir objetos que estén ocultos para el usuario a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Se debe enviar un error al método [System. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) si la ruta de acceso representa un elemento que está oculto para el usuario y [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) establezca en `false`.

- La implementación del método [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de efectuar cualquier cambio en el almacén de datos. Este método se utiliza para confirmar la ejecución de una operación cuando se realiza un cambio en el almacén de datos, por ejemplo, la eliminación de archivos. El método [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envía el nombre del recurso que se va a cambiar al usuario, con el tiempo de ejecución de Windows PowerShell y controla cualquier configuración de línea de comandos o variables de preferencia en determinar lo que se debe mostrar.

  Después de que se devuelva `true`la llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) , el método [System. Management. Automation. Provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) debe llamar a la [ Método System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Este método envía un mensaje al usuario para permitir que los comentarios comprueben si la operación debe continuar. La llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) permite realizar una comprobación adicional de las modificaciones del sistema potencialmente peligrosas.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Recuperación de parámetros dinámicos para ClearItem

A veces `Clear-Item` , el cmdlet requiere parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de elementos de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) . Este método recupera los parámetros dinámicos para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o [System. Management. Automation. Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar `Clear-Item` los parámetros al cmdlet.

Este proveedor de elementos no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Realizar una acción predeterminada para un elemento

Un proveedor de elementos de Windows PowerShell puede implementar el método [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) para admitir `Invoke-Item` llamadas del cmdlet, lo que permite al proveedor realizar una acción predeterminada. para el elemento en la ruta de acceso especificada. Por ejemplo, el proveedor FileSystem podría usar este método para llamar a ShellExecute para un elemento específico.

Este proveedor no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Aspectos que se deben recordar sobre la implementación de InvokeDefaultAction

Las condiciones siguientes pueden aplicarse a una implementación de [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- Al definir la clase de proveedor, un proveedor de elementos de Windows PowerShell podría declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación de [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) debe asegurarse de que la ruta de acceso que se pasa al método cumple esos requisitos. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben establecer ni escribir objetos ocultos del usuario a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Se debe enviar un error al método [System. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) si la ruta de acceso representa un elemento que está oculto para el usuario y [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) establezca en `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Recuperación de parámetros dinámicos para InvokeDefaultAction

A veces `Invoke-Item` , el cmdlet requiere parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de elementos de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) . Este método recupera los parámetros dinámicos para el elemento en la ruta de acceso indicada y devuelve un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o [System. Management. Automation. Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los `Invoke-Item` parámetros dinámicos al cmdlet.

Este proveedor de elementos no implementa este método. Sin embargo, el código siguiente es la implementación predeterminada de este método.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementar métodos y clases auxiliares

Este proveedor de elementos implementa varios métodos y clases auxiliares que usan los métodos de invalidación públicos definidos por Windows PowerShell. El código de estos métodos auxiliares y clases se muestra en la sección [código de ejemplo](#code-sample) .

### <a name="normalizepath-method"></a>Método NormalizePath

Este proveedor de elementos implementa un método auxiliar de NormalizePath para asegurarse de que la ruta de acceso tiene un formato coherente. El formato especificado usa una barra diagonal inversa\\() como separador.

### <a name="pathisdrive-method"></a>Método PathIsDrive

Este proveedor de elementos implementa un método auxiliar de PathIsDrive para determinar si la ruta de acceso especificada es realmente el nombre de la unidad.

### <a name="chunkpath-method"></a>Método ChunkPath

Este proveedor de elementos implementa un método auxiliar ChunkPath que divide la ruta de acceso especificada para que el proveedor pueda identificar sus elementos individuales. Devuelve una matriz formada por los elementos de la ruta de acceso.

### <a name="gettable-method"></a>GetTable (método)

Este proveedor de elementos implementa el método auxiliar GetTables que devuelve un objeto DatabaseTableInfo que representa información sobre la tabla especificada en la llamada.

### <a name="getrow-method"></a>Método GetRow

El método [System. Management. Automation. Provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) de este proveedor de elementos llama al método auxiliar de GetRows. Este método auxiliar recupera un objeto DatabaseRowInfo que representa información sobre la fila especificada en la tabla.

### <a name="databasetableinfo-class"></a>Clase DatabaseTableInfo

Este proveedor de elementos define una clase DatabaseTableInfo que representa una colección de información de una tabla de datos de la base de datos. Esta clase es similar a la clase [System. IO. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .

El proveedor del elemento de ejemplo define un método DatabaseTableInfo. GetTables que devuelve una colección de objetos de información de tabla que definen las tablas de la base de datos. Este método incluye un bloque try/catch para asegurarse de que cualquier error de base de datos se muestra como una fila con cero entradas.

### <a name="databaserowinfo-class"></a>Clase DatabaseRowInfo

Este proveedor de elementos define la clase auxiliar DatabaseRowInfo que representa una fila de una tabla de la base de datos. Esta clase es similar a la clase [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) .

El proveedor de ejemplo define un método DatabaseRowInfo. GetRows para devolver una colección de objetos de información de fila para la tabla especificada. Este método incluye un bloque try/catch para detectar excepciones. Los errores no producirán ninguna información de fila.

## <a name="code-sample"></a>Código de ejemplo

Para obtener el código de ejemplo completo, vea el [ejemplo de código AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definir tipos de objeto y formato

Al escribir un proveedor, puede ser necesario agregar miembros a los objetos existentes o definir nuevos objetos. Cuando termine, cree un archivo de tipos que Windows PowerShell pueda usar para identificar a los miembros del objeto y un archivo de formato que define cómo se muestra el objeto. Para obtener más información acerca de, vea [extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Compilar el proveedor de Windows PowerShell

Vea [Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Probar el proveedor de Windows PowerShell

Cuando este proveedor de elementos de Windows PowerShell se registra con Windows PowerShell, solo puede probar la funcionalidad básica y de unidad del proveedor. Para probar la manipulación de los elementos, también debe implementar la funcionalidad de contenedor descrita en [implementación de un proveedor de Windows PowerShell de contenedor](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Vea también

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guía del programador de Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Crear proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Diseño del proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo funciona Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Creación de un contenedor de Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Crear un proveedor de Windows PowerShell para la unidad](./creating-a-windows-powershell-drive-provider.md)

[Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)