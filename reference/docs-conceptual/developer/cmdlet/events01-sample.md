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
# <a name="events01-sample"></a>Ejemplo Events01

En este ejemplo se muestra cómo crear un cmdlet que permite al usuario registrarse para los eventos generados por [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).
Con este cmdlet, los usuarios pueden registrar una acción para que se ejecute cuando se cree un archivo en un directorio específico.
Este ejemplo se deriva de la clase base [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Cómo compilar el ejemplo mediante Visual Studio.

1. Con el SDK de Windows PowerShell 2,0 instalado, vaya a la carpeta Events01.
   La ubicación predeterminada es `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.

2. Haga doble clic en el icono del archivo de solución (. sln).
   Se abrirá el proyecto de ejemplo en Microsoft Visual Studio.

3. En el menú **Compilar**, seleccione **Compilar solución**.
   La biblioteca del ejemplo se compilará en las carpetas predeterminadas `\bin` o `\bin\debug`.

### <a name="how-to-run-the-sample"></a>Ejecución del ejemplo

1. Cree la siguiente carpeta de módulo:

    `[user]/documents/windowspowershell/modules/events01`

2. Copie el archivo de biblioteca del ejemplo en la carpeta del módulo.

3. Inicie Windows PowerShell.

4. Ejecute el siguiente comando para cargar el cmdlet en Windows PowerShell:

    ```powershell
    import-module events01
    ```

5. Use el cmdlet Register-FileSystemEvent para registrar una acción que escribirá un mensaje cuando se cree un archivo en el directorio temporal.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. Cree un archivo en el directorio TEMP y tenga en cuenta que la acción se ejecuta (se muestra el mensaje).

Esta es una salida de ejemplo que se produce al seguir estos pasos.

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

## <a name="requirements"></a>Requisitos

Este ejemplo requiere Windows PowerShell 2,0.

## <a name="demonstrates"></a>Demuestra

Este ejemplo muestra lo siguiente.

### <a name="how-to-write-a-cmdlet-for-event-registration"></a>Cómo escribir un cmdlet para el registro de eventos

El cmdlet se deriva de la clase [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) , que proporciona compatibilidad con los parámetros comunes a los cmdlets de `Register-*Event`.
Los cmdlets que se derivan de [Microsoft. PowerShell. Commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) solo necesitan definir sus parámetros particulares e invalidar los métodos abstractos `GetSourceObject` y `GetSourceObjectEventName`.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo registrarse para eventos generados por [System. IO. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).

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

## <a name="see-also"></a>Véase también

[Escribir un cmdlet de Windows PowerShell](writing-a-windows-powershell-cmdlet.md)