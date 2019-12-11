---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recursos de DSC Archive
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954772"
---
# <a name="dsc-archive-resource"></a>Recursos de DSC Archive

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso Archive de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para desempaquetar archivos de almacenamiento (.zip) en una ruta de acceso específica.

## <a name="syntax"></a>Sintaxis

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Destination |Especifica la ubicación donde quiere garantizar que se extraiga el contenido del archivo. |
|Ruta |Especifica la ruta de acceso de origen del archivo. |
|Checksum |Define el tipo que se usará cuando se determine si dos archivos son iguales. Si no se especifica **Checksum**, solo se usa el nombre del archivo o directorio para la comparación. Los valores válidos son: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. Si especifica **Checksum** sin **Validate**, se producirá un error de configuración. |
|Force |Determinadas operaciones de archivos (por ejemplo, sobrescribir un archivo o eliminar un directorio que no está vacío) provocarán un error. Si se usa la propiedad **Force**, se invalidan estos errores. El valor predeterminado es **False**. |
|Validar| Utiliza la propiedad **Checksum** para determinar si el archivo coincide con la firma. Si especifica **Checksum** sin **Validate**, se producirá un error de configuración. Si especifica **Validate** sin **Checksum**, se usará una suma de comprobación _SHA-256_ **Checksum** de forma predeterminada. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina si se debe comprobar si existe el contenido del archivo en **Destination**. Establezca esta propiedad en **Present** para asegurarse de que el contenido exista. Establézcala en **Absent** para asegurarse de que no exista. El valor predeterminado es **Present**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar el recurso Archive para asegurarse de que el contenido de un archivo llamado `Test.zip` exista y se extraiga en un destino determinado.

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```