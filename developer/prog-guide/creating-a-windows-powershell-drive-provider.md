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
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="a7057-102">Creación de un proveedor de unidad de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7057-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="a7057-103">Este tema describe cómo crear un proveedor de unidades de Windows PowerShell que proporciona una manera de obtener acceso a un almacén de datos a través de una unidad de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7057-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="a7057-104">Este tipo de proveedor también se conoce como proveedores de la unidad de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7057-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="a7057-105">Las unidades de Windows PowerShell usadas el proveedor proporcionan los medios para conectarse al almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="a7057-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="a7057-106">El proveedor de la unidad de Windows PowerShell descrito aquí proporciona acceso a una base de datos de Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="a7057-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="a7057-107">Para este proveedor, la unidad de Windows PowerShell representa la base de datos (es posible agregar cualquier número de unidades a un proveedor de unidades), los contenedores de nivel superior de la unidad representan las tablas de la base de datos, y los elementos de los contenedores de las filas de las tablas.</span><span class="sxs-lookup"><span data-stu-id="a7057-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

<span data-ttu-id="a7057-108">Esta es una lista de las secciones de este tema.</span><span class="sxs-lookup"><span data-stu-id="a7057-108">Here is a list of the sections in this topic.</span></span> <span data-ttu-id="a7057-109">Si no está familiarizado con la escritura de un proveedor de la unidad de Windows PowerShell, lea estas secciones en el orden en que aparecen.</span><span class="sxs-lookup"><span data-stu-id="a7057-109">If you are unfamiliar with writing a Windows PowerShell drive provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="a7057-110">Sin embargo, si está familiarizado con la escritura de un proveedor de unidades, vaya directamente a la información que necesita.</span><span class="sxs-lookup"><span data-stu-id="a7057-110">However, if you are familiar with writing a drive provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="a7057-111">Definición de la clase de proveedor de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="a7057-111">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="a7057-112">Definir la funcionalidad de Base</span><span class="sxs-lookup"><span data-stu-id="a7057-112">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="a7057-113">Creación de información de estado de la unidad</span><span class="sxs-lookup"><span data-stu-id="a7057-113">Creating Drive State Information</span></span>](#Creating-Drive-State-Information)

- [<span data-ttu-id="a7057-114">Creación de una unidad</span><span class="sxs-lookup"><span data-stu-id="a7057-114">Creating a Drive</span></span>](#Creating-a-Drive)

- [<span data-ttu-id="a7057-115">Asociar los parámetros dinámicos a NewDrive</span><span class="sxs-lookup"><span data-stu-id="a7057-115">Attaching Dynamic Parameters to NewDrive</span></span>](#Attaching-Dynamic-Parameters-to-NewDrive)

- [<span data-ttu-id="a7057-116">Quitar una unidad</span><span class="sxs-lookup"><span data-stu-id="a7057-116">Removing a Drive</span></span>](#Removing-a-Drive)

- [<span data-ttu-id="a7057-117">Inicialización predeterminada de unidades</span><span class="sxs-lookup"><span data-stu-id="a7057-117">Initializing Default Drives</span></span>](#Initializing-Default-Drives)

- [<span data-ttu-id="a7057-118">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="a7057-118">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="a7057-119">Probar el proveedor de la unidad de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="a7057-119">Testing the Windows PowerShell Drive Provider</span></span>](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="a7057-120">Definición de la clase de proveedor de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="a7057-120">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="a7057-121">El proveedor de la unidad debe definir una clase .NET que se deriva de la [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase base.</span><span class="sxs-lookup"><span data-stu-id="a7057-121">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="a7057-122">Esta es la definición de clase para este proveedor de unidad:</span><span class="sxs-lookup"><span data-stu-id="a7057-122">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="a7057-123">Tenga en cuenta que en este ejemplo, el [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) atributo especifica un nombre descriptivo para el proveedor y las capacidades específicas de Windows PowerShell que el proveedor durante el procesamiento de comandos, expone el tiempo de ejecución de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7057-123">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="a7057-124">Los valores posibles para las capacidades del proveedor se definen mediante la [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeración.</span><span class="sxs-lookup"><span data-stu-id="a7057-124">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="a7057-125">Este proveedor de la unidad no es compatible con cualquiera de estas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="a7057-125">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="a7057-126">Definir la funcionalidad de Base</span><span class="sxs-lookup"><span data-stu-id="a7057-126">Defining Base Functionality</span></span>

<span data-ttu-id="a7057-127">Como se describe en [proveedor de diseño de Windows PowerShell](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) clase se deriva de la [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) clase base que define los métodos necesarios para inicializar y sin inicializar el proveedor.</span><span class="sxs-lookup"><span data-stu-id="a7057-127">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="a7057-128">Para implementar la funcionalidad para agregar información de inicialización específicas de la sesión y para liberar los recursos utilizados por el proveedor, consulte [creación de un proveedor de PowerShell de Windows básico](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a7057-128">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="a7057-129">Sin embargo, la mayoría de proveedores (incluido el proveedor que se describe aquí) puede usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7057-129">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="a7057-130">Creación de información de estado de la unidad</span><span class="sxs-lookup"><span data-stu-id="a7057-130">Creating Drive State Information</span></span>

<span data-ttu-id="a7057-131">Todos los proveedores de Windows PowerShell se consideran sin estado, lo que significa que el proveedor de la unidad debe crear cualquier información de estado que se necesita el tiempo de ejecución de Windows PowerShell cuando llama a su proveedor.</span><span class="sxs-lookup"><span data-stu-id="a7057-131">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="a7057-132">Para este proveedor de la unidad, la información de estado incluye la conexión a la base de datos que se mantiene como parte de la información de la unidad.</span><span class="sxs-lookup"><span data-stu-id="a7057-132">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="a7057-133">Este es el código que muestra cómo esta información se almacena en el [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto que describe la unidad:</span><span class="sxs-lookup"><span data-stu-id="a7057-133">Here is code that shows how this information is stored in the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="a7057-134">Creación de una unidad</span><span class="sxs-lookup"><span data-stu-id="a7057-134">Creating a Drive</span></span>

<span data-ttu-id="a7057-135">Para permitir que el tiempo de ejecución de Windows PowerShell crear una unidad, el proveedor de la unidad debe implementar la [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método.</span><span class="sxs-lookup"><span data-stu-id="a7057-135">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="a7057-136">El código siguiente muestra la implementación de la [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) método para este proveedor de unidad:</span><span class="sxs-lookup"><span data-stu-id="a7057-136">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="a7057-137">La invalidación de este método debe hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a7057-137">Your override of this method should do the following:</span></span>

- <span data-ttu-id="a7057-138">Compruebe que la [System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) miembro existe y que puede establecer una conexión al almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="a7057-138">Verify that the [System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="a7057-139">Crear una unidad y rellenar el miembro de la conexión, como soporte del `New-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a7057-139">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="a7057-140">Validar la [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto para la unidad propuesta.</span><span class="sxs-lookup"><span data-stu-id="a7057-140">Validate the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="a7057-141">Modificar el [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) objeto que describe la unidad con información de confiabilidad o rendimiento necesarios, o proporcionar datos adicionales para los llamadores usando la unidad.</span><span class="sxs-lookup"><span data-stu-id="a7057-141">Modify the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="a7057-142">Controlar los errores mediante la [System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) método y, luego, devolverla `null`.</span><span class="sxs-lookup"><span data-stu-id="a7057-142">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="a7057-143">Este método devuelve la información de unidad que se pasó al método o una versión específica del proveedor del mismo.</span><span class="sxs-lookup"><span data-stu-id="a7057-143">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="a7057-144">Asociar los parámetros dinámicos a NewDrive</span><span class="sxs-lookup"><span data-stu-id="a7057-144">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="a7057-145">El `New-PSDrive` cmdlet admitido por el proveedor de la unidad, es posible que requieren parámetros adicionales.</span><span class="sxs-lookup"><span data-stu-id="a7057-145">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="a7057-146">Para asociar estos parámetros dinámicos al cmdlet, el proveedor implementa la [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) método.</span><span class="sxs-lookup"><span data-stu-id="a7057-146">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="a7057-147">Este método devuelve un objeto que tiene las propiedades y campos con atributos similares a una clase de cmdlet de análisis o un [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objeto.</span><span class="sxs-lookup"><span data-stu-id="a7057-147">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="a7057-148">Este proveedor de la unidad no invalida este método.</span><span class="sxs-lookup"><span data-stu-id="a7057-148">This drive provider does not override this method.</span></span> <span data-ttu-id="a7057-149">Sin embargo, el código siguiente muestra la implementación predeterminada de este método:</span><span class="sxs-lookup"><span data-stu-id="a7057-149">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="a7057-150">Quitar una unidad</span><span class="sxs-lookup"><span data-stu-id="a7057-150">Removing a Drive</span></span>

<span data-ttu-id="a7057-151">Para cerrar la conexión de base de datos, el proveedor de la unidad debe implementar la [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método.</span><span class="sxs-lookup"><span data-stu-id="a7057-151">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="a7057-152">Este método cierra la conexión a la unidad después de limpiar cualquier información específica del proveedor.</span><span class="sxs-lookup"><span data-stu-id="a7057-152">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="a7057-153">El código siguiente muestra la implementación de la [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) método para este proveedor de unidad:</span><span class="sxs-lookup"><span data-stu-id="a7057-153">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="a7057-154">Si se puede quitar la unidad, el método debe devolver la información que se pasa al método a través de la `drive` parámetro.</span><span class="sxs-lookup"><span data-stu-id="a7057-154">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="a7057-155">Si no se puede quitar la unidad, el método debe escribir una excepción y, a continuación, devolver `null`.</span><span class="sxs-lookup"><span data-stu-id="a7057-155">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="a7057-156">Si el proveedor no invalida este método, la implementación predeterminada de este método sólo devuelve información de la unidad que se pasa como entrada.</span><span class="sxs-lookup"><span data-stu-id="a7057-156">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="a7057-157">Inicialización predeterminada de unidades</span><span class="sxs-lookup"><span data-stu-id="a7057-157">Initializing Default Drives</span></span>

<span data-ttu-id="a7057-158">La unidad proveedor implementa la [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método montar unidades de disco.</span><span class="sxs-lookup"><span data-stu-id="a7057-158">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="a7057-159">Por ejemplo, el proveedor de Active Directory puede montar una unidad para el contexto de nomenclatura si el equipo está unido a un dominio predeterminado.</span><span class="sxs-lookup"><span data-stu-id="a7057-159">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="a7057-160">Este método devuelve una colección de información de unidad sobre las unidades inicializadas o una colección vacía.</span><span class="sxs-lookup"><span data-stu-id="a7057-160">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="a7057-161">Se realiza la llamada a este método después de las llamadas en tiempo de ejecución de Windows PowerShell la [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) método para inicializar el proveedor.</span><span class="sxs-lookup"><span data-stu-id="a7057-161">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="a7057-162">Este proveedor de la unidad no invalida el [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) método.</span><span class="sxs-lookup"><span data-stu-id="a7057-162">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="a7057-163">Sin embargo, el código siguiente muestra la implementación predeterminada, que devuelve una colección vacía de unidad:</span><span class="sxs-lookup"><span data-stu-id="a7057-163">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="a7057-164">Cosas que recordar acerca de cómo implementar InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="a7057-164">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="a7057-165">Todos los proveedores de la unidad deben montar una unidad raíz para ayudar al usuario con capacidad de detección.</span><span class="sxs-lookup"><span data-stu-id="a7057-165">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="a7057-166">La unidad raíz podría enumerar las ubicaciones que actúan como raíces para otras unidades montadas.</span><span class="sxs-lookup"><span data-stu-id="a7057-166">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="a7057-167">Por ejemplo, el proveedor de Active Directory puede crear una unidad que se enumera los contextos de nomenclatura que se encuentra en la `namingContext` atributos en la raíz del entorno del sistema distribuido (DSE).</span><span class="sxs-lookup"><span data-stu-id="a7057-167">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="a7057-168">Esto ayuda a los usuarios a detectar los puntos de montaje para otras unidades.</span><span class="sxs-lookup"><span data-stu-id="a7057-168">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a7057-169">Ejemplo de código</span><span class="sxs-lookup"><span data-stu-id="a7057-169">Code Sample</span></span>

<span data-ttu-id="a7057-170">Para el código de ejemplo completo, vea [AccessDbProviderSample02 código de ejemplo](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="a7057-170">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="a7057-171">Probar el proveedor de la unidad de PowerShell de Windows</span><span class="sxs-lookup"><span data-stu-id="a7057-171">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="a7057-172">Cuando se ha registrado el proveedor de Windows PowerShell con Windows PowerShell, puede probarla mediante la ejecución de los cmdlets compatibles en la línea de comandos, incluidos los de cualquier disposición mediante la derivación.</span><span class="sxs-lookup"><span data-stu-id="a7057-172">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="a7057-173">Vamos a probar el proveedor de la unidad.</span><span class="sxs-lookup"><span data-stu-id="a7057-173">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="a7057-174">Ejecute el `Get-PSProvider` para recuperar la lista de proveedores para asegurarse de que el proveedor de la unidad AccessDB está presente:</span><span class="sxs-lookup"><span data-stu-id="a7057-174">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="a7057-175">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="a7057-175">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="a7057-176">Aparecerá el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="a7057-176">The following output appears:</span></span>

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

2. <span data-ttu-id="a7057-177">Asegúrese de que un nombre de servidor de base de datos (DSN) existe para la base de datos mediante el acceso a la **orígenes de datos** parte de la **herramientas administrativas** para el sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="a7057-177">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="a7057-178">En el **DSN de usuario** de tabla, haga doble clic en **base de datos de MS Access** y agregue la ruta de acceso de unidad C:\ps\northwind.mdb.</span><span class="sxs-lookup"><span data-stu-id="a7057-178">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="a7057-179">Cree una nueva unidad utilizando el proveedor de la unidad de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a7057-179">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="a7057-180">**PS > nuevo-psdrive-nombre mydb-raíz c:\ps\northwind.mdb - psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="a7057-180">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="a7057-181">Aparecerá el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="a7057-181">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="a7057-182">Validar la conexión.</span><span class="sxs-lookup"><span data-stu-id="a7057-182">Validate the connection.</span></span> <span data-ttu-id="a7057-183">Dado que la conexión se define como un miembro de la unidad, puede comprobar mediante el cmdlet Get-PDDrive.</span><span class="sxs-lookup"><span data-stu-id="a7057-183">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a7057-184">El usuario aún no se puede interactuar con el proveedor como una unidad, como el proveedor necesita la funcionalidad del contenedor para esa interacción.</span><span class="sxs-lookup"><span data-stu-id="a7057-184">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="a7057-185">Para obtener más información, consulte [creación de un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="a7057-185">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="a7057-186">**PS > .connection (mydb get-psdrive)**</span><span class="sxs-lookup"><span data-stu-id="a7057-186">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="a7057-187">Aparecerá el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="a7057-187">The following output appears:</span></span>

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

5. <span data-ttu-id="a7057-188">Quite la unidad y salir del shell:</span><span class="sxs-lookup"><span data-stu-id="a7057-188">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="a7057-189">**PS > remove-psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="a7057-189">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="a7057-190">**PS > Salir**</span><span class="sxs-lookup"><span data-stu-id="a7057-190">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="a7057-191">Véase también</span><span class="sxs-lookup"><span data-stu-id="a7057-191">See Also</span></span>

[<span data-ttu-id="a7057-192">Creación de proveedores de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7057-192">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="a7057-193">Diseñar el proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a7057-193">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="a7057-194">Creación de un proveedor de PowerShell de Windows básico</span><span class="sxs-lookup"><span data-stu-id="a7057-194">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)