---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso nxArchive de DSC para Linux
ms.openlocfilehash: 800954478f149e29c22d1a88304c3be9950f109a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048043"
---
# <a name="dsc-for-linux-nxarchive-resource"></a>Recurso nxArchive de DSC para Linux

El recurso **nxArchive** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para desempaquetar archivos de almacenamiento (.tar, .zip) en una ruta de acceso específica de un nodo Linux.

## <a name="syntax"></a>Sintaxis

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Propiedades

|  Propiedad |  Descripción |
|---|---|
| SourcePath| Especifica la ruta de acceso de origen del archivo. Debe ser un archivo .tar, .zip o .tar.gz. |
| DestinationPath| Especifica la ubicación donde quiere garantizar que se extraiga el contenido del archivo.|
| Checksum| Define el tipo que se utilizará al determinar si se ha actualizado el archivo de origen. Los valores son: "ctime", "mtime" o "md5". El valor predeterminado es "md5".|
| Force| Determinadas operaciones de archivos (por ejemplo, sobrescribir un archivo o eliminar un directorio que no está vacío) provocarán un error. Si se usa la propiedad **Force**, se invalidan estos errores. El valor predeterminado es **$false**.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|
| Ensure| Determina si se debe comprobar si existe el contenido del archivo en **Destination**. Establezca esta propiedad en "Present" para asegurarse de que el contenido exista. Establézcala en "Absent" para asegurarse de que no exista. El valor predeterminado es "Present".|

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el recurso **nxArchive** para asegurarse de que el contenido de un archivo llamado `website.tar` exista y se extraiga en un destino determinado.

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```