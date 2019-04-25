---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Corrección de errores de WMF 5.1
ms.openlocfilehash: f53fc40b79a3906ac2025b0eff342c0705b82655
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085055"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="26b85-103">Corrección de errores de WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="26b85-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="26b85-104">Correcciones de errores</span><span class="sxs-lookup"><span data-stu-id="26b85-104">Bug fixes</span></span>

<span data-ttu-id="26b85-105">Se han corregido los siguientes errores importantes en WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="26b85-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a><span data-ttu-id="26b85-106">La detección automática de módulos usa `$env:PSModulePath` completamente</span><span class="sxs-lookup"><span data-stu-id="26b85-106">Module auto-discovery fully honors `$env:PSModulePath`</span></span>

<span data-ttu-id="26b85-107">La detección automática de módulos (carga de módulos automáticamente sin un cmdlet Import-Module explícito al llamar a un comando) se introdujo en WMF 3.</span><span class="sxs-lookup"><span data-stu-id="26b85-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span>
<span data-ttu-id="26b85-108">Cuando se introdujo, PowerShell comprobaba los comandos en `$PSHome\Modules` antes de usar `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="26b85-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="26b85-109">WMF 5.1 cambia este comportamiento para usar `$env:PSModulePath` completamente.</span><span class="sxs-lookup"><span data-stu-id="26b85-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span>
<span data-ttu-id="26b85-110">Esto permite que un módulo creado por el usuario que define los comandos que proporciona PowerShell (por ejemplo, `Get-ChildItem`) se cargue automáticamente y reemplace correctamente el comando integrado.</span><span class="sxs-lookup"><span data-stu-id="26b85-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="26b85-111">El redireccionamiento de archivos deja de integrar `-Encoding Unicode` como parte del código</span><span class="sxs-lookup"><span data-stu-id="26b85-111">File redirection no longer hard-codes `-Encoding Unicode`</span></span>

<span data-ttu-id="26b85-112">En todas las versiones anteriores de PowerShell, era imposible controlar la codificación de archivos usada por el operador de redireccionamiento de archivos (p. ej., `Get-ChildItem > out.txt` porque PowerShell agregó `-Encoding Unicode`).</span><span class="sxs-lookup"><span data-stu-id="26b85-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator, e.g. `Get-ChildItem > out.txt` because PowerShell added `-Encoding Unicode`.</span></span>

<span data-ttu-id="26b85-113">A partir de WMF 5.1, se puede cambiar la codificación de archivos del redireccionamiento mediante el establecimiento de `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="26b85-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="26b85-114">Se ha corregido una regresión en el acceso de los miembros de `System.Reflection.TypeInfo`</span><span class="sxs-lookup"><span data-stu-id="26b85-114">Fixed a regression in accessing members of `System.Reflection.TypeInfo`</span></span>

