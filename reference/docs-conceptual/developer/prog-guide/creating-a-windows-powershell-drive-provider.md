---
title: Crear un proveedor de unidades de Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: 2e3d97e224b06bdf36ac0bc1237911e029ea762d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366834"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Creación de un proveedor de unidad de Windows PowerShell

En este tema se describe cómo crear un proveedor de unidades de Windows PowerShell que proporciona una manera de tener acceso a un almacén de datos a través de una unidad de Windows PowerShell. Este tipo de proveedor también se conoce como proveedores de unidades de Windows PowerShell. Las unidades de Windows PowerShell que usa el proveedor proporcionan los medios para conectarse al almacén de datos.

El proveedor de unidades de Windows PowerShell que se describe aquí proporciona acceso a una base de datos de Microsoft Access. Para este proveedor, la unidad de Windows PowerShell representa la base de datos (es posible agregar cualquier número de unidades a un proveedor de unidades), los contenedores de nivel superior de la unidad representan las tablas de la base de datos y los elementos de los contenedores representan las filas de las tablas.

## <a name="defining-the-windows-powershell-provider-class"></a>Definir la clase de proveedor de Windows PowerShell

El proveedor de unidades debe definir una clase .NET que derive de la clase base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Esta es la definición de clase para este proveedor de unidades:

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Observe que en este ejemplo, el atributo [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) especifica un nombre descriptivo para el proveedor y las capacidades específicas de Windows PowerShell que el proveedor expone a las ventanas. Tiempo de ejecución de PowerShell durante el procesamiento de comandos. Los valores posibles para las capacidades del proveedor se definen mediante la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Este proveedor de unidades no es compatible con ninguna de estas funcionalidades.

## <a name="defining-base-functionality"></a>Definir la funcionalidad básica

Como se describe en [diseñar un proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md), la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) se deriva de la clase base [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) que define los métodos necesarios para inicializar y anular la inicialización del proveedor. Para implementar la funcionalidad para agregar información de inicialización específica de la sesión y liberar recursos utilizados por el proveedor, consulte [crear un proveedor de Windows PowerShell básico](./creating-a-basic-windows-powershell-provider.md). Sin embargo, la mayoría de los proveedores (incluido el proveedor descrito aquí) pueden usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.

## <a name="creating-drive-state-information"></a>Creando información de estado de la unidad

Todos los proveedores de Windows PowerShell se consideran sin estado, lo que significa que el proveedor de unidades debe crear cualquier información de estado que sea necesaria para el tiempo de ejecución de Windows PowerShell cuando llame a su proveedor.

Para este proveedor de unidades, la información de estado incluye la conexión a la base de datos que se guarda como parte de la información de la unidad. Este es el código que muestra cómo se almacena esta información en el objeto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) que describe la unidad:

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Crear una unidad

Para permitir que el tiempo de ejecución de Windows PowerShell cree una unidad, el proveedor de la unidad debe implementar el método [System. Management. Automation. Provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) . En el código siguiente se muestra la implementación del método [System. Management. Automation. Provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) para este proveedor de unidades:

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

La invalidación de este método debe hacer lo siguiente:

- Compruebe que el miembro [System. Management. Automation. PSDriveinfo. root *](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) existe y que se puede realizar una conexión al almacén de datos.

- Cree una unidad y rellene el miembro de conexión, en compatibilidad con el cmdlet `New-PSDrive`.

- Valide el objeto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) de la unidad propuesta.

- Modifique el objeto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) que describe la unidad con cualquier información de rendimiento o confiabilidad necesaria, o proporcione datos adicionales para los autores de llamadas que usan la unidad.

- Controle los errores con el método [System. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) y, a continuación, devuelva `null`.

  Este método devuelve la información de la unidad que se pasó al método o a una versión específica del proveedor.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Adjuntar parámetros dinámicos a NewDrive

Es posible que el cmdlet `New-PSDrive` que admite el proveedor de unidades requiera parámetros adicionales. Para adjuntar estos parámetros dinámicos al cmdlet, el proveedor implementa el método [System. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) . Este método devuelve un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .

