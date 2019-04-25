---
ms.date: 3/18/2019
title: Creación de consultas Get-WinEvent con FilterHashtable
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058835"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>Creación de consultas Get-WinEvent con FilterHashtable

Para leer la entrada de blog original de **Scripting Guy** del 3 de junio de 2014, consulte [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/) (Uso de FilterHashTable para filtrar registros de eventos con PowerShell).

Este artículo es un extracto de la entrada de blog original y se explica cómo usar el parámetro **FilterHashtable** del cmdlet `Get-WinEvent` para filtrar registros de eventos. El cmdlet `Get-WinEvent` de PowerShell es un método eficaz para filtrar registros de diagnóstico y eventos de Windows. El rendimiento mejora cuando una consulta `Get-WinEvent` utiliza el parámetro **FilterHashtable**.

Cuando se trabaja con registros de eventos de gran tamaño, no resulta eficaz enviar objetos a través de la canalización hasta el comando `Where-Object`. Antes de PowerShell 6, el cmdlet `Get-EventLog` era otra alternativa para obtener datos de registro. Por ejemplo, los comandos siguientes no son suficientes para filtrar los registros **Microsoft-Windows-Defrag**:

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

El siguiente comando usa una tabla hash que mejora el rendimiento:

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>Entradas de blog sobre la enumeración

