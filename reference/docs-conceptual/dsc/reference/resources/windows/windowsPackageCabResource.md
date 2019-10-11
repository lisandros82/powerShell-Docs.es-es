---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso WindowsPackageCab de DSC
ms.openlocfilehash: ec465b2c3b1d180ba46ee24a61f2be1129148962
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954642"
---
# <a name="dsc-windowspackagecab-resource"></a>Recurso WindowsPackageCab de DSC

> Se aplica a: Windows PowerShell 5.1

El recurso **WindowsPackageCab** de Desired State Configuration (DSC) de Windows PowerShell ofrece un mecanismo para instalar o desinstalar paquetes de archivos .cab de Windows en un nodo de destino.

El nodo de destino debe tener instalado el módulo PowerShell de DISM. Para información, consulte [Use DISM in Windows PowerShell](/windows-hardware/manufacture/desktop/use-dism-in-windows-powershell-s14) (Uso de DISM en Windows PowerShell).

## <a name="syntax"></a>Sintaxis

```Syntax
{
    Name = [string]
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    Ensure = [string] { Absent | Present }
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Nombre |Indica el nombre del paquete para el que quiere garantizar un estado específico. |
|SourcePath |Indica la ruta de acceso donde reside el paquete. |
|LogPath |Indica la ruta de acceso completa donde quiere que el proveedor guarde un archivo de registro para instalar o desinstalar el paquete. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica si el paquete está instalado. Establezca esta propiedad en**Absent** para asegurarse de que el paquete no esté instalado (o se desinstale el paquete si está instalado). Establézcala en **Present** para asegurarse de que el paquete esté instalado. **Ensure** es una propiedad obligatoria en el recurso **WindowsPackageCab**. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

## <a name="example"></a>Ejemplo

La configuración de ejemplo siguiente toma parámetros de entrada y se asegura de que el archivo .cab especificado en el parámetro `$Name` esté instalado.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```