---
title: Creación de un proveedor de propiedades de PowerShell de Windows | Microsoft Docs
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
ms.openlocfilehash: 6ec0752a9ae06c5c2cdd1a1851caeeff52d8eb74
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055162"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Creación de un proveedor de propiedades de Windows PowerShell

Este tema describe cómo crear un proveedor que permite al usuario manipular las propiedades de elementos en un almacén de datos. Como consecuencia, este tipo de proveedor se conoce como un proveedor de propiedades de Windows PowerShell. Por ejemplo, el proveedor del registro proporcionado por los valores clave del registro controladores de Windows PowerShell como propiedades del elemento clave del registro. Debe agregar este tipo de proveedor de la [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfaz a la implementación de la clase. NET.

> [!NOTE]
> Windows PowerShell proporciona un archivo de plantilla que puede usar para desarrollar un proveedor de Windows PowerShell. El archivo TemplateProvider.cs está disponible en el Microsoft Windows Software Development Kit para Windows Vista y .NET Framework 3.0 Runtime Components. Para obtener instrucciones de descarga, vea [cómo instalar Windows PowerShell y descarga el SDK de Windows PowerShell](/powershell/developer/installing-the-windows-powershell-sdk).
>
> La plantilla descargada está disponible en el  **\<ejemplos de PowerShell >** directory. Debe realizar una copia de este archivo y usar la copia para crear un nuevo proveedor de Windows PowerShell, quitar cualquier funcionalidad que no es necesario.
>
> Para obtener más información acerca de otras implementaciones del proveedor de Windows PowerShell, consulte [diseñar su proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Los métodos de su proveedor de propiedades deben escribir los objetos mediante el [System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) método.

En la lista siguiente contiene las secciones de este tema. Si no está familiarizado con la escritura de un proveedor de propiedades de Windows PowerShell, lea esta información en el orden en que aparece. Sin embargo, si está familiarizado con la escritura de un proveedor de propiedades de Windows PowerShell, vaya directamente a la información que necesita.

- [Define el proveedor de Windows PowerShell](#Defining-the-Windows-PowerShell-provider)

- [Definir la funcionalidad de Base](#Defining-Base-Functionality)

- [Recuperación de propiedades](#Retrieving-Properties)

- [Asociar los parámetros dinámicos a la `Get-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [Establecer las propiedades](#Setting-Properties)

- [Asociar los parámetros dinámicos a la `Set-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [Cuando se borra una propiedad](#Clearing-Properties)

- [Asociar los parámetros dinámicos a la `Clear-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [Creación del proveedor de Windows PowerShell](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>Define el proveedor de Windows PowerShell

Un proveedor de propiedades debe crear una clase .NET que admita la [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfaz. Aquí es la declaración de clase predeterminada desde el archivo TemplateProvider.cs proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definir la funcionalidad de Base

El [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) interfaz se puede adjuntar a cualquiera de las clases base del proveedor, con la excepción de la [ System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase. Agregar la funcionalidad básica requerida por la clase base que está usando. Para obtener más información acerca de las clases bases, vea [diseñar su proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Recuperación de propiedades

Para recuperar las propiedades, el proveedor debe implementar la [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) método para admitir llamadas desde el `Get-ItemProperty` cmdlet. Este método recupera las propiedades del elemento situado en la ruta de acceso interna del proveedor especificado (completo).

El `providerSpecificPickList` parámetro indica qué propiedades se deben recuperar. Si este parámetro es `null` o está vacío, el método debe recuperar todas las propiedades. Además, [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) escribe una instancia de un [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objeto que representa un bolsa de propiedades de las propiedades recuperadas. El método debe devolver nada.

Se recomienda que la implementación de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) admite la expansión de caracteres comodín de los nombres de propiedad para cada elemento en la lista de selección. Para ello, use el [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) clase para realizar la coincidencia de patrones de caracteres comodín.

Esta es la implementación predeterminada de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) desde el archivo TemplateProvider.cs proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Cosas que recordar acerca de cómo implementar GetProperty

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Al definir la clase de proveedor, un proveedor de propiedades de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos del elemento especificado (método) capacidades. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben recuperar un lector para los objetos que se ocultan al usuario a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que se oculta al usuario y [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Asociar los parámetros dinámicos al Cmdlet Get-ItemProperty.

El `Get-ItemProperty` cmdlet podría requerir parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, debe implementar el proveedor de propiedades de Windows PowerShell la [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) método. El `path` parámetro indica un nombre completo interno del proveedor de ruta de acceso, mientras que el `providerSpecificPickList` parámetro especifica las propiedades específicas del proveedor especificadas en la línea de comandos. Este parámetro puede ser `null` o vacío si las propiedades se canalizan al cmdlet. En este caso, este método devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El tiempo de ejecución de Windows PowerShell usa el objeto devuelto para agregar los parámetros al cmdlet.

Esta es la implementación predeterminada de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) desde el archivo TemplateProvider.cs proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Establecer las propiedades

Para establecer propiedades, debe implementar el proveedor de propiedades de Windows PowerShell la [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método para admitir llamadas desde el `Set-ItemProperty` cmdlet. Este método establece una o varias propiedades del elemento en la ruta de acceso especificada y sobrescribe las propiedades proporcionadas según sea necesario. [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) también escribe una instancia de un [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objeto que representa un contenedor de propiedades de la actualización Propiedades.

Esta es la implementación predeterminada de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) desde el archivo TemplateProvider.cs proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Cosas que recordar sobre la implementación de Set-ItemProperty.

Las siguientes condiciones pueden aplicarse a una implementación de [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Al definir la clase de proveedor, un proveedor de propiedades de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) método debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos del elemento especificado capacidades. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben recuperar un lector para los objetos que se ocultan al usuario a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que se oculta al usuario y [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

- La implementación de la [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) debe llamar al método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cualquier cambio en el almacén de datos. Este método se utiliza para confirmar la ejecución de una operación cuando se modifica el estado del sistema, por ejemplo, cambiar el nombre de archivos. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envía el nombre del recurso que se puede cambiar para el usuario, con el tiempo de ejecución de Windows PowerShell y cualquier configuración de línea de comandos o variables de preferencia en la determinación de control ¿Qué se debe mostrar.

  Después de llamar a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve `true`, si se pueden realizar las modificaciones del sistema potencialmente peligrosos, el [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) debe llamar al método el [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envía un mensaje de confirmación al usuario para que los comentarios adicionales indicar que debe continuarse la operación.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Asociar los parámetros dinámicos para el Cmdlet Set-ItemProperty.

El `Set-ItemProperty` cmdlet podría requerir parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, debe implementar el proveedor de propiedades de Windows PowerShell la [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) método. Este método devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El `null` valor puede devolverse si no hay parámetros dinámicos que se van a ser agregados.

Esta es la implementación predeterminada de [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) desde el archivo TemplateProvider.cs proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Borrar propiedades

Para borrar las propiedades, debe implementar el proveedor de propiedades de Windows PowerShell la [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) método para admitir llamadas desde el `Clear-ItemProperty` cmdlet. Este método establece una o varias propiedades para el elemento situado en la ruta de acceso especificada.

Esta es la implementación predeterminada de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) desde el archivo TemplateProvider.cs proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Lo que debe recordar acerca de cómo implementar ClearProperty

Las siguientes condiciones pueden aplicarse a la implementación de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Al definir la clase de proveedor, un proveedor de propiedades de Windows PowerShell puede declarar las capacidades del proveedor de ExpandWildcards, filtro, Include o Exclude, desde el [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. En estos casos, la implementación de la [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) debe asegurarse de que la ruta de acceso que se pasa al método cumple los requisitos del elemento especificado (método) capacidades. Para ello, el método debe tener acceso a la propiedad adecuada, por ejemplo, el [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) y [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) propiedades.

- De forma predeterminada, las invalidaciones de este método no deben recuperar un lector para los objetos que se ocultan al usuario a menos que el [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) propiedad está establecida en `true`. Se debe escribir un error si la ruta de acceso representa un elemento que se oculta al usuario y [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) está establecido en `false`.

- La implementación de la [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) debe llamar al método [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) y comprobar su valor devuelto antes de realizar cualquier cambio en el almacén de datos. Este método se utiliza para confirmar la ejecución de una operación antes de que se realiza un cambio en el estado del sistema, como borrar el contenido. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) envía el nombre del recurso que se puede cambiar para el usuario, con el tiempo de ejecución de Windows PowerShell teniendo en cuenta cualquier configuración de línea de comandos o variables de preferencia en determinar lo que debe mostrarse.

  Después de llamar a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) devuelve `true`, si se pueden realizar las modificaciones del sistema potencialmente peligrosos, el [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) debe llamar al método el [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) método. Este método envía un mensaje de confirmación al usuario para que los comentarios adicionales indicar que debe continuarse la operación potencialmente peligrosa.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Asociar los parámetros dinámicos al Cmdlet Clear-ItemProperty.

El `Clear-ItemProperty` cmdlet podría requerir parámetros adicionales que se especifican de forma dinámica en tiempo de ejecución. Para proporcionar estos parámetros dinámicos, debe implementar el proveedor de propiedades de Windows PowerShell la [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) método. Este método devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto. El `null` valor puede devolverse si no hay parámetros dinámicos que se van a ser agregados.

Esta es la implementación predeterminada de [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) desde el archivo TemplateProvider.cs proporcionado por Windows PowerShell.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Creación del proveedor de Windows PowerShell

Consulte [cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Véase también

[Proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Proveedor de PowerShell de Windows de su diseño](./designing-your-windows-powershell-provider.md)

[Extensión de tipos de objeto y el formato](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Cómo registrar Cmdlets, proveedores y aplicaciones Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)