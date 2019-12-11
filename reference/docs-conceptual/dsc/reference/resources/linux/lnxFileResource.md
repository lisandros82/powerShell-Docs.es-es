---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso nxFile de DSC para Linux
ms.openlocfilehash: be5f098d2fe1c8b354c07e6a8f882b8fdf00e1db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954832"
---
# <a name="dsc-for-linux-nxfile-resource"></a>Recurso nxFile de DSC para Linux

El recurso **nxFile** de Desired State Configuration (DSC) de PowerShell ofrece un mecanismo para administrar archivos y directorios en un nodo de Linux.

## <a name="syntax"></a>Sintaxis

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|DestinationPath |Especifica la ubicación donde desea garantizar el estado de un archivo o directorio. |
|SourcePath |Especifica la ruta de acceso de la que se copiará el recurso de archivo o carpeta. Esta ruta de acceso puede ser una ruta de acceso local o una dirección URL `http/https/ftp`. Las direcciones URL remotas `http/https/ftp` solo se admiten cuando el valor de la propiedad **Type** es **File**. |
|Tipo |Especifica si el recurso que se está configurando es un directorio o un archivo. Establezca esta propiedad en **Directory** para indicar que el recurso es un directorio. Establézcala en **File** para indicar que el recurso es un archivo. El valor predeterminado es **File**. |
|Contenido |Especifica el contenido de un archivo, como una cadena determinada. |
|Checksum |Define el tipo que se usará cuando se determine si dos archivos son iguales. Si no se especifica **Checksum**, solo se usa el nombre del archivo o directorio para la comparación. Los valores son: **ctime**, **mtime** o **md5**. |
|Recurse |Indica si se incluyen los subdirectorios. Establezca esta propiedad en `$true` para indicar que quiere que los subdirectorios se incluyan. El valor predeterminado es `$false`. Esta propiedad solo es válida cuando la propiedad **Type** está establecida en **Directory**. |
|Force |Determinadas operaciones de archivos (por ejemplo, sobrescribir un archivo o eliminar un directorio que no está vacío) provocarán un error. Si se usa la propiedad **Force**, se invalidan estos errores. El valor predeterminado es `$false`. |
|Vínculos |Especifica el comportamiento deseado de los vínculos simbólicos. Establezca esta propiedad en **follow** para seguir los vínculos simbólicos y actuar sobre el destino de los vínculos. Por ejemplo, para copiar el archivo en lugar del vínculo. Establezca esta propiedad en **manage** para actuar sobre el vínculo. Por ejemplo, para copiar el propio vínculo. Establezca esta propiedad en **ignore** para omitir los vínculos simbólicos. |
|Grupo |El nombre del elemento **Group** con permisos para el archivo o directorio. |
|Modo |Especifica los permisos deseados para el recurso, en notación octal o simbólica. Por ejemplo, **777** o **rwxrwxrwx**. Si utiliza la notación simbólica, no especifique el primer carácter que indica el directorio o archivo. |
|Propietario |El nombre del elemento Group propietario del archivo o directorio. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina si se debe comprobar si existe el archivo. Establezca esta propiedad en **Present** para asegurarse de que el archivo exista. Establézcala en **Absent** para asegurarse de que el archivo no exista. El valor predeterminado es **Present**. |

## <a name="additional-information"></a>Información adicional

Linux y Windows usan distintos caracteres de salto de línea en los archivos de texto de forma predeterminada, y esto puede provocar resultados inesperados cuando se configuran algunos archivos en un equipo Linux con **nxFile**. Hay varias maneras de administrar el contenido de un archivo de Linux a la vez que se evitan los problemas provocados por los caracteres de salto de línea inesperados:

1. Copie el archivo desde un origen remoto (http, https o FTP)

   Realice una copia intermedia en un servidor web o FTP accesible para los nodos que va a configurar. Defina la propiedad **SourcePath** del recurso **nxFile** con la dirección URL de la web o el ftp para el archivo.

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      nxFile resolvConf
      {
         SourcePath = "http://10.185.85.11/conf/resolv.conf"
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
      }
   }
   ```

1. lea el contenido del archivo del script de PowerShell con [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) tras establecer la propiedad **$OFS** que utilizará el carácter de salto de línea de Linux.

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      $OFS = "`n"
      $Contents = Get-Content C:\temp\resolv.conf

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = "$Contents"
      }
   }
   ```

1. use una función de PowerShell para reemplazar los saltos de línea de Windows por caracteres de salto de línea de Linux.

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
      Return $outputStr
   }

   Import-DSCResource -Module nx

   Node $Node
   {
      $Contents = @'
   search contoso.com
   domain contoso.com
   nameserver 10.185.85.11
   '@
       $Contents = LinuxString $Contents

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = $Contents
      }
   }
   ```

## <a name="example"></a>Ejemplo

El ejemplo siguiente se asegura de que el directorio `/opt/mydir` exista y de que un archivo con el contenido especificado exista en este directorio.

```powershell
Import-DSCResource -Module nx

Node $node {
    nxFile DirectoryExample
    {
        Ensure = "Present"
        DestinationPath = "/opt/mydir"
        Type = "Directory"
    }

    nxFile FileExample
    {
        Ensure = "Present"
        Destinationpath = "/opt/mydir/myfile"
        Contents=@"
#!/bin/bash`necho "hello world"`n
"@
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```