---
title: Información general del proveedor de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 81f6c8cd75ccea9e711cd8f6d6daa6cca5a499a0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366294"
---
# <a name="windows-powershell-provider-overview"></a>Información general sobre Proveedor de Windows PowerShell

Un proveedor de Windows PowerShell permite que cualquier almacén de datos se exponga como un sistema de archivos como si fuera una unidad montada. Por ejemplo, el proveedor de registro integrado le permite navegar por el registro como si fuera la unidad de `c` del equipo. Un proveedor también puede invalidar los cmdlets de `Item` (por ejemplo, `Get-Item`, `Set-Item`, etc.) de forma que los datos del almacén de datos se puedan tratar como archivos y directorios se tratan al navegar por un sistema de archivos. Para obtener más información sobre los proveedores y las unidades, y los proveedores integrados en Windows PowerShell, consulte [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).

## <a name="providers-and-drives"></a>Proveedores y unidades

Un proveedor define la lógica que se utiliza para obtener acceso, navegar y editar un almacén de datos, mientras que una unidad especifica un punto de entrada específico a un almacén de datos (o una parte de un almacén de datos) que es del tipo definido por el proveedor. Por ejemplo, el proveedor del registro permite tener acceso a los subárboles y las claves de un registro, y las unidades HKLM y HKCU especifican los subárboles correspondientes en el registro. Las unidades HKLM y HKCU usan el proveedor del registro.

Al escribir un proveedor, puede especificar las unidades de discos predeterminadas que se crean automáticamente cuando el proveedor está disponible. También se define un método para crear unidades nuevas que usan ese proveedor.

## <a name="type-of-providers"></a>Tipo de proveedores

Hay varios tipos de proveedores, cada uno de los cuales proporciona un nivel de funcionalidad diferente. Un proveedor se implementa como una clase que se deriva de uno de los descendientes de la clase [System. Management. Automation. SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory?view=pscore-6.2.0) **CmdletProvider** . Para obtener información sobre los diferentes tipos de proveedores, consulte [tipos de proveedor](./provider-types.md).

## <a name="provider-cmdlets"></a>Cmdlets de proveedor

Los proveedores pueden implementar métodos que se corresponden con los cmdlets de, creando comportamientos personalizados para esos cmdlets cuando se usan en una unidad para ese proveedor. Dependiendo del tipo de proveedor, están disponibles diferentes conjuntos de cmdlets. Para obtener una lista completa de los cmdlets disponibles para la personalización en proveedores, consulte [cmdlets de proveedor](./provider-cmdlets.md).

## <a name="provider-paths"></a>Rutas de proveedor

Los usuarios navegan por unidades de proveedor como sistemas de archivos. Por este motivo, esperan que la sintaxis de las rutas de acceso corresponda a las rutas de acceso utilizadas en la navegación del sistema de archivos. Cuando un usuario ejecuta un cmdlet de proveedor, especifica una ruta de acceso al elemento al que se va a acceder. La ruta de acceso especificada se puede interpretar de varias maneras. Un proveedor debe admitir uno o varios de los siguientes tipos de ruta de acceso.

### <a name="drive-qualified-paths"></a>Rutas de acceso calificadas por unidad

