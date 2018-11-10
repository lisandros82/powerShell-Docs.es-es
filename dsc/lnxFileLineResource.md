---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso nxFileLine de DSC para Linux
ms.openlocfilehash: 6a91db25638b09659adfabcec78f91bcb2e69dd9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225597"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>Recurso nxFileLine de DSC para Linux

El recurso **nxFileLine** de Desired State Configuration (DSC) de PowerShell ofrece un mecanismo para administrar líneas dentro de un archivo de configuración en un nodo de Linux.

## <a name="syntax"></a>Sintaxis

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propiedades

|  Propiedad |  Descripción |
|---|---|
| FilePath| La ruta de acceso completa al archivo para administrar las líneas en el nodo de destino.|
| ContainsLine| Una línea que debe asegurarse que exista en el archivo. Esta línea se anexará al archivo si no existe en él. **ContainsLine** es una propiedad obligatoria, pero se puede establecer en una cadena vacía (`ContainsLine = ""`) si no se necesita.|
| DoesNotContainPattern| Un patrón de expresiones regulares para las líneas que no deben existir en el archivo. Para todas las líneas que existan en el archivo y coincidan con esta expresión regular, se quitará la línea del archivo.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Ejemplo

En este ejemplo se muestra cómo utilizar el recurso **nxFileLine** para configurar el archivo `/etc/sudoers`, asegurándose de que el usuario monuser esté configurado como not requiretty.

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```