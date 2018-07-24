---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: b279d388754c5ee42215f21317f7b3d8089b7608
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093888"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="2600e-102">Estado coherente unificado y representación de estado</span><span class="sxs-lookup"><span data-stu-id="2600e-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="2600e-103">En este versión se incluye una serie de mejoras para el estado de LCM y el estado de DSC creados por las automatizaciones.</span><span class="sxs-lookup"><span data-stu-id="2600e-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="2600e-104">Incluyen representaciones de estado y de estado unificado coherente, la propiedad datatime administrable de los objetos de estado devueltos por el cmdlet `Get-DscConfigurationStatus` y la propiedad state details de LCM mejorada devuelta por el cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="2600e-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="2600e-105">La representación del estado de las operaciones de DSC y LCM se revisa y unifica de acuerdo con las reglas siguientes:</span><span class="sxs-lookup"><span data-stu-id="2600e-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="2600e-106">El recurso Notprocessed no afecta al estado de DSC y LCM.</span><span class="sxs-lookup"><span data-stu-id="2600e-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
1. <span data-ttu-id="2600e-107">LCM deja de procesar más recursos cuando encuentra un recurso que solicita un reinicio.</span><span class="sxs-lookup"><span data-stu-id="2600e-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
1. <span data-ttu-id="2600e-108">Un recurso que solicita un reinicio no está en el estado deseado hasta el reinicio se produce realmente.</span><span class="sxs-lookup"><span data-stu-id="2600e-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
1. <span data-ttu-id="2600e-109">Después de encontrar un recurso que genera un error, LCM sigue procesando más recursos, siempre que estos no dependan del que produjo el error.</span><span class="sxs-lookup"><span data-stu-id="2600e-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
1. <span data-ttu-id="2600e-110">El estado general devuelto por el cmdlet `Get-DscConfigurationStatus` es el superconjunto de estado de todos los recursos.</span><span class="sxs-lookup"><span data-stu-id="2600e-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
1. <span data-ttu-id="2600e-111">El estado PendingReboot es un superconjunto del estado PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="2600e-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

   <span data-ttu-id="2600e-112">En la siguiente tabla se muestran el estado resultante y las propiedades relacionadas con el estado en algunos escenarios típicos.</span><span class="sxs-lookup"><span data-stu-id="2600e-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

   | <span data-ttu-id="2600e-113">Escenario</span><span class="sxs-lookup"><span data-stu-id="2600e-113">Scenario</span></span>                    | <span data-ttu-id="2600e-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="2600e-114">LCMState</span></span>       | <span data-ttu-id="2600e-115">Estado</span><span class="sxs-lookup"><span data-stu-id="2600e-115">Status</span></span> | <span data-ttu-id="2600e-116">Reinicio solicitado</span><span class="sxs-lookup"><span data-stu-id="2600e-116">Reboot Requested</span></span>  | <span data-ttu-id="2600e-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="2600e-117">ResourcesInDesiredState</span></span>  | <span data-ttu-id="2600e-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="2600e-118">ResourcesNotInDesiredState</span></span> |
   |---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
   | <span data-ttu-id="2600e-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="2600e-119">S**^**</span></span>                          | <span data-ttu-id="2600e-120">Inactivo</span><span class="sxs-lookup"><span data-stu-id="2600e-120">Idle</span></span>                 | <span data-ttu-id="2600e-121">Correcto</span><span class="sxs-lookup"><span data-stu-id="2600e-121">Success</span></span>    | <span data-ttu-id="2600e-122">$false</span><span class="sxs-lookup"><span data-stu-id="2600e-122">$false</span></span>        | <span data-ttu-id="2600e-123">S</span><span class="sxs-lookup"><span data-stu-id="2600e-123">S</span></span>                            | <span data-ttu-id="2600e-124">$null</span><span class="sxs-lookup"><span data-stu-id="2600e-124">$null</span></span>                          |
   | <span data-ttu-id="2600e-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="2600e-125">F**^**</span></span>                          | <span data-ttu-id="2600e-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2600e-126">PendingConfiguration</span></span> | <span data-ttu-id="2600e-127">Error</span><span class="sxs-lookup"><span data-stu-id="2600e-127">Failure</span></span>    | <span data-ttu-id="2600e-128">$false</span><span class="sxs-lookup"><span data-stu-id="2600e-128">$false</span></span>        | <span data-ttu-id="2600e-129">$null</span><span class="sxs-lookup"><span data-stu-id="2600e-129">$null</span></span>                        | <span data-ttu-id="2600e-130">F</span><span class="sxs-lookup"><span data-stu-id="2600e-130">F</span></span>                              |
   | <span data-ttu-id="2600e-131">S, F</span><span class="sxs-lookup"><span data-stu-id="2600e-131">S,F</span></span>                             | <span data-ttu-id="2600e-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2600e-132">PendingConfiguration</span></span> | <span data-ttu-id="2600e-133">Error</span><span class="sxs-lookup"><span data-stu-id="2600e-133">Failure</span></span>    | <span data-ttu-id="2600e-134">$false</span><span class="sxs-lookup"><span data-stu-id="2600e-134">$false</span></span>        | <span data-ttu-id="2600e-135">S</span><span class="sxs-lookup"><span data-stu-id="2600e-135">S</span></span>                            | <span data-ttu-id="2600e-136">F</span><span class="sxs-lookup"><span data-stu-id="2600e-136">F</span></span>                              |
   | <span data-ttu-id="2600e-137">F, S</span><span class="sxs-lookup"><span data-stu-id="2600e-137">F,S</span></span>                             | <span data-ttu-id="2600e-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2600e-138">PendingConfiguration</span></span> | <span data-ttu-id="2600e-139">Error</span><span class="sxs-lookup"><span data-stu-id="2600e-139">Failure</span></span>    | <span data-ttu-id="2600e-140">$false</span><span class="sxs-lookup"><span data-stu-id="2600e-140">$false</span></span>        | <span data-ttu-id="2600e-141">S</span><span class="sxs-lookup"><span data-stu-id="2600e-141">S</span></span>                            | <span data-ttu-id="2600e-142">F</span><span class="sxs-lookup"><span data-stu-id="2600e-142">F</span></span>                              |
   | <span data-ttu-id="2600e-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="2600e-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="2600e-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2600e-144">PendingConfiguration</span></span> | <span data-ttu-id="2600e-145">Error</span><span class="sxs-lookup"><span data-stu-id="2600e-145">Failure</span></span>    | <span data-ttu-id="2600e-146">$false</span><span class="sxs-lookup"><span data-stu-id="2600e-146">$false</span></span>        | <span data-ttu-id="2600e-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="2600e-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="2600e-148">F</span><span class="sxs-lookup"><span data-stu-id="2600e-148">F</span></span>                              |
   | <span data-ttu-id="2600e-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="2600e-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="2600e-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2600e-150">PendingConfiguration</span></span> | <span data-ttu-id="2600e-151">Error</span><span class="sxs-lookup"><span data-stu-id="2600e-151">Failure</span></span>    | <span data-ttu-id="2600e-152">$false</span><span class="sxs-lookup"><span data-stu-id="2600e-152">$false</span></span>        | <span data-ttu-id="2600e-153">S</span><span class="sxs-lookup"><span data-stu-id="2600e-153">S</span></span>                            | <span data-ttu-id="2600e-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="2600e-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
   | <span data-ttu-id="2600e-155">S, r</span><span class="sxs-lookup"><span data-stu-id="2600e-155">S, r</span></span>                            | <span data-ttu-id="2600e-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="2600e-156">PendingReboot</span></span>        | <span data-ttu-id="2600e-157">Correcto</span><span class="sxs-lookup"><span data-stu-id="2600e-157">Success</span></span>    | <span data-ttu-id="2600e-158">$true</span><span class="sxs-lookup"><span data-stu-id="2600e-158">$true</span></span>         | <span data-ttu-id="2600e-159">S</span><span class="sxs-lookup"><span data-stu-id="2600e-159">S</span></span>                            | <span data-ttu-id="2600e-160">r</span><span class="sxs-lookup"><span data-stu-id="2600e-160">r</span></span>                              |
   | <span data-ttu-id="2600e-161">F, r</span><span class="sxs-lookup"><span data-stu-id="2600e-161">F, r</span></span>                            | <span data-ttu-id="2600e-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="2600e-162">PendingReboot</span></span>        | <span data-ttu-id="2600e-163">Error</span><span class="sxs-lookup"><span data-stu-id="2600e-163">Failure</span></span>    | <span data-ttu-id="2600e-164">$true</span><span class="sxs-lookup"><span data-stu-id="2600e-164">$true</span></span>         | <span data-ttu-id="2600e-165">$null</span><span class="sxs-lookup"><span data-stu-id="2600e-165">$null</span></span>                        | <span data-ttu-id="2600e-166">F, r</span><span class="sxs-lookup"><span data-stu-id="2600e-166">F, r</span></span>                           |
   | <span data-ttu-id="2600e-167">r, S</span><span class="sxs-lookup"><span data-stu-id="2600e-167">r, S</span></span>                            | <span data-ttu-id="2600e-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="2600e-168">PendingReboot</span></span>        | <span data-ttu-id="2600e-169">Correcto</span><span class="sxs-lookup"><span data-stu-id="2600e-169">Success</span></span>    | <span data-ttu-id="2600e-170">$true</span><span class="sxs-lookup"><span data-stu-id="2600e-170">$true</span></span>         | <span data-ttu-id="2600e-171">$null</span><span class="sxs-lookup"><span data-stu-id="2600e-171">$null</span></span>                        | <span data-ttu-id="2600e-172">r</span><span class="sxs-lookup"><span data-stu-id="2600e-172">r</span></span>                              |
   | <span data-ttu-id="2600e-173">r, F</span><span class="sxs-lookup"><span data-stu-id="2600e-173">r, F</span></span>                            | <span data-ttu-id="2600e-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="2600e-174">PendingReboot</span></span>        | <span data-ttu-id="2600e-175">Correcto</span><span class="sxs-lookup"><span data-stu-id="2600e-175">Success</span></span>    | <span data-ttu-id="2600e-176">$true</span><span class="sxs-lookup"><span data-stu-id="2600e-176">$true</span></span>         | <span data-ttu-id="2600e-177">$null</span><span class="sxs-lookup"><span data-stu-id="2600e-177">$null</span></span>                        | <span data-ttu-id="2600e-178">r</span><span class="sxs-lookup"><span data-stu-id="2600e-178">r</span></span>                              |

   <span data-ttu-id="2600e-179">^
   S<sub>i</sub>: serie de recursos que se aplicaron correctamente F<sub>i</sub>: serie de recursos que no se aplicaron correctamente r: recurso que requiere un reinicio \*</span><span class="sxs-lookup"><span data-stu-id="2600e-179">^
   S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

   ```powershell
   $LCMState = (Get-DscLocalConfigurationManager).LCMState
   $Status = (Get-DscConfigurationStatus).Status

   $RebootRequested = (Get-DscConfigurationStatus).RebootRequested

   $ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

   $ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
   ```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="2600e-180">Mejora en el cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="2600e-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="2600e-181">En esta versión, se incluyen algunas mejoras en el cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="2600e-181">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="2600e-182">Anteriormente, la propiedad StartDate de los objetos devueltos por el cmdlet era de tipo String.</span><span class="sxs-lookup"><span data-stu-id="2600e-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="2600e-183">Ahora, es de tipo Datetime, que facilita la selección y el filtrado complejos según las propiedades intrínsecas de un objeto Datetime.</span><span class="sxs-lookup"><span data-stu-id="2600e-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

