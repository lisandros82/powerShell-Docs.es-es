---
title: Inicio rápido del proveedor de Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 949c0d63b1e5bca1bfe670362df4297c29e98fcc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359924"
---
# <a name="windows-powershell-provider-quickstart"></a>Inicio rápido de Proveedor de Windows PowerShell

En este tema se explica cómo crear un proveedor de Windows PowerShell que tenga la funcionalidad básica de crear una nueva unidad. Para obtener información general sobre los proveedores, consulte [información general del proveedor de Windows PowerShell](./windows-powershell-provider-overview.md). Para obtener ejemplos de proveedores con una funcionalidad más completa, vea [ejemplos](./provider-samples.md)de proveedores.

## <a name="writing-a-basic-provider"></a>Escribir un proveedor básico

La funcionalidad más básica de un proveedor de Windows PowerShell es crear y quitar unidades. En este ejemplo, se implementan los métodos [System. Management. Automation. Provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) y [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) de la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . También verá cómo declarar una clase de proveedor.

Al escribir un proveedor, puede especificar las unidades de discos predeterminadas que se crean automáticamente cuando el proveedor está disponible. También se define un método para crear unidades nuevas que usan ese proveedor.

Los ejemplos que se proporcionan en este tema se basan en el ejemplo [AccessDBProviderSample02](./accessdbprovidersample02.md) , que forma parte de un ejemplo más grande que representa una base de datos de Access como una unidad de Windows PowerShell.

### <a name="setting-up-the-project"></a>Configurar el proyecto

En Visual Studio, cree un proyecto de biblioteca de clases denominado AccessDBProviderSample. Complete los pasos siguientes para configurar el proyecto para que se inicie Windows PowerShell y el proveedor se cargue en la sesión, al compilar e iniciar el proyecto.

##### <a name="configure-the-provider-project"></a>Configurar el proyecto de proveedor

1. Agregue el ensamblado System. Management. Automation como una referencia al proyecto.

2. Haga clic en **proyecto > propiedades de AccessDBProviderSample > depurar**. En **iniciar proyecto**, haga clic en **iniciar programa externo**y navegue hasta el archivo ejecutable de Windows PowerShell (normalmente c:\Windows\System32\WindowsPowerShell\v1.0\\. PowerShell. exe).

3. En **Opciones de inicio**, escriba lo siguiente en el cuadro argumentos de la **línea de comandos** : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Declarar la clase de proveedor

Nuestro proveedor se deriva de la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . La mayoría de los proveedores que proporcionan funcionalidad real (acceso y manipulación de elementos, navegación del almacén de datos y obtención y configuración de contenido de elementos) se derivan de la clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

Además de especificar que la clase deriva de [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), debe decorarla con [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) como se muestra en el ejemplo.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a>Implementación de NewDrive

El método [System. Management. Automation. Provider. Drivecmdletprovider. newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) lo llama el motor de Windows PowerShell cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) y especifica el nombre del proveedor. El motor de Windows PowerShell pasa el parámetro PSDriveInfo y el método devuelve la nueva unidad al motor de Windows PowerShell. Este método se debe declarar dentro de la clase creada anteriormente.

El método comprueba primero para asegurarse de que el objeto de unidad y la raíz de la unidad que se pasaron existen, devolviendo `null` si alguno de ellos no es así. A continuación, usa un constructor de la clase interna AccessDBPSDriveInfo para crear una nueva unidad y una conexión a la base de datos de Access que la unidad representa.

```csharp
protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    }
```

A continuación se muestra la clase interna AccessDBPSDriveInfo que incluye el constructor utilizado para crear una nueva unidad y contiene la información de estado de la unidad.

```csharp
internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  }
```

### <a name="implementing-removedrive"></a>Implementación de RemoveDrive

El método [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) lo llama el motor de Windows PowerShell cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) . El método de este proveedor cierra la conexión a la base de datos de Access.

```csharp
protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    }
```