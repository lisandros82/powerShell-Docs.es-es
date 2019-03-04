---
title: Ejemplo Events01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 3edbcabeff0c8d84831823df11749d152b347566
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863341"
---
# <a name="events01-sample"></a><span data-ttu-id="f7471-102">Ejemplo Events01</span><span class="sxs-lookup"><span data-stu-id="f7471-102">Events01 Sample</span></span>

<span data-ttu-id="f7471-103">En este ejemplo se muestra cómo crear un cmdlet que permite al usuario al registrarse para eventos generados por [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="f7471-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="f7471-104">Con este cmdlet, los usuarios pueden registrar una acción que se ejecutará cuando se crea un archivo en un directorio específico.</span><span class="sxs-lookup"><span data-stu-id="f7471-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="f7471-105">En este ejemplo se deriva de la [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) clase base.</span><span class="sxs-lookup"><span data-stu-id="f7471-105">This sample derives from the [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="f7471-106">Cómo generar el ejemplo mediante Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7471-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="f7471-107">Con Windows PowerShell 2.0 instalado el SDK, vaya a la carpeta Events01.</span><span class="sxs-lookup"><span data-stu-id="f7471-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span> <span data-ttu-id="f7471-108">La ubicación predeterminada es C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span><span class="sxs-lookup"><span data-stu-id="f7471-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span></span>

2. <span data-ttu-id="f7471-109">Haga doble clic en el icono del archivo de solución (.sln).</span><span class="sxs-lookup"><span data-stu-id="f7471-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="f7471-110">Se abre el proyecto de ejemplo en Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7471-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="f7471-111">En el **compilar** menú, seleccione **compilar solución**.</span><span class="sxs-lookup"><span data-stu-id="f7471-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="f7471-112">En las carpetas \bin o \bin\debug de forma predeterminada, se compilará la biblioteca para el ejemplo.</span><span class="sxs-lookup"><span data-stu-id="f7471-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="f7471-113">Cómo ejecutar el ejemplo</span><span class="sxs-lookup"><span data-stu-id="f7471-113">How to run the sample</span></span>

1. <span data-ttu-id="f7471-114">Cree la siguiente carpeta del módulo:</span><span class="sxs-lookup"><span data-stu-id="f7471-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="f7471-115">Copie el archivo de biblioteca para el ejemplo en la carpeta del módulo.</span><span class="sxs-lookup"><span data-stu-id="f7471-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="f7471-116">Inicie Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f7471-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="f7471-117">Ejecute el siguiente comando para cargar el cmdlet en Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f7471-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="f7471-118">Use el cmdlet Register-FileSystemEvent para registrar una acción que se escribirá un mensaje cuando se crea un archivo en el directorio TEMP.</span><span class="sxs-lookup"><span data-stu-id="f7471-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="f7471-119">Cree un archivo en el directorio TEMP y tenga en cuenta que se ejecuta la acción (se muestra el mensaje).</span><span class="sxs-lookup"><span data-stu-id="f7471-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="f7471-120">Se trata de una salida de ejemplo que da como resultado, siga estos pasos.</span><span class="sxs-lookup"><span data-stu-id="f7471-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="f7471-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7471-121">Requirements</span></span>

<span data-ttu-id="f7471-122">Este ejemplo requiere Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="f7471-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f7471-123">Demostraciones</span><span class="sxs-lookup"><span data-stu-id="f7471-123">Demonstrates</span></span>

<span data-ttu-id="f7471-124">Este ejemplo muestra lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="f7471-124">This sample demonstrates the following.</span></span>

- <span data-ttu-id="f7471-125">Cómo escribir un cmdlet para el registro de eventos.</span><span class="sxs-lookup"><span data-stu-id="f7471-125">How to write a cmdlet for event registration.</span></span> <span data-ttu-id="f7471-126">El cmdlet se deriva de la [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) (clase), que proporciona compatibilidad para los parámetros comunes a Register-\* cmdlets del evento.</span><span class="sxs-lookup"><span data-stu-id="f7471-126">The cmdlet derives from the [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the Register-\*Event cmdlets.</span></span> <span data-ttu-id="f7471-127">Los cmdlets que se derivan de [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) sólo tiene que definir sus parámetros concretos e invalidar la `GetSourceObject` y `GetSourceObjectEventName` métodos abstractos.</span><span class="sxs-lookup"><span data-stu-id="f7471-127">Cmdlets that are derived from [Microsoft.Powershell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="f7471-128">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="f7471-128">Example</span></span>

<span data-ttu-id="f7471-129">En este ejemplo se muestra cómo registrar los eventos generados por [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span><span class="sxs-lookup"><span data-stu-id="f7471-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f7471-130">Véase también</span><span class="sxs-lookup"><span data-stu-id="f7471-130">See Also</span></span>

[<span data-ttu-id="f7471-131">Escribir un cmdlet de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f7471-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)