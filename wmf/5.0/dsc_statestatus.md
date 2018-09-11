---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339878"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="c1386-102">Estado coherente unificado y representación de estado</span><span class="sxs-lookup"><span data-stu-id="c1386-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="c1386-103">En este versión se incluye una serie de mejoras para el estado de LCM y el estado de DSC creados por las automatizaciones.</span><span class="sxs-lookup"><span data-stu-id="c1386-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="c1386-104">Incluyen representaciones de estado y de estado unificado coherente, la propiedad datatime administrable de los objetos de estado devueltos por el cmdlet `Get-DscConfigurationStatus` y la propiedad state details de LCM mejorada devuelta por el cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="c1386-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="c1386-105">La representación del estado de las operaciones de DSC y LCM se revisa y unifica de acuerdo con las reglas siguientes:</span><span class="sxs-lookup"><span data-stu-id="c1386-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="c1386-106">El recurso Notprocessed no afecta al estado de DSC y LCM.</span><span class="sxs-lookup"><span data-stu-id="c1386-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="c1386-107">LCM deja de procesar más recursos cuando encuentra un recurso que solicita un reinicio.</span><span class="sxs-lookup"><span data-stu-id="c1386-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="c1386-108">Un recurso que solicita un reinicio no está en el estado deseado hasta el reinicio se produce realmente.</span><span class="sxs-lookup"><span data-stu-id="c1386-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="c1386-109">Después de encontrar un recurso que genera un error, LCM sigue procesando más recursos, siempre que estos no dependan del que produjo el error.</span><span class="sxs-lookup"><span data-stu-id="c1386-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="c1386-110">El estado general devuelto por el cmdlet `Get-DscConfigurationStatus` es el superconjunto de estado de todos los recursos.</span><span class="sxs-lookup"><span data-stu-id="c1386-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="c1386-111">El estado PendingReboot es un superconjunto del estado PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="c1386-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="c1386-112">En la siguiente tabla se muestran el estado resultante y las propiedades relacionadas con el estado en algunos escenarios típicos.</span><span class="sxs-lookup"><span data-stu-id="c1386-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="c1386-113">Escenario</span><span class="sxs-lookup"><span data-stu-id="c1386-113">Scenario</span></span>                        | <span data-ttu-id="c1386-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="c1386-114">LCMState</span></span>             | <span data-ttu-id="c1386-115">Estado</span><span class="sxs-lookup"><span data-stu-id="c1386-115">Status</span></span>     | <span data-ttu-id="c1386-116">Reinicio solicitado</span><span class="sxs-lookup"><span data-stu-id="c1386-116">Reboot Requested</span></span> | <span data-ttu-id="c1386-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="c1386-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="c1386-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="c1386-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="c1386-119">S<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="c1386-119">S<sub>i</sub></span></span>                   | <span data-ttu-id="c1386-120">Inactivo</span><span class="sxs-lookup"><span data-stu-id="c1386-120">Idle</span></span>                 | <span data-ttu-id="c1386-121">Correcto</span><span class="sxs-lookup"><span data-stu-id="c1386-121">Success</span></span>    | <span data-ttu-id="c1386-122">$false</span><span class="sxs-lookup"><span data-stu-id="c1386-122">$false</span></span>        | <span data-ttu-id="c1386-123">S</span><span class="sxs-lookup"><span data-stu-id="c1386-123">S</span></span>                            | <span data-ttu-id="c1386-124">$null</span><span class="sxs-lookup"><span data-stu-id="c1386-124">$null</span></span>                          |
| <span data-ttu-id="c1386-125">F<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="c1386-125">F<sub>i</sub></span></span>                   | <span data-ttu-id="c1386-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c1386-126">PendingConfiguration</span></span> | <span data-ttu-id="c1386-127">Error</span><span class="sxs-lookup"><span data-stu-id="c1386-127">Failure</span></span>    | <span data-ttu-id="c1386-128">$false</span><span class="sxs-lookup"><span data-stu-id="c1386-128">$false</span></span>        | <span data-ttu-id="c1386-129">$null</span><span class="sxs-lookup"><span data-stu-id="c1386-129">$null</span></span>                        | <span data-ttu-id="c1386-130">F</span><span class="sxs-lookup"><span data-stu-id="c1386-130">F</span></span>                              |
| <span data-ttu-id="c1386-131">S, F</span><span class="sxs-lookup"><span data-stu-id="c1386-131">S,F</span></span>                             | <span data-ttu-id="c1386-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c1386-132">PendingConfiguration</span></span> | <span data-ttu-id="c1386-133">Error</span><span class="sxs-lookup"><span data-stu-id="c1386-133">Failure</span></span>    | <span data-ttu-id="c1386-134">$false</span><span class="sxs-lookup"><span data-stu-id="c1386-134">$false</span></span>        | <span data-ttu-id="c1386-135">S</span><span class="sxs-lookup"><span data-stu-id="c1386-135">S</span></span>                            | <span data-ttu-id="c1386-136">F</span><span class="sxs-lookup"><span data-stu-id="c1386-136">F</span></span>                              |
| <span data-ttu-id="c1386-137">F, S</span><span class="sxs-lookup"><span data-stu-id="c1386-137">F,S</span></span>                             | <span data-ttu-id="c1386-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c1386-138">PendingConfiguration</span></span> | <span data-ttu-id="c1386-139">Error</span><span class="sxs-lookup"><span data-stu-id="c1386-139">Failure</span></span>    | <span data-ttu-id="c1386-140">$false</span><span class="sxs-lookup"><span data-stu-id="c1386-140">$false</span></span>        | <span data-ttu-id="c1386-141">S</span><span class="sxs-lookup"><span data-stu-id="c1386-141">S</span></span>                            | <span data-ttu-id="c1386-142">F</span><span class="sxs-lookup"><span data-stu-id="c1386-142">F</span></span>                              |
| <span data-ttu-id="c1386-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="c1386-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="c1386-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c1386-144">PendingConfiguration</span></span> | <span data-ttu-id="c1386-145">Error</span><span class="sxs-lookup"><span data-stu-id="c1386-145">Failure</span></span>    | <span data-ttu-id="c1386-146">$false</span><span class="sxs-lookup"><span data-stu-id="c1386-146">$false</span></span>        | <span data-ttu-id="c1386-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="c1386-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="c1386-148">F</span><span class="sxs-lookup"><span data-stu-id="c1386-148">F</span></span>                              |
| <span data-ttu-id="c1386-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="c1386-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="c1386-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c1386-150">PendingConfiguration</span></span> | <span data-ttu-id="c1386-151">Error</span><span class="sxs-lookup"><span data-stu-id="c1386-151">Failure</span></span>    | <span data-ttu-id="c1386-152">$false</span><span class="sxs-lookup"><span data-stu-id="c1386-152">$false</span></span>        | <span data-ttu-id="c1386-153">S</span><span class="sxs-lookup"><span data-stu-id="c1386-153">S</span></span>                            | <span data-ttu-id="c1386-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="c1386-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="c1386-155">S, r</span><span class="sxs-lookup"><span data-stu-id="c1386-155">S, r</span></span>                            | <span data-ttu-id="c1386-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="c1386-156">PendingReboot</span></span>        | <span data-ttu-id="c1386-157">Correcto</span><span class="sxs-lookup"><span data-stu-id="c1386-157">Success</span></span>    | <span data-ttu-id="c1386-158">$true</span><span class="sxs-lookup"><span data-stu-id="c1386-158">$true</span></span>         | <span data-ttu-id="c1386-159">S</span><span class="sxs-lookup"><span data-stu-id="c1386-159">S</span></span>                            | <span data-ttu-id="c1386-160">r</span><span class="sxs-lookup"><span data-stu-id="c1386-160">r</span></span>                              |
| <span data-ttu-id="c1386-161">F, r</span><span class="sxs-lookup"><span data-stu-id="c1386-161">F, r</span></span>                            | <span data-ttu-id="c1386-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="c1386-162">PendingReboot</span></span>        | <span data-ttu-id="c1386-163">Error</span><span class="sxs-lookup"><span data-stu-id="c1386-163">Failure</span></span>    | <span data-ttu-id="c1386-164">$true</span><span class="sxs-lookup"><span data-stu-id="c1386-164">$true</span></span>         | <span data-ttu-id="c1386-165">$null</span><span class="sxs-lookup"><span data-stu-id="c1386-165">$null</span></span>                        | <span data-ttu-id="c1386-166">F, r</span><span class="sxs-lookup"><span data-stu-id="c1386-166">F, r</span></span>                           |
| <span data-ttu-id="c1386-167">r, S</span><span class="sxs-lookup"><span data-stu-id="c1386-167">r, S</span></span>                            | <span data-ttu-id="c1386-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="c1386-168">PendingReboot</span></span>        | <span data-ttu-id="c1386-169">Correcto</span><span class="sxs-lookup"><span data-stu-id="c1386-169">Success</span></span>    | <span data-ttu-id="c1386-170">$true</span><span class="sxs-lookup"><span data-stu-id="c1386-170">$true</span></span>         | <span data-ttu-id="c1386-171">$null</span><span class="sxs-lookup"><span data-stu-id="c1386-171">$null</span></span>                        | <span data-ttu-id="c1386-172">r</span><span class="sxs-lookup"><span data-stu-id="c1386-172">r</span></span>                              |
| <span data-ttu-id="c1386-173">r, F</span><span class="sxs-lookup"><span data-stu-id="c1386-173">r, F</span></span>                            | <span data-ttu-id="c1386-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="c1386-174">PendingReboot</span></span>        | <span data-ttu-id="c1386-175">Correcto</span><span class="sxs-lookup"><span data-stu-id="c1386-175">Success</span></span>    | <span data-ttu-id="c1386-176">$true</span><span class="sxs-lookup"><span data-stu-id="c1386-176">$true</span></span>         | <span data-ttu-id="c1386-177">$null</span><span class="sxs-lookup"><span data-stu-id="c1386-177">$null</span></span>                        | <span data-ttu-id="c1386-178">r</span><span class="sxs-lookup"><span data-stu-id="c1386-178">r</span></span>                              |

