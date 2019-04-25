---
title: 'Referencia de Windows PowerShell: Novedades'
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080533"
---
# <a name="whats-new"></a>Novedades

Windows PowerShell 2.0 proporciona las siguientes características nuevas para su uso al escribir cmdlets, proveedores y aplicaciones host.

## <a name="modules"></a>Módulos

Ahora puede empaquetar y distribuir las soluciones de Windows PowerShell mediante el uso de módulos. Los módulos le permiten a la partición, organizar y abstraer el código de Windows PowerShell en unidades independientes y reutilizables. Para obtener más información acerca de los módulos, consulte escribir un módulo de Windows PowerShell.

## <a name="the-powershell-class"></a>La clase de PowerShell

La clase de PowerShell proporciona una solución más sencilla para crear aplicaciones, denominadas aplicaciones de host, que se ejecutan mediante programación los comandos. Esta clase permite crear una canalización de comandos, especifique el espacio de ejecución que se usa para ejecutar los comandos y especifique invocar los comandos de forma sincrónica o asincrónica.

## <a name="the-runspacepool-class"></a>La clase RunspacePool

Los grupos del espacio de ejecución permiten crear varios espacios de ejecución mediante el uso de una sola llamada. El método CreateRunspacePool proporciona varias sobrecargas que pueden usarse para crear espacios de ejecución que tienen las mismas características, como el mismo host, el estado de sesión inicial y la información de conexión.

## <a name="the-initialsessionstate-class"></a>La clase InitialSessionState

La clase InitialSessionState permite crear una configuración de estado de sesión que se utiliza cuando se abre un espacio de ejecución. Puede crear una configuración personalizada, una configuración predeterminada que incluye los comandos proporcionados por mshshort y una configuración cuyos comandos están restringidas según las capacidades de la sesión.

## <a name="remote-runspaces"></a>Espacios de ejecución remota

Ahora puede crear espacios de ejecución que se pueden abrir en equipos remotos, lo que permite ejecutar comandos en la máquina remota y recopilar los resultados de forma local. Para crear un espacio de ejecución remoto, debe especificar la información sobre la conexión remota al crear el espacio de ejecución. Vea los métodos CreateRunspace y CreateRunspacePool para obtener ejemplos. La información de conexión se define mediante la clase RunspaceConnectionInfo.

## <a name="private-runspace-elements"></a>Elementos de espacio de ejecución privada

Ahora puede crear espacios de ejecución cuyos elementos son públicas o privadas. Esto le permite crear espacios de ejecución cuyos elementos están disponibles para el espacio de ejecución, pero no están disponibles para el usuario. Vea la clase ConstrainedSessionStateEntry para averiguar qué elementos del espacio de ejecución se pueden hacer privados.

## <a name="runspace-threading-modes-and-apartment-state"></a>Espacio de ejecución de los modos y estado de apartamento de subprocesos

Ahora puede especificar cómo se crean subprocesos y se utilizan al ejecutar comandos en un espacio de ejecución. Vea las propiedades System.Management.Automation.Runspaces.Runspace.ThreadOptions y System.Management.Automation.Runspaces.RunspacePool.ThreadOptions.

Ahora puede obtener el estado de apartamento de los subprocesos que se utilizan para ejecutar comandos en un espacio de ejecución. Vea las propiedades System.Management.Automation.Runspaces.Runspace.ApartmentState y System.Management.Automation.Runspaces.RunspacePool.ApartmentState.

## <a name="transaction-cmdlets"></a>Cmdlets de transacción

Ahora puede crear cmdlets que puede usarse dentro de una transacción. Cuando se usa un cmdlet en una transacción, sus acciones son temporales y pueden aceptan o rechazan mediante los cmdlets de transacción proporcionados por Windows PowerShell.

Para obtener más información acerca de las transacciones, vea cómo se admiten transacciones.

## <a name="transaction-provider"></a>Proveedor de transacción

Ahora puede crear proveedores que se pueden utilizar dentro de una transacción. Al igual que los cmdlets, cuando se usa un proveedor en una transacción, sus acciones son temporales y pueden aceptan o rechazan mediante los cmdlets de transacción proporcionados por Windows PowerShell.

Para obtener más información acerca de cómo especificar la compatibilidad con transacciones dentro de una clase de proveedor, vea la propiedad System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities.

## <a name="job-cmdlets"></a>Cmdlets de trabajo

Ahora puede escribir cmdlets que puede llevar a cabo su acción como un trabajo. Estos trabajos se ejecutan en segundo plano sin interactuar con la sesión actual. Para obtener más información acerca de cómo Windows PowerShell es compatible con los trabajos, vea los trabajos en segundo plano.

## <a name="cmdlet-output-types"></a>Tipos de salida del cmdlet

Ahora puede especificar los tipos de .NET Framework que se devuelven los cmdlets al declarar el atributo OutputType al escribir sus cmdlets. Esto permitirá que otras personas determinar qué tipo de objetos se devuelven mediante un cmdlet echando un vistazo a la propiedad OutputType del cmdlet.

## <a name="event-support"></a>Compatibilidad con eventos

Ahora puede escribir cmdlets que agregan y consumir eventos. Vea la clase PSEvent.

## <a name="proxy-commands"></a>Comandos de proxy

Ahora puede escribir comandos de proxy que pueden usarse para ejecutar otro comando. Un comando de proxy permite controlar qué funcionalidad del cmdlet de origen está disponible para el usuario. Por ejemplo, puede crear un comando de proxy que se quita un parámetro proporcionado por el comando de origen. Vea la clase ProxyCommand.

## <a name="multiple-choice-prompts"></a>Varios mensajes de elección

Ahora puede escribir aplicaciones que pueden proporcionar indicaciones que permiten al usuario seleccionar varias opciones. Vea la interfaz IHostUISupportsMultipleChoiceSelection

## <a name="interactive-sessions"></a>Sesiones interactivas

Ahora puede escribir aplicaciones que se pueden iniciar y detener una sesión interactiva en un equipo remoto.
Vea la interfaz IHostSupportsInteractiveSession.

## <a name="custom-cmdlet-help-for-providers"></a>Ayuda de Cmdlet personalizado para los proveedores

Ahora puede crear temas de ayuda personalizados para los cmdlets de proveedor. Temas de Ayuda de cmdlet personalizado se puede explicar cómo funciona el cmdlet en el proveedor ruta de acceso y el documento de características especiales, incluidos los parámetros dinámicos que el proveedor se agrega al cmdlet.
