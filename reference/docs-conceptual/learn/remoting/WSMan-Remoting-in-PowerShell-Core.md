---
title: Comunicación remota de WS-Management (WSMan) en PowerShell Core
description: Comunicación remota en PowerShell Core con WSMan
ms.date: 08/06/2018
ms.openlocfilehash: e5f00128bc8ebc1b432cc77a5896a9e09d684109
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058886"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="5b7af-103">Comunicación remota de WS-Management (WSMan) en PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5b7af-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="5b7af-104">Instrucciones para crear un punto de conexión de comunicación remota</span><span class="sxs-lookup"><span data-stu-id="5b7af-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="5b7af-105">El paquete de PowerShell Core para Windows incluye un complemento WinRM (`pwrshplugin.dll`) y un script de instalación (`Install-PowerShellRemoting.ps1`) en `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="5b7af-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="5b7af-106">Estos archivos permiten que PowerShell acepte conexiones remotas entrantes de PowerShell cuando se especifica su punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="5b7af-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="5b7af-107">Motivaciones</span><span class="sxs-lookup"><span data-stu-id="5b7af-107">Motivation</span></span>

<span data-ttu-id="5b7af-108">Una instalación de PowerShell puede establecer sesiones de PowerShell en equipos remotos a través `New-PSSession` y `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="5b7af-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="5b7af-109">Para permitirle aceptar conexiones remotas entrantes de PowerShell, el usuario debe crear un punto de conexión de comunicación remota de WinRM.</span><span class="sxs-lookup"><span data-stu-id="5b7af-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="5b7af-110">Se trata de un escenario de participación explícito, en el que el usuario ejecuta Install-PowerShellRemoting.ps1 para crear el punto de conexión de WinRM.</span><span class="sxs-lookup"><span data-stu-id="5b7af-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="5b7af-111">El script de instalación es una solución a corto plazo, hasta que agreguemos funcionalidad adicional a `Enable-PSRemoting` para realizar la misma acción.</span><span class="sxs-lookup"><span data-stu-id="5b7af-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="5b7af-112">Para más información, vea problema [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="5b7af-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="5b7af-113">Acciones de script</span><span class="sxs-lookup"><span data-stu-id="5b7af-113">Script Actions</span></span>

<span data-ttu-id="5b7af-114">El script</span><span class="sxs-lookup"><span data-stu-id="5b7af-114">The script</span></span>

1. <span data-ttu-id="5b7af-115">Crea un directorio para el complemento en `$env:windir\System32\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="5b7af-115">Creates a directory for the plug-in within `$env:windir\System32\PowerShell`</span></span>
1. <span data-ttu-id="5b7af-116">Copia pwrshplugin.dll en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="5b7af-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="5b7af-117">Genera un archivo de configuración.</span><span class="sxs-lookup"><span data-stu-id="5b7af-117">Generates a configuration file</span></span>
1. <span data-ttu-id="5b7af-118">Registra el complemento con WinRM.</span><span class="sxs-lookup"><span data-stu-id="5b7af-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="5b7af-119">Registro</span><span class="sxs-lookup"><span data-stu-id="5b7af-119">Registration</span></span>

<span data-ttu-id="5b7af-120">El script debe ejecutarse en una sesión de PowerShell de nivel de administrador y se ejecuta en dos modos.</span><span class="sxs-lookup"><span data-stu-id="5b7af-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="5b7af-121">Ejecutado por la instancia de PowerShell que registrará</span><span class="sxs-lookup"><span data-stu-id="5b7af-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="5b7af-122">Ejecutado por otra instancia de PowerShell en nombre de la instancia que registrará</span><span class="sxs-lookup"><span data-stu-id="5b7af-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="5b7af-123">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5b7af-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="5b7af-124">**NOTA**: El script de registro de comunicación remota reiniciará WinRM, por lo que todas las sesiones PSRP existentes se cerrarán inmediatamente tras ejecutar el script.</span><span class="sxs-lookup"><span data-stu-id="5b7af-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="5b7af-125">Si se ejecuta durante una sesión remota, la conexión finalizará.</span><span class="sxs-lookup"><span data-stu-id="5b7af-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="5b7af-126">Cómo conectarse al nuevo punto de conexión</span><span class="sxs-lookup"><span data-stu-id="5b7af-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="5b7af-127">Cree una sesión de PowerShell en el nuevo punto de conexión de PowerShell. Para ello, especifique `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="5b7af-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="5b7af-128">Para conectarse a la instancia de PowerShell en el ejemplo anterior, use una de las opciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="5b7af-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="5b7af-129">Tenga en cuenta que las invocaciones `New-PSSession` y `Enter-PSSession` que no especifiquen `-ConfigurationName` tendrán como destino el punto de conexión predeterminado de PowerShell, `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="5b7af-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>