<span data-ttu-id="2600e-184">A continuación se ofrece un ejemplo que devuelve todos los registros de operaciones de DSC que se produjeron el mismo día de la semana que hoy.</span><span class="sxs-lookup"><span data-stu-id="2600e-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="2600e-185">Se eliminaron los registros de las operaciones que no realizan cambios en la configuración del nodo (es decir, las operaciones de solo lectura).</span><span class="sxs-lookup"><span data-stu-id="2600e-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="2600e-186">Por lo tanto, las operaciones `Test-DscConfiguration` y `Get-DscConfiguration` ya no están adulteradas en los objetos devueltos desde el cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="2600e-186">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span>
<span data-ttu-id="2600e-187">Los registros de la operación de metaconfiguración se agregaron a la devolución del cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="2600e-187">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="2600e-188">A continuación se ofrece un ejemplo de resultado devuelto del cmdlet `Get-DscConfigurationStatus` –All.</span><span class="sxs-lookup"><span data-stu-id="2600e-188">Following is an example of result returned from `Get-DscConfigurationStatus` –All cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="2600e-189">Mejora en el cmdlet Get-DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2600e-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="2600e-190">Se agregó un nuevo campo de LCMStateDetail al objeto devuelto del cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="2600e-190">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="2600e-191">Este campo se rellena cuando el valor de LCMState es "Ocupado".</span><span class="sxs-lookup"><span data-stu-id="2600e-191">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="2600e-192">Se puede recuperar mediante el siguiente cmdlet:</span><span class="sxs-lookup"><span data-stu-id="2600e-192">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="2600e-193">A continuación se ofrece un ejemplo de salidas de una supervisión continua en una configuración que requiere dos reinicios en un nodo remoto.</span><span class="sxs-lookup"><span data-stu-id="2600e-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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