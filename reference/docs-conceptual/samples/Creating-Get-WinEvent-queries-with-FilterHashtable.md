---
ms.date: 09/13/2019
title: Creación de consultas Get-WinEvent con FilterHashtable
ms.openlocfilehash: 35d18dc894d90e698b38395b79ff4cf395515909
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444390"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="7ea6d-102">Creación de consultas Get-WinEvent con FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="7ea6d-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="7ea6d-103">Para leer la entrada de blog original de **Scripting Guy** del 3 de junio de 2014, consulte [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/) (Uso de FilterHashTable para filtrar registros de eventos con PowerShell).</span><span class="sxs-lookup"><span data-stu-id="7ea6d-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="7ea6d-104">Este artículo es un extracto de la entrada de blog original y se explica cómo usar el parámetro **FilterHashtable** del cmdlet `Get-WinEvent` para filtrar registros de eventos.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="7ea6d-105">El cmdlet `Get-WinEvent` de PowerShell es un método eficaz para filtrar registros de diagnóstico y eventos de Windows.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="7ea6d-106">El rendimiento mejora cuando una consulta `Get-WinEvent` utiliza el parámetro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="7ea6d-107">Cuando se trabaja con registros de eventos de gran tamaño, no resulta eficaz enviar objetos a través de la canalización hasta el comando `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="7ea6d-108">Antes de PowerShell 6, el cmdlet `Get-EventLog` era otra alternativa para obtener datos de registro.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="7ea6d-109">Por ejemplo, los comandos siguientes no son suficientes para filtrar los registros **Microsoft-Windows-Defrag**:</span><span class="sxs-lookup"><span data-stu-id="7ea6d-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

<span data-ttu-id="7ea6d-110">El siguiente comando usa una tabla hash que mejora el rendimiento:</span><span class="sxs-lookup"><span data-stu-id="7ea6d-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="7ea6d-111">Entradas de blog sobre la enumeración</span><span class="sxs-lookup"><span data-stu-id="7ea6d-111">Blog posts about enumeration</span></span>

<span data-ttu-id="7ea6d-112">En este artículo se presenta información acerca de cómo usar los valores enumerados en una tabla hash.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="7ea6d-113">Para obtener más información sobre la enumeración, lea estas entradas de blog de **Scripting Guy**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="7ea6d-114">Para crear una función que devuelva los valores enumerados, consulte [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values) (Enumeraciones y valores).</span><span class="sxs-lookup"><span data-stu-id="7ea6d-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="7ea6d-115">Para obtener más información, consulte la [serie de entradas de blob de Scripting Guy sobre la enumeración](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="7ea6d-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-key-value-pairs"></a><span data-ttu-id="7ea6d-116">Pares clave-valor de tablas hash</span><span class="sxs-lookup"><span data-stu-id="7ea6d-116">Hash table key-value pairs</span></span>

<span data-ttu-id="7ea6d-117">Para generar consultas eficaces, utilice el cmdlet `Get-WinEvent` con el parámetro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="7ea6d-118">**FilterHashtable** acepta una tabla hash como un filtro para obtener información específica de los registros de eventos de Windows.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="7ea6d-119">Una tabla hash usa pares **clave-valor**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-119">A hash table uses **key-value** pairs.</span></span> <span data-ttu-id="7ea6d-120">Para obtener más información sobre las tablas hash, consulte [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="7ea6d-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="7ea6d-121">Si los pares **clave-valor** se encuentran en la misma línea, se deben separar mediante punto y coma.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-121">If the **key-value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="7ea6d-122">Si cada par **clave-valor** está en una línea independiente, no es necesario usar punto y coma.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-122">If each **key-value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="7ea6d-123">Por ejemplo, en este artículo se colocan los pares **clave-valor** en líneas independientes y no se usan puntos y comas.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-123">For example, this article places **key-value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="7ea6d-124">En este ejemplo se usan varios de los pares **clave-valor** del parámetro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-124">This sample uses several of the **FilterHashtable** parameter's **key-value** pairs.</span></span> <span data-ttu-id="7ea6d-125">La consulta completada incluye **LogName**, **ProviderName**, **Keywords**, **ID** y **Level**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="7ea6d-126">Los pares **clave-valor** aceptados se muestran en la tabla siguiente y se incluyen en la documentación del parámetro **FilterHashtable** de [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-126">The accepted **key-value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="7ea6d-127">En la tabla siguiente se muestran los nombres de clave, los tipos de datos y si se aceptan caracteres comodín para un valor de datos.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

