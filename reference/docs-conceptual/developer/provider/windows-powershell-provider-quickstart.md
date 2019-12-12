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
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="b8903-102">Inicio rápido de Proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8903-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="b8903-103">En este tema se explica cómo crear un proveedor de Windows PowerShell que tenga la funcionalidad básica de crear una nueva unidad.</span><span class="sxs-lookup"><span data-stu-id="b8903-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="b8903-104">Para obtener información general sobre los proveedores, consulte [información general del proveedor de Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b8903-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="b8903-105">Para obtener ejemplos de proveedores con una funcionalidad más completa, vea [ejemplos](./provider-samples.md)de proveedores.</span><span class="sxs-lookup"><span data-stu-id="b8903-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="b8903-106">Escribir un proveedor básico</span><span class="sxs-lookup"><span data-stu-id="b8903-106">Writing a basic provider</span></span>

<span data-ttu-id="b8903-107">La funcionalidad más básica de un proveedor de Windows PowerShell es crear y quitar unidades.</span><span class="sxs-lookup"><span data-stu-id="b8903-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="b8903-108">En este ejemplo, se implementan los métodos [System. Management. Automation. Provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) y [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) de la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b8903-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="b8903-109">También verá cómo declarar una clase de proveedor.</span><span class="sxs-lookup"><span data-stu-id="b8903-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="b8903-110">Al escribir un proveedor, puede especificar las unidades de discos predeterminadas que se crean automáticamente cuando el proveedor está disponible.</span><span class="sxs-lookup"><span data-stu-id="b8903-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="b8903-111">También se define un método para crear unidades nuevas que usan ese proveedor.</span><span class="sxs-lookup"><span data-stu-id="b8903-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="b8903-112">Los ejemplos que se proporcionan en este tema se basan en el ejemplo [AccessDBProviderSample02](./accessdbprovidersample02.md) , que forma parte de un ejemplo más grande que representa una base de datos de Access como una unidad de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8903-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="b8903-113">Configurar el proyecto</span><span class="sxs-lookup"><span data-stu-id="b8903-113">Setting up the project</span></span>

<span data-ttu-id="b8903-114">En Visual Studio, cree un proyecto de biblioteca de clases denominado AccessDBProviderSample.</span><span class="sxs-lookup"><span data-stu-id="b8903-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="b8903-115">Complete los pasos siguientes para configurar el proyecto para que se inicie Windows PowerShell y el proveedor se cargue en la sesión, al compilar e iniciar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="b8903-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="b8903-116">Configurar el proyecto de proveedor</span><span class="sxs-lookup"><span data-stu-id="b8903-116">Configure the provider project</span></span>

1. <span data-ttu-id="b8903-117">Agregue el ensamblado System. Management. Automation como una referencia al proyecto.</span><span class="sxs-lookup"><span data-stu-id="b8903-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="b8903-118">Haga clic en **proyecto > propiedades de AccessDBProviderSample > depurar**.</span><span class="sxs-lookup"><span data-stu-id="b8903-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="b8903-119">En **iniciar proyecto**, haga clic en **iniciar programa externo**y navegue hasta el archivo ejecutable de Windows PowerShell (normalmente c:\Windows\System32\WindowsPowerShell\v1.0\\. PowerShell. exe).</span><span class="sxs-lookup"><span data-stu-id="b8903-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="b8903-120">En **Opciones de inicio**, escriba lo siguiente en el cuadro argumentos de la **línea de comandos** : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="b8903-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="b8903-121">Declarar la clase de proveedor</span><span class="sxs-lookup"><span data-stu-id="b8903-121">Declaring the provider class</span></span>

<span data-ttu-id="b8903-122">Nuestro proveedor se deriva de la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b8903-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="b8903-123">La mayoría de los proveedores que proporcionan funcionalidad real (acceso y manipulación de elementos, navegación del almacén de datos y obtención y configuración de contenido de elementos) se derivan de la clase [System. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b8903-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="b8903-124">Además de especificar que la clase deriva de [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), debe decorarla con [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) como se muestra en el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="b8903-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="b8903-125">Implementación de NewDrive</span><span class="sxs-lookup"><span data-stu-id="b8903-125">Implementing NewDrive</span></span>

<span data-ttu-id="b8903-126">El método [System. Management. Automation. Provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) lo llama el motor de Windows PowerShell cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) y especifica el nombre del proveedor.</span><span class="sxs-lookup"><span data-stu-id="b8903-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="b8903-127">El motor de Windows PowerShell pasa el parámetro PSDriveInfo y el método devuelve la nueva unidad al motor de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b8903-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="b8903-128">Este método se debe declarar dentro de la clase creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b8903-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="b8903-129">El método comprueba primero para asegurarse de que el objeto de unidad y la raíz de la unidad que se pasaron existen, devolviendo `null` si alguno de ellos no es así.</span><span class="sxs-lookup"><span data-stu-id="b8903-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="b8903-130">A continuación, usa un constructor de la clase interna AccessDBPSDriveInfo para crear una nueva unidad y una conexión a la base de datos de Access que la unidad representa.</span><span class="sxs-lookup"><span data-stu-id="b8903-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="b8903-131">A continuación se muestra la clase interna AccessDBPSDriveInfo que incluye el constructor utilizado para crear una nueva unidad y contiene la información de estado de la unidad.</span><span class="sxs-lookup"><span data-stu-id="b8903-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="b8903-132">Implementación de RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="b8903-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="b8903-133">El método [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) lo llama el motor de Windows PowerShell cuando un usuario llama al cmdlet [Microsoft. PowerShell. Commands. RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) .</span><span class="sxs-lookup"><span data-stu-id="b8903-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet.</span></span> <span data-ttu-id="b8903-134">El método de este proveedor cierra la conexión a la base de datos de Access.</span><span class="sxs-lookup"><span data-stu-id="b8903-134">The method in this provider closes the connection to the Access database.</span></span>

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