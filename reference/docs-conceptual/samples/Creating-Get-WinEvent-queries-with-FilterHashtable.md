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
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="d606f-102">Creación de consultas Get-WinEvent con FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="d606f-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="d606f-103">Para leer la entrada de blog original de **Scripting Guy** del 3 de junio de 2014, consulte [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/) (Uso de FilterHashTable para filtrar registros de eventos con PowerShell).</span><span class="sxs-lookup"><span data-stu-id="d606f-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="d606f-104">Este artículo es un extracto de la entrada de blog original y se explica cómo usar el parámetro **FilterHashtable** del cmdlet `Get-WinEvent` para filtrar registros de eventos.</span><span class="sxs-lookup"><span data-stu-id="d606f-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="d606f-105">El cmdlet `Get-WinEvent` de PowerShell es un método eficaz para filtrar registros de diagnóstico y eventos de Windows.</span><span class="sxs-lookup"><span data-stu-id="d606f-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="d606f-106">El rendimiento mejora cuando una consulta `Get-WinEvent` utiliza el parámetro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="d606f-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="d606f-107">Cuando se trabaja con registros de eventos de gran tamaño, no resulta eficaz enviar objetos a través de la canalización hasta el comando `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="d606f-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="d606f-108">Antes de PowerShell 6, el cmdlet `Get-EventLog` era otra alternativa para obtener datos de registro.</span><span class="sxs-lookup"><span data-stu-id="d606f-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="d606f-109">Por ejemplo, los comandos siguientes no son suficientes para filtrar los registros **Microsoft-Windows-Defrag**:</span><span class="sxs-lookup"><span data-stu-id="d606f-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

<span data-ttu-id="d606f-110">El siguiente comando usa una tabla hash que mejora el rendimiento:</span><span class="sxs-lookup"><span data-stu-id="d606f-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="d606f-111">Entradas de blog sobre la enumeración</span><span class="sxs-lookup"><span data-stu-id="d606f-111">Blog posts about enumeration</span></span>

<span data-ttu-id="d606f-112">En este artículo se presenta información acerca de cómo usar los valores enumerados en una tabla hash.</span><span class="sxs-lookup"><span data-stu-id="d606f-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="d606f-113">Para obtener más información sobre la enumeración, lea estas entradas de blog de **Scripting Guy**.</span><span class="sxs-lookup"><span data-stu-id="d606f-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="d606f-114">Para crear una función que devuelva los valores enumerados, consulte [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values) (Enumeraciones y valores).</span><span class="sxs-lookup"><span data-stu-id="d606f-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="d606f-115">Para obtener más información, consulte la [serie de entradas de blob de Scripting Guy sobre la enumeración](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="d606f-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-keyvalue-pairs"></a><span data-ttu-id="d606f-116">Pares clave-valor de tablas hash</span><span class="sxs-lookup"><span data-stu-id="d606f-116">Hash table key/value pairs</span></span>