<span data-ttu-id="26b85-115">Una regresión introducida en WMF 5.0 interrumpía el acceso de los miembros de `System.Reflection.RuntimeType`, por ejemplo, `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="26b85-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, e.g. `[int].ImplementedInterfaces`.</span></span>
<span data-ttu-id="26b85-116">Este error se ha corregido en WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="26b85-116">This bug has been fixed in WMF 5.1.</span></span>


### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="26b85-117">Se han corregido algunos problemas con objetos COM</span><span class="sxs-lookup"><span data-stu-id="26b85-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="26b85-118">WMF 5.0 introdujo un nuevo enlazador COM para invocar métodos en objetos COM y acceder a propiedades de objetos COM.</span><span class="sxs-lookup"><span data-stu-id="26b85-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span>
<span data-ttu-id="26b85-119">Este nuevo enlazador ha mejorado considerablemente el rendimiento, pero también ha presentado algunos errores que se han corregido en WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="26b85-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="26b85-120">Las conversiones de argumentos no siempre se realizaban correctamente</span><span class="sxs-lookup"><span data-stu-id="26b85-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="26b85-121">En el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="26b85-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="26b85-122">El método SendKeys espera una cadena, pero PowerShell no ha convertido el carácter en una cadena, lo que aplaza la conversión a IDispatch:: Invoke, que usa VariantChangeType para realizar la conversión, lo que en este ejemplo provocó el envío de las claves '1', '7' y '3', en lugar de la clave Volume.Mute, que era la que se esperaba.</span><span class="sxs-lookup"><span data-stu-id="26b85-122">The SendKeys method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to IDispatch::Invoke, which uses VariantChangeType to do the conversion, which in this example resulted in sending the keys '1', '7', and '3' instead of the expected Volume.Mute key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="26b85-123">Los objetos COM enumerables no siempre se controlan correctamente</span><span class="sxs-lookup"><span data-stu-id="26b85-123">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="26b85-124">PowerShell normalmente enumera la mayoría de los objetos enumerables, pero una regresión introducida en WMF 5.0 impidió la enumeración de objetos COM que implementan IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="26b85-124">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span>  <span data-ttu-id="26b85-125">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="26b85-125">For example:</span></span>

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="26b85-126">En el ejemplo anterior, WMF 5.0 escribió incorrectamente Scripting.Dictionary en la canalización, en lugar de enumerar los pares clave-valor.</span><span class="sxs-lookup"><span data-stu-id="26b85-126">In the above example, WMF 5.0 incorrectly wrote the Scripting.Dictionary to the pipeline instead of enumerating the key/value pairs.</span></span>

<span data-ttu-id="26b85-127">Este cambio también permite solucionar el [problema 1752224 en Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span><span class="sxs-lookup"><span data-stu-id="26b85-127">This change also addresses [issue 1752224 on Connect](https://connect.microsoft.com/PowerShell/feedback/details/1752224)</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="26b85-128">`[ordered]` no se permitía en las clases</span><span class="sxs-lookup"><span data-stu-id="26b85-128">`[ordered]` was not allowed inside classes</span></span>

<span data-ttu-id="26b85-129">WMF 5.0 introdujo clases con una validación de los literales de tipo que se usan en las clases.</span><span class="sxs-lookup"><span data-stu-id="26b85-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span>
<span data-ttu-id="26b85-130">`[ordered]` parece un literal de tipo, pero no es un verdadero tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="26b85-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span>
<span data-ttu-id="26b85-131">WMF 5.0 informaba incorrectamente de un error en `[ordered]` dentro de una clase:</span><span class="sxs-lookup"><span data-stu-id="26b85-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="26b85-132">Los temas de ayuda con varias versiones no funcionan</span><span class="sxs-lookup"><span data-stu-id="26b85-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="26b85-133">Antes de WMF 5.1, si había varias versiones de un módulo instaladas y todas compartían un tema de ayuda, por ejemplo, about_PSReadline, `help about_PSReadline` devolvía varios temas sin ninguna forma obvia de ver la ayuda real.</span><span class="sxs-lookup"><span data-stu-id="26b85-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="26b85-134">WMF 5.1 corrige este problema, para lo que devuelve la ayuda de la versión más reciente del tema.</span><span class="sxs-lookup"><span data-stu-id="26b85-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="26b85-135">`Get-Help` no proporciona una forma de especificar para qué versión se quiere la ayuda.</span><span class="sxs-lookup"><span data-stu-id="26b85-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span>
<span data-ttu-id="26b85-136">Para solucionar este problema, navegue hasta el directorio modules y vea la ayuda directamente con una herramienta como su editor favorito.</span><span class="sxs-lookup"><span data-stu-id="26b85-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="26b85-137">La lectura de powerShell.exe desde STDIN dejó de funcionar</span><span class="sxs-lookup"><span data-stu-id="26b85-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="26b85-138">Los clientes utilizan `powershell -command -` de las aplicaciones nativas para ejecutar PowerShell pasando el script a través de STDIN. Desafortunadamente esto se ha interrumpido debido a otros cambios en el host de consola.</span><span class="sxs-lookup"><span data-stu-id="26b85-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken due to other changes it the console host.</span></span>

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="26b85-139">powershell.exe origina un punto máximo en el uso de CPU en el inicio</span><span class="sxs-lookup"><span data-stu-id="26b85-139">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="26b85-140">PowerShell usa una consulta WMI para comprobar que se ha iniciado a través de la directiva de grupo para evitar los retrasos en el inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="26b85-140">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span>
<span data-ttu-id="26b85-141">La consulta WMI termina con la inyección de tzres.mui.dll en todos los procesos del sistema, puesto que la clase Win32_Process de WMI intenta recuperar la información de la zona horaria local.</span><span class="sxs-lookup"><span data-stu-id="26b85-141">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI Win32_Process class attempts to retrieve local timezone information.</span></span>
<span data-ttu-id="26b85-142">Esto produce un gran aumento de la CPU en wmiprvse (el host del proveedor WMI).</span><span class="sxs-lookup"><span data-stu-id="26b85-142">This results in a large CPU spike in wmiprvse (the WMI provider host).</span></span>
<span data-ttu-id="26b85-143">La solución consiste en utilizar llamadas a la API de Win32 para obtener la misma información en lugar de usar WMI.</span><span class="sxs-lookup"><span data-stu-id="26b85-143">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
