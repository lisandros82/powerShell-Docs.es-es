---
ms.date: 08/23/2018
keywords: powershell, cmdlet
title: Descripción de los módulos de PowerShell
ms.openlocfilehash: 3033a4fe1a704fbbfa76e6d38662c8b22c3dbd9b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030381"
---
# <a name="understanding-pipelines"></a>Descripción de las canalizaciones

Las canalizaciones actúan como una serie de segmentos de canalización conectados. Los elementos que se mueven por la canalización pasan a través de cada segmento. Para crear una canalización en PowerShell, se conectan comandos con el operador de canalización "|". La salida de cada comando se usa como entrada para el siguiente.

La notación utilizada para las canalizaciones es similar a la notación utilizada en otros shells. A primera vista, puede que no sea evidente en qué se diferencian las canalizaciones en PowerShell. Aunque se ve texto en la pantalla, PowerShell canaliza objetos, no texto, entre los comandos.

## <a name="the-powershell-pipeline"></a>Canalización de PowerShell

Las canalizaciones son sin duda el concepto más valioso usado en las interfaces de línea de comandos. Cuando se usan correctamente, las canalizaciones reducen el esfuerzo de usar comandos complejos y facilitan la visualización del flujo de trabajo de los comandos. Cada comando de una canalización (denominado un elemento de canalización) pasa la salida al siguiente comando de la canalización elemento por elemento. Los comandos no tienen que controlar más de un elemento a la vez. El resultado es un menor consumo de recursos y la capacidad de empezar a obtener la salida inmediatamente.

Por ejemplo, si usa el cmdlet `Out-Host` para forzar una presentación página por página de la salida de otro comando, la salida tiene el aspecto del texto normal que se muestra en la pantalla, dividida en páginas:

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

La paginación también reduce la utilización de la CPU porque el procesamiento se transfiere al cmdlet `Out-Host` cuando tiene una página completa lista para mostrar. Los cmdlets que lo preceden en la canalización pausan la ejecución hasta que la siguiente página de salida está disponible.

Puede ver cómo la canalización impacta el uso de la memoria y la CPU en el Administrador de tareas de Windows si compara estos comandos:

- `Get-ChildItem C:\Windows -Recurse`
- `Get-ChildItem C:\Windows -Recurse | Out-Host -Paging`

> [!NOTE]
> No todos los hosts de PowerShell admiten el parámetro **Paging**. Por ejemplo, cuando intenta usar el parámetro **Paging** en PowerShell ISE, verá el error siguiente:
>
> ```Output
> out-lineoutput : The method or operation is not implemented.
> At line:1 char:1
> + Get-ChildItem C:\Windows -Recurse | Out-Host -Paging
> + ~~~~~~~~~~~~~~~~~~~~~~~~~~~
>     + CategoryInfo          : NotSpecified: (:) [out-lineoutput], NotImplementedException
>     + FullyQualifiedErrorId : System.NotImplementedException,Microsoft.PowerShell.Commands.OutLineOutputCommand
> ```

## <a name="objects-in-the-pipeline"></a>Objetos de la canalización

Cuando se ejecuta un cmdlet en PowerShell, se verá la salida del texto debido a la necesidad de representar objetos como texto en una ventana de la consola. Es posible que la salida de texto no muestre todas las propiedades del objeto que se está emitiendo.

Por ejemplo, tenga en cuenta el cmdlet `Get-Location`. Si ejecuta `Get-Location` mientras la ubicación actual es el directorio raíz de la unidad C, verá la siguiente salida:

```
PS> Get-Location

Path
----
C:\
```

La salida de texto es un resumen de la información y no una representación completa del objeto devuelto por `Get-Location`. El encabezado de la salida se agrega mediante el proceso que formatea los datos para su visualización en pantalla.

Al canalizar la salida al cmdlet `Get-Member`, se obtiene información sobre el objeto devuelto por `Get-Location`.

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

`Get-Location` devuelve un objeto **PathInfo** que contiene la ruta de acceso actual y otra información.
