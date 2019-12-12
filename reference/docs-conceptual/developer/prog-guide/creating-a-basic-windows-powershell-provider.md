---
title: Crear un proveedor básico de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: e825581b96f0f33893b38f9f6499dd46a7bf38eb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360524"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Diseño de un proveedor de Windows PowerShell básico

Este tema es el punto de partida para aprender a crear un proveedor de Windows PowerShell. El proveedor básico que se describe aquí proporciona métodos para iniciar y detener el proveedor y, aunque este proveedor no proporciona un medio para tener acceso a un almacén de datos o para obtener o establecer los datos en el almacén de datos, proporciona la funcionalidad básica que requiere todos los proveedores.

Como se mencionó anteriormente, el proveedor básico que se describe aquí implementa métodos para iniciar y detener el proveedor. El tiempo de ejecución de Windows PowerShell llama a estos métodos para inicializar y anular la inicialización del proveedor.

> [!NOTE]
> Puede encontrar un ejemplo de este proveedor en el archivo AccessDBSampleProvider01.cs proporcionado por Windows PowerShell.

## <a name="defining-the-windows-powershell-provider-class"></a>Definir la clase de proveedor de Windows PowerShell

El primer paso para crear un proveedor de Windows PowerShell es definir su clase .NET. Este proveedor básico define una clase denominada `AccessDBProvider` que se deriva de la clase base [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .

Se recomienda colocar las clases de proveedor en un espacio de nombres `Providers` del espacio de nombres de la API, por ejemplo, xxx. PowerShell. Providers. Este proveedor usa el espacio de nombres `Microsoft.Samples.PowerShell.Provider`, en el que se ejecutan todos los ejemplos del proveedor de Windows PowerShell.

> [!NOTE]
> La clase de un proveedor de Windows PowerShell debe marcarse explícitamente como Public. Las clases no marcadas como públicas tendrán como valor predeterminado Internal y no se encontrarán en tiempo de ejecución de Windows PowerShell.

Esta es la definición de clase para este proveedor básico:

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Justo antes de la definición de clase, debe declarar el atributo [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) con la sintaxis [CmdletProvider ()].

Puede establecer palabras clave de atributo para declarar más la clase si es necesario. Observe que el atributo [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) declarado aquí incluye dos parámetros. El primer parámetro de atributo especifica el nombre descriptivo predeterminado para el proveedor, que el usuario puede modificar más adelante. El segundo parámetro especifica las capacidades definidas por Windows PowerShell que el proveedor expone al tiempo de ejecución de Windows PowerShell durante el procesamiento de comandos. Los valores posibles para las capacidades del proveedor se definen mediante la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Dado que se trata de un proveedor base, no admite ninguna funcionalidad.

> [!NOTE]
> El nombre completo del proveedor de Windows PowerShell incluye el nombre del ensamblado y otros atributos determinados por Windows PowerShell en el momento del registro del proveedor.

## <a name="defining-provider-specific-state-information"></a>Definir la información de estado específica del proveedor

La clase base [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) y todas las clases derivadas se consideran sin estado porque el tiempo de ejecución de Windows PowerShell crea instancias de proveedor solo según sea necesario. Por consiguiente, si el proveedor requiere un control total y el mantenimiento del estado de los datos específicos del proveedor, debe derivar una clase de la clase [System. Management. Automation. providerinfo devuelto por](/dotnet/api/System.Management.Automation.ProviderInfo) . La clase derivada debe definir los miembros necesarios para mantener el estado de forma que se pueda tener acceso a los datos específicos del proveedor cuando el tiempo de ejecución de Windows PowerShell llame al método [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) para inicializar el proveedor.

Un proveedor de Windows PowerShell también puede mantener el estado basado en la conexión. Para obtener más información sobre cómo mantener el estado de conexión, vea [crear un proveedor de unidades de PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Inicializar el proveedor

Para inicializar el proveedor, el tiempo de ejecución de Windows PowerShell llama al método [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) cuando se inicia Windows PowerShell. En su mayor parte, el proveedor puede usar la implementación predeterminada de este método, que simplemente devuelve el objeto [System. Management. Automation. providerinfo devuelto por](/dotnet/api/System.Management.Automation.ProviderInfo) que describe el proveedor. Sin embargo, en caso de que desee agregar información de inicialización adicional, debe implementar su propio método [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) que devuelve una versión modificada del objeto [System. Management. Automation. providerinfo devuelto por](/dotnet/api/System.Management.Automation.ProviderInfo) que se pasa al proveedor. En general, este método debe devolver el objeto [System. Management. Automation. providerinfo devuelto por](/dotnet/api/System.Management.Automation.ProviderInfo) proporcionado que se le ha pasado o un objeto [System. Management. Automation. providerinfo devuelto por](/dotnet/api/System.Management.Automation.ProviderInfo) modificado que contiene otra información de inicialización.

Este proveedor básico no invalida este método. Sin embargo, en el código siguiente se muestra la implementación predeterminada de este método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

El proveedor puede mantener el estado de la información específica del proveedor, tal como se describe en definir el estado de los [datos específicos del proveedor](#defining-provider-specific-state-information). En este caso, la implementación debe reemplazar el método [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) para devolver una instancia de la clase derivada.

## <a name="start-dynamic-parameters"></a>Iniciar parámetros dinámicos

La implementación del proveedor del método [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) podría requerir parámetros adicionales. En este caso, el proveedor debe reemplazar el método [System. Management. Automation. Provider. Cmdletprovider. Startdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) y devolver un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .

Este proveedor básico no invalida este método. Sin embargo, en el código siguiente se muestra la implementación predeterminada de este método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Anulando la inicialización del proveedor

Para liberar los recursos que usa el proveedor de Windows PowerShell, el proveedor debe implementar su propio método [System. Management. Automation. Provider. Cmdletprovider. Stop *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) . Este método es llamado por el tiempo de ejecución de Windows PowerShell para anular la inicialización del proveedor al cerrar una sesión.

Este proveedor básico no invalida este método. Sin embargo, en el código siguiente se muestra la implementación predeterminada de este método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Ejemplo de código

Para obtener el código de ejemplo completo, vea el [ejemplo de código AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Probar el proveedor de Windows PowerShell

Una vez que el proveedor de Windows PowerShell se ha registrado con Windows PowerShell, puede probarlo mediante la ejecución de los cmdlets admitidos en la línea de comandos. Para este proveedor básico, ejecute el nuevo Shell y use el cmdlet `Get-PSProvider` para recuperar la lista de proveedores y asegurarse de que el proveedor AccessDb está presente.

```powershell
Get-PSProvider
```

Aparecerá el siguiente resultado:

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>Véase también

[Crear proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Diseño del proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)
