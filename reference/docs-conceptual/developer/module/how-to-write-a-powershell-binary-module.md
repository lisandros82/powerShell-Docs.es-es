---
title: Cómo escribir un módulo binario de PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367124"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Cómo escribir un módulo binario de PowerShell

Un módulo binario puede ser cualquier ensamblado (. dll) que contenga clases de cmdlet. De forma predeterminada, todos los cmdlets del ensamblado se importan cuando se importa el módulo binario. Sin embargo, puede restringir los cmdlets que se importan creando un manifiesto de módulo cuyo módulo raíz es el ensamblado. (Por ejemplo, la clave CmdletsToExport del manifiesto se puede usar para exportar solo los cmdlets necesarios). Además, un módulo binario puede contener archivos adicionales, una estructura de directorios y otras partes de información útil de administración que no puede tener un único cmdlet.

En el procedimiento siguiente se describe cómo crear e instalar un módulo binario de PowerShell.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Cómo crear e instalar un módulo binario de PowerShell

1. Cree una solución de PowerShell binaria (como un cmdlet escrito C#en), con las funcionalidades que necesita y asegúrese de que se ejecuta correctamente.

   Desde el punto de vista del código, el núcleo de un módulo binario es simplemente un ensamblado de cmdlet. De hecho, PowerShell tratará un solo ensamblado de cmdlet como módulo, en términos de carga y descarga, sin ningún esfuerzo adicional en la parte del desarrollador. Para obtener más información sobre cómo escribir un cmdlet, consulte [escribir un cmdlet de Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Si es necesario, cree el resto de la solución: (cmdlets adicionales, archivos XML, etc.) y describirlas con un manifiesto del módulo.

   Además de describir los ensamblados de cmdlet en la solución, un manifiesto de módulo puede describir cómo desea que se exporte e importe el módulo, qué cmdlets se expondrán y qué archivos adicionales se incluirán en el módulo.
   Como se indicó anteriormente, PowerShell puede tratar un cmdlet binario como un módulo sin ningún esfuerzo adicional.
   Como tal, un manifiesto de módulo es útil principalmente para combinar varios archivos en un único paquete o para controlar explícitamente la publicación de un ensamblado determinado.
   Para obtener más información, vea [Cómo escribir un manifiesto del módulo de PowerShell](how-to-write-a-powershell-module-manifest.md).

   El código siguiente es un bloque de C# código muy simple que contiene tres cmdlets en el mismo archivo que se pueden usar como módulo.

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. Empaquete la solución y guarde el paquete en algún lugar de la ruta de acceso del módulo de PowerShell.

   La variable de entorno global `PSModulePath` describe las rutas de acceso predeterminadas que PowerShell usará para buscar el módulo. Por ejemplo, una ruta de acceso común para guardar un módulo en un sistema sería `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Si no utiliza las rutas de acceso predeterminadas, tendrá que indicar explícitamente la ubicación del módulo durante la instalación. Asegúrese de crear una carpeta para guardar el módulo en, ya que es posible que necesite la carpeta para almacenar varios ensamblados y archivos de la solución.

   Tenga en cuenta que técnicamente no es necesario instalar el módulo en ningún lugar del `PSModulePath`; estos son simplemente las ubicaciones predeterminadas que PowerShell buscará en el módulo. Sin embargo, se recomienda que lo haga, a menos que tenga una buena razón para almacenar el módulo en otra parte. Para obtener más información, vea [instalar un módulo de PowerShell](./installing-a-powershell-module.md) y [modificar la ruta de instalación del módulo de PowerShell](./modifying-the-psmodulepath-installation-path.md).

4. Importe el módulo en PowerShell con una llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   La llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cargará el módulo en la memoria activa. Si usa PowerShell 3,0 y versiones posteriores, la llamada al nombre del módulo en el código también lo importará; para obtener más información, vea [importar un módulo de PowerShell](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importar ensamblados de complementos como módulos

Los cmdlets y proveedores que existen en ensamblados de complementos se pueden cargar como módulos binarios. Cuando los ensamblados de complemento se cargan como módulos binarios, los cmdlets y proveedores del complemento están disponibles para el usuario, pero la clase de complemento del ensamblado se omite y el complemento no está registrado. Como resultado, los cmdlets de complemento proporcionados por Windows PowerShell no pueden detectar el complemento aunque los cmdlets y proveedores estén disponibles para la sesión.

Además, los archivos de formato o de tipos a los que hace referencia el complemento no se pueden importar como parte de un módulo binario.
Para importar los archivos de formato y tipos, debe crear un manifiesto de módulo.
Vea [Cómo escribir un manifiesto del módulo de PowerShell](how-to-write-a-powershell-module-manifest.md).

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
