---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Instalar el SDK de Windows PowerShell
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893545"
---
# <a name="installing-the-windows-powershell-sdk"></a>Instalar el SDK de Windows PowerShell

En el siguiente tema se describe cómo instalar PowerShell SDK en distintas versiones de Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Instalar el SDK de Windows PowerShell 3.0 para Windows 8 y Windows Server 2012

Windows PowerShell 3.0 se instala automáticamente con Windows 8 y Windows Server 2012.
Además, puede descargar e instalar los ensamblados de referencia para Windows PowerShell 3.0 como parte de Windows 8 SDK.
Estos ensamblados le permiten escribir cmdlets, proveedores y programas host para Windows PowerShell 3.0.
Al instalar Windows SDK para Windows 8, los ensamblados de Windows PowerShell se instalan automáticamente en la carpeta de ensamblados de referencia, en `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.
Para obtener más información, consulte el [sitio de descarga del SDK de Windows 8](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).
También hay disponibles ejemplos de código de Windows PowerShell en el Centro de desarrollo.
Para obtener más información, consulte la página de ejemplos de código de escritorio en el [sitio del Centro de desarrollo](https://code.msdn.microsoft.com:443/windowsdesktop/).

Además, Windows PowerShell 3.0 también es compatible con Windows PowerShell 2.0 SDK, que incluye varios ejemplos de código.
Más abajo le indicamos cómo descargar Windows PowerShell 2.0 SDK.
(Tenga en cuenta que, a pesar de que los ejemplos de código de la versión 2.0 son compatibles con Windows 8 y Windows PowerShell 3.0, no puede instalar Windows PowerShell 2.0 en una plataforma de Windows 8).

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Instalar el SDK de Windows PowerShell 3.0 para Windows 7 y Windows Server 2008 R2

Windows 7 y Windows Server 2008 R2 tienen instalado automáticamente PowerShell 2.0.
Además, puede instalar PowerShell 3.0 en estos sistemas.
(Para obtener más información, consulte [Instalación de Windows PowerShell](Installing-Windows-PowerShell.md)).
Tal como se ha descrito anteriormente, también puede instalar Windows 8 SDK en Windows 7 y Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Instalar el SDK de Windows PowerShell 2.0 para Windows 7, Vista, XP, Server 2003 y Server 2008

El SDK de Windows PowerShell 2.0 proporciona los ensamblados de referencia necesarios para escribir cmdlets, proveedores y aplicaciones host, así como código de ejemplo en C# que se puede usar como punto de partida para comenzar a escribir código.

Para instalar este SDK, consulte [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560) (SDK de Windows PowerShell 2.0).

## <a name="reference-assemblies"></a>Ensamblados de referencia

Los ensamblados de referencia se instalan de forma predeterminada en la siguiente ubicación: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE] 
> El código compilado con los ensamblados de Windows PowerShell 2.0 no puede cargarse en instalaciones de Windows PowerShell 1.0.
> Sin embargo, el código compilado con los ensamblados de Windows PowerShell 1.0 sí puede cargarse en las instalaciones de Windows PowerShell 2.0.

## <a name="samples"></a>muestras

Los ejemplos de código se instalan de forma predeterminada en la siguiente ubicación: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

En las secciones siguientes, se proporciona una breve descripción de lo que hace cada ejemplo.

## <a name="cmdlet-samples"></a>Ejemplos de cmdlet

### <a name="getprocesssample01"></a>GetProcessSample01

Muestra cómo escribir un cmdlet sencillo que obtiene todos los procesos en el equipo local.

### <a name="getprocesssample02"></a>GetProcessSample02

Muestra cómo agregar parámetros al cmdlet.
El cmdlet toma uno o más nombres de proceso y devuelve los procesos coincidentes.

### <a name="getprocesssample03"></a>GetProcessSample03

Muestra cómo agregar parámetros que aceptan la entrada desde la canalización.

### <a name="getprocesssample04"></a>GetProcessSample04

Muestra cómo controlar errores de no terminación.

### <a name="getprocesssample05"></a>GetProcessSample05

Muestra cómo mostrar una lista de procesos especificados.

### <a name="selectobject"></a>SelectObject

Muestra cómo escribir un filtro para seleccionar solo determinados objetos.

### <a name="selectstring"></a>SelectString

Muestra cómo buscar patrones específicos en archivos.

### <a name="stopprocesssample01"></a>StopProcessSample01

Muestra cómo implementar un parámetro *PassThru* y cómo solicitar comentarios de los usuarios mediante llamadas a los métodos [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) y [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).
Los usuarios especifican el parámetro *PassThru* cuando quieren forzar al cmdlet a devolver un objeto.

### <a name="stopprocesssample02"></a>StopProcessSample02

Muestra cómo detener un proceso específico.

### <a name="stopprocesssample03"></a>StopProcessSample03

Muestra cómo declarar los alias de parámetros y cómo agregar compatibilidad con caracteres comodín.

### <a name="stopprocesssample04"></a>StopProcessSample04

Muestra cómo declarar los conjuntos de parámetros y el objeto que el cmdlet toma como entrada, y también cómo especificar el parámetro predeterminado configurado para usarse.

## <a name="remoting-samples"></a>Ejemplos de comunicación remota

### <a name="remoterunspace01"></a>RemoteRunspace01

Muestra cómo crear un espacio de ejecución remoto que se usa para establecer una conexión remota.

### <a name="remoterunspacepool01"></a>RemoteRunspacePool01

Muestra cómo crear un grupo de espacio de ejecución remoto y cómo ejecutar varios comandos simultáneamente mediante el uso de este grupo.

### <a name="serialization01"></a>Serialization01

Muestra cómo examinar una clase .NET existente y cómo asegurarse de que se conserva la información de las propiedades públicas seleccionadas de esta clase a través de la serialización o deserialización.

### <a name="serialization02"></a>Serialization02

Muestra cómo examinar una clase .NET existente y cómo asegurarse de que la información de la instancia de esta clase se conserva en la serialización o deserialización cuando la información no está disponible en las propiedades públicas de la clase.

### <a name="serialization03"></a>Serialization03

Muestra cómo examinar una clase .NET existente y cómo asegurarse de que las instancias de esta clase y de las clases derivadas se deserializan (rehidratan) en objetos .NET dinámicos.

## <a name="event-samples"></a>Ejemplos de eventos

### <a name="event01"></a>Event01

Muestra cómo crear un cmdlet para el registro de eventos mediante la derivación de ObjectEventRegistrationBase.

### <a name="event02"></a>Event02

Muestra cómo recibir notificaciones de eventos de Windows PowerShell que se generan en equipos remotos.
Usa el evento PSEventReceived que se expone a través de la clase [Runspace](/dotnet/api/system.management.automation.runspaces.runspace).

## <a name="hosting-application-samples"></a>Ejemplos de aplicación host

### <a name="runspace01"></a>Runspace01

Muestra cómo usar la clase [PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) de forma sincrónica.
El cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) devuelve objetos [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) para cada proceso que se ejecuta en el equipo local.

### <a name="runspace02"></a>Runspace02

Muestra cómo usar la clase [PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar los cmdlets [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) y [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) de forma sincrónica.
El cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) devuelve objetos [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) para cada proceso que se ejecuta en el equipo local y `Sort-Object` ordena los objetos según su propiedad [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx).
Los resultados de estos comandos se muestran mediante un control [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx).

### <a name="runspace03"></a>Runspace03

Muestra cómo usar la clase [PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar un script de forma sincrónica y cómo controlar los errores de no terminación.
El script recibe una lista de nombres de procesos y después los recupera.
Los resultados del script, incluidos los errores de no terminación generados al ejecutarlo, se muestran en una ventana de consola.

### <a name="runspace04"></a>Runspace04

Muestra cómo usar la clase [PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar comandos y cómo capturar los errores de terminación que se producen al ejecutar dichos comandos.
Se ejecutan dos comandos; al último, se le pasa un argumento de parámetro que no es válido.
Como resultado, no se devuelve ningún objeto y se produce un error de terminación.

### <a name="runspace05"></a>Runspace05

Muestra cómo agregar un complemento a un objeto [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) para que el cmdlet del complemento esté disponible al abrir el espacio de ejecución.
El complemento proporciona un cmdlet Get-Proc (definido por el [ejemplo GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) que se ejecuta de forma sincrónica mediante un objeto [PowerShell](/dotnet/api/system.management.automation.powershell).

### <a name="runspace06"></a>Runspace06

Muestra cómo agregar un módulo a un objeto [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) para que el módulo se cargue al abrir el espacio de ejecución.
El módulo proporciona un cmdlet Get-Proc (definido por el [ejemplo GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) que se ejecuta de forma sincrónica mediante un objeto [PowerShell](/dotnet/api/system.management.automation.powershell).

### <a name="runspace07"></a>Runspace07

Muestra cómo crear un espacio de ejecución y lo usa para ejecutar dos cmdlets de forma sincrónica mediante un objeto [PowerShell](/dotnet/api/system.management.automation.powershell).

### <a name="runspace08"></a>Runspace08

Muestra cómo agregar comandos y argumentos a la canalización de un objeto [PowerShell](/dotnet/api/system.management.automation.powershell) y cómo ejecutar los comandos de forma sincrónica.

### <a name="runspace09"></a>Runspace09

Muestra cómo agregar un script a la canalización de un objeto [PowerShell](/dotnet/api/system.management.automation.powershell) y cómo ejecutar el script de forma asincrónica.
Los eventos se usan para controlar la salida del script.

### <a name="runspace10"></a>Runspace10

Muestra cómo crear un estado de sesión inicial predeterminado, cómo agregar un cmdlet a [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), cómo crear un espacio de ejecución que use el estado de sesión inicial y cómo ejecutar el comando con un objeto [PowerShell](/dotnet/api/system.management.automation.powershell).

### <a name="runspace11"></a>Runspace11

Muestra cómo usar la clase [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) para crear un comando de proxy que llama a un cmdlet existente, pero restringe el conjunto de parámetros disponibles.
El comando de proxy se agrega entonces a un estado de sesión inicial que se usa para crear un espacio de ejecución restringido.
Esto significa que el usuario puede tener acceso a la funcionalidad del cmdlet solo mediante el comando de proxy.

### <a name="powershell01"></a>PowerShell01

Muestra cómo crear un espacio de ejecución restringido mediante un objeto [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate).

### <a name="powershell02"></a>PowerShell02

Muestra cómo usar un grupo de espacio de ejecución para ejecutar varios comandos simultáneamente.

## <a name="host-samples"></a>Ejemplos de host

### <a name="host01"></a>Host01

Muestra cómo implementar una aplicación host que usa un host personalizado.
En este ejemplo se crea un espacio de ejecución que usa el host personalizado y, después, se usa la API [PowerShell](/dotnet/api/system.management.automation.powershell) para ejecutar un script que llame al código "exit".
La aplicación host examina después la salida del script e imprime los resultados.

### <a name="host02"></a>Host02

Muestra cómo escribir una aplicación host que usa el tiempo de ejecución de Windows PowerShell junto con una implementación de host personalizado.
La aplicación host establece la referencia cultural del host en alemán, ejecuta el cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process), muestra los resultados tal como los vería con pwrsh.exe e imprime los datos y la hora actuales en alemán.

### <a name="host03"></a>Host03

Muestra cómo crear una aplicación host basada en consola interactiva que lee los comandos de la línea de comandos, los ejecuta y muestra sus resultados en la consola.

### <a name="host04"></a>Host04

Muestra cómo crear una aplicación host basada en consola interactiva que lee los comandos de la línea de comandos, los ejecuta y muestra sus resultados en la consola.
Esta aplicación host también permite mostrar avisos para que el usuario pueda especificar varias opciones.

### <a name="host05"></a>Host05

Muestra cómo crear una aplicación host basada en consola interactiva que lee los comandos de la línea de comandos, los ejecuta y muestra sus resultados en la consola.
Esta aplicación host también admite llamadas a equipos remotos mediante los cmdlets [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) y [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession).

### <a name="host06"></a>Host06

Muestra cómo crear una aplicación host basada en consola interactiva que lee los comandos de la línea de comandos, los ejecuta y muestra sus resultados en la consola.
Además, este ejemplo utiliza las API de Tokenizer para especificar el color del texto que el usuario ha escrito.

## <a name="provider-samples"></a>Ejemplos de proveedor

### <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Muestra cómo declarar una clase de proveedor que se deriva directamente de la clase [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider).
Se incluye aquí solo por cuestiones de integridad.

### <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

Muestra cómo sobrescribir los métodos [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) y [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) para admitir llamadas a los cmdlets `New-PSDrive` y `Remove-PSDrive`.
La clase de proveedor de este ejemplo se deriva de la clase [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider).

### <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Muestra cómo sobrescribir los métodos [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) y [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) para admitir llamadas a los cmdlets `Get-Item` y `Set-Item`.
La clase de proveedor de este ejemplo se deriva de la clase [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider).

### <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a los cmdlets `Copy-Item`, `Get-ChildItem`, `New-Item` y `Remove-Item`.
Estos métodos deberían implementarse cuando el almacén de datos contengan elementos que son contenedores.
Un contenedor es un grupo de elementos secundarios con un elemento primario común.
La clase de proveedor de este ejemplo se deriva de la clase [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider).

### <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

Muestra cómo sobrescribir los métodos de contenedor para admitir llamadas a los cmdlets `Move-Item` y `Join-Path`.
Estos métodos deberían implementarse cuando el usuario necesite mover elementos dentro de un contenedor y si el almacén de datos tiene contenedores anidados.
La clase de proveedor de este ejemplo se deriva de la clase [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider).

### <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Muestra cómo sobrescribir los métodos de contenido para admitir llamadas a los cmdlets `Clear-Content`, `Get-Content` y `Set-Content`.
Estos métodos deberían implementarse cuando el usuario necesite administrar el contenido de los elementos en el almacén de datos.
La clase de proveedor de este ejemplo se deriva de la clase [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider); también se implementa la interfaz [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider).