---
title: Instalar el SDK de Windows PowerShell
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367274"
---
# <a name="installing-the-windows-powershell-sdk"></a>Instalar el SDK de Windows PowerShell

Se aplica a: Windows PowerShell 2,0, Windows PowerShell 3,0

En el siguiente tema se describe cómo instalar PowerShell SDK en distintas versiones de Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Instalar el SDK de Windows PowerShell 3.0 para Windows 8 y Windows Server 2012

Windows PowerShell 3.0 se instala automáticamente con Windows 8 y Windows Server 2012. Además, puede descargar e instalar los ensamblados de referencia para Windows PowerShell 3.0 como parte de Windows 8 SDK. Estos ensamblados le permiten escribir cmdlets, proveedores y programas host para Windows PowerShell 3.0. Al instalar Windows SDK para Windows 8, los ensamblados de Windows PowerShell se instalan automáticamente en la carpeta de ensamblados de referencia, en \Archivos de programa (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0. Para obtener más información, consulte el sitio de descarga del SDK de Windows 8. También hay disponibles ejemplos de código de Windows PowerShell en el Centro de desarrollo.
Para obtener más información, vea la página de ejemplo de código de escritorio en el sitio del centro de desarrollo.

Además, Windows PowerShell 3.0 también es compatible con Windows PowerShell 2.0 SDK, que incluye varios ejemplos de código. Más abajo le indicamos cómo descargar Windows PowerShell 2.0 SDK. (Tenga en cuenta que, a pesar de que los ejemplos de código de la versión 2.0 son compatibles con Windows 8 y Windows PowerShell 3.0, no puede instalar Windows PowerShell 2.0 en una plataforma de Windows 8).

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Instalar el SDK de Windows PowerShell 3.0 para Windows 7 y Windows Server 2008 R2

Windows 7 y Windows Server 2008 R2 tienen instalado automáticamente PowerShell 2.0. Además, puede instalar PowerShell 3.0 en estos sistemas. (Para obtener más información, consulte Instalación de Windows PowerShell). Tal como se ha descrito anteriormente, también puede instalar Windows 8 SDK en Windows 7 y Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Instalar el SDK de Windows PowerShell 2.0 para Windows 7, Vista, XP, Server 2003 y Server 2008

El SDK de Windows PowerShell 2.0 proporciona los ensamblados de referencia necesarios para escribir cmdlets, proveedores y aplicaciones host, así como código de ejemplo en C# que se puede usar como punto de partida para comenzar a escribir código.

Para instalar este SDK, consulte el SDK de Windows PowerShell 2,0.

### <a name="reference-assemblies"></a>Ensamblados de referencia

Los ensamblados de referencia se instalan en la siguiente ubicación de forma predeterminada: C:\Archivos de Programa\reference Assemblies\Microsoft\WindowsPowerShell\V1.0.

> [!NOTE]
>
> El código compilado con los ensamblados de Windows PowerShell 2.0 no puede cargarse en instalaciones de Windows PowerShell 1.0. Sin embargo, el código compilado con los ensamblados de Windows PowerShell 1.0 sí puede cargarse en las instalaciones de Windows PowerShell 2.0.


### <a name="samples"></a>muestras

Los ejemplos de código se instalan en la siguiente ubicación de forma predeterminada: C:\Archivos de Programa\microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. En las secciones siguientes, se proporciona una breve descripción de lo que hace cada ejemplo.

#### <a name="cmdlet-samples"></a>Ejemplos de cmdlet

- GetProcessSample01: muestra cómo escribir un cmdlet sencillo que obtiene todos los procesos en el equipo local.
- GetProcessSample02: muestra cómo agregar parámetros al cmdlet. El cmdlet toma uno o más nombres de proceso y devuelve los procesos coincidentes.
- GetProcessSample03: muestra cómo agregar parámetros que aceptan la entrada de la canalización.
- GetProcessSample04: muestra cómo controlar los errores de no terminación.
- GetProcessSample05: muestra cómo mostrar una lista de los procesos especificados.
- SeleccionarObjeto: muestra cómo escribir un filtro para seleccionar solo determinados objetos.
- SelectString: muestra cómo buscar los patrones especificados en los archivos.
- StopProcessSample01: muestra cómo implementar un parámetro PassThru y cómo solicitar comentarios del usuario mediante llamadas a los métodos ShouldProcess y ShouldContinue. Los usuarios especifican el parámetro PassThru cuando quieren forzar que el cmdlet devuelva un objeto.
- StopProcessSample02: muestra cómo detener un proceso específico.
- StopProcessSample03: muestra cómo declarar alias para los parámetros y cómo admitir caracteres comodín.
- StopProcessSample04: muestra cómo declarar conjuntos de parámetros, el objeto que el cmdlet toma como entrada y cómo especificar el conjunto de parámetros predeterminado que se va a usar.

#### <a name="remoting-samples"></a>Ejemplos de comunicación remota

- RemoteRunspace01: muestra cómo crear un espacio de ejecución remoto que se usa para establecer una conexión remota.
- RemoteRunspacePool01: muestra cómo crear un grupo de espacio de ejecución remoto y cómo ejecutar varios comandos simultáneamente mediante este grupo.
- Serialization01: muestra cómo examinar una clase .NET existente y asegurarse de que la información de las propiedades públicas seleccionadas de esta clase se conserva en la serialización o deserialización.
- Serialization02: muestra cómo examinar una clase .NET existente y cómo asegurarse de que la información de la instancia de esta clase se conserva en la serialización o deserialización cuando la información no está disponible en las propiedades públicas de la clase.
- Serialization03: muestra cómo examinar una clase .NET existente y cómo asegurarse de que las instancias de esta clase y de las clases derivadas se deserializan (se rehidratan) en objetos .NET activos.

#### <a name="event-samples"></a>Ejemplos de eventos

- Event01: muestra cómo crear un cmdlet para el registro de eventos mediante la derivación de ObjectEventRegistrationBase.
- Event02: muestra cómo recibir notificaciones de eventos de Windows PowerShell que se generan en equipos remotos. Usa el evento Pseventreceived que se expuesto a través de la clase Runspace.

#### <a name="hosting-application-samples"></a>Ejemplos de aplicación host

- Runspace01: muestra cómo usar la clase de PowerShell para ejecutar el cmdlet `Get-Process` sincrónicamente.
El cmdlet `Get-Process` devuelve objetos Process para cada proceso que se ejecuta en el equipo local.
- Runspace02: muestra cómo usar la clase de PowerShell para ejecutar los cmdlets `Get-Process` y `Sort-Object` sincrónicamente. El cmdlet `Get-Process` devuelve objetos Process para cada proceso que se ejecuta en el equipo local y el `Sort-Object` ordena los objetos según su propiedad ID. Los resultados de estos comandos se muestran mediante un control DataGridView.
- Runspace03: muestra cómo usar la clase de PowerShell para ejecutar un script de forma sincrónica y cómo controlar los errores de no terminación. El script recibe una lista de nombres de procesos y después los recupera. Los resultados del script, incluidos los errores de no terminación generados al ejecutarlo, se muestran en una ventana de consola.
- Runspace04: muestra cómo usar la clase de PowerShell para ejecutar comandos y cómo detectar los errores de terminación que se producen al ejecutar los comandos. Se ejecutan dos comandos; al último, se le pasa un argumento de parámetro que no es válido. Como resultado, no se devuelve ningún objeto y se produce un error de terminación.
- Runspace05: muestra cómo agregar un complemento a un objeto InitialSessionState para que el cmdlet del complemento esté disponible cuando se abra el espacio de ejecución. El complemento proporciona un cmdlet Get-proc (definido por el ejemplo GetProcessSample01) que se ejecuta de forma sincrónica mediante un objeto de PowerShell.
- Runspace06: muestra cómo agregar un módulo a un objeto InitialSessionState para que el módulo se cargue cuando se abra el espacio de ejecución. El módulo proporciona un cmdlet Get-proc (definido por el ejemplo GetProcessSample02) que se ejecuta de forma sincrónica mediante un objeto de PowerShell.
- Runspace07: muestra cómo crear un espacio de ejecución y, a continuación, usar ese espacio de ejecución para ejecutar dos cmdlets de forma sincrónica mediante un objeto de PowerShell.
- Runspace08: muestra cómo agregar comandos y argumentos a la canalización de un objeto de PowerShell y cómo ejecutar los comandos sincrónicamente.
- Runspace09: muestra cómo agregar un script a la canalización de un objeto de PowerShell y cómo ejecutar el script de forma asincrónica. Los eventos se usan para controlar la salida del script.
- Runspace10: muestra cómo crear un estado de sesión inicial predeterminado, cómo agregar un cmdlet a InitialSessionState, cómo crear un espacio de ejecución que usa el estado de sesión inicial y cómo ejecutar el comando mediante un objeto de PowerShell.
- Runspace11: muestra cómo usar la clase ProxyCommand para crear un comando de proxy que llama a un cmdlet existente, pero restringe el conjunto de parámetros disponibles. El comando de proxy se agrega entonces a un estado de sesión inicial que se usa para crear un espacio de ejecución restringido. Esto significa que el usuario puede tener acceso a la funcionalidad del cmdlet solo mediante el comando de proxy.
- PowerShell01: muestra cómo crear un espacio de ejecución restringido mediante un objeto InitialSessionState.
- PowerShell02: muestra cómo usar un grupo de espacio de ejecución para ejecutar varios comandos simultáneamente.

#### <a name="host-samples"></a>Ejemplos de host

- Host01: muestra cómo implementar una aplicación host que usa un host personalizado. En este ejemplo se crea un espacio de ejecución que usa el host personalizado y, después, se usa la API de PowerShell para ejecutar un script que llama a "Exit". La aplicación host examina después la salida del script e imprime los resultados.
- Host02: muestra cómo escribir una aplicación host que usa el tiempo de ejecución de Windows PowerShell junto con una implementación de host personalizado. La aplicación host establece la referencia cultural del host en alemán, ejecuta el cmdlet `Get-Process` y muestra los resultados tal y como se verán con pwrsh. exe y, a continuación, imprime los datos y la hora actuales en alemán.
- Host03: muestra cómo compilar una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola.
- Host04: muestra cómo compilar una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola. Esta aplicación host también permite mostrar avisos para que el usuario pueda especificar varias opciones.
- Host05: muestra cómo compilar una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola. Esta aplicación host también admite llamadas a equipos remotos mediante los cmdlets `Enter-PsSession` y `Exit-PsSession`.
- Host06: muestra cómo compilar una aplicación host basada en consola interactiva que lee comandos desde la línea de comandos, ejecuta los comandos y, a continuación, muestra los resultados en la consola. Además, este ejemplo utiliza las API de Tokenizer para especificar el color del texto que el usuario ha escrito.

#### <a name="provider-samples"></a>Ejemplos de proveedor

- AccessDBProviderSample01: muestra cómo declarar una clase de proveedor que se deriva directamente de la clase CmdletProvider. Se incluye aquí solo por cuestiones de integridad.

- AccessDBProviderSample02: muestra cómo sobrescribir los métodos NewDrive y RemoveDrive para admitir llamadas a los cmdlets `New-PSDrive` y `Remove-PSDrive`. La clase de proveedor de este ejemplo se deriva de la clase DriveCmdletProvider.

- AccessDBProviderSample03: muestra cómo sobrescribir los métodos GetItem y SetItem para admitir llamadas a los cmdlets `Get-Item` y `Set-Item`. La clase de proveedor de este ejemplo se deriva de la clase ItemCmdletProvider.

- AccessDBProviderSample04: muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a los cmdlets `Copy-Item`, `Get-ChildItem`, `New-Item` y `Remove-Item`. Estos métodos deberían implementarse cuando el almacén de datos contengan elementos que son contenedores. Un contenedor es un grupo de elementos secundarios con un elemento primario común. La clase de proveedor de este ejemplo se deriva de la clase ItemCmdletProvider.

- AccessDBProviderSample05: muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a los cmdlets `Move-Item` y `Join-Path`. Estos métodos deberían implementarse cuando el usuario necesite mover elementos dentro de un contenedor y si el almacén de datos tiene contenedores anidados. La clase de proveedor de este ejemplo se deriva de la clase NavigationCmdletProvider.

- AccessDBProviderSample06: muestra cómo sobrescribir métodos de contenido para admitir llamadas a los cmdlets `Clear-Content`, `Get-Content` y `Set-Content`. Estos métodos deberían implementarse cuando el usuario necesite administrar el contenido de los elementos en el almacén de datos. La clase de proveedor de este ejemplo se deriva de la clase NavigationCmdletProvider e implementa la interfaz IContentCmdletProvider.
