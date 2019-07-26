---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso nxScript de DSC para Linux
ms.openlocfilehash: 0ad0530f1de7b86ff48c4eb1f79870f6682894a1
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372168"
---
# <a name="dsc-for-linux-nxscript-resource"></a>Recurso nxScript de DSC para Linux

El recurso **nxScript** de la configuración de estado deseado (DSC) de PowerShell ofrece un mecanismo para ejecutar scripts de Linux en un nodo de Linux.

## <a name="syntax"></a>Sintaxis

```
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Propiedades

|  Propiedad |  Descripción |
|---|---|
| GetScript| Proporciona un script para devolver el estado actual de la máquina.  Este script se ejecuta al invocar el script [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer). El script debe comenzar con el par de caracteres shebang, como por ejemplo: #!/bin/bash.|
| SetScript| Proporciona un script que define el estado correcto de la máquina. Cuando se invoca el script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), el bloque **TestScript** se ejecuta primero. Si el bloque **TestScript** devuelve un código de salida distinto de 0, se ejecutará el bloque **SetScript**. Si el bloque **TestScript** devuelve un código de salida de 0, no se ejecutará el bloque **SetScript**. El script debe comenzar con el par de caracteres shebang, como por ejemplo: `#!/bin/bash`.|
| TestScript| Proporciona un script que evalúa si el nodo tiene actualmente el estado correcto. Cuando se invoca el script [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer), este se ejecuta. Si devuelve un código de salida distinto de 0, se ejecutará el bloque SetScript. Si devuelve un código de salida de 0, no se ejecutará el bloque **SetScript**. El bloque **TestScript** también se ejecuta cuando se invoca el script [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer). Sin embargo, en este caso, el bloque **SetScript** no se ejecutará, independientemente del código de salida que se devuelva del bloque **TestScript**. El bloque **TestScript** debe tener contenido y debe devolver un código de salida de 0 si la configuración real coincide con la configuración del estado deseado actual, y un código de salida distinto de 0 si no coincide. (La configuración de estado deseado actual es la última configuración establecida en el nodo que está usando DSC). El script debe comenzar con el par de caracteres shebang, como por ejemplo: 1#!/bin/bash.1|
| Usuario| El usuario con el que se ejecutará el script.|
| Grupo| El grupo con el que se ejecutará el script.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento **ID** del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el uso del recurso **nxScript** para realizar una administración de configuración adicional.

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
}
}
```
