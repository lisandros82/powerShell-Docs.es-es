---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Problemas conocidos de WMF 5.1
ms.openlocfilehash: 74e5a6763a8a780000bf876f34caa9646a2a416a
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892144"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="04610-103">Problemas conocidos de WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="04610-103">Known Issues in WMF 5.1</span></span>

> [!Note]
> <span data-ttu-id="04610-104">Esta información está sujeta a cambios.</span><span class="sxs-lookup"><span data-stu-id="04610-104">This information is subject to change.</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="04610-105">Inicio del acceso directo de PowerShell como administrador</span><span class="sxs-lookup"><span data-stu-id="04610-105">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="04610-106">Al instalar WMF, si intenta iniciar PowerShell como administrador desde el acceso directo, puede obtener el mensaje "Error no especificado".</span><span class="sxs-lookup"><span data-stu-id="04610-106">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span>
<span data-ttu-id="04610-107">Vuelva a abrir el acceso directo como no administrador y este ya funcionará incluso como administrador.</span><span class="sxs-lookup"><span data-stu-id="04610-107">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="04610-108">Pester</span><span class="sxs-lookup"><span data-stu-id="04610-108">Pester</span></span>

<span data-ttu-id="04610-109">En esta versión, hay dos problemas que deben tenerse en cuenta cuando se utilice Pester en Nano Server:</span><span class="sxs-lookup"><span data-stu-id="04610-109">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="04610-110">La realización de pruebas en el propio Pester puede provocar errores debido a las diferencias entre FULL CLR y CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="04610-110">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="04610-111">En concreto, el método Validate no está disponible en el tipo XmlDocument.</span><span class="sxs-lookup"><span data-stu-id="04610-111">In particular, the Validate method is not available on the XmlDocument type.</span></span> <span data-ttu-id="04610-112">Se sabe que seis pruebas que intentan validar el esquema de los registros de salida de NUnit generan un error.</span><span class="sxs-lookup"><span data-stu-id="04610-112">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="04610-113">En la actualidad, una prueba de cobertura de código genera un error porque el recurso de DSC *WindowsFeature* no existe en Nano Server.</span><span class="sxs-lookup"><span data-stu-id="04610-113">One Code Coverage test fails currently because the *WindowsFeature* DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="04610-114">Sin embargo, estos errores suelen ser poco preocupantes y pueden ignorarse.</span><span class="sxs-lookup"><span data-stu-id="04610-114">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="04610-115">Validación de operaciones</span><span class="sxs-lookup"><span data-stu-id="04610-115">Operation Validation</span></span>

- <span data-ttu-id="04610-116">Se produce un error de `Update-Help` para el módulo Microsoft.PowerShell.Operation.Validation porque el URI de ayuda no funciona.</span><span class="sxs-lookup"><span data-stu-id="04610-116">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="04610-117">DSC después de desinstalar WMF</span><span class="sxs-lookup"><span data-stu-id="04610-117">DSC after uninstall WMF</span></span>

- <span data-ttu-id="04610-118">La desinstalación de WMF no elimina los documentos MOF de DSC desde la carpeta de configuración.</span><span class="sxs-lookup"><span data-stu-id="04610-118">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="04610-119">DSC no funcionará correctamente si los documentos MOF contienen propiedades más recientes que no están disponibles en los sistemas más antiguos.</span><span class="sxs-lookup"><span data-stu-id="04610-119">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="04610-120">En este caso, ejecute el siguiente script desde la consola de PowerShell con privilegios elevados para limpiar los estados de DSC.</span><span class="sxs-lookup"><span data-stu-id="04610-120">In this case, run the following script from elevated PowerShell console to to clean up the DSC states.</span></span>

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="04610-121">Cuentas virtuales de JEA</span><span class="sxs-lookup"><span data-stu-id="04610-121">JEA Virtual Accounts</span></span>

<span data-ttu-id="04610-122">Los puntos de conexión de JEA y las configuraciones de sesión configuradas para usar las cuentas virtuales de WMF 5.0 no se configurará para utilizar una cuenta virtual después de actualizar a WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="04610-122">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span>
<span data-ttu-id="04610-123">Esto significa que los comandos que se ejecutan en sesiones de JEA se ejecutarán bajo la identidad del usuario que se conecta en lugar de una cuenta de administrador temporal, impidiendo posiblemente que el usuario ejecute comandos que requieren privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="04610-123">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span>
<span data-ttu-id="04610-124">Para restaurar las cuentas virtuales, debe anular el registro y volver a registrar las configuraciones de sesión que utilizan las cuentas virtuales.</span><span class="sxs-lookup"><span data-stu-id="04610-124">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```