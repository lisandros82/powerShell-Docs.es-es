---
title: Inicio rápido de proveedor de PowerShell de Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 151b7125afe1b0d386467a0e5f89225716857ac2
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054924"
---
# <a name="windows-powershell-provider-quickstart"></a>Inicio rápido de Proveedor de Windows PowerShell

En este tema se explica cómo crear un proveedor de Windows PowerShell que tiene la funcionalidad básica de la creación de una nueva unidad. Para obtener información general sobre los proveedores, consulte [Introducción al proveedor de Windows PowerShell](./windows-powershell-provider-overview.md). Para obtener ejemplos de proveedores con la funcionalidad más completa, consulte [muestras de proveedor](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Escribir un proveedor básico

Es la funcionalidad más básica de un proveedor de Windows PowerShell crear y quitar unidades. En este ejemplo, implementamos el [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) y [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) métodos de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase. También verá cómo declarar una clase de proveedor.

Al escribir un proveedor, puede especificar unidades predeterminado que se crean automáticamente cuando el proveedor está disponible. También define un método para crear nuevas unidades que usan ese proveedor.

Los ejemplos proporcionados en este tema se basan en el [AccessDBProviderSample02](./accessdbprovidersample02.md) ejemplo, que forma parte de un ejemplo más grande que representa una base de datos de Access como una unidad de Windows PowerShell.

### <a name="setting-up-the-project"></a>Configurar el proyecto

En Visual Studio, cree un proyecto de biblioteca de clases denominado AccessDBProviderSample. Complete los pasos siguientes para configurar el proyecto para que Windows PowerShell se iniciará y el proveedor se cargará en la sesión, al crear e iniciar el proyecto.

##### <a name="configure-the-provider-project"></a>Configurar el proyecto de proveedor

1. Agregue el ensamblado System.Management.Automation como una referencia al proyecto.

2. Haga clic en **proyecto > Propiedades AccessDBProviderSample > depurar**. En **Iniciar proyecto**, haga clic en **iniciar programa externo**y navegue hasta el archivo ejecutable de Windows PowerShell (normalmente c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).

3. En **opciones de inicio**, escriba lo siguiente en el **argumentos de línea de comandos** cuadro: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Declarar la clase de proveedor

Nuestro proveedor deriva el [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase. La mayoría de los proveedores que proporcionan la funcionalidad real (acceso y manipular elementos, navegar por el almacén de datos y obtener y establecer el contenido de elementos) que se deriva de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase.

Además de especificar que la clase se deriva de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), debe decorar con el [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) tal como se muestra en el ejemplo.

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

### <a name="implementing-newdrive"></a>Implementar NewDrive

El [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método se llama el motor de Windows PowerShell cuando un usuario llama a la [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)cmdlet especificando el nombre del proveedor. El parámetro PSDriveInfo se pasa por el motor de Windows PowerShell y el método devuelve la nueva unidad al motor de Windows PowerShell. Este método debe declararse dentro de la clase creada anteriormente.

El método comprueba primero para asegurarse de que el objeto de unidad y la raíz de la unidad que se pasaron en existen, se devuelve `null` si cualquiera de ellos no lo hacen. A continuación, usa un constructor de la clase interna AccessDBPSDriveInfo para crear una nueva unidad y representa una conexión a la base de datos de acceso a la unidad.

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

La siguiente es la clase interna AccessDBPSDriveInfo que incluye el constructor usado para crear una nueva unidad y contiene la información de estado de la unidad.

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

### <a name="implementing-removedrive"></a>Implementar RemoveDrive

El [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método se llama el motor de Windows PowerShell cuando un usuario llama a la [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet. El método de este proveedor cierra la conexión a la base de datos de Access.

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