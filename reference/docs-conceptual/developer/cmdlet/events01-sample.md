---
title: Ejemplo de Events01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 8f745cc0e5ef6db7a6bbdf39d826103f3b8a98ce
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369744"
---
# <a name="events01-sample"></a><span data-ttu-id="752bf-102">Ejemplo Events01</span><span class="sxs-lookup"><span data-stu-id="752bf-102">Events01 Sample</span></span>

<span data-ttu-id="752bf-103">En este ejemplo se muestra cómo crear un cmdlet que permite al usuario registrarse para los eventos generados por [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="752bf-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>
<span data-ttu-id="752bf-104">Con este cmdlet, los usuarios pueden registrar una acción para que se ejecute cuando se cree un archivo en un directorio específico.</span><span class="sxs-lookup"><span data-stu-id="752bf-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span>
<span data-ttu-id="752bf-105">Este ejemplo se deriva de la clase base [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .</span><span class="sxs-lookup"><span data-stu-id="752bf-105">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="752bf-106">Cómo compilar el ejemplo mediante Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="752bf-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="752bf-107">Con el SDK de Windows PowerShell 2,0 instalado, vaya a la carpeta Events01.</span><span class="sxs-lookup"><span data-stu-id="752bf-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span>
   <span data-ttu-id="752bf-108">La ubicación predeterminada es `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span><span class="sxs-lookup"><span data-stu-id="752bf-108">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="752bf-109">Haga doble clic en el icono del archivo de solución (. sln).</span><span class="sxs-lookup"><span data-stu-id="752bf-109">Double-click the icon for the solution (.sln) file.</span></span>
   <span data-ttu-id="752bf-110">Se abrirá el proyecto de ejemplo en Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="752bf-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="752bf-111">En el menú **Compilar**, seleccione **Compilar solución**.</span><span class="sxs-lookup"><span data-stu-id="752bf-111">In the **Build** menu, select **Build Solution**.</span></span>
   <span data-ttu-id="752bf-112">La biblioteca del ejemplo se compilará en las carpetas predeterminadas `\bin` o `\bin\debug`.</span><span class="sxs-lookup"><span data-stu-id="752bf-112">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="752bf-113">Ejecución del ejemplo</span><span class="sxs-lookup"><span data-stu-id="752bf-113">How to run the sample</span></span>

1. <span data-ttu-id="752bf-114">Cree la siguiente carpeta de módulo:</span><span class="sxs-lookup"><span data-stu-id="752bf-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="752bf-115">Copie el archivo de biblioteca del ejemplo en la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="752bf-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="752bf-116">Inicie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="752bf-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="752bf-117">Ejecute el siguiente comando para cargar el cmdlet en Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="752bf-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="752bf-118">Use el cmdlet Register-FileSystemEvent para registrar una acción que escribirá un mensaje cuando se cree un archivo en el directorio temporal.</span><span class="sxs-lookup"><span data-stu-id="752bf-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="752bf-119">Cree un archivo en el directorio TEMP y tenga en cuenta que la acción se ejecuta (se muestra el mensaje).</span><span class="sxs-lookup"><span data-stu-id="752bf-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="752bf-120">Esta es una salida de ejemplo que se produce al seguir estos pasos.</span><span class="sxs-lookup"><span data-stu-id="752bf-120">This is a sample output that results by following these steps.</span></span>

```output
Id              Name            State      HasMoreData     Location             Command
--              ----            -----      -----------     --------             -------
1               26932870-d3b... NotStarted False                                 Write-Host "A f...

```

```powershell
Set-Content $env:temp\test.txt "This is a test file"
```

```output
A file was created in the TEMP directory
```

## <a name="requirements"></a><span data-ttu-id="752bf-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="752bf-121">Requirements</span></span>

<span data-ttu-id="752bf-122">Este ejemplo requiere Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="752bf-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="752bf-123">Demuestra</span><span class="sxs-lookup"><span data-stu-id="752bf-123">Demonstrates</span></span>

<span data-ttu-id="752bf-124">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="752bf-124">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="752bf-125">Cómo escribir un cmdlet para el registro de eventos</span><span class="sxs-lookup"><span data-stu-id="752bf-125">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="752bf-126">El cmdlet se deriva de la clase [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) , que proporciona compatibilidad con los parámetros comunes a los cmdlets de `Register-*Event`.</span><span class="sxs-lookup"><span data-stu-id="752bf-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span>
<span data-ttu-id="752bf-127">Los cmdlets que se derivan de [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) solo necesitan definir sus parámetros particulares e invalidar los métodos abstractos `GetSourceObject` y `GetSourceObjectEventName`.</span><span class="sxs-lookup"><span data-stu-id="752bf-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="752bf-128">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="752bf-128">Example</span></span>

<span data-ttu-id="752bf-129">En este ejemplo se muestra cómo registrarse para eventos generados por [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="752bf-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="752bf-130">Véase también</span><span class="sxs-lookup"><span data-stu-id="752bf-130">See Also</span></span>

[<span data-ttu-id="752bf-131">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="752bf-131">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)