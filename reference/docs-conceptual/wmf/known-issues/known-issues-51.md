---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: Problemas conocidos de WMF 5.1
ms.openlocfilehash: 8348f9d45dca32dcda2ef8baa75d586c8728d0a4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147955"
---
# <a name="known-issues-in-wmf-51"></a><span data-ttu-id="a097b-103">Problemas conocidos de WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="a097b-103">Known Issues in WMF 5.1</span></span>

## <a name="starting-powershell-shortcut-as-administrator"></a><span data-ttu-id="a097b-104">Inicio del acceso directo de PowerShell como administrador</span><span class="sxs-lookup"><span data-stu-id="a097b-104">Starting PowerShell shortcut as Administrator</span></span>

<span data-ttu-id="a097b-105">Al instalar WMF, si intenta iniciar PowerShell como administrador desde el acceso directo, puede obtener el mensaje "Error no especificado".</span><span class="sxs-lookup"><span data-stu-id="a097b-105">Upon installing WMF, if you try to start PowerShell as administrator from the shortcut, you may get an "Unspecified error" message.</span></span> <span data-ttu-id="a097b-106">Vuelva a abrir el acceso directo como no administrador y este ya funcionará incluso como administrador.</span><span class="sxs-lookup"><span data-stu-id="a097b-106">Reopen the shortcut as non-administrator and the shortcut now works even as administrator.</span></span>

## <a name="pester"></a><span data-ttu-id="a097b-107">Pester</span><span class="sxs-lookup"><span data-stu-id="a097b-107">Pester</span></span>

<span data-ttu-id="a097b-108">En esta versión, hay dos problemas que deben tenerse en cuenta cuando se utilice Pester en Nano Server:</span><span class="sxs-lookup"><span data-stu-id="a097b-108">In this release, there are two issues you should be aware of when using Pester on Nano Server:</span></span>

- <span data-ttu-id="a097b-109">La realización de pruebas en el propio Pester puede provocar errores debido a las diferencias entre FULL CLR y CORE CLR.</span><span class="sxs-lookup"><span data-stu-id="a097b-109">Running tests against Pester itself can result in some failures because of differences between FULL CLR and CORE CLR.</span></span> <span data-ttu-id="a097b-110">En concreto, el método **Validate** no está disponible en el tipo **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="a097b-110">In particular, the **Validate** method is not available on the **XmlDocument** type.</span></span> <span data-ttu-id="a097b-111">Se sabe que seis pruebas que intentan validar el esquema de los registros de salida de NUnit generan un error.</span><span class="sxs-lookup"><span data-stu-id="a097b-111">Six tests which attempt to validate the schema of the NUnit output logs are known to fail.</span></span>
- <span data-ttu-id="a097b-112">Una prueba de cobertura de código genera un error porque el recurso de DSC **WindowsFeature** no existe en Nano Server.</span><span class="sxs-lookup"><span data-stu-id="a097b-112">One code coverage test fails because the **WindowsFeature** DSC Resource does not exist in Nano Server.</span></span> <span data-ttu-id="a097b-113">Sin embargo, estos errores suelen ser poco preocupantes y pueden ignorarse.</span><span class="sxs-lookup"><span data-stu-id="a097b-113">However, these failures are generally benign and can safely be ignored.</span></span>

## <a name="operation-validation"></a><span data-ttu-id="a097b-114">Validación de operaciones</span><span class="sxs-lookup"><span data-stu-id="a097b-114">Operation Validation</span></span>

- <span data-ttu-id="a097b-115">Se produce un error de `Update-Help` para el módulo Microsoft.PowerShell.Operation.Validation porque el URI de ayuda no funciona.</span><span class="sxs-lookup"><span data-stu-id="a097b-115">`Update-Help` fails for Microsoft.PowerShell.Operation.Validation module due to non-working help URI</span></span>

## <a name="dsc-after-uninstall-wmf"></a><span data-ttu-id="a097b-116">DSC después de desinstalar WMF</span><span class="sxs-lookup"><span data-stu-id="a097b-116">DSC after uninstall WMF</span></span>

- <span data-ttu-id="a097b-117">La desinstalación de WMF no elimina los documentos MOF de DSC desde la carpeta de configuración.</span><span class="sxs-lookup"><span data-stu-id="a097b-117">Uninstalling WMF does not delete DSC MOF documents from the configuration folder.</span></span> <span data-ttu-id="a097b-118">DSC no funcionará correctamente si los documentos MOF contienen propiedades más recientes que no están disponibles en los sistemas más antiguos.</span><span class="sxs-lookup"><span data-stu-id="a097b-118">DSC won't work properly if the MOF documents contain newer properties which are not available on the older systems.</span></span> <span data-ttu-id="a097b-119">En este caso, ejecute el siguiente script desde la consola de PowerShell con privilegios elevados para limpiar los estados de DSC.</span><span class="sxs-lookup"><span data-stu-id="a097b-119">In this case, run the following script from elevated PowerShell console to clean up the DSC states.</span></span>

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a><span data-ttu-id="a097b-120">Cuentas virtuales de JEA</span><span class="sxs-lookup"><span data-stu-id="a097b-120">JEA Virtual Accounts</span></span>

<span data-ttu-id="a097b-121">Los puntos de conexión de JEA y las configuraciones de sesión configuradas para usar las cuentas virtuales de WMF 5.0 no se configurará para utilizar una cuenta virtual después de actualizar a WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="a097b-121">JEA endpoints and session configurations configured to use virtual accounts in WMF 5.0 will not be configured to use a virtual account after upgrading to WMF 5.1.</span></span> <span data-ttu-id="a097b-122">Esto significa que los comandos que se ejecutan en sesiones de JEA se ejecutarán bajo la identidad del usuario que se conecta en lugar de una cuenta de administrador temporal, impidiendo posiblemente que el usuario ejecute comandos que requieren privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="a097b-122">This means that commands run in JEA sessions will run under the connecting user's identity instead of a temporary administrator account, potentially preventing the user from running commands which require elevated privileges.</span></span> <span data-ttu-id="a097b-123">Para restaurar las cuentas virtuales, debe anular el registro y volver a registrar las configuraciones de sesión que utilizan las cuentas virtuales.</span><span class="sxs-lookup"><span data-stu-id="a097b-123">To restore the virtual accounts, you need to unregister and re-register any session configurations that use virtual accounts.</span></span>

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