|    <span data-ttu-id="7ea6d-128">Nombre de clave</span><span class="sxs-lookup"><span data-stu-id="7ea6d-128">Key name</span></span>    | <span data-ttu-id="7ea6d-129">Tipo de datos de valor</span><span class="sxs-lookup"><span data-stu-id="7ea6d-129">Value data type</span></span> | <span data-ttu-id="7ea6d-130">¿Acepta caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="7ea6d-130">Accepts wildcard characters?</span></span> |
| -------------- | --------------- | ---------------------------- |
| <span data-ttu-id="7ea6d-131">LogName</span><span class="sxs-lookup"><span data-stu-id="7ea6d-131">LogName</span></span>        | `<String[]>`    | <span data-ttu-id="7ea6d-132">Sí</span><span class="sxs-lookup"><span data-stu-id="7ea6d-132">Yes</span></span>                          |
| <span data-ttu-id="7ea6d-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="7ea6d-133">ProviderName</span></span>   | `<String[]>`    | <span data-ttu-id="7ea6d-134">Sí</span><span class="sxs-lookup"><span data-stu-id="7ea6d-134">Yes</span></span>                          |
| <span data-ttu-id="7ea6d-135">Ruta</span><span class="sxs-lookup"><span data-stu-id="7ea6d-135">Path</span></span>           | `<String[]>`    | <span data-ttu-id="7ea6d-136">No</span><span class="sxs-lookup"><span data-stu-id="7ea6d-136">No</span></span>                           |
| <span data-ttu-id="7ea6d-137">Palabras clave</span><span class="sxs-lookup"><span data-stu-id="7ea6d-137">Keywords</span></span>       | `<Long[]>`      | <span data-ttu-id="7ea6d-138">No</span><span class="sxs-lookup"><span data-stu-id="7ea6d-138">No</span></span>                           |
| <span data-ttu-id="7ea6d-139">ID</span><span class="sxs-lookup"><span data-stu-id="7ea6d-139">ID</span></span>             | `<Int32[]>`     | <span data-ttu-id="7ea6d-140">No</span><span class="sxs-lookup"><span data-stu-id="7ea6d-140">No</span></span>                           |
| <span data-ttu-id="7ea6d-141">Nivel</span><span class="sxs-lookup"><span data-stu-id="7ea6d-141">Level</span></span>          | `<Int32[]>`     | <span data-ttu-id="7ea6d-142">No</span><span class="sxs-lookup"><span data-stu-id="7ea6d-142">No</span></span>                           |
| <span data-ttu-id="7ea6d-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="7ea6d-143">StartTime</span></span>      | `<DateTime>`    | <span data-ttu-id="7ea6d-144">No</span><span class="sxs-lookup"><span data-stu-id="7ea6d-144">No</span></span>                           |
| <span data-ttu-id="7ea6d-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="7ea6d-145">EndTime</span></span>        | `<DateTime>`    | <span data-ttu-id="7ea6d-146">No</span><span class="sxs-lookup"><span data-stu-id="7ea6d-146">No</span></span>                           |
| <span data-ttu-id="7ea6d-147">UserID</span><span class="sxs-lookup"><span data-stu-id="7ea6d-147">UserID</span></span>         | `<SID>`         | <span data-ttu-id="7ea6d-148">No</span><span class="sxs-lookup"><span data-stu-id="7ea6d-148">No</span></span>                           |
| <span data-ttu-id="7ea6d-149">Datos</span><span class="sxs-lookup"><span data-stu-id="7ea6d-149">Data</span></span>           | `<String[]>`    | <span data-ttu-id="7ea6d-150">No</span><span class="sxs-lookup"><span data-stu-id="7ea6d-150">No</span></span>                           |
| `<named-data>` | `<String[]>`    | <span data-ttu-id="7ea6d-151">No</span><span class="sxs-lookup"><span data-stu-id="7ea6d-151">No</span></span>                           |

<span data-ttu-id="7ea6d-152">La clave `<named-data>` representa un campo de datos de evento con nombre.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-152">The `<named-data>` key represents a named event data field.</span></span> <span data-ttu-id="7ea6d-153">Por ejemplo, el evento 1008 de Perflib puede contener los siguientes datos de evento:</span><span class="sxs-lookup"><span data-stu-id="7ea6d-153">For example, the Perflib event 1008 can contain the following event data:</span></span>

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

