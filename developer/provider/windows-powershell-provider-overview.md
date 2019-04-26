---
title: Información general sobre el proveedor de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 0d4addc0a064873701ae15c204dbd335f3374ab7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080921"
---
# <a name="windows-powershell-provider-overview"></a>Información general sobre Proveedor de Windows PowerShell

Un proveedor de Windows PowerShell permite a cualquier almacén de datos se exponga como un sistema de archivos como si fuese una unidad montada. Por ejemplo, el proveedor de registro integrado permite navegar por el registro como deberá desplazarse el `c` unidad del equipo. También puede invalidar un proveedor de la `Item` cmdlets (por ejemplo, `Get-Item`, `Set-Item`, etc.) que se pueden tratar los datos en el almacén de datos, como archivos y directorios se tratan al navegar por un sistema de archivos. Para obtener más información acerca de los proveedores y las unidades y los proveedores integrados en Windows PowerShell, consulte [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Los proveedores y unidades

Un proveedor define la lógica que se usa para tener acceso a, explorar y editar un almacén de datos, mientras que una unidad especifica un punto de entrada específica para un almacén de datos (o una parte de un almacén de datos) que es del tipo definido por el proveedor. Por ejemplo, el proveedor del registro permite obtener acceso a los subárboles y claves en un registro y las unidades HKLM y HKCU especifican los subárboles del registro correspondientes. Las unidades HKLM y HKCU usan el proveedor de registro.

Al escribir un proveedor, puede especificar unidades predeterminado que se crean automáticamente cuando el proveedor está disponible. También define un método para crear nuevas unidades que usan ese proveedor.

## <a name="type-of-providers"></a>Tipo de proveedores

Hay varios tipos de proveedores, cada uno de los cuales proporciona un nivel de funcionalidad diferentes. Un proveedor se implementa como una clase que derive de uno de los descendientes de los [System.Management.Automation.Sessionstatecategory.Cmdletprovider](/dotnet/api/System.Management.Automation.SessionStateCategory.CmdletProvider) clase. Para obtener información sobre los diferentes tipos de proveedores, consulte [tipos de proveedor](./provider-types.md).

## <a name="provider-cmdlets"></a>Cmdlets de proveedor

Los proveedores pueden implementar métodos que corresponden a los cmdlets, crear comportamientos personalizados para estos cmdlets cuando se usa en una unidad para ese proveedor. Según el tipo de proveedor, diferentes conjuntos de cmdlets están disponibles. Para obtener una lista completa de los cmdlets disponibles para la personalización de los proveedores, consulte [cmdlets de proveedor](./provider-cmdlets.md).

## <a name="provider-paths"></a>Rutas de acceso del proveedor

Los usuarios navegar por las unidades del proveedor, como los sistemas de archivos. Por este motivo, esperan que la sintaxis de las rutas de acceso para que coincida con las rutas de exploración del sistema de archivos. Cuando un usuario ejecuta un cmdlet de proveedor, especifique una ruta de acceso al elemento que desea tener acceso. La ruta de acceso especificada se puede interpretar de varias maneras. Un proveedor debe admitir uno o varios de los siguientes tipos de ruta de acceso.

### <a name="drive-qualified-paths"></a>Rutas de acceso completa a la unidad

Una ruta de acceso completa a la unidad es una combinación de la unidad de Windows PowerShell a través del cual se tiene acceso al elemento, el contenedor y subcontenedores en el que se encuentra el elemento y el nombre del elemento. (Las unidades se definen mediante el proveedor que se usa para tener acceso al almacén de datos. Esta ruta de acceso comienza con el nombre de la unidad seguido de dos puntos (:). Por ejemplo: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Rutas de acceso completo del proveedor

Para permitir que el motor de Windows PowerShell inicializar y anular la inicialización de su proveedor, el proveedor debe admitir una ruta de acceso de proveedor. Por ejemplo, el usuario puede inicializar y anular la inicialización del proveedor del sistema de archivos, ya que define la siguiente ruta de acceso completo del proveedor: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Rutas de acceso directo del proveedor

Para permitir el acceso remoto a su proveedor de Windows PowerShell, debe admitir una ruta de acceso directo del proveedor para pasar directamente al proveedor de Windows PowerShell para la ubicación actual. Por ejemplo, puede usar el proveedor de Windows PowerShell del registro `\\server\regkeypath` como una ruta de acceso directo del proveedor.

### <a name="provider-internal-paths"></a>Rutas de acceso interna del proveedor

Para permitir que el cmdlet de proveedor obtener acceso a datos mediante interfaces de programación de aplicaciones (API) de que no sean de Windows PowerShell, el proveedor de Windows PowerShell debe admitir una ruta de acceso interna del proveedor. Esta ruta de acceso se indica después de la "::" en la ruta de acceso de proveedor. Por ejemplo, la ruta de acceso interna del proveedor para el proveedor de filesystem de Windows PowerShell es `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Reemplazar parámetros de cmdlet

El comportamiento de algunos cmdlets específicos del proveedor puede reemplazarse por un proveedor. Para que obtener una lista de parámetros que se pueden invalidar y cómo reemplazar en la clase de proveedor, consulte [parámetros de cmdlet de proveedor](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>Parámetros dinámicos

Los proveedores pueden definir los parámetros dinámicos que se agregan a un cmdlet de proveedor cuando el usuario especifica un valor determinado para uno de los parámetros del cmdlet estáticos. Para ello, un proveedor de implementación de uno o varios métodos de parámetros dinámicos. Para obtener una lista de parámetros de cmdlet que puede usarse para agregar el parámetro dinámico y los métodos usados para implementarlos, consulte [parámetros dinámicos del cmdlet de proveedor](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Capacidades del proveedor

El [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración define una serie de funcionalidades que los proveedores pueden admitir. Éstos incluyen la capacidad para usar caracteres comodín, filtrar elementos y compatibilidad con transacciones. Para especificar las capacidades de un proveedor, agregue una lista de valores de la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración, combinada con un valor lógico `OR` operación, como el [ System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) propiedad (el segundo parámetro del atributo) de la [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo para la clase de proveedor. Por ejemplo, el atributo siguiente especifica que el proveedor admite la [System.Management.Automation.Provider.Providercapabilities.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.ShouldProcess) y [ System.Management.Automation.Provider.Providercapabilities.Transactions](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.Transactions) capacidades.

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Ayuda del cmdlet de proveedor

Al escribir un proveedor, puede implementar su propia ayuda de los cmdlets de proveedor que proporciona soporte técnico. Esto incluye un solo tema de ayuda para cada cmdlet de proveedor o de varias versiones de un tema de ayuda para los casos donde actúa el cmdlet de proveedor de forma distinta según el uso de parámetros dinámicos. Para admitir la Ayuda de cmdlet específico del proveedor, el proveedor debe implementar la [System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) interfaz.

El motor de Windows PowerShell que llama a la [System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) método para mostrar el tema de ayuda para los cmdlets de proveedor. El motor de proporciona el nombre del cmdlet que el usuario especificado cuando se ejecuta el `Get-Help` cmdlet y la ruta de acceso actual del usuario. La ruta de acceso actual es necesario si el proveedor implementa distintas versiones del mismo proveedor cmdlet para unidades distintas. El método debe devolver una cadena que contiene el XML de la Ayuda del cmdlet.

Se escribe el contenido del archivo de ayuda mediante PSMAML XML. Este es el mismo esquema XML que se usa para escribir contenido de ayuda para cmdlets independientes. Agregue el contenido de su cmdlet personalizado ayuda al archivo de ayuda para el proveedor en el `CmdletHelpPaths` elemento. El ejemplo siguiente se muestra el `command` (elemento) para un cmdlet de proveedor único y muestra cómo especificar el nombre del cmdlet de proveedor que el proveedor. Es compatible con

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>Véase también

[Funcionalidad de proveedor de PowerShell de Windows](./provider-types.md)

[Cmdlets de proveedor](./provider-cmdlets.md)

[Escribir un proveedor de Windows PowerShell](./writing-a-windows-powershell-provider.md)