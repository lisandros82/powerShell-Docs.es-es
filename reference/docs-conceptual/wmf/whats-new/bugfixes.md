---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Corrección de errores de WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147855"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="647c4-103">Corrección de errores de WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="647c4-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="647c4-104">Correcciones de errores</span><span class="sxs-lookup"><span data-stu-id="647c4-104">Bug fixes</span></span>

<span data-ttu-id="647c4-105">Se han corregido los siguientes errores importantes en WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="647c4-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a><span data-ttu-id="647c4-106">La detección automática de módulos usa PSModulePath completamente</span><span class="sxs-lookup"><span data-stu-id="647c4-106">Module auto-discovery fully honors PSModulePath</span></span>

<span data-ttu-id="647c4-107">La detección automática de módulos (carga de módulos automáticamente sin un cmdlet Import-Module explícito al llamar a un comando) se introdujo en WMF 3.</span><span class="sxs-lookup"><span data-stu-id="647c4-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="647c4-108">Cuando se introdujo, PowerShell comprobaba los comandos en `$PSHome\Modules` antes de usar `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="647c4-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="647c4-109">WMF 5.1 cambia este comportamiento para usar `$env:PSModulePath` completamente.</span><span class="sxs-lookup"><span data-stu-id="647c4-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="647c4-110">Esto permite que un módulo creado por el usuario que define los comandos que proporciona PowerShell (por ejemplo, `Get-ChildItem`) se cargue automáticamente y reemplace correctamente el comando integrado.</span><span class="sxs-lookup"><span data-stu-id="647c4-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="647c4-111">El redireccionamiento de archivos deja de codificar -Encoding Unicode de forma rígida</span><span class="sxs-lookup"><span data-stu-id="647c4-111">File redirection no longer hard-codes -Encoding Unicode</span></span>

<span data-ttu-id="647c4-112">En todas las versiones anteriores de PowerShell, era imposible controlar la codificación de archivos usada por el operador de redireccionamiento de archivos.</span><span class="sxs-lookup"><span data-stu-id="647c4-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator.</span></span>

<span data-ttu-id="647c4-113">A partir de WMF 5.1, se puede cambiar la codificación de archivos del redireccionamiento mediante el establecimiento de `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="647c4-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="647c4-114">Se corrigió una regresión en el acceso de los miembros de System.Reflection.TypeInfo</span><span class="sxs-lookup"><span data-stu-id="647c4-114">Fixed a regression in accessing members of System.Reflection.TypeInfo</span></span>

<span data-ttu-id="647c4-115">Una regresión introducida en WMF 5.0 interrumpía el acceso de los miembros de `System.Reflection.RuntimeType`, por ejemplo, `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="647c4-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, for example, `[int].ImplementedInterfaces`.</span></span> <span data-ttu-id="647c4-116">Este error se ha corregido en WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="647c4-116">This bug has been fixed in WMF 5.1.</span></span>

### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="647c4-117">Se han corregido algunos problemas con objetos COM</span><span class="sxs-lookup"><span data-stu-id="647c4-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="647c4-118">WMF 5.0 introdujo un nuevo enlazador COM para invocar métodos en objetos COM y acceder a propiedades de objetos COM.</span><span class="sxs-lookup"><span data-stu-id="647c4-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="647c4-119">Este nuevo enlazador ha mejorado considerablemente el rendimiento, pero también ha presentado algunos errores que se han corregido en WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="647c4-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="647c4-120">Las conversiones de argumentos no siempre se realizaban correctamente</span><span class="sxs-lookup"><span data-stu-id="647c4-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="647c4-121">En el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="647c4-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="647c4-122">El método **SendKeys**espera una cadena, pero PowerShell no ha convertido el carácter en una cadena, lo que aplaza la conversión a **IDispatch::Invoke**, que usa **VariantChangeType** para realizar la conversión.</span><span class="sxs-lookup"><span data-stu-id="647c4-122">The **SendKeys** method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to **IDispatch::Invoke**, which uses **VariantChangeType** to do the conversion.</span></span> <span data-ttu-id="647c4-123">En este ejemplo, esto provocó el envío de las claves "1", "7" y "3" en lugar de la clave **Volume.Mute** que se esperaba.</span><span class="sxs-lookup"><span data-stu-id="647c4-123">In this example, this resulted in sending the keys '1', '7', and '3' instead of the expected **Volume.Mute** key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="647c4-124">Los objetos COM enumerables no siempre se controlan correctamente</span><span class="sxs-lookup"><span data-stu-id="647c4-124">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="647c4-125">PowerShell normalmente enumera la mayoría de los objetos enumerables, pero una regresión introducida en WMF 5.0 impidió la enumeración de objetos COM que implementan IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="647c4-125">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span> <span data-ttu-id="647c4-126">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="647c4-126">For example:</span></span>

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

