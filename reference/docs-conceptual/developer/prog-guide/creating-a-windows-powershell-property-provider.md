---
title: Crear un proveedor de propiedades de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: c36b93a5b4d3e7ef92d7f5b16381a8def2dd5466
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360484"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Creación de un proveedor de propiedades de Windows PowerShell

En este tema se describe cómo crear un proveedor que permita al usuario manipular las propiedades de los elementos de un almacén de datos. Como consecuencia, este tipo de proveedor se conoce como proveedor de propiedades de Windows PowerShell. Por ejemplo, el proveedor del registro proporcionado por Windows PowerShell controla los valores de clave del registro como propiedades del elemento de clave del registro. Este tipo de proveedor debe agregar la interfaz [System. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) a la implementación de la clase .net.

> [!NOTE]
> Windows PowerShell proporciona un archivo de plantilla que puede usar para desarrollar un proveedor de Windows PowerShell. El archivo TemplateProvider.cs está disponible en el kit de desarrollo de software de Microsoft Windows para Windows Vista y .NET Framework componentes en tiempo de ejecución de 3,0. Para obtener instrucciones de descarga, consulte [Cómo instalar Windows PowerShell y descargar el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> La plantilla descargada está disponible en el directorio **@no__t ejemplos de 1PowerShell >** . Debe realizar una copia de este archivo y usar la copia para crear un nuevo proveedor de Windows PowerShell, quitando las funciones que no necesite.
>
> Para obtener más información sobre otras implementaciones del proveedor de Windows PowerShell, vea [diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Los métodos del proveedor de propiedades deben escribir cualquier objeto mediante el método [System. Management. Automation. Provider. Cmdletprovider. Writepropertyobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) .

## <a name="defining-the-windows-powershell-provider"></a>Definir el proveedor de Windows PowerShell

Un proveedor de propiedades debe crear una clase .NET que admita la interfaz [System. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) . Esta es la declaración de clase predeterminada del archivo TemplateProvider.cs proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definir la funcionalidad básica

La interfaz [System. Management. Automation. Provider. Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) se puede adjuntar a cualquiera de las clases base del proveedor, con la excepción de la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Agregue la funcionalidad básica requerida por la clase base que está utilizando. Para obtener más información sobre las clases base, vea [diseñar un proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Recuperar propiedades

Para recuperar las propiedades, el proveedor debe implementar el método [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) para admitir llamadas del cmdlet `Get-ItemProperty`. Este método recupera las propiedades del elemento que se encuentra en la ruta de acceso interna del proveedor especificado (completo).

El parámetro `providerSpecificPickList` indica las propiedades que se van a recuperar. Si este parámetro es `null` o está vacío, el método debe recuperar todas las propiedades. Además, [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) escribe una instancia de un objeto [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) que representa un contenedor de propiedades de las propiedades recuperadas. El método no debe devolver nada.

Se recomienda que la implementación de [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) admita la expansión de caracteres comodín de los nombres de propiedad para cada elemento de la lista de selección. Para ello, use la clase [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) para realizar la coincidencia de patrones de caracteres comodín.

Esta es la implementación predeterminada de [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) del archivo TemplateProvider.CS proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Aspectos que se deben recordar para implementar GetProperty

Se pueden aplicar las siguientes condiciones a su implementación de [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Al definir la clase de proveedor, un proveedor de propiedades de Windows PowerShell podría declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben recuperar un lector para objetos ocultos del usuario a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que está oculto para el usuario y [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Asociar parámetros dinámicos al cmdlet Get-ItemProperty

El cmdlet `Get-ItemProperty` podría requerir parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de propiedades de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) . El parámetro `path` indica que la ruta de acceso interna del proveedor es completa, mientras que el parámetro `providerSpecificPickList` especifica las propiedades específicas del proveedor que se escriben en la línea de comandos. Este parámetro puede ser `null` o estar vacío si las propiedades se canalizan al cmdlet. En este caso, este método devuelve un objeto que tiene propiedades y campos con los atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet.

Esta es la implementación predeterminada de [System. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) del archivo TemplateProvider.CS proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Establecer propiedades

Para establecer las propiedades, el proveedor de propiedades de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) para admitir llamadas del cmdlet `Set-ItemProperty`. Este método establece una o más propiedades del elemento en la ruta de acceso especificada y sobrescribe las propiedades proporcionadas según sea necesario. [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) también escribe una instancia de un objeto [System. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) que representa un contenedor de propiedades de las propiedades actualizadas.

Esta es la implementación predeterminada de [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) del archivo TemplateProvider.CS proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Aspectos que se deben recordar sobre la implementación de set-ItemProperty

Las condiciones siguientes pueden aplicarse a una implementación de [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Al definir la clase de proveedor, un proveedor de propiedades de Windows PowerShell podría declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben recuperar un lector para objetos ocultos del usuario a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que está oculto para el usuario y [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

- La implementación del método [System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cambios en el almacén de datos. Este método se usa para confirmar la ejecución de una operación cuando se realiza un cambio en el estado del sistema, por ejemplo, cambiar el nombre de los archivos. [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envía el nombre del recurso que se va a cambiar al usuario, con el tiempo de ejecución de Windows PowerShell y controlando cualquier configuración de línea de comandos o variables de preferencia para determinar qué debe mostrarse.

  Después de la llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve `true`, si se pueden realizar modificaciones de sistema potencialmente peligrosas, el [ El método System. Management. Automation. Provider. Ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) debe llamar al método [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Este método envía un mensaje de confirmación al usuario para permitir comentarios adicionales para indicar que la operación debe continuar.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Asociar los parámetros dinámicos para el cmdlet Set-ItemProperty

El cmdlet `Set-ItemProperty` podría requerir parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de propiedades de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Ipropertycmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) . Este método devuelve un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Se puede devolver el valor `null` si no se va a agregar ningún parámetro dinámico.

Esta es la implementación predeterminada de [System. Management. Automation. Provider. Ipropertycmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) del archivo TemplateProvider.CS proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Borrar propiedades

Para borrar propiedades, el proveedor de propiedades de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) para admitir llamadas del cmdlet `Clear-ItemProperty`. Este método establece una o más propiedades para el elemento situado en la ruta de acceso especificada.

Esta es la implementación predeterminada de [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) del archivo TemplateProvider.CS proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Cosas que recordar sobre la implementación de ClearProperty

Se pueden aplicar las siguientes condiciones a su implementación de [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Al definir la clase de proveedor, un proveedor de propiedades de Windows PowerShell podría declarar las capacidades del proveedor de ExpandWildcards, Filter, include o exclude de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . En estos casos, la implementación del método [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos de las capacidades especificadas. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, las propiedades [System. Management. Automation. Provider. Cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [System. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .

- De forma predeterminada, las invalidaciones de este método no deben recuperar un lector para objetos ocultos del usuario a menos que la propiedad [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) esté establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que está oculto para el usuario y [System. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

- La implementación del método [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) debe llamar a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cambios en el almacén de datos. Este método se usa para confirmar la ejecución de una operación antes de que se realice un cambio en el estado del sistema, como el borrado de contenido. [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envía el nombre del recurso que se va a cambiar al usuario, con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos o variables de preferencia para determinar Qué se debe mostrar.

  Después de la llamada a [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve `true`, si se pueden realizar modificaciones de sistema potencialmente peligrosas, el [ El método System. Management. Automation. Provider. Ipropertycmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) debe llamar al método [System. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Este método envía un mensaje de confirmación al usuario para permitir comentarios adicionales para indicar que la operación potencialmente peligrosa debe continuar.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Adjuntar parámetros dinámicos al cmdlet Clear-ItemProperty

El cmdlet `Clear-ItemProperty` podría requerir parámetros adicionales que se especifican dinámicamente en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, el proveedor de propiedades de Windows PowerShell debe implementar el método [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) . Este método devuelve un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) . Se puede devolver el valor `null` si no se va a agregar ningún parámetro dinámico.

Esta es la implementación predeterminada de [System. Management. Automation. Provider. Ipropertycmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) del archivo TemplateProvider.CS proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Compilar el proveedor de Windows PowerShell

Vea [Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Véase también

[Proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Diseño del proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Extender tipos de objeto y formato](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo registrar cmdlets, proveedores y aplicaciones host](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)