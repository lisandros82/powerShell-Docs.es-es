---
title: Creación de un proveedor de la unidad de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: d1546ab0b0e6b5502f35c92c01ce148211c53db2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855801"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Creación de un proveedor de unidad de Windows PowerShell

Este tema describe cómo crear un proveedor de unidades de Windows PowerShell que proporciona una manera de obtener acceso a un almacén de datos a través de una unidad de Windows PowerShell. Este tipo de proveedor también se conoce como proveedores de la unidad de Windows PowerShell. Las unidades de Windows PowerShell usadas el proveedor proporcionan los medios para conectarse al almacén de datos.

El proveedor de la unidad de Windows PowerShell descrito aquí proporciona acceso a una base de datos de Microsoft Access. Para este proveedor, la unidad de Windows PowerShell representa la base de datos (es posible agregar cualquier número de unidades a un proveedor de unidades), los contenedores de nivel superior de la unidad representan las tablas de la base de datos, y los elementos de los contenedores de las filas de las tablas.

Esta es una lista de las secciones de este tema. Si no está familiarizado con la escritura de un proveedor de la unidad de Windows PowerShell, lea estas secciones en el orden en que aparecen. Sin embargo, si está familiarizado con la escritura de un proveedor de unidades, vaya directamente a la información que necesita.