- <span data-ttu-id="c1386-179">S<sub>i</sub>: serie de recursos que se aplicaron correctamente</span><span class="sxs-lookup"><span data-stu-id="c1386-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="c1386-180">S<sub>i</sub>: serie de recursos que no se aplicaron correctamente</span><span class="sxs-lookup"><span data-stu-id="c1386-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="c1386-181">r: recurso que requiere un reinicio</span><span class="sxs-lookup"><span data-stu-id="c1386-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="c1386-182">Mejora en el cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="c1386-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="c1386-183">En esta versión, se incluyen algunas mejoras en el cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="c1386-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="c1386-184">Anteriormente, la propiedad StartDate de los objetos devueltos por el cmdlet era de tipo String.</span><span class="sxs-lookup"><span data-stu-id="c1386-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="c1386-185">Ahora, es de tipo Datetime, que facilita la selección y el filtrado complejos según las propiedades intrínsecas de un objeto Datetime.</span><span class="sxs-lookup"><span data-stu-id="c1386-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

<span data-ttu-id="c1386-186">En el ejemplo siguiente se devuelven todos los registros de operaciones de DSC que se produjeron el mismo día de la semana que el día actual.</span><span class="sxs-lookup"><span data-stu-id="c1386-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="c1386-187">Se eliminaron los registros de las operaciones que no realizan cambios en la configuración del nodo (es decir, las operaciones de solo lectura).</span><span class="sxs-lookup"><span data-stu-id="c1386-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="c1386-188">Por lo tanto, las operaciones `Test-DscConfiguration` y `Get-DscConfiguration` ya no están adulteradas en los objetos devueltos desde el cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="c1386-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="c1386-189">Los registros de la operación de metaconfiguración se agregaron a la devolución del cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="c1386-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="c1386-190">A continuación se ofrece un ejemplo de resultado devuelto del cmdlet `Get-DscConfigurationStatus –All`.</span><span class="sxs-lookup"><span data-stu-id="c1386-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="c1386-191">Mejora en el cmdlet Get-DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="c1386-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="c1386-192">Se agregó un nuevo campo de LCMStateDetail al objeto devuelto del cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="c1386-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="c1386-193">Este campo se rellena cuando el valor de LCMState es "Ocupado".</span><span class="sxs-lookup"><span data-stu-id="c1386-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="c1386-194">Se puede recuperar mediante el siguiente cmdlet:</span><span class="sxs-lookup"><span data-stu-id="c1386-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="c1386-195">A continuación se ofrece un ejemplo de salidas de una supervisión continua en una configuración que requiere dos reinicios en un nodo remoto.</span><span class="sxs-lookup"><span data-stu-id="c1386-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

```output
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```