Una ruta de acceso completa a una unidad es una combinación del nombre del elemento, el contenedor y los subcontenedores en los que se encuentra el elemento, y la unidad de Windows PowerShell a través de la que se tiene acceso al elemento. (Las unidades se definen mediante el proveedor que se utiliza para tener acceso al almacén de datos. Esta ruta de acceso comienza con el nombre de la unidad seguido de dos puntos (:). Por ejemplo: `get-childitem C:`

### <a name="provider-qualified-paths"></a>Rutas de acceso calificadas por el proveedor

Para que el motor de Windows PowerShell pueda inicializar y anular la inicialización del proveedor, el proveedor debe admitir una ruta de acceso calificada por el proveedor. Por ejemplo, el usuario puede inicializar y anular la inicialización del proveedor FileSystem porque define la siguiente ruta de acceso completa del proveedor: `FileSystem::\\uncshare\abc\bar`.

### <a name="provider-direct-paths"></a>Proveedor-rutas de acceso directas

Para permitir el acceso remoto a su proveedor de Windows PowerShell, debe admitir una ruta de acceso directa de proveedor para pasar directamente al proveedor de Windows PowerShell para la ubicación actual. Por ejemplo, el proveedor de Windows PowerShell del registro puede usar `\\server\regkeypath` como una ruta de acceso directa de proveedor.

### <a name="provider-internal-paths"></a>Rutas internas del proveedor

Para permitir que el cmdlet de proveedor acceda a los datos mediante interfaces de programación de aplicaciones (API) que no son de Windows PowerShell, el proveedor de Windows PowerShell debe admitir una ruta de acceso interna del proveedor. Esta ruta de acceso se indica después de "::" en la ruta de acceso completa del proveedor. Por ejemplo, la ruta de acceso interna del proveedor para el proveedor de Windows PowerShell de sistema de archivos es `\\uncshare\abc\bar`.

## <a name="overriding-cmdlet-parameters"></a>Reemplazar parámetros de cmdlet

Un proveedor puede invalidar el comportamiento de algunos cmdlets específicos del proveedor. Para obtener una lista de parámetros que se pueden invalidar y cómo invalidarlos en la clase de proveedor, consulte [parámetros de cmdlet de proveedor](./provider-cmdlet-parameters.md) .

## <a name="dynamic-parameters"></a>Parámetros dinámicos

Los proveedores pueden definir los parámetros dinámicos que se agregan a un cmdlet de proveedor cuando el usuario especifica un determinado valor para uno de los parámetros estáticos del cmdlet. Para ello, un proveedor implementa uno o más métodos de parámetros dinámicos. Para obtener una lista de parámetros de cmdlet que se pueden usar para agregar parámetros dinámicos y los métodos usados para implementarlos, consulte [parámetros dinámicos de cmdlet de proveedor](./provider-cmdlet-dynamic-parameters.md).

## <a name="provider-capabilities"></a>Capacidades del proveedor

La enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) define una serie de funcionalidades que los proveedores pueden admitir. Entre ellas se incluye la capacidad de usar caracteres comodín, filtrar elementos y admitir transacciones. Para especificar las capacidades de un proveedor, agregue una lista de valores de la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) , combinado con una operación de `OR` lógica, como la propiedad [System. Management. Automation. Provider. Cmdletproviderattribute. Providercapabilities *](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities) (el segundo parámetro del atributo) del atributo [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) de la clase de proveedor. Por ejemplo, el atributo siguiente especifica que el proveedor admite las capacidades de **las transacciones** [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **ShouldProcess** y [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) .

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>Ayuda del cmdlet de proveedor

Al escribir un proveedor, puede implementar su propia ayuda para los cmdlets de proveedor que admite. Esto incluye un solo tema de ayuda para cada cmdlet de proveedor o varias versiones de un tema de ayuda para los casos en los que el cmdlet de proveedor actúa de forma diferente en función del uso de parámetros dinámicos. Para admitir la ayuda específica del cmdlet del proveedor, el proveedor debe implementar la interfaz [System. Management. Automation. Provider. Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp) .

El motor de Windows PowerShell llama al método [System. Management. Automation. Provider. Icmdletprovidersupportshelp. Gethelpmaml *](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml) para mostrar el tema de ayuda de los cmdlets del proveedor. El motor proporciona el nombre del cmdlet que el usuario especificó al ejecutar el cmdlet `Get-Help` y la ruta de acceso actual del usuario. La ruta de acceso actual es necesaria si el proveedor implementa diferentes versiones del mismo cmdlet de proveedor para diferentes unidades. El método debe devolver una cadena que contenga el XML para la ayuda del cmdlet.

El contenido del archivo de ayuda se escribe mediante PSMAML XML. Este es el mismo esquema XML que se usa para escribir el contenido de la ayuda para los cmdlets independientes. Agregue el contenido de la ayuda del cmdlet personalizado al archivo de ayuda del proveedor en el elemento `CmdletHelpPaths`. En el ejemplo siguiente se muestra el elemento `command` para un cmdlet de proveedor único y se muestra cómo se especifica el nombre del cmdlet de proveedor que tiene el proveedor. admite

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

[Funcionalidad del proveedor de Windows PowerShell](./provider-types.md)

[Cmdlets de proveedor](./provider-cmdlets.md)

[Escribir un proveedor de Windows PowerShell](./writing-a-windows-powershell-provider.md)