<span data-ttu-id="647c4-127">En el ejemplo anterior, WMF 5.0 escribió incorrectamente **Scripting.Dictionary** en la canalización, en lugar de enumerar los pares clave-valor.</span><span class="sxs-lookup"><span data-stu-id="647c4-127">In the above example, WMF 5.0 incorrectly wrote the **Scripting.Dictionary** to the pipeline instead of enumerating the key/value pairs.</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="647c4-128">[ordered] no se permitía en las clases</span><span class="sxs-lookup"><span data-stu-id="647c4-128">[ordered] was not allowed inside classes</span></span>

<span data-ttu-id="647c4-129">WMF 5.0 introdujo clases con una validación de los literales de tipo que se usan en las clases.</span><span class="sxs-lookup"><span data-stu-id="647c4-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span> <span data-ttu-id="647c4-130">`[ordered]` parece un literal de tipo, pero no es un verdadero tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="647c4-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="647c4-131">WMF 5.0 informaba incorrectamente de un error en `[ordered]` dentro de una clase:</span><span class="sxs-lookup"><span data-stu-id="647c4-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="647c4-132">Los temas de ayuda con varias versiones no funcionan</span><span class="sxs-lookup"><span data-stu-id="647c4-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="647c4-133">Antes de WMF 5.1, si había varias versiones de un módulo instaladas y todas compartían un tema de ayuda, por ejemplo, about_PSReadline, `help about_PSReadline` devolvía varios temas sin ninguna forma obvia de ver la ayuda real.</span><span class="sxs-lookup"><span data-stu-id="647c4-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="647c4-134">WMF 5.1 corrige este problema, para lo que devuelve la ayuda de la versión más reciente del tema.</span><span class="sxs-lookup"><span data-stu-id="647c4-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="647c4-135">`Get-Help` no proporciona una forma de especificar para qué versión se quiere la ayuda.</span><span class="sxs-lookup"><span data-stu-id="647c4-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="647c4-136">Para solucionar este problema, navegue hasta el directorio modules y vea la ayuda directamente con una herramienta como su editor favorito.</span><span class="sxs-lookup"><span data-stu-id="647c4-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="647c4-137">La lectura de powerShell.exe desde STDIN dejó de funcionar</span><span class="sxs-lookup"><span data-stu-id="647c4-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="647c4-138">Los clientes utilizan `powershell -command -` de las aplicaciones nativas para ejecutar PowerShell pasando el script a través de STDIN. Desafortunadamente esto se ha interrumpido debido a otros cambios en el host de consola.</span><span class="sxs-lookup"><span data-stu-id="647c4-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken by other changes in the console host.</span></span>

<span data-ttu-id="647c4-139">Esto se corrigió para la versión 5.1 en la Actualización de aniversario de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="647c4-139">This is fixed for version 5.1 in the Windows 10 Anniversary Update.</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="647c4-140">powershell.exe origina un punto máximo en el uso de CPU en el inicio</span><span class="sxs-lookup"><span data-stu-id="647c4-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="647c4-141">PowerShell usa una consulta WMI para comprobar que se ha iniciado a través de la directiva de grupo para evitar los retrasos en el inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="647c4-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span> <span data-ttu-id="647c4-142">La consulta WMI termina con la inyección de tzres.mui.dll en todos los procesos del sistema, puesto que la clase **Win32_Process** de WMI intenta recuperar la información de la zona horaria local.</span><span class="sxs-lookup"><span data-stu-id="647c4-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI **Win32_Process** class attempts to retrieve local timezone information.</span></span> <span data-ttu-id="647c4-143">Esto produce un gran aumento de la CPU en **wmiprvse** (el host del proveedor WMI).</span><span class="sxs-lookup"><span data-stu-id="647c4-143">This results in a large CPU spike in **wmiprvse** (the WMI provider host).</span></span> <span data-ttu-id="647c4-144">La solución consiste en utilizar llamadas a la API de Win32 para obtener la misma información en lugar de usar WMI.</span><span class="sxs-lookup"><span data-stu-id="647c4-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
