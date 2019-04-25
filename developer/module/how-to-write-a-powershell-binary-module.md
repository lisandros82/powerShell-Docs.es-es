---
title: Cómo escribir un módulo de PowerShell binario | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082233"
---
# <a name="how-to-write-a-powershell-binary-module"></a>Cómo escribir un módulo binario de PowerShell

Un módulo binario puede ser cualquier ensamblado (.dll) que contiene las clases de cmdlet. De forma predeterminada, se importan todos los cmdlets en el ensamblado cuando se importa el módulo binario. Sin embargo, puede restringir los cmdlets que se importan mediante la creación de un manifiesto de módulo cuyo módulo raíz es el ensamblado. (Por ejemplo, la clave CmdletsToExport del manifiesto puede utilizarse para exportar únicamente los cmdlets que son necesarios.) Además, un módulo binario puede contener otras piezas útiles de información de administración que un solo cmdlet no puede, una estructura de directorios y archivos adicionales.

El siguiente procedimiento describe cómo crear e instalar un módulo binario de PowerShell.

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>Cómo crear e instalar un módulo binario de PowerShell

1. Crear una solución de PowerShell binaria (por ejemplo, un cmdlet escrito en C#), con las capacidades que necesita y asegurarse de que se ejecuta correctamente.

   Desde una perspectiva de código, el núcleo de un módulo binario es simplemente un ensamblado de cmdlet. De hecho, PowerShell tratará el ensamblado de un solo cmdlet como un módulo, en cuanto a carga y descarga sin ningún esfuerzo adicional por parte del desarrollador. Para obtener más información sobre cómo escribir un cmdlet, consulte [escribir un Cmdlet de Windows PowerShell](../cmdlet/writing-a-windows-powershell-cmdlet.md).

2. Si es necesario, cree el resto de la solución: (otros cmdlets, archivos XML etc.) y se describen con un manifiesto de módulo.

   Además de describir los ensamblados de cmdlet en la solución, un manifiesto de módulo puede describir cómo desea que el módulo exporta y se importa, se expondrán los cmdlets y lo pasará archivos adicionales en el módulo. Como se indicó anteriormente sin embargo, PowerShell puede tratar un cmdlet binario como un módulo sin ningún esfuerzo adicional. Por lo tanto, un manifiesto de módulo es útil principalmente para combinar varios archivos en un único paquete, o para controlar explícitamente la publicación de un ensamblado determinado. Para obtener más información, consulte [cómo escribir un manifiesto del módulo de PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).

   El siguiente código es muy sencillo C# bloque de código que contiene tres cmdlets en el mismo archivo que se pueden usar como un módulo.

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

3. Empaquetar la solución y guardar el paquete en cualquier ubicación en la ruta de acceso del módulo de PowerShell.

   El `PSModulePath` variable de entorno global describe las rutas de acceso predeterminada que va a usar para buscar el módulo de PowerShell. Por ejemplo, podría ser una ruta de acceso comunes para guardar un módulo en un sistema `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`. Si no utiliza las rutas de acceso de forma predeterminada, deberá indicar explícitamente la ubicación de su módulo durante la instalación. Asegúrese de crear una carpeta para guardar el módulo, como es posible que necesite la carpeta para almacenar varios ensamblados y archivos de la solución.

   Tenga en cuenta que técnicamente no deberá instalar el módulo en cualquier lugar en el `PSModulePath` -son simplemente las ubicaciones predeterminadas que se va a buscar el módulo de PowerShell. Sin embargo, se considera una práctica recomendada para ello, a menos que tenga una buena razón para almacenar el módulo en otro lugar. Para obtener más información, consulte [instalar un módulo de PowerShell](./installing-a-powershell-module.md) y [modificar la ruta de instalación del módulo de PowerShell](./modifying-the-psmodulepath-installation-path.md).

4. Importe el módulo de PowerShell con una llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).

   Una llamada a [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cargará el módulo en la memoria activa. Si está usando PowerShell 3.0 y versiones posteriores, basta con llamar al nombre del módulo en el código también importará Para obtener más información, consulte [importar un módulo de PowerShell](./importing-a-powershell-module.md).

## <a name="importing-snap-in-assemblies-as-modules"></a>Importando ensamblados de complementos como módulos

Los cmdlets y proveedores que existen en ensamblados de complementos se pueden cargar como módulos binarios. Cuando los ensamblados de complementos se cargan como módulos binarios, los cmdlets y proveedores en el complemento están disponibles para el usuario, pero se omite la clase de complemento en el ensamblado y el complemento no está registrado. Como resultado, los cmdlets del complemento proporcionados por Windows PowerShell no puede detectar el complemento, aunque los cmdlets y proveedores están disponibles para la sesión.

Además, los archivos de formato o tipos que se hace referencia mediante el complemento no se puede importar como parte de un módulo binario. Para importar los archivos de formato y tipos debe crear un manifiesto de módulo. Ver, [cómo escribir un manifiesto de módulo de PowerShell](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6).

## <a name="see-also"></a>Véase también

[Escribir un módulo de Windows PowerShell](./writing-a-windows-powershell-module.md)
