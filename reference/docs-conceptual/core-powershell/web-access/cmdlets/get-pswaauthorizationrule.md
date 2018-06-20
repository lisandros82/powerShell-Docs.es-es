---
ms.topic: reference
keywords: powershell, cmdlet
ms.date: 12/12/2016
title: Get-PswaAuthorizationRule
ms.openlocfilehash: d61dce18e87311d7d815a689ba675db44aaec3cb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188915"
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="c017e-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c017e-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="c017e-104">SINOPSIS</span><span class="sxs-lookup"><span data-stu-id="c017e-104">SYNOPSIS</span></span>

<span data-ttu-id="c017e-105">Devuelve un conjunto de las reglas de autorización de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="c017e-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="c017e-106">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="c017e-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="c017e-107">ID</span><span class="sxs-lookup"><span data-stu-id="c017e-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="c017e-108">Nombre</span><span class="sxs-lookup"><span data-stu-id="c017e-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="c017e-109">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="c017e-109">DESCRIPTION</span></span>

<span data-ttu-id="c017e-110">El cmdlet **Get-PswaAuthorizationRule** devuelve un conjunto de las reglas de autorización de Windows PowerShell® Web Access.</span><span class="sxs-lookup"><span data-stu-id="c017e-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="c017e-111">Si no se especifica ni el parámetro **Id** ni el parámetro **RuleName**, este cmdlet mostrará todas las reglas.</span><span class="sxs-lookup"><span data-stu-id="c017e-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="c017e-112">El parámetro **Id** se puede usar para filtrar los resultados.</span><span class="sxs-lookup"><span data-stu-id="c017e-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="c017e-113">PARÁMETROS</span><span class="sxs-lookup"><span data-stu-id="c017e-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="c017e-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="c017e-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="c017e-115">Especifica los identificadores (ID) de las reglas que debe obtener este cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c017e-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="c017e-116">Si no se especifica ningún identificador, este cmdlet devolverá todas las reglas de autorización.</span><span class="sxs-lookup"><span data-stu-id="c017e-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||
|-|-|
| <span data-ttu-id="c017e-117">Alias</span><span class="sxs-lookup"><span data-stu-id="c017e-117">Aliases</span></span>                              | <span data-ttu-id="c017e-118">ninguno</span><span class="sxs-lookup"><span data-stu-id="c017e-118">none</span></span>                                 |
| <span data-ttu-id="c017e-119">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="c017e-119">Required?</span></span>                            | <span data-ttu-id="c017e-120">falso</span><span class="sxs-lookup"><span data-stu-id="c017e-120">false</span></span>                                |
| <span data-ttu-id="c017e-121">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="c017e-121">Position?</span></span>                            | <span data-ttu-id="c017e-122">2</span><span class="sxs-lookup"><span data-stu-id="c017e-122">2</span></span>                                    |
| <span data-ttu-id="c017e-123">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c017e-123">Default Value</span></span>                        | <span data-ttu-id="c017e-124">ninguno</span><span class="sxs-lookup"><span data-stu-id="c017e-124">none</span></span>                                 |
| <span data-ttu-id="c017e-125">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="c017e-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c017e-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c017e-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="c017e-127">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="c017e-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c017e-128">falso</span><span class="sxs-lookup"><span data-stu-id="c017e-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="c017e-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="c017e-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="c017e-130">Especifica los nombres de las reglas de autorización que se van a recuperar.</span><span class="sxs-lookup"><span data-stu-id="c017e-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="c017e-131">Este parámetro devuelve todas las reglas que coinciden exactamente con los nombres de las reglas de las cadenas de esta matriz.</span><span class="sxs-lookup"><span data-stu-id="c017e-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||
|-|-|
| <span data-ttu-id="c017e-132">Alias</span><span class="sxs-lookup"><span data-stu-id="c017e-132">Aliases</span></span>                              | <span data-ttu-id="c017e-133">ninguno</span><span class="sxs-lookup"><span data-stu-id="c017e-133">none</span></span>                                 |
| <span data-ttu-id="c017e-134">¿Requerido?</span><span class="sxs-lookup"><span data-stu-id="c017e-134">Required?</span></span>                            | <span data-ttu-id="c017e-135">true</span><span class="sxs-lookup"><span data-stu-id="c017e-135">true</span></span>                                 |
| <span data-ttu-id="c017e-136">¿Posición?</span><span class="sxs-lookup"><span data-stu-id="c017e-136">Position?</span></span>                            | <span data-ttu-id="c017e-137">2</span><span class="sxs-lookup"><span data-stu-id="c017e-137">2</span></span>                                    |
| <span data-ttu-id="c017e-138">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="c017e-138">Default Value</span></span>                        | <span data-ttu-id="c017e-139">ninguno</span><span class="sxs-lookup"><span data-stu-id="c017e-139">none</span></span>                                 |
| <span data-ttu-id="c017e-140">¿Aceptar canalización?</span><span class="sxs-lookup"><span data-stu-id="c017e-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="c017e-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="c017e-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="c017e-142">¿Aceptar caracteres comodín?</span><span class="sxs-lookup"><span data-stu-id="c017e-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="c017e-143">falso</span><span class="sxs-lookup"><span data-stu-id="c017e-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="c017e-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="c017e-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="c017e-145">Este cmdlet admite los parámetros comunes: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer y -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="c017e-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="c017e-146">Para más información, vea [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c017e-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="c017e-147">ENTRADAS</span><span class="sxs-lookup"><span data-stu-id="c017e-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="c017e-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="c017e-148">int\[\]</span></span>

<span data-ttu-id="c017e-149">Este cmdlet acepta como entrada una matriz de enteros o una matriz de valores de cadena.</span><span class="sxs-lookup"><span data-stu-id="c017e-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="c017e-150">String\[\]</span><span class="sxs-lookup"><span data-stu-id="c017e-150">String\[\]</span></span>

<span data-ttu-id="c017e-151">Este cmdlet acepta como entrada una matriz de enteros o una matriz de valores de cadena.</span><span class="sxs-lookup"><span data-stu-id="c017e-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="c017e-152">SALIDAS</span><span class="sxs-lookup"><span data-stu-id="c017e-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="c017e-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="c017e-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="c017e-154">Este cmdlet genera un objeto PswaAuthorizationRule como salida.</span><span class="sxs-lookup"><span data-stu-id="c017e-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="c017e-155">EJEMPLOS</span><span class="sxs-lookup"><span data-stu-id="c017e-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="c017e-156">EJEMPLO 1</span><span class="sxs-lookup"><span data-stu-id="c017e-156">EXAMPLE 1</span></span>

<span data-ttu-id="c017e-157">Este ejemplo obtiene todas las reglas.</span><span class="sxs-lookup"><span data-stu-id="c017e-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="c017e-158">EJEMPLO 2</span><span class="sxs-lookup"><span data-stu-id="c017e-158">EXAMPLE 2</span></span>

<span data-ttu-id="c017e-159">Este ejemplo obtiene una regla con un identificador de *2*.</span><span class="sxs-lookup"><span data-stu-id="c017e-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="c017e-160">EJEMPLO 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="c017e-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="c017e-161">En este ejemplo se muestra cómo el cmdlet acepta un valor de la canalización.</span><span class="sxs-lookup"><span data-stu-id="c017e-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="c017e-162">En este cmdlet se pasa un identificador y un nombre de regla.</span><span class="sxs-lookup"><span data-stu-id="c017e-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="c017e-163">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="c017e-163">Related topics</span></span>

- [<span data-ttu-id="c017e-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c017e-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="c017e-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c017e-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="c017e-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="c017e-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="c017e-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="c017e-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)