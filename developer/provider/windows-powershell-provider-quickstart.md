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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080890"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="b5417-102">Inicio rápido de Proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b5417-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="b5417-103">En este tema se explica cómo crear un proveedor de Windows PowerShell que tiene la funcionalidad básica de la creación de una nueva unidad.</span><span class="sxs-lookup"><span data-stu-id="b5417-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="b5417-104">Para obtener información general sobre los proveedores, consulte [Introducción al proveedor de Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b5417-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="b5417-105">Para obtener ejemplos de proveedores con la funcionalidad más completa, consulte [muestras de proveedor](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b5417-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="b5417-106">Escribir un proveedor básico</span><span class="sxs-lookup"><span data-stu-id="b5417-106">Writing a basic provider</span></span>

<span data-ttu-id="b5417-107">Es la funcionalidad más básica de un proveedor de Windows PowerShell crear y quitar unidades.</span><span class="sxs-lookup"><span data-stu-id="b5417-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="b5417-108">En este ejemplo, implementamos el [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) y [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) métodos de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="b5417-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="b5417-109">También verá cómo declarar una clase de proveedor.</span><span class="sxs-lookup"><span data-stu-id="b5417-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="b5417-110">Al escribir un proveedor, puede especificar unidades predeterminado que se crean automáticamente cuando el proveedor está disponible.</span><span class="sxs-lookup"><span data-stu-id="b5417-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="b5417-111">También define un método para crear nuevas unidades que usan ese proveedor.</span><span class="sxs-lookup"><span data-stu-id="b5417-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="b5417-112">Los ejemplos proporcionados en este tema se basan en el [AccessDBProviderSample02](./accessdbprovidersample02.md) ejemplo, que forma parte de un ejemplo más grande que representa una base de datos de Access como una unidad de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5417-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="b5417-113">Configurar el proyecto</span><span class="sxs-lookup"><span data-stu-id="b5417-113">Setting up the project</span></span>

<span data-ttu-id="b5417-114">En Visual Studio, cree un proyecto de biblioteca de clases denominado AccessDBProviderSample.</span><span class="sxs-lookup"><span data-stu-id="b5417-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="b5417-115">Complete los pasos siguientes para configurar el proyecto para que Windows PowerShell se iniciará y el proveedor se cargará en la sesión, al crear e iniciar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="b5417-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="b5417-116">Configurar el proyecto de proveedor</span><span class="sxs-lookup"><span data-stu-id="b5417-116">Configure the provider project</span></span>

1. <span data-ttu-id="b5417-117">Agregue el ensamblado System.Management.Automation como una referencia al proyecto.</span><span class="sxs-lookup"><span data-stu-id="b5417-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="b5417-118">Haga clic en **proyecto > Propiedades AccessDBProviderSample > depurar**.</span><span class="sxs-lookup"><span data-stu-id="b5417-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="b5417-119">En **Iniciar proyecto**, haga clic en **iniciar programa externo**y navegue hasta el archivo ejecutable de Windows PowerShell (normalmente c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="b5417-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="b5417-120">En **opciones de inicio**, escriba lo siguiente en el **argumentos de línea de comandos** cuadro: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="b5417-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="b5417-121">Declarar la clase de proveedor</span><span class="sxs-lookup"><span data-stu-id="b5417-121">Declaring the provider class</span></span>

<span data-ttu-id="b5417-122">Nuestro proveedor deriva el [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="b5417-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="b5417-123">La mayoría de los proveedores que proporcionan la funcionalidad real (acceso y manipular elementos, navegar por el almacén de datos y obtener y establecer el contenido de elementos) que se deriva de la [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) clase.</span><span class="sxs-lookup"><span data-stu-id="b5417-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="b5417-124">Además de especificar que la clase se deriva de [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), debe decorar con el [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) tal como se muestra en el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="b5417-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="b5417-125">Implementar NewDrive</span><span class="sxs-lookup"><span data-stu-id="b5417-125">Implementing NewDrive</span></span>

<span data-ttu-id="b5417-126">El [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método se llama el motor de Windows PowerShell cuando un usuario llama a la [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)cmdlet especificando el nombre del proveedor.</span><span class="sxs-lookup"><span data-stu-id="b5417-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="b5417-127">El parámetro PSDriveInfo se pasa por el motor de Windows PowerShell y el método devuelve la nueva unidad al motor de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5417-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="b5417-128">Este método debe declararse dentro de la clase creada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b5417-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="b5417-129">El método comprueba primero para asegurarse de que el objeto de unidad y la raíz de la unidad que se pasaron en existen, se devuelve `null` si cualquiera de ellos no lo hacen.</span><span class="sxs-lookup"><span data-stu-id="b5417-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="b5417-130">A continuación, usa un constructor de la clase interna AccessDBPSDriveInfo para crear una nueva unidad y representa una conexión a la base de datos de acceso a la unidad.</span><span class="sxs-lookup"><span data-stu-id="b5417-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="b5417-131">La siguiente es la clase interna AccessDBPSDriveInfo que incluye el constructor usado para crear una nueva unidad y contiene la información de estado de la unidad.</span><span class="sxs-lookup"><span data-stu-id="b5417-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="b5417-132">Implementar RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="b5417-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="b5417-133">El [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método se llama el motor de Windows PowerShell cuando un usuario llama a la [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b5417-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span></span> <span data-ttu-id="b5417-134">El método de este proveedor cierra la conexión a la base de datos de Access.</span><span class="sxs-lookup"><span data-stu-id="b5417-134">The method in this provider closes the connection to the Access database.</span></span>

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