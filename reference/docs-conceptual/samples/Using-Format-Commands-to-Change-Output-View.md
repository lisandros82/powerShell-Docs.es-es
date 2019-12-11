---
ms.date: 11/22/2019
keywords: powershell, cmdlet
title: Usar comandos de formato para cambiar la vista de salida
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417595"
---
# <a name="using-format-commands-to-change-output-view"></a>Usar comandos de formato para cambiar la vista de salida

PowerShell tiene un conjunto de cmdlets que permite controlar cómo se muestran las propiedades para determinados objetos. Los nombres de todos los cmdlets empiezan con el verbo `Format`. Permiten seleccionar las propiedades que se quieren mostrar.

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

En este artículo se describen los cmdlets `Format-Wide`, `Format-List` y `Format-Table`.

Cada tipo de objeto de PowerShell tiene propiedades predeterminadas que se usan si no se especifican las propiedades que se van a mostrar. Cada cmdlet usa el mismo parámetro **Property** para especificar las propiedades que se quieren mostrar. Como `Format-Wide` solo muestra una única propiedad, su parámetro **Property** solo toma un único valor, pero los parámetros de propiedad de `Format-List` y `Format-Table` aceptan una lista de nombres de propiedades.

En este ejemplo, la salida predeterminada del cmdlet `Get-Process` muestra que hay dos instancias de Internet Explorer en ejecución.

```powershell
Get-Process -Name iexplore
```

El formato predeterminado de los objetos **Process** muestra estas propiedades:

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a>Usar Format-Wide para la salida de un solo elemento

De manera predeterminada, el cmdlet `Format-Wide` solo muestra la propiedad predeterminada de un objeto. La información asociada a cada objeto se muestra en una sola columna:

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

También puede especificar una propiedad no predeterminada:

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>Controlar la presentación de Format-Wide con Column

Con el cmdlet `Format-Wide`, no se pueden varias propiedades a la vez. Esto resulta útil para mostrar listas grandes en varias columnas.

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a>Usar Format-List para obtener una vista de lista

El cmdlet `Format-List` muestra un objeto en forma de lista, donde cada propiedad aparece etiquetada en una línea distinta:

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

Puede especificar tantas propiedades como desee:

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Obtener información detallada usando Format-List con caracteres comodín

El cmdlet `Format-List` permite usar un carácter comodín como valor de su parámetro **Property**. Esto le permite visualizar información detallada. A menudo, los objetos incluyen más información de la necesaria, por lo que PowerShell no muestra todos los valores de propiedad de forma predeterminada. Para mostrar todas las propiedades de un objeto, use el comando `Format-List -Property *`. El siguiente comando genera más de 60 líneas de salida para un único proceso:

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

Aunque el comando `Format-List` resulta útil para mostrar detalles, si quiere una visión general de la salida que incluya muchos elementos, una vista tabular más sencilla suele ser más conveniente.

## <a name="using-format-table-for-tabular-output"></a>Usar Format-Table para la salida tabular

Si usa el cmdlet `Format-Table` sin nombres de propiedades especificados para dar formato a la salida del comando `Get-Process`, obtendrá exactamente la misma salida que sin un cmdlet `Format`. De forma predeterminada, PowerShell muestra los objetos **Process** en formato tabular.

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a>Mejorar la salida de Format-Table (AutoSize)

Aunque una vista tabular resulta útil para mostrar mucha información, puede ser difícil de interpretar si la pantalla es demasiado estrecha para los datos. En el ejemplo anterior, el resultado se trunca. Si especifica el parámetro **AutoSize** al ejecutar el comando `Format-Table`, PowerShell calcula los anchos de columna en función de los datos reales que se muestran. Esto hace que las columnas sean legibles.

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

Es posible que el cmdlet `Format-Table` todavía trunque los datos, pero solo al final de la pantalla. Las propiedades distintas de la última que se muestra obtienen el tamaño que necesitan para que su elemento de datos más largo se muestre correctamente.

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

El comando `Format-Table` asume que las propiedades se enumeran por orden de importancia. Por tanto, intenta mostrar de forma completa las propiedades lo más cerca posible del principio. Si el comando `Format-Table` no puede mostrar todas las propiedades, quita algunas columnas de la pantalla. Puede ver este comportamiento en el ejemplo anterior de la propiedad **DependentServices**.

### <a name="wrapping-format-table-output-in-columns-wrap"></a>Ajustar la salida de Format-Table en columnas (Wrap)

Puede forzar que los datos de `Format-Table` largos se encapsulen dentro de la columna de presentación mediante el parámetro **Wrap**. Es posible que el parámetro **Wrap** no realice la acción prevista, ya que usa la configuración predeterminada si no se especifica también **AutoSize**:

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

El uso del parámetro **Wrap** por sí solo no ralentiza en exceso el procesamiento. Sin embargo, el uso de **AutoSize** para dar formato a una lista de archivos recursiva de una estructura de directorios de gran tamaño puede tardar mucho tiempo y consumir una gran cantidad de memoria antes de que se muestren los primeros elementos de la salida.

Si no le preocupa la carga del sistema, **AutoSize** funciona bien con el parámetro **Wrap**.
Las columnas iniciales siguen usando todo el ancho necesario para mostrar los elementos en una línea, pero la columna final se ajusta, si es necesario.

> [!NOTE]
> Es posible que algunas columnas no se muestren si se especifican primero las más anchas. Para obtener los mejores resultados, especifique primero los elementos de datos más pequeños.

En el ejemplo siguiente, primero se especifican las propiedades más anchas.

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

Incluso con el ajuste, se omite la columna **Id** final:

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a>Organización de la salida tabular (-GroupBy)

Otro parámetro útil para el control de la salida tabular es **GroupBy**. Las listas tabulares largas pueden ser especialmente difíciles de comparar. El parámetro **GroupBy** agrupa la salida según un valor de propiedad. Por ejemplo, los servicios se pueden agrupar por valor **StartType** para facilitar la inspección y omitir el valor **StartType** de la lista de propiedades:

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
