---
title: 'Referencia de Windows PowerShell: novedades'
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366094"
---
# <a name="whats-new"></a>Novedades

Windows PowerShell 2,0 proporciona las siguientes características nuevas para su uso al escribir cmdlets, proveedores y aplicaciones host.

## <a name="modules"></a>Módulos

Ahora puede empaquetar y distribuir soluciones de Windows PowerShell mediante el uso de módulos. Los módulos le permiten particionar, organizar y abstraer el código de Windows PowerShell en unidades reutilizables independientes. Para obtener más información sobre los módulos, consulte escribir un módulo de Windows PowerShell.

## <a name="the-powershell-class"></a>La clase de PowerShell

La clase de PowerShell proporciona una solución más sencilla para crear aplicaciones, denominadas aplicaciones host, que ejecutan comandos mediante programación. Esta clase permite crear una canalización de comandos, especificar el espacio de ejecución que se usa para ejecutar los comandos y especificar invocar los comandos de forma sincrónica o asincrónica.

## <a name="the-runspacepool-class"></a>La clase RunspacePool

Los grupos de espacio de ejecución permiten crear varios espacios de ejecución mediante una sola llamada. El método CreateRunspacePool proporciona varias sobrecargas que se pueden usar para crear espacios de inicio que tienen las mismas características, como el mismo host, el estado de sesión inicial y la información de conexión.

## <a name="the-initialsessionstate-class"></a>La clase InitialSessionState

La clase InitialSessionState permite crear una configuración de estado de sesión que se utiliza cuando se abre un espacio de ejecución. Puede crear una configuración personalizada, una configuración predeterminada que incluye los comandos proporcionados por mshshort y una configuración cuyos comandos están restringidos en función de las capacidades de la sesión.

## <a name="remote-runspaces"></a>Espacios de control remotos

Ahora puede crear espacios de ejecución que se puedan abrir en equipos remotos, lo que le permite ejecutar comandos en el equipo remoto y recopilar los resultados de forma local. Para crear un espacio de ejecución remoto, debe especificar información sobre la conexión remota al crear el espacio de ejecución. Vea los métodos CreateRunspace y CreateRunspacePool para obtener ejemplos. La información de conexión se define mediante la clase RunspaceConnectionInfo.

## <a name="private-runspace-elements"></a>Elementos Private runspace

Ahora puede crear espacios de espacios cuyos elementos sean públicos o privados. Esto permite crear espacios de ejecución cuyos elementos están disponibles en el espacio de ejecución, pero no están disponibles para el usuario. Vea la clase ConstrainedSessionStateEntry para averiguar qué elementos del espacio de ejecución se pueden convertir en privados.

## <a name="runspace-threading-modes-and-apartment-state"></a>Modos de subproceso de espacio de ejecución y estado de apartamento

Ahora puede especificar cómo se crean y se usan los subprocesos cuando se ejecutan comandos en un espacio de ejecución. Vea las propiedades System. Management. Automation. espacios de ejecución. ThreadOptions y System. Management. Automation. runspace. RunspacePool. ThreadOptions.

Ahora puede obtener el estado de apartamento de los subprocesos que se usan para ejecutar comandos en un espacio de ejecución. Vea las propiedades System. Management. Automation. Runspace. Runspace. ApartmentState y System. Management. Automation. runspace. RunspacePool. ApartmentState.

## <a name="transaction-cmdlets"></a>Cmdlets de transacciones

Ahora puede crear cmdlets que se pueden usar dentro de una transacción. Cuando se usa un cmdlet en una transacción, sus acciones son temporales y pueden ser aceptadas o rechazadas por los cmdlets de transacciones proporcionados por Windows PowerShell.

Para obtener más información acerca de las transacciones, consulte How to Support Transactions.

## <a name="transaction-provider"></a>Proveedor de transacciones

Ahora puede crear proveedores que se pueden usar dentro de una transacción. Similar a los cmdlets, cuando un proveedor se usa en una transacción, sus acciones son temporales y pueden ser aceptadas o rechazadas por los cmdlets de transacciones proporcionados por Windows PowerShell.

Para obtener más información sobre cómo especificar la compatibilidad con la transacción en una clase de proveedor, vea la propiedad System. Management. Automation. Provider. CmdletProviderAttribute. ProviderCapabilities.

## <a name="job-cmdlets"></a>Cmdlets de trabajo

Ahora puede escribir cmdlets que pueden realizar su acción como un trabajo. Estos trabajos se ejecutan en segundo plano sin interactuar con la sesión actual. Para obtener más información acerca de cómo Windows PowerShell admite trabajos, consulte trabajos en segundo plano.

## <a name="cmdlet-output-types"></a>Tipos de salida de cmdlet

Ahora puede especificar los tipos de .NET Framework devueltos por los cmdlets declarando el atributo OutputType al escribir los cmdlets. Esto permitirá que otros usuarios determinen qué tipo de objetos devuelve un cmdlet examinando la propiedad OutputType del cmdlet.

## <a name="event-support"></a>Compatibilidad con eventos

Ahora puede escribir cmdlets que agreguen y consuman eventos. Vea la clase PSEvent.

## <a name="proxy-commands"></a>Comandos de proxy

Ahora puede escribir comandos de proxy que se pueden usar para ejecutar otro comando. Un comando proxy permite controlar qué funcionalidad del cmdlet de origen está disponible para el usuario. Por ejemplo, puede crear un comando de proxy que quite un parámetro proporcionado por el comando de origen. Vea la clase ProxyCommand.

## <a name="multiple-choice-prompts"></a>Solicitudes de varias opciones

Ahora puede escribir aplicaciones que puedan proporcionar mensajes que permitan al usuario seleccionar varias opciones. Vea la interfaz IHostUISupportsMultipleChoiceSelection

## <a name="interactive-sessions"></a>Sesiones interactivas

Ahora puede escribir aplicaciones que pueden iniciar y detener una sesión interactiva en un equipo remoto.
Vea la interfaz IHostSupportsInteractiveSession.

## <a name="custom-cmdlet-help-for-providers"></a>Ayuda de cmdlet personalizada para proveedores

Ahora puede crear temas de ayuda personalizados para los cmdlets de proveedor. Los temas de ayuda de los cmdlets personalizados pueden explicar cómo funciona el cmdlet en la ruta de acceso del proveedor y documentar las características especiales, incluidos los parámetros dinámicos que el proveedor agrega al cmdlet.