En este artículo se presenta información acerca de cómo usar los valores enumerados en una tabla hash. Para obtener más información sobre la enumeración, lea estas entradas de blog de **Scripting Guy**. Para crear una función que devuelva los valores enumerados, consulte [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values) (Enumeraciones y valores).
Para obtener más información, consulte la [serie de entradas de blob de Scripting Guy sobre la enumeración](https://devblogs.microsoft.com/scripting/?s=about+enumeration).

## <a name="hash-table-keyvalue-pairs"></a>Pares clave-valor de tablas hash

Para generar consultas eficaces, utilice el cmdlet `Get-WinEvent` con el parámetro **FilterHashtable**.
**FilterHashtable** acepta una tabla hash como un filtro para obtener información específica de los registros de eventos de Windows. Una tabla hash usa pares **clave-valor**. Para obtener más información sobre las tablas hash, consulte [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Si los pares **clave-valor** se encuentran en la misma línea, deben estar separados por puntos y comas. Si cada par **clave-valor** está en una línea independiente, no es necesario usar puntos y comas. Por ejemplo, en este artículo se colocan los pares **clave-valor** en líneas independientes y no se usan puntos y comas.

En este ejemplo se utilizan varios de los pares **clave-valor** del parámetro **FilterHashtable**. La consulta completada incluye **LogName**, **ProviderName**, **Keywords**, **ID** y **Level**.

Los pares **clave-valor** aceptados se muestran en la tabla siguiente y se incluyen en la documentación del parámetro **FilterHashtable** de [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
.

En la tabla siguiente se muestran los nombres de clave, los tipos de datos y si se aceptan caracteres comodín para un valor de datos.

| Nombre de clave     | Tipo de datos de valor    | ¿Acepta caracteres comodín? |
|------------- | ------------------ | ---------------------------- |
| LogName      | `<String[]>`       | Sí |
| ProviderName | `<String[]>`       | Sí |
| Ruta         | `<String[]>`       | No  |
| Palabras clave     | `<Long[]>`         | No  |
| ID           | `<Int32[]>`        | No  |
| Nivel        | `<Int32[]>`        | No  |
| StartTime    | `<DateTime>`       | No  |
| EndTime      | `<DateTime>`       | No  |
| UserID       | `<SID>`            | No  |
| Datos         | `<String[]>`       | No  |
| *            | `<String[]>`       | No  |

## <a name="building-a-query-with-a-hash-table"></a>Creación de una consulta con una tabla hash

Para comprobar los resultados y solucionar problemas, ayuda a generar la tabla hash con un par **clave-valor** a la vez. La consulta obtiene datos del registro **Aplicación**. La tabla hash es equivalente a `Get-WinEvent –LogName Application`.

Para comenzar, cree la consulta `Get-WinEvent`. Use el par **clave-valor**  del parámetro **FilterHashtable** con la clave, **LogName**, y el valor, **Aplicación**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

Continúe para generar la tabla hash con la clave **ProviderName**. **ProviderName** es el nombre que aparece en el campo **Origen** del **Visor de eventos de Windows**. Por ejemplo, **.NET Runtime** en la captura de pantalla siguiente:

![Imagen de los orígenes del Visor de eventos de Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

Actualice la tabla hash e incluya el par **clave-valor** con la clave, **ProviderName, y el valor, **.NET Runtime**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Si la consulta tiene que obtener datos de registros de eventos archivados, use la clave **Path**. El valor **Path** especifica la ruta de acceso completa al archivo de registro. Para obtener más información, consulte la entrada de blog de **Scripting Guy** [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors) (Uso de PowerShell para analizar registros de eventos guardados de errores).

## <a name="using-enumerated-values-in-a-hash-table"></a>Uso de valores enumerados en una tabla hash

**Keywords** es la siguiente clave de la tabla hash. El tipo de datos **Keywords** es una matriz del tipo de valor `[long]` que contiene una gran cantidad. Use el comando siguiente para encontrar el valor máximo de `[long]`:

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

Para la clave **Keywords**, PowerShell usa un número, no una cadena como **Seguridad**. El **Visor de eventos de Windows** muestra las **palabras clave** como cadenas, pero son valores enumerados. En la tabla hash, si usa la clave **Keywords** con un valor de cadena, se muestra un mensaje de error.

Abra el **Visor de eventos de Windows** y en el panel **Acciones**, haga clic en **Filtrar registro actual**.
El menú desplegable **Palabras clave** muestra las palabras clave disponibles, como se ilustra en la captura de pantalla siguiente:

![Imagen de las palabras clave del Visor de eventos de Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Use el siguiente comando para mostrar los nombres de propiedades `StandardEventKeywords`.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

Los valores enumerados se documentan en **.NET Framework**. Para obtener más información, consulte [ StandardEventKeywords Enum ](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).

Los valores enumerados y nombres de **Keywords** son los siguientes:

| Nombre             |  Value            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| Ninguno             | 0                 |

Actualice la tabla hash e incluya el par **clave-valor** con la clave, **Keywords** y el valor de enumeración **EventLogClassic**, **36028797018963968**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Valor de propiedad estática de palabras clave (opcional)

La clave **Keywords** se enumera, pero puede usar un nombre de propiedad estática en la consulta de tabla hash.
En lugar de usar la cadena devuelta, el nombre de propiedad debe convertirse en un valor con la propiedad **Value__**.

Por ejemplo, el script siguiente usa la propiedad **Value__**.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>Filtro por identificador de evento

Para obtener datos más específicos, los resultados de la consulta se filtran por **identificador de evento**. Se hace referencia al **identificador de evento** en la tabla hash como la clave **ID** y el valor es un **identificador de evento** determinado. El **Visor de eventos de Windows** muestra el **identificador de evento**. En este ejemplo se utiliza **Event Id 1023**.

Actualice la tabla hash e incluya el par **clave-valor** con la clave, **ID**, y el valor, **1023**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>Filtro por nivel

Para refinar más los resultados e incluir solo los eventos que indican errores, use la clave **Level**.
El **Visor de eventos de Windows** muestra el **nivel** como valores de cadena, pero son valores enumerados. En la tabla hash, si usa la clave **Level** con un valor de cadena, se muestra un mensaje de error.

**Level** tiene valores como **Error**, **Advertencia** o **Información**. Use el siguiente comando para mostrar los nombres de propiedades `StandardEventLevel`.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

Los valores enumerados se documentan en **.NET Framework**. Para obtener más información, consulte [ StandardEventLevel Enum](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).

Los valores enumerados y nombres de la clave **Level** son los siguientes:

| Nombre           | Value |
| -------------- | ----- |
| Verbose        |   5   |
| Informativo  |   4   |
| Advertencia        |   3   |
| Error de :          |   2   |
| Crítico       |   1   |
| LogAlways      |   0   |

La tabla hash de la consulta completada incluye la clave, **Level**, y el valor, **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>Propiedad estática de nivel en enumeración (opcional)

La clave **Level** se enumera, pero puede usar un nombre de propiedad estática en la consulta de tabla hash.
En lugar de usar la cadena devuelta, el nombre de propiedad debe convertirse en un valor con la propiedad **Value__**.

Por ejemplo, el script siguiente usa la propiedad **Value__**.

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```