---
title: Creación de un proveedor de PowerShell de Windows básico | Microsoft Docs
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
ms.openlocfilehash: 19cc3817016d96e1412a5f3506e9d694ba55b48d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082080"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Diseño de un proveedor de Windows PowerShell básico

En este tema es el punto de partida para aprender a crear un proveedor de Windows PowerShell. El proveedor básico que se describen aquí proporciona métodos para iniciar y detener el proveedor y, aunque este proveedor no proporciona un medio para tener acceso a un almacén de datos o para obtener o establecer los datos en el almacén de datos, proporcionan la funcionalidad básica requerida por todos los proveedores.

Como se mencionó anteriormente, el proveedor básico descrito aquí implementa métodos para iniciar y detener el proveedor. El tiempo de ejecución de Windows PowerShell llama a estos métodos para inicializar y anular la inicialización del proveedor.

> [!NOTE]
> Puede encontrar un ejemplo de este proveedor en el archivo AccessDBSampleProvider01.cs proporcionado por Windows PowerShell.

Las secciones de este tema incluyen lo siguiente:

- [Definición de la clase de proveedor de PowerShell de Windows](#Defining-the-Windows-PowerShell-Provider-Class)

- [Definir la información de estado específica del proveedor](#Defining-Provider-Specific-State-Information)

- [Inicializar el proveedor](#Initializing-the-Provider)

- [Iniciar los parámetros dinámicos](#Start-Dynamic-Parameters)

- [Cancelar la inicialización del proveedor](#Uninitializing-the-Provider)

- [Ejemplo de código](#Code-Sample)

- [Probar el proveedor de Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definición de la clase de proveedor de PowerShell de Windows

El primer paso para crear un proveedor de Windows PowerShell es definir su clase. NET. Este proveedor básico define una clase denominada `AccessDBProvider` que se deriva el [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) clase base.

Se recomienda que coloque las clases de proveedor en un `Providers` espacio de nombres de su espacio de nombres de API, por ejemplo, xxx. PowerShell.Providers. Este proveedor utiliza la `Microsoft.Samples.PowerShell.Provider` espacio de nombres, en el que se ejecutan todas las muestras de proveedor de Windows PowerShell.

> [!NOTE]
> La clase para un proveedor de Windows PowerShell debe marcarse explícitamente como pública. Las clases no está marcadas como público predeterminado será interno y no se encontrará el tiempo de ejecución de Windows PowerShell.

Esta es la definición de clase para este proveedor básico:

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Justo antes de la definición de clase debe declarar la [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo con la sintaxis [CmdletProvider()].

Puede establecer las palabras clave de atributo para declarar aún más la clase si es necesario. Tenga en cuenta que el [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo declarado aquí incluye dos parámetros. El primer parámetro de atributo especifica el nombre predeterminado para el proveedor, que el usuario puede modificar más adelante. El segundo parámetro especifica las capacidades definidas en Windows PowerShell que expone el proveedor para el tiempo de ejecución de Windows PowerShell durante el procesamiento de comandos. Los valores posibles para las capacidades del proveedor se definen mediante la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. Se trata de un proveedor de base, es compatible con ninguna capacidad.

> [!NOTE]
> El nombre completo del proveedor de Windows PowerShell incluye el nombre del ensamblado y otros atributos que se determina mediante Windows PowerShell tras el registro del proveedor.

## <a name="defining-provider-specific-state-information"></a>Definir la información de estado específica del proveedor

El [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) clase base y todas las clases derivadas se consideran sin estado porque el tiempo de ejecución de Windows PowerShell crea instancias del proveedor solo según sea necesario. Por lo tanto, si su proveedor requiere control total y el mantenimiento de estado para los datos específicos del proveedor, debe derivar una clase de la [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) clase. La clase derivada debe definir los miembros necesarios para mantener el estado para que los datos específicos del proveedor pueden obtenerse cuando el tiempo de ejecución de Windows PowerShell llama a la [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método para inicializar el proveedor.

Un proveedor de Windows PowerShell también puede mantener el estado de conexión. Para obtener más información sobre cómo mantener el estado de conexión, consulte [creación de un proveedor de la unidad de PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Inicializar el proveedor

Para inicializar el proveedor, las llamadas en tiempo de ejecución de Windows PowerShell la [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método cuando se inicia Windows PowerShell. En su mayor parte, el proveedor puede usar la implementación predeterminada de este método, que simplemente devuelve el [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objeto que describe el proveedor. Sin embargo, en el caso donde desea agregar la información de inicialización adicionales, debe implementar su propio [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método que devuelve una versión modificada de la [ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objeto que se pasa al proveedor. En general, este método debe devolver proporcionado [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objeto pasa a él o una modificada [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objeto contiene información de inicialización.

Este proveedor básico no invalida este método. Sin embargo, el código siguiente muestra la implementación predeterminada de este método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

El proveedor puede mantener el estado de la información específica del proveedor como se describe en [estado de los datos específicos del proveedor definir](#Defining-Provider-Specific-State-Information). En este caso, debe invalidar la implementación de la [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método para devolver una instancia de la clase derivada.

## <a name="start-dynamic-parameters"></a>Iniciar los parámetros dinámicos

La implementación del proveedor de la [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método puede requerir parámetros adicionales. En este caso, debe invalidar el proveedor la [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) método y devolver un objeto que tiene las propiedades y campos con el análisis de atributos similar a un clase del cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto.

Este proveedor básico no invalida este método. Sin embargo, el código siguiente muestra la implementación predeterminada de este método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Cancelar la inicialización del proveedor

Para liberar los recursos que usa el proveedor de Windows PowerShell, el proveedor debe implementar su propio [System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) método. Este método es invocado por el tiempo de ejecución de Windows PowerShell para anular la inicialización del proveedor en el cierre de sesión.

Este proveedor básico no invalida este método. Sin embargo, el código siguiente muestra la implementación predeterminada de este método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Ejemplo de código

Para el código de ejemplo completo, vea [AccessDbProviderSample01 código de ejemplo](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Probar el proveedor de Windows PowerShell

Una vez que se ha registrado el proveedor de Windows PowerShell con Windows PowerShell, puede probarla mediante la ejecución de los cmdlets compatibles en la línea de comandos. Para este proveedor básica, ejecute el nuevo shell y usar el `Get-PSProvider` cmdlet para recuperar la lista de proveedores y asegúrese de que el proveedor de AccessDb está presente.

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

[Creación de proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)