Este proveedor de unidades no invalida este método. Sin embargo, en el código siguiente se muestra la implementación predeterminada de este método:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Quitar una unidad

Para cerrar la conexión de base de datos, el proveedor de la unidad debe implementar el método [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) . Este método cierra la conexión a la unidad después de limpiar cualquier información específica del proveedor.

En el código siguiente se muestra la implementación del método [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) para este proveedor de unidades:

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Si se puede quitar la unidad, el método debe devolver la información que se pasa al método a través del parámetro `drive`. Si no se puede quitar la unidad, el método debe escribir una excepción y, a continuación, devolver `null`. Si el proveedor no invalida este método, la implementación predeterminada de este método simplemente devuelve la información de la unidad que se pasa como entrada.

## <a name="initializing-default-drives"></a>Inicializando unidades predeterminadas

El proveedor de unidades implementa el método [System. Management. Automation. Provider. Drivecmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) para montar unidades. Por ejemplo, el proveedor de Active Directory podría montar una unidad para el contexto de nomenclatura predeterminado si el equipo está unido a un dominio.

Este método devuelve una colección de información de la unidad sobre las unidades inicializadas, o una colección vacía. La llamada a este método se realiza después de que el tiempo de ejecución de Windows PowerShell llame al método [System. Management. Automation. Provider. Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) para inicializar el proveedor.

Este proveedor de unidades no invalida el método [System. Management. Automation. Provider. Drivecmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) . Sin embargo, en el código siguiente se muestra la implementación predeterminada, que devuelve una colección de unidades vacía:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Aspectos que se deben recordar sobre la implementación de InitializeDefaultDrives

Todos los proveedores de unidades deben montar una unidad raíz para ayudar al usuario a detectar. La unidad raíz podría mostrar ubicaciones que sirvan como raíces para otras unidades montadas. Por ejemplo, el proveedor de Active Directory podría crear una unidad que muestre los contextos de nomenclatura que se encuentran en los atributos `namingContext` en el entorno de sistema distribuido raíz (DSE). Esto ayuda a los usuarios a detectar puntos de montaje para otras unidades.

## <a name="code-sample"></a>Código de ejemplo

Para obtener el código de ejemplo completo, vea el [ejemplo de código AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Probar el proveedor de unidades de Windows PowerShell

Cuando el proveedor de Windows PowerShell se ha registrado con Windows PowerShell, puede probarlo mediante la ejecución de los cmdlets admitidos en la línea de comandos, incluidos los cmdlets disponibles por derivación. Vamos a probar el proveedor de la unidad de ejemplo.

1. Ejecute el cmdlet `Get-PSProvider` para recuperar la lista de proveedores para asegurarse de que el proveedor de la unidad AccessDB está presente:

   **@No__t de > de PS-1**

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

2. Asegúrese de que existe un nombre de servidor de base de datos (DSN) para la base de datos mediante el acceso a la parte de **orígenes de datos** de las **herramientas administrativas** del sistema operativo. En la tabla **DSN de usuario** , haga doble clic en base de datos de **MS Access** y agregue la ruta de acceso de la unidad C:\ps\northwind.mdb.

3. Cree una nueva unidad con el proveedor de unidades de ejemplo:

   **PS > New-PSDrive-Name mydb-root c:\ps\northwind.mdb-psprovider AccessDb**

   Aparecerá el siguiente resultado:

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Valide la conexión. Dado que la conexión se define como un miembro de la unidad, puede comprobarla con el cmdlet Get-PDDrive.

   > [!NOTE]
   > El usuario todavía no puede interactuar con el proveedor como una unidad, ya que el proveedor necesita la funcionalidad de contenedor para esa interacción. Para obtener más información, vea [crear un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

   **PS > (get-PSDrive mydb). Connection**

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

5. Quite la unidad y salga del shell:

   **PS > Remove-PSDrive mydb**

   **Salida de > de PS**

## <a name="see-also"></a>Véase también

[Crear proveedores de Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Diseño del proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Crear un proveedor básico de Windows PowerShell](./creating-a-basic-windows-powershell-provider.md)
