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
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="8ddfc-102">Creación de un proveedor de unidad de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ddfc-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="8ddfc-103">En este tema se describe cómo crear un proveedor de unidades de Windows PowerShell que proporciona una manera de tener acceso a un almacén de datos a través de una unidad de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="8ddfc-104">Este tipo de proveedor también se conoce como proveedores de unidades de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="8ddfc-105">Las unidades de Windows PowerShell que usa el proveedor proporcionan los medios para conectarse al almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="8ddfc-106">El proveedor de unidades de Windows PowerShell que se describe aquí proporciona acceso a una base de datos de Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="8ddfc-107">Para este proveedor, la unidad de Windows PowerShell representa la base de datos (es posible agregar cualquier número de unidades a un proveedor de unidades), los contenedores de nivel superior de la unidad representan las tablas de la base de datos y los elementos de los contenedores representan las filas de las tablas.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="8ddfc-108">Definir la clase de proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ddfc-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="8ddfc-109">El proveedor de unidades debe definir una clase .NET que derive de la clase base [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="8ddfc-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="8ddfc-110">Esta es la definición de clase para este proveedor de unidades:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-110">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="8ddfc-111">Observe que en este ejemplo, el atributo [System. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) especifica un nombre descriptivo para el proveedor y las capacidades específicas de Windows PowerShell que el proveedor expone a las ventanas. Tiempo de ejecución de PowerShell durante el procesamiento de comandos.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="8ddfc-112">Los valores posibles para las capacidades del proveedor se definen mediante la enumeración [System. Management. Automation. Provider. Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) .</span><span class="sxs-lookup"><span data-stu-id="8ddfc-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="8ddfc-113">Este proveedor de unidades no es compatible con ninguna de estas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="8ddfc-114">Definir la funcionalidad básica</span><span class="sxs-lookup"><span data-stu-id="8ddfc-114">Defining Base Functionality</span></span>

<span data-ttu-id="8ddfc-115">Como se describe en [diseñar un proveedor de Windows PowerShell](./designing-your-windows-powershell-provider.md), la clase [System. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) se deriva de la clase base [System. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) que define los métodos necesarios para inicializar y anular la inicialización del proveedor.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="8ddfc-116">Para implementar la funcionalidad para agregar información de inicialización específica de la sesión y liberar recursos utilizados por el proveedor, consulte [crear un proveedor de Windows PowerShell básico](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8ddfc-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="8ddfc-117">Sin embargo, la mayoría de los proveedores (incluido el proveedor descrito aquí) pueden usar la implementación predeterminada de esta funcionalidad proporcionada por Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="8ddfc-118">Creando información de estado de la unidad</span><span class="sxs-lookup"><span data-stu-id="8ddfc-118">Creating Drive State Information</span></span>

<span data-ttu-id="8ddfc-119">Todos los proveedores de Windows PowerShell se consideran sin estado, lo que significa que el proveedor de unidades debe crear cualquier información de estado que sea necesaria para el tiempo de ejecución de Windows PowerShell cuando llame a su proveedor.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="8ddfc-120">Para este proveedor de unidades, la información de estado incluye la conexión a la base de datos que se guarda como parte de la información de la unidad.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="8ddfc-121">Este es el código que muestra cómo se almacena esta información en el objeto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) que describe la unidad:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="8ddfc-122">Crear una unidad</span><span class="sxs-lookup"><span data-stu-id="8ddfc-122">Creating a Drive</span></span>

<span data-ttu-id="8ddfc-123">Para permitir que el tiempo de ejecución de Windows PowerShell cree una unidad, el proveedor de la unidad debe implementar el método [System. Management. Automation. Provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) .</span><span class="sxs-lookup"><span data-stu-id="8ddfc-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="8ddfc-124">En el código siguiente se muestra la implementación del método [System. Management. Automation. Provider. Drivecmdletprovider. newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) para este proveedor de unidades:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="8ddfc-125">La invalidación de este método debe hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="8ddfc-126">Compruebe que el miembro [System. Management. Automation. PSDriveinfo. root \*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) existe y que se puede realizar una conexión al almacén de datos.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="8ddfc-127">Cree una unidad y rellene el miembro de conexión, en compatibilidad con el cmdlet `New-PSDrive`.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="8ddfc-128">Valide el objeto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) de la unidad propuesta.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="8ddfc-129">Modifique el objeto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) que describe la unidad con cualquier información de rendimiento o confiabilidad necesaria, o proporcione datos adicionales para los autores de llamadas que usan la unidad.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="8ddfc-130">Controle los errores con el método [System. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) y, a continuación, devuelva `null`.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="8ddfc-131">Este método devuelve la información de la unidad que se pasó al método o a una versión específica del proveedor.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="8ddfc-132">Adjuntar parámetros dinámicos a NewDrive</span><span class="sxs-lookup"><span data-stu-id="8ddfc-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="8ddfc-133">Es posible que el cmdlet `New-PSDrive` que admite el proveedor de unidades requiera parámetros adicionales.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="8ddfc-134">Para adjuntar estos parámetros dinámicos al cmdlet, el proveedor implementa el método [System. Management. Automation. Provider. Drivecmdletprovider. Newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="8ddfc-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="8ddfc-135">Este método devuelve un objeto que tiene propiedades y campos con atributos de análisis similares a una clase de cmdlet o un objeto [System. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .</span><span class="sxs-lookup"><span data-stu-id="8ddfc-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="8ddfc-136">Este proveedor de unidades no invalida este método.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-136">This drive provider does not override this method.</span></span> <span data-ttu-id="8ddfc-137">Sin embargo, en el código siguiente se muestra la implementación predeterminada de este método:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="8ddfc-138">Quitar una unidad</span><span class="sxs-lookup"><span data-stu-id="8ddfc-138">Removing a Drive</span></span>

<span data-ttu-id="8ddfc-139">Para cerrar la conexión de base de datos, el proveedor de la unidad debe implementar el método [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .</span><span class="sxs-lookup"><span data-stu-id="8ddfc-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="8ddfc-140">Este método cierra la conexión a la unidad después de limpiar cualquier información específica del proveedor.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="8ddfc-141">En el código siguiente se muestra la implementación del método [System. Management. Automation. Provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) para este proveedor de unidades:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="8ddfc-142">Si se puede quitar la unidad, el método debe devolver la información que se pasa al método a través del parámetro `drive`.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="8ddfc-143">Si no se puede quitar la unidad, el método debe escribir una excepción y, a continuación, devolver `null`.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="8ddfc-144">Si el proveedor no invalida este método, la implementación predeterminada de este método simplemente devuelve la información de la unidad que se pasa como entrada.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="8ddfc-145">Inicializando unidades predeterminadas</span><span class="sxs-lookup"><span data-stu-id="8ddfc-145">Initializing Default Drives</span></span>

<span data-ttu-id="8ddfc-146">El proveedor de unidades implementa el método [System. Management. Automation. Provider. Drivecmdletprovider. Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) para montar unidades.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="8ddfc-147">Por ejemplo, el proveedor de Active Directory podría montar una unidad para el contexto de nomenclatura predeterminado si el equipo está unido a un dominio.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="8ddfc-148">Este método devuelve una colección de información de la unidad sobre las unidades inicializadas, o una colección vacía.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="8ddfc-149">La llamada a este método se realiza después de que el tiempo de ejecución de Windows PowerShell llame al método [System. Management. Automation. Provider. Cmdletprovider. Start \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) para inicializar el proveedor.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="8ddfc-150">Este proveedor de unidades no invalida el método [System. Management. Automation. Provider. Drivecmdletprovider. Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) .</span><span class="sxs-lookup"><span data-stu-id="8ddfc-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="8ddfc-151">Sin embargo, en el código siguiente se muestra la implementación predeterminada, que devuelve una colección de unidades vacía:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="8ddfc-152">Aspectos que se deben recordar sobre la implementación de InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="8ddfc-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="8ddfc-153">Todos los proveedores de unidades deben montar una unidad raíz para ayudar al usuario a detectar.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="8ddfc-154">La unidad raíz podría mostrar ubicaciones que sirvan como raíces para otras unidades montadas.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="8ddfc-155">Por ejemplo, el proveedor de Active Directory podría crear una unidad que muestre los contextos de nomenclatura que se encuentran en los atributos `namingContext` en el entorno de sistema distribuido raíz (DSE).</span><span class="sxs-lookup"><span data-stu-id="8ddfc-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="8ddfc-156">Esto ayuda a los usuarios a detectar puntos de montaje para otras unidades.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8ddfc-157">Código de ejemplo</span><span class="sxs-lookup"><span data-stu-id="8ddfc-157">Code Sample</span></span>

<span data-ttu-id="8ddfc-158">Para obtener el código de ejemplo completo, vea el [ejemplo de código AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8ddfc-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="8ddfc-159">Probar el proveedor de unidades de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ddfc-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="8ddfc-160">Cuando el proveedor de Windows PowerShell se ha registrado con Windows PowerShell, puede probarlo mediante la ejecución de los cmdlets admitidos en la línea de comandos, incluidos los cmdlets disponibles por derivación.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="8ddfc-161">Vamos a probar el proveedor de la unidad de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="8ddfc-162">Ejecute el cmdlet `Get-PSProvider` para recuperar la lista de proveedores para asegurarse de que el proveedor de la unidad AccessDB está presente:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="8ddfc-163">**@No__t de > de PS-1**</span><span class="sxs-lookup"><span data-stu-id="8ddfc-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="8ddfc-164">Aparecerá el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-164">The following output appears:</span></span>

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

2. <span data-ttu-id="8ddfc-165">Asegúrese de que existe un nombre de servidor de base de datos (DSN) para la base de datos mediante el acceso a la parte de **orígenes de datos** de las **herramientas administrativas** del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="8ddfc-166">En la tabla **DSN de usuario** , haga doble clic en base de datos de **MS Access** y agregue la ruta de acceso de la unidad C:\ps\northwind.mdb.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="8ddfc-167">Cree una nueva unidad con el proveedor de unidades de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-167">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="8ddfc-168">**PS > New-PSDrive-Name mydb-root c:\ps\northwind.mdb-psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="8ddfc-168">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="8ddfc-169">Aparecerá el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-169">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="8ddfc-170">Valide la conexión.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-170">Validate the connection.</span></span> <span data-ttu-id="8ddfc-171">Dado que la conexión se define como un miembro de la unidad, puede comprobarla con el cmdlet Get-PDDrive.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-171">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="8ddfc-172">El usuario todavía no puede interactuar con el proveedor como una unidad, ya que el proveedor necesita la funcionalidad de contenedor para esa interacción.</span><span class="sxs-lookup"><span data-stu-id="8ddfc-172">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="8ddfc-173">Para obtener más información, vea [crear un proveedor de contenedores de Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8ddfc-173">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="8ddfc-174">**PS > (get-PSDrive mydb). Connection**</span><span class="sxs-lookup"><span data-stu-id="8ddfc-174">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="8ddfc-175">Aparecerá el siguiente resultado:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-175">The following output appears:</span></span>

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

5. <span data-ttu-id="8ddfc-176">Quite la unidad y salga del shell:</span><span class="sxs-lookup"><span data-stu-id="8ddfc-176">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="8ddfc-177">**PS > Remove-PSDrive mydb**</span><span class="sxs-lookup"><span data-stu-id="8ddfc-177">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="8ddfc-178">**Salida de > de PS**</span><span class="sxs-lookup"><span data-stu-id="8ddfc-178">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="8ddfc-179">Véase también</span><span class="sxs-lookup"><span data-stu-id="8ddfc-179">See Also</span></span>

[<span data-ttu-id="8ddfc-180">Crear proveedores de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ddfc-180">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="8ddfc-181">Diseño del proveedor de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ddfc-181">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="8ddfc-182">Crear un proveedor básico de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8ddfc-182">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)