- [Definición de la clase de proveedor de PowerShell de Windows](#Defining-the-Windows-PowerShell-Provider-Class)

- [Definir la funcionalidad de Base](#Defining-Base-Functionality)

- [Creación de información de estado de la unidad](#Creating-Drive-State-Information)

- [Creación de una unidad](#Creating-a-Drive)

- [Asociar los parámetros dinámicos a NewDrive](#Attaching-Dynamic-Parameters-to-NewDrive)

- [Quitar una unidad](#Removing-a-Drive)

- [Inicialización predeterminada de unidades](#Initializing-Default-Drives)

- [Ejemplo de código](#Code-Sample)

- [Probar el proveedor de la unidad de PowerShell de Windows](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definición de la clase de proveedor de PowerShell de Windows

El proveedor de la unidad debe definir una clase .NET que se deriva de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase base. Esta es la definición de clase para este proveedor de unidad:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Tenga en cuenta que en este ejemplo, el [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo especifica un nombre descriptivo para el proveedor y las capacidades específicas de Windows PowerShell que el proveedor durante el procesamiento de comandos, expone el tiempo de ejecución de Windows PowerShell. Los valores posibles para las capacidades del proveedor se definen mediante la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración. Este proveedor de la unidad no es compatible con cualquiera de estas funcionalidades.

## <a name="defining-base-functionality"></a>Definir la funcionalidad de Base

Como se describe en [proveedor de diseño de Windows PowerShell](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase se deriva de la [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) clase base que define los métodos necesarios para inicializar y sin inicializar el proveedor. Para implementar la funcionalidad para agregar información de inicialización específicas de la sesión y para liberar los recursos utilizados por el proveedor, consulte [creación de un proveedor de PowerShell de Windows básico](./creating-a-basic-windows-powershell-provider.md). Sin embargo, la mayoría de proveedores (incluido el proveedor que se describe aquí) puede usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.

## <a name="creating-drive-state-information"></a>Creación de información de estado de la unidad

Todos los proveedores de Windows PowerShell se consideran sin estado, lo que significa que el proveedor de la unidad debe crear cualquier información de estado que se necesita el tiempo de ejecución de Windows PowerShell cuando llama a su proveedor.

Para este proveedor de la unidad, la información de estado incluye la conexión a la base de datos que se mantiene como parte de la información de la unidad. Este es el código que muestra cómo esta información se almacena en el [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto que describe la unidad:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Creación de una unidad

Para permitir que el tiempo de ejecución de Windows PowerShell crear una unidad, el proveedor de la unidad debe implementar la [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método. El código siguiente muestra la implementación de la [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método para este proveedor de unidad:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

La invalidación de este método debe hacer lo siguiente:

- Compruebe que la [System.Management.Automation.Psdriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) miembro existe y que puede establecer una conexión al almacén de datos.

- Crear una unidad y rellenar el miembro de la conexión, como soporte del `New-PSDrive` cmdlet.

- Validar la [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto para la unidad propuesta.

- Modificar el [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto que describe la unidad con información de confiabilidad o rendimiento necesarios, o proporcionar datos adicionales para los llamadores usando la unidad.

- Controlar los errores mediante la [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método y, luego, devolverla `null`.

  Este método devuelve la información de unidad que se pasó al método o una versión específica del proveedor del mismo.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Asociar los parámetros dinámicos a NewDrive

El `New-PSDrive` cmdlet admitido por el proveedor de la unidad, es posible que requieren parámetros adicionales. Para asociar estos parámetros dinámicos al cmdlet, el proveedor implementa la [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) método. Este método devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto.

Este proveedor de la unidad no invalida este método. Sin embargo, el código siguiente muestra la implementación predeterminada de este método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Quitar una unidad

Para cerrar la conexión de base de datos, el proveedor de la unidad debe implementar la [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método. Este método cierra la conexión a la unidad después de limpiar cualquier información específica del proveedor.

El código siguiente muestra la implementación de la [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método para este proveedor de unidad:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Si se puede quitar la unidad, el método debe devolver la información que se pasa al método a través de la `drive` parámetro. Si no se puede quitar la unidad, el método debe escribir una excepción y, a continuación, devolver `null`. Si el proveedor no invalida este método, la implementación predeterminada de este método sólo devuelve información de la unidad que se pasa como entrada.

## <a name="initializing-default-drives"></a>Inicialización predeterminada de unidades

La unidad proveedor implementa la [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método montar unidades de disco. Por ejemplo, el proveedor de Active Directory puede montar una unidad para el contexto de nomenclatura si el equipo está unido a un dominio predeterminado.

Este método devuelve una colección de información de unidad sobre las unidades inicializadas o una colección vacía. Se realiza la llamada a este método después de las llamadas en tiempo de ejecución de Windows PowerShell la [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método para inicializar el proveedor.

Este proveedor de la unidad no invalida el [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método. Sin embargo, el código siguiente muestra la implementación predeterminada, que devuelve una colección vacía de unidad:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Cosas que recordar acerca de cómo implementar InitializeDefaultDrives

Todos los proveedores de la unidad deben montar una unidad raíz para ayudar al usuario con capacidad de detección. La unidad raíz podría enumerar las ubicaciones que actúan como raíces para otras unidades montadas. Por ejemplo, el proveedor de Active Directory puede crear una unidad que se enumera los contextos de nomenclatura que se encuentra en la `namingContext` atributos en la raíz del entorno del sistema distribuido (DSE). Esto ayuda a los usuarios a detectar los puntos de montaje para otras unidades.

## <a name="code-sample"></a>Ejemplo de código

Para el código de ejemplo completo, vea [AccessDbProviderSample02 código de ejemplo](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Probar el proveedor de la unidad de PowerShell de Windows

Cuando se ha registrado el proveedor de Windows PowerShell con Windows PowerShell, puede probarla mediante la ejecución de los cmdlets compatibles en la línea de comandos, incluidos los de cualquier disposición mediante la derivación. Vamos a probar el proveedor de la unidad.

1. Ejecute el `Get-PSProvider` para recuperar la lista de proveedores para asegurarse de que el proveedor de la unidad AccessDB está presente:

   **PS> `Get-PSProvider`**

   Aparecerá el siguiente resultado:

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Asegúrese de que un nombre de servidor de base de datos (DSN) existe para la base de datos mediante el acceso a la **orígenes de datos** parte de la **herramientas administrativas** para el sistema operativo. En el **DSN de usuario** de tabla, haga doble clic en **base de datos de MS Access** y agregue la ruta de acceso de unidad C:\ps\northwind.mdb.

3. Cree una nueva unidad utilizando el proveedor de la unidad de ejemplo:

   **PS > nuevo-psdrive-nombre mydb-raíz c:\ps\northwind.mdb - psprovider AccessDb**

   Aparecerá el siguiente resultado:

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Validar la conexión. Dado que la conexión se define como un miembro de la unidad, puede comprobar mediante el cmdlet Get-PDDrive.

   > [!NOTE]
   > El usuario aún no se puede interactuar con el proveedor como una unidad, como el proveedor necesita la funcionalidad del contenedor para esa interacción. Para obtener más información, consulte [creación de un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

   **PS > .connection (mydb get-psdrive)**

   Aparecerá el siguiente resultado:

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. Quite la unidad y salir del shell:

   **PS > remove-psdrive mydb**

   **PS > Salir**

## <a name="see-also"></a>Véase también

[Creación de proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Diseñar el proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Creación de un proveedor de PowerShell de Windows básico](./creating-a-basic-windows-powershell-provider.md)