<span data-ttu-id="d606f-117">Para generar consultas eficaces, utilice el cmdlet `Get-WinEvent` con el parámetro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="d606f-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="d606f-118">**FilterHashtable** acepta una tabla hash como un filtro para obtener información específica de los registros de eventos de Windows.</span><span class="sxs-lookup"><span data-stu-id="d606f-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="d606f-119">Una tabla hash usa pares **clave-valor**.</span><span class="sxs-lookup"><span data-stu-id="d606f-119">A hash table uses **key/value** pairs.</span></span> <span data-ttu-id="d606f-120">Para obtener más información sobre las tablas hash, consulte [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="d606f-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="d606f-121">Si los pares **clave-valor** se encuentran en la misma línea, deben estar separados por puntos y comas.</span><span class="sxs-lookup"><span data-stu-id="d606f-121">If the **key/value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="d606f-122">Si cada par **clave-valor** está en una línea independiente, no es necesario usar puntos y comas.</span><span class="sxs-lookup"><span data-stu-id="d606f-122">If each **key/value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="d606f-123">Por ejemplo, en este artículo se colocan los pares **clave-valor** en líneas independientes y no se usan puntos y comas.</span><span class="sxs-lookup"><span data-stu-id="d606f-123">For example, this article places **key/value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="d606f-124">En este ejemplo se utilizan varios de los pares **clave-valor** del parámetro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="d606f-124">This sample uses several of the **FilterHashtable** parameter's **key/value** pairs.</span></span> <span data-ttu-id="d606f-125">La consulta completada incluye **LogName**, **ProviderName**, **Keywords**, **ID** y **Level**.</span><span class="sxs-lookup"><span data-stu-id="d606f-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="d606f-126">Los pares **clave-valor** aceptados se muestran en la tabla siguiente y se incluyen en la documentación del parámetro **FilterHashtable** de [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
.</span><span class="sxs-lookup"><span data-stu-id="d606f-126">The accepted **key/value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="d606f-127">En la tabla siguiente se muestran los nombres de clave, los tipos de datos y si se aceptan caracteres comodín para un valor de datos.</span><span class="sxs-lookup"><span data-stu-id="d606f-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

| <span data-ttu-id="d606f-128">Nombre de clave</span><span class="sxs-lookup"><span data-stu-id="d606f-128">Key name</span></span>     | <span data-ttu-id="d606f-129">Tipo de datos de valor</span><span class="sxs-lookup"><span data-stu-id="d606f-129">Value data type</span></span>    | <span data-ttu-id="d606f-130">¿Acepta caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="d606f-130">Accepts wildcard characters?</span></span> |
|------------- | ------------------ | ---------------------------- |
| <span data-ttu-id="d606f-131">LogName</span><span class="sxs-lookup"><span data-stu-id="d606f-131">LogName</span></span>      | `<String[]>`       | <span data-ttu-id="d606f-132">Sí</span><span class="sxs-lookup"><span data-stu-id="d606f-132">Yes</span></span> |
| <span data-ttu-id="d606f-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="d606f-133">ProviderName</span></span> | `<String[]>`       | <span data-ttu-id="d606f-134">Sí</span><span class="sxs-lookup"><span data-stu-id="d606f-134">Yes</span></span> |
| <span data-ttu-id="d606f-135">Ruta</span><span class="sxs-lookup"><span data-stu-id="d606f-135">Path</span></span>         | `<String[]>`       | <span data-ttu-id="d606f-136">No</span><span class="sxs-lookup"><span data-stu-id="d606f-136">No</span></span>  |
| <span data-ttu-id="d606f-137">Palabras clave</span><span class="sxs-lookup"><span data-stu-id="d606f-137">Keywords</span></span>     | `<Long[]>`         | <span data-ttu-id="d606f-138">No</span><span class="sxs-lookup"><span data-stu-id="d606f-138">No</span></span>  |
| <span data-ttu-id="d606f-139">ID</span><span class="sxs-lookup"><span data-stu-id="d606f-139">ID</span></span>           | `<Int32[]>`        | <span data-ttu-id="d606f-140">No</span><span class="sxs-lookup"><span data-stu-id="d606f-140">No</span></span>  |
| <span data-ttu-id="d606f-141">Nivel</span><span class="sxs-lookup"><span data-stu-id="d606f-141">Level</span></span>        | `<Int32[]>`        | <span data-ttu-id="d606f-142">No</span><span class="sxs-lookup"><span data-stu-id="d606f-142">No</span></span>  |
| <span data-ttu-id="d606f-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="d606f-143">StartTime</span></span>    | `<DateTime>`       | <span data-ttu-id="d606f-144">No</span><span class="sxs-lookup"><span data-stu-id="d606f-144">No</span></span>  |
| <span data-ttu-id="d606f-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="d606f-145">EndTime</span></span>      | `<DateTime>`       | <span data-ttu-id="d606f-146">No</span><span class="sxs-lookup"><span data-stu-id="d606f-146">No</span></span>  |
| <span data-ttu-id="d606f-147">UserID</span><span class="sxs-lookup"><span data-stu-id="d606f-147">UserID</span></span>       | `<SID>`            | <span data-ttu-id="d606f-148">No</span><span class="sxs-lookup"><span data-stu-id="d606f-148">No</span></span>  |
| <span data-ttu-id="d606f-149">Datos</span><span class="sxs-lookup"><span data-stu-id="d606f-149">Data</span></span>         | `<String[]>`       | <span data-ttu-id="d606f-150">No</span><span class="sxs-lookup"><span data-stu-id="d606f-150">No</span></span>  |
| *            | `<String[]>`       | <span data-ttu-id="d606f-151">No</span><span class="sxs-lookup"><span data-stu-id="d606f-151">No</span></span>  |

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="d606f-152">Creación de una consulta con una tabla hash</span><span class="sxs-lookup"><span data-stu-id="d606f-152">Building a query with a hash table</span></span>

<span data-ttu-id="d606f-153">Para comprobar los resultados y solucionar problemas, ayuda a generar la tabla hash con un par **clave-valor** a la vez.</span><span class="sxs-lookup"><span data-stu-id="d606f-153">To verify results and troubleshoot problems, it helps to build the hash table one **key/value** pair at a time.</span></span> <span data-ttu-id="d606f-154">La consulta obtiene datos del registro **Aplicación**.</span><span class="sxs-lookup"><span data-stu-id="d606f-154">The query gets data from the **Application** log.</span></span> <span data-ttu-id="d606f-155">La tabla hash es equivalente a `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="d606f-155">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="d606f-156">Para comenzar, cree la consulta `Get-WinEvent`.</span><span class="sxs-lookup"><span data-stu-id="d606f-156">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="d606f-157">Use el par **clave-valor**  del parámetro **FilterHashtable** con la clave, **LogName**, y el valor, **Aplicación**.</span><span class="sxs-lookup"><span data-stu-id="d606f-157">Use the **FilterHashtable** parameter's **key/value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="d606f-158">Continúe para generar la tabla hash con la clave **ProviderName**.</span><span class="sxs-lookup"><span data-stu-id="d606f-158">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="d606f-159">**ProviderName** es el nombre que aparece en el campo **Origen** del **Visor de eventos de Windows**.</span><span class="sxs-lookup"><span data-stu-id="d606f-159">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="d606f-160">Por ejemplo, **.NET Runtime** en la captura de pantalla siguiente:</span><span class="sxs-lookup"><span data-stu-id="d606f-160">For example, **.NET Runtime** in the following screenshot:</span></span>

![Imagen de los orígenes del Visor de eventos de Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="d606f-162">Actualice la tabla hash e incluya el par **clave-valor** con la clave, \*\*ProviderName, y el valor, **.NET Runtime**.</span><span class="sxs-lookup"><span data-stu-id="d606f-162">Update the hash table and include the **key/value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="d606f-163">Si la consulta tiene que obtener datos de registros de eventos archivados, use la clave **Path**.</span><span class="sxs-lookup"><span data-stu-id="d606f-163">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="d606f-164">El valor **Path** especifica la ruta de acceso completa al archivo de registro.</span><span class="sxs-lookup"><span data-stu-id="d606f-164">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="d606f-165">Para obtener más información, consulte la entrada de blog de **Scripting Guy** [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors) (Uso de PowerShell para analizar registros de eventos guardados de errores).</span><span class="sxs-lookup"><span data-stu-id="d606f-165">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="d606f-166">Uso de valores enumerados en una tabla hash</span><span class="sxs-lookup"><span data-stu-id="d606f-166">Using enumerated values in a hash table</span></span>

<span data-ttu-id="d606f-167">**Keywords** es la siguiente clave de la tabla hash.</span><span class="sxs-lookup"><span data-stu-id="d606f-167">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="d606f-168">El tipo de datos **Keywords** es una matriz del tipo de valor `[long]` que contiene una gran cantidad.</span><span class="sxs-lookup"><span data-stu-id="d606f-168">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="d606f-169">Use el comando siguiente para encontrar el valor máximo de `[long]`:</span><span class="sxs-lookup"><span data-stu-id="d606f-169">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="d606f-170">Para la clave **Keywords**, PowerShell usa un número, no una cadena como **Seguridad**.</span><span class="sxs-lookup"><span data-stu-id="d606f-170">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="d606f-171">El **Visor de eventos de Windows** muestra las **palabras clave** como cadenas, pero son valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="d606f-171">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="d606f-172">En la tabla hash, si usa la clave **Keywords** con un valor de cadena, se muestra un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="d606f-172">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="d606f-173">Abra el **Visor de eventos de Windows** y en el panel **Acciones**, haga clic en **Filtrar registro actual**.</span><span class="sxs-lookup"><span data-stu-id="d606f-173">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="d606f-174">El menú desplegable **Palabras clave** muestra las palabras clave disponibles, como se ilustra en la captura de pantalla siguiente:</span><span class="sxs-lookup"><span data-stu-id="d606f-174">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Imagen de las palabras clave del Visor de eventos de Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="d606f-176">Use el siguiente comando para mostrar los nombres de propiedades `StandardEventKeywords`.</span><span class="sxs-lookup"><span data-stu-id="d606f-176">Use the following command to display the `StandardEventKeywords` property names.</span></span>

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

<span data-ttu-id="d606f-177">Los valores enumerados se documentan en **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="d606f-177">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="d606f-178">Para obtener más información, consulte [ StandardEventKeywords Enum ](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="d606f-178">For more information, see [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="d606f-179">Los valores enumerados y nombres de **Keywords** son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="d606f-179">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="d606f-180">Nombre</span><span class="sxs-lookup"><span data-stu-id="d606f-180">Name</span></span>             |  <span data-ttu-id="d606f-181">Value</span><span class="sxs-lookup"><span data-stu-id="d606f-181">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="d606f-182">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="d606f-182">AuditFailure</span></span>     | <span data-ttu-id="d606f-183">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="d606f-183">4503599627370496</span></span>  |
| <span data-ttu-id="d606f-184">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="d606f-184">AuditSuccess</span></span>     | <span data-ttu-id="d606f-185">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="d606f-185">9007199254740992</span></span>  |
| <span data-ttu-id="d606f-186">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="d606f-186">CorrelationHint2</span></span> | <span data-ttu-id="d606f-187">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="d606f-187">18014398509481984</span></span> |
| <span data-ttu-id="d606f-188">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="d606f-188">EventLogClassic</span></span>  | <span data-ttu-id="d606f-189">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="d606f-189">36028797018963968</span></span> |
| <span data-ttu-id="d606f-190">Sqm</span><span class="sxs-lookup"><span data-stu-id="d606f-190">Sqm</span></span>              | <span data-ttu-id="d606f-191">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="d606f-191">2251799813685248</span></span>  |
| <span data-ttu-id="d606f-192">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="d606f-192">WdiDiagnostic</span></span>    | <span data-ttu-id="d606f-193">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="d606f-193">1125899906842624</span></span>  |
| <span data-ttu-id="d606f-194">WdiContext</span><span class="sxs-lookup"><span data-stu-id="d606f-194">WdiContext</span></span>       | <span data-ttu-id="d606f-195">562949953421312</span><span class="sxs-lookup"><span data-stu-id="d606f-195">562949953421312</span></span>   |
| <span data-ttu-id="d606f-196">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="d606f-196">ResponseTime</span></span>     | <span data-ttu-id="d606f-197">281474976710656</span><span class="sxs-lookup"><span data-stu-id="d606f-197">281474976710656</span></span>   |
| <span data-ttu-id="d606f-198">Ninguno</span><span class="sxs-lookup"><span data-stu-id="d606f-198">None</span></span>             | <span data-ttu-id="d606f-199">0</span><span class="sxs-lookup"><span data-stu-id="d606f-199">0</span></span>                 |

<span data-ttu-id="d606f-200">Actualice la tabla hash e incluya el par **clave-valor** con la clave, **Keywords** y el valor de enumeración **EventLogClassic**, **36028797018963968**.</span><span class="sxs-lookup"><span data-stu-id="d606f-200">Update the hash table and include the **key/value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="d606f-201">Valor de propiedad estática de palabras clave (opcional)</span><span class="sxs-lookup"><span data-stu-id="d606f-201">Keywords static property value (optional)</span></span>

<span data-ttu-id="d606f-202">La clave **Keywords** se enumera, pero puede usar un nombre de propiedad estática en la consulta de tabla hash.</span><span class="sxs-lookup"><span data-stu-id="d606f-202">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="d606f-203">En lugar de usar la cadena devuelta, el nombre de propiedad debe convertirse en un valor con la propiedad **Value__**.</span><span class="sxs-lookup"><span data-stu-id="d606f-203">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="d606f-204">Por ejemplo, el script siguiente usa la propiedad **Value__**.</span><span class="sxs-lookup"><span data-stu-id="d606f-204">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="d606f-205">Filtro por identificador de evento</span><span class="sxs-lookup"><span data-stu-id="d606f-205">Filtering by Event Id</span></span>

<span data-ttu-id="d606f-206">Para obtener datos más específicos, los resultados de la consulta se filtran por **identificador de evento**. Se hace referencia al **identificador de evento** en la tabla hash como la clave **ID** y el valor es un **identificador de evento** determinado. El **Visor de eventos de Windows** muestra el **identificador de evento**. En este ejemplo se utiliza **Event Id 1023**.</span><span class="sxs-lookup"><span data-stu-id="d606f-206">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="d606f-207">Actualice la tabla hash e incluya el par **clave-valor** con la clave, **ID**, y el valor, **1023**.</span><span class="sxs-lookup"><span data-stu-id="d606f-207">Update the hash table and include the **key/value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="d606f-208">Filtro por nivel</span><span class="sxs-lookup"><span data-stu-id="d606f-208">Filtering by Level</span></span>

<span data-ttu-id="d606f-209">Para refinar más los resultados e incluir solo los eventos que indican errores, use la clave **Level**.</span><span class="sxs-lookup"><span data-stu-id="d606f-209">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="d606f-210">El **Visor de eventos de Windows** muestra el **nivel** como valores de cadena, pero son valores enumerados.</span><span class="sxs-lookup"><span data-stu-id="d606f-210">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="d606f-211">En la tabla hash, si usa la clave **Level** con un valor de cadena, se muestra un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="d606f-211">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="d606f-212">**Level** tiene valores como **Error**, **Advertencia** o **Información**.</span><span class="sxs-lookup"><span data-stu-id="d606f-212">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="d606f-213">Use el siguiente comando para mostrar los nombres de propiedades `StandardEventLevel`.</span><span class="sxs-lookup"><span data-stu-id="d606f-213">Use the following command to display the `StandardEventLevel` property names.</span></span>

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

<span data-ttu-id="d606f-214">Los valores enumerados se documentan en **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="d606f-214">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="d606f-215">Para obtener más información, consulte [ StandardEventLevel Enum](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="d606f-215">For more information, see [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="d606f-216">Los valores enumerados y nombres de la clave **Level** son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="d606f-216">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="d606f-217">Nombre</span><span class="sxs-lookup"><span data-stu-id="d606f-217">Name</span></span>           | <span data-ttu-id="d606f-218">Value</span><span class="sxs-lookup"><span data-stu-id="d606f-218">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="d606f-219">Verbose</span><span class="sxs-lookup"><span data-stu-id="d606f-219">Verbose</span></span>        |   <span data-ttu-id="d606f-220">5</span><span class="sxs-lookup"><span data-stu-id="d606f-220">5</span></span>   |
| <span data-ttu-id="d606f-221">Informativo</span><span class="sxs-lookup"><span data-stu-id="d606f-221">Informational</span></span>  |   <span data-ttu-id="d606f-222">4</span><span class="sxs-lookup"><span data-stu-id="d606f-222">4</span></span>   |
| <span data-ttu-id="d606f-223">Advertencia</span><span class="sxs-lookup"><span data-stu-id="d606f-223">Warning</span></span>        |   <span data-ttu-id="d606f-224">3</span><span class="sxs-lookup"><span data-stu-id="d606f-224">3</span></span>   |
| <span data-ttu-id="d606f-225">Error de :</span><span class="sxs-lookup"><span data-stu-id="d606f-225">Error</span></span>          |   <span data-ttu-id="d606f-226">2</span><span class="sxs-lookup"><span data-stu-id="d606f-226">2</span></span>   |
| <span data-ttu-id="d606f-227">Crítico</span><span class="sxs-lookup"><span data-stu-id="d606f-227">Critical</span></span>       |   <span data-ttu-id="d606f-228">1</span><span class="sxs-lookup"><span data-stu-id="d606f-228">1</span></span>   |
| <span data-ttu-id="d606f-229">LogAlways</span><span class="sxs-lookup"><span data-stu-id="d606f-229">LogAlways</span></span>      |   <span data-ttu-id="d606f-230">0</span><span class="sxs-lookup"><span data-stu-id="d606f-230">0</span></span>   |

<span data-ttu-id="d606f-231">La tabla hash de la consulta completada incluye la clave, **Level**, y el valor, **2**.</span><span class="sxs-lookup"><span data-stu-id="d606f-231">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="d606f-232">Propiedad estática de nivel en enumeración (opcional)</span><span class="sxs-lookup"><span data-stu-id="d606f-232">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="d606f-233">La clave **Level** se enumera, pero puede usar un nombre de propiedad estática en la consulta de tabla hash.</span><span class="sxs-lookup"><span data-stu-id="d606f-233">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="d606f-234">En lugar de usar la cadena devuelta, el nombre de propiedad debe convertirse en un valor con la propiedad **Value__**.</span><span class="sxs-lookup"><span data-stu-id="d606f-234">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="d606f-235">Por ejemplo, el script siguiente usa la propiedad **Value__**.</span><span class="sxs-lookup"><span data-stu-id="d606f-235">For example, the following script uses the **Value__** property.</span></span>

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