<span data-ttu-id="7ea6d-154">Puede consultar estos eventos con el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="7ea6d-154">You can query for these events using the following command:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

> [!NOTE]
> <span data-ttu-id="7ea6d-155">La capacidad de consultar `<named-data>` se ha agregado en PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-155">The ability to query for `<named-data>` was added in PowerShell 6.</span></span>

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="7ea6d-156">Creación de una consulta con una tabla hash</span><span class="sxs-lookup"><span data-stu-id="7ea6d-156">Building a query with a hash table</span></span>

<span data-ttu-id="7ea6d-157">Para comprobar los resultados y solucionar problemas, es de utilidad generar la tabla hash con un par **clave-valor** a la vez.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-157">To verify results and troubleshoot problems, it helps to build the hash table one **key-value** pair at a time.</span></span> <span data-ttu-id="7ea6d-158">La consulta obtiene datos del registro **Aplicación**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-158">The query gets data from the **Application** log.</span></span> <span data-ttu-id="7ea6d-159">La tabla hash es equivalente a `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-159">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="7ea6d-160">Para comenzar, cree la consulta `Get-WinEvent`.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-160">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="7ea6d-161">Use el par **clave-valor** del parámetro **FilterHashtable** con la clave **LogName** y el valor **Application**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-161">Use the **FilterHashtable** parameter's **key-value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="7ea6d-162">Continúe para generar la tabla hash con la clave **ProviderName**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-162">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="7ea6d-163">**ProviderName** es el nombre que aparece en el campo **Origen** del **Visor de eventos de Windows**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-163">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="7ea6d-164">Por ejemplo, **.NET Runtime** en la captura de pantalla siguiente:</span><span class="sxs-lookup"><span data-stu-id="7ea6d-164">For example, **.NET Runtime** in the following screenshot:</span></span>

![Imagen de los orígenes del Visor de eventos de Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="7ea6d-166">Actualice la tabla hash e incluya el par **clave-valor** con la clave \*\*ProviderName y el valor **.NET Runtime**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-166">Update the hash table and include the **key-value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="7ea6d-167">Si la consulta tiene que obtener datos de registros de eventos archivados, use la clave **Path**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-167">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="7ea6d-168">El valor **Path** especifica la ruta de acceso completa al archivo de registro.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-168">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="7ea6d-169">Para obtener más información, consulte la entrada de blog de **Scripting Guy** [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors) (Uso de PowerShell para analizar registros de eventos guardados de errores).</span><span class="sxs-lookup"><span data-stu-id="7ea6d-169">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="7ea6d-170">Uso de valores enumerados en una tabla hash</span><span class="sxs-lookup"><span data-stu-id="7ea6d-170">Using enumerated values in a hash table</span></span>

<span data-ttu-id="7ea6d-171">**Keywords** es la siguiente clave de la tabla hash.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-171">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="7ea6d-172">El tipo de datos **Keywords** es una matriz del tipo de valor `[long]` que contiene una gran cantidad.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-172">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="7ea6d-173">Use el comando siguiente para encontrar el valor máximo de `[long]`:</span><span class="sxs-lookup"><span data-stu-id="7ea6d-173">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="7ea6d-174">Para la clave **Keywords**, PowerShell usa un número, no una cadena como **Seguridad**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-174">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="7ea6d-175">El **Visor de eventos de Windows** muestra las **palabras clave** como cadenas, pero son valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-175">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="7ea6d-176">En la tabla hash, si usa la clave **Keywords** con un valor de cadena, se muestra un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-176">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="7ea6d-177">Abra el **Visor de eventos de Windows** y en el panel **Acciones**, haga clic en **Filtrar registro actual**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-177">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="7ea6d-178">El menú desplegable **Palabras clave** muestra las palabras clave disponibles, como se ilustra en la captura de pantalla siguiente:</span><span class="sxs-lookup"><span data-stu-id="7ea6d-178">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Imagen de las palabras clave del Visor de eventos de Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="7ea6d-180">Use el siguiente comando para mostrar los nombres de propiedades `StandardEventKeywords`.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-180">Use the following command to display the `StandardEventKeywords` property names.</span></span>

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

<span data-ttu-id="7ea6d-181">Los valores enumerados se documentan en **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-181">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="7ea6d-182">Para obtener más información, consulte [ StandardEventKeywords Enum ](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="7ea6d-182">For more information, see [StandardEventKeywords Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="7ea6d-183">Los valores enumerados y nombres de **Keywords** son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="7ea6d-183">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="7ea6d-184">Nombre</span><span class="sxs-lookup"><span data-stu-id="7ea6d-184">Name</span></span>             |  <span data-ttu-id="7ea6d-185">Value</span><span class="sxs-lookup"><span data-stu-id="7ea6d-185">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="7ea6d-186">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="7ea6d-186">AuditFailure</span></span>     | <span data-ttu-id="7ea6d-187">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="7ea6d-187">4503599627370496</span></span>  |
| <span data-ttu-id="7ea6d-188">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="7ea6d-188">AuditSuccess</span></span>     | <span data-ttu-id="7ea6d-189">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="7ea6d-189">9007199254740992</span></span>  |
| <span data-ttu-id="7ea6d-190">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="7ea6d-190">CorrelationHint2</span></span> | <span data-ttu-id="7ea6d-191">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="7ea6d-191">18014398509481984</span></span> |
| <span data-ttu-id="7ea6d-192">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="7ea6d-192">EventLogClassic</span></span>  | <span data-ttu-id="7ea6d-193">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="7ea6d-193">36028797018963968</span></span> |
| <span data-ttu-id="7ea6d-194">Sqm</span><span class="sxs-lookup"><span data-stu-id="7ea6d-194">Sqm</span></span>              | <span data-ttu-id="7ea6d-195">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="7ea6d-195">2251799813685248</span></span>  |
| <span data-ttu-id="7ea6d-196">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="7ea6d-196">WdiDiagnostic</span></span>    | <span data-ttu-id="7ea6d-197">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="7ea6d-197">1125899906842624</span></span>  |
| <span data-ttu-id="7ea6d-198">WdiContext</span><span class="sxs-lookup"><span data-stu-id="7ea6d-198">WdiContext</span></span>       | <span data-ttu-id="7ea6d-199">562949953421312</span><span class="sxs-lookup"><span data-stu-id="7ea6d-199">562949953421312</span></span>   |
| <span data-ttu-id="7ea6d-200">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="7ea6d-200">ResponseTime</span></span>     | <span data-ttu-id="7ea6d-201">281474976710656</span><span class="sxs-lookup"><span data-stu-id="7ea6d-201">281474976710656</span></span>   |
| <span data-ttu-id="7ea6d-202">Ninguno</span><span class="sxs-lookup"><span data-stu-id="7ea6d-202">None</span></span>             | <span data-ttu-id="7ea6d-203">0</span><span class="sxs-lookup"><span data-stu-id="7ea6d-203">0</span></span>                 |

<span data-ttu-id="7ea6d-204">Actualice la tabla hash e incluya el par **clave-valor** con la clave **Keywords** y el valor de enumeración **EventLogClassic**, **36028797018963968**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-204">Update the hash table and include the **key-value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="7ea6d-205">Valor de propiedad estática de palabras clave (opcional)</span><span class="sxs-lookup"><span data-stu-id="7ea6d-205">Keywords static property value (optional)</span></span>

<span data-ttu-id="7ea6d-206">La clave **Keywords** se enumera, pero puede usar un nombre de propiedad estática en la consulta de tabla hash.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-206">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="7ea6d-207">En lugar de usar la cadena devuelta, el nombre de propiedad debe convertirse en un valor con la propiedad **Value__** .</span><span class="sxs-lookup"><span data-stu-id="7ea6d-207">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="7ea6d-208">Por ejemplo, el script siguiente usa la propiedad **Value__** .</span><span class="sxs-lookup"><span data-stu-id="7ea6d-208">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="7ea6d-209">Filtro por identificador de evento</span><span class="sxs-lookup"><span data-stu-id="7ea6d-209">Filtering by Event Id</span></span>

<span data-ttu-id="7ea6d-210">Para obtener datos más específicos, los resultados de la consulta se filtran por **identificador de evento**. Se hace referencia al **identificador de evento** en la tabla hash como la clave **ID** y el valor es un **identificador de evento** determinado. El **Visor de eventos de Windows** muestra el **identificador de evento**. En este ejemplo se utiliza **Event Id 1023**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-210">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="7ea6d-211">Actualice la tabla hash e incluya el par **clave-valor** con la clave **ID** y el valor **1023**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-211">Update the hash table and include the **key-value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="7ea6d-212">Filtro por nivel</span><span class="sxs-lookup"><span data-stu-id="7ea6d-212">Filtering by Level</span></span>

<span data-ttu-id="7ea6d-213">Para refinar más los resultados e incluir solo los eventos que indican errores, use la clave **Level**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-213">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="7ea6d-214">El **Visor de eventos de Windows** muestra el **nivel** como valores de cadena, pero son valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-214">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="7ea6d-215">En la tabla hash, si usa la clave **Level** con un valor de cadena, se muestra un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-215">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="7ea6d-216">**Level** tiene valores como **Error**, **Advertencia** o **Información**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-216">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="7ea6d-217">Use el siguiente comando para mostrar los nombres de propiedades `StandardEventLevel`.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-217">Use the following command to display the `StandardEventLevel` property names.</span></span>

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

<span data-ttu-id="7ea6d-218">Los valores enumerados se documentan en **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-218">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="7ea6d-219">Para obtener más información, consulte [ StandardEventLevel Enum](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="7ea6d-219">For more information, see [StandardEventLevel Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="7ea6d-220">Los valores enumerados y nombres de la clave **Level** son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="7ea6d-220">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="7ea6d-221">Nombre</span><span class="sxs-lookup"><span data-stu-id="7ea6d-221">Name</span></span>           | <span data-ttu-id="7ea6d-222">Value</span><span class="sxs-lookup"><span data-stu-id="7ea6d-222">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="7ea6d-223">Verbose</span><span class="sxs-lookup"><span data-stu-id="7ea6d-223">Verbose</span></span>        |   <span data-ttu-id="7ea6d-224">5</span><span class="sxs-lookup"><span data-stu-id="7ea6d-224">5</span></span>   |
| <span data-ttu-id="7ea6d-225">Informativo</span><span class="sxs-lookup"><span data-stu-id="7ea6d-225">Informational</span></span>  |   <span data-ttu-id="7ea6d-226">4</span><span class="sxs-lookup"><span data-stu-id="7ea6d-226">4</span></span>   |
| <span data-ttu-id="7ea6d-227">Advertencia</span><span class="sxs-lookup"><span data-stu-id="7ea6d-227">Warning</span></span>        |   <span data-ttu-id="7ea6d-228">3</span><span class="sxs-lookup"><span data-stu-id="7ea6d-228">3</span></span>   |
| <span data-ttu-id="7ea6d-229">Error de :</span><span class="sxs-lookup"><span data-stu-id="7ea6d-229">Error</span></span>          |   <span data-ttu-id="7ea6d-230">2</span><span class="sxs-lookup"><span data-stu-id="7ea6d-230">2</span></span>   |
| <span data-ttu-id="7ea6d-231">Crítico</span><span class="sxs-lookup"><span data-stu-id="7ea6d-231">Critical</span></span>       |   <span data-ttu-id="7ea6d-232">1</span><span class="sxs-lookup"><span data-stu-id="7ea6d-232">1</span></span>   |
| <span data-ttu-id="7ea6d-233">LogAlways</span><span class="sxs-lookup"><span data-stu-id="7ea6d-233">LogAlways</span></span>      |   <span data-ttu-id="7ea6d-234">0</span><span class="sxs-lookup"><span data-stu-id="7ea6d-234">0</span></span>   |

<span data-ttu-id="7ea6d-235">La tabla hash de la consulta completada incluye la clave, **Level**, y el valor, **2**.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-235">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="7ea6d-236">Propiedad estática de nivel en enumeración (opcional)</span><span class="sxs-lookup"><span data-stu-id="7ea6d-236">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="7ea6d-237">La clave **Level** se enumera, pero puede usar un nombre de propiedad estática en la consulta de tabla hash.</span><span class="sxs-lookup"><span data-stu-id="7ea6d-237">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="7ea6d-238">En lugar de usar la cadena devuelta, el nombre de propiedad debe convertirse en un valor con la propiedad **Value__** .</span><span class="sxs-lookup"><span data-stu-id="7ea6d-238">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="7ea6d-239">Por ejemplo, el script siguiente usa la propiedad **Value__** .</span><span class="sxs-lookup"><span data-stu-id="7ea6d-239">For example, the following script uses the **Value__** property.</span></span>

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