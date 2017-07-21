---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
contributor: ryanpu
title: Mejoras de Just Enough Administration (JEA)
ms.openlocfilehash: 2811b4deb3f4fca513791c7389ee5f9f877dbfe8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-to-just-enough-administration-jea"></a><span data-ttu-id="19de9-103">Mejoras de Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="19de9-103">Improvements to Just Enough Administration (JEA)</span></span>

## <a name="constrained-file-copy-tofrom-jea-endpoints"></a><span data-ttu-id="19de9-104">Copia restringida de archivos a o desde puntos de conexión JEA</span><span class="sxs-lookup"><span data-stu-id="19de9-104">Constrained file copy to/from JEA endpoints</span></span>

<span data-ttu-id="19de9-105">Ahora puede copiar remotamente archivos a o desde un punto de conexión JEA sin tener que preocuparse por si el usuario que se conecta puede copiar *cualquier otro* archivo del sistema.</span><span class="sxs-lookup"><span data-stu-id="19de9-105">You can now remotely copy files to/from a JEA endpoint and rest assured that the connecting user can't copy just *any* file on your system.</span></span>
<span data-ttu-id="19de9-106">Esto se puede realizar si configura el archivo PSSC para que monte una unidad de usuario para los usuarios que se conectan.</span><span class="sxs-lookup"><span data-stu-id="19de9-106">This is possible by configuring your PSSC file to mount a user drive for connecting users.</span></span>
<span data-ttu-id="19de9-107">La unidad de usuario es un PSDrive nuevo único para cada usuario que se conecta y que se mantiene conectado entre sesiones.</span><span class="sxs-lookup"><span data-stu-id="19de9-107">The user drive is a new PSDrive that is unique to each connecting user and persists across sessions.</span></span>
<span data-ttu-id="19de9-108">Cuando se usa Copy-Item para copiar archivos a o desde una sesión JEA, se restringe para que solo permita el acceso a la unidad de usuario.</span><span class="sxs-lookup"><span data-stu-id="19de9-108">When Copy-Item is used to copy files to or from a JEA session, it is constrained to only allow access to the user drive.</span></span>
<span data-ttu-id="19de9-109">Si intenta copiar archivos a cualquier otro PSDrive, se producirá un error.</span><span class="sxs-lookup"><span data-stu-id="19de9-109">Attempts to copy files to any other PSDrive will fail.</span></span>

<span data-ttu-id="19de9-110">Para configurar la unidad de usuario en el archivo de configuración de la sesión JEA, use los siguientes campos nuevos:</span><span class="sxs-lookup"><span data-stu-id="19de9-110">To set up the user drive in your JEA session configuration file, use the following new fields:</span></span>

```powershell
MountUserDrive = $true
UserDriveMaximumSize = 10485760    # 10 MB
```

<span data-ttu-id="19de9-111">La carpeta de respaldo de la unidad de usuario se creará en `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span><span class="sxs-lookup"><span data-stu-id="19de9-111">The folder backing the user drive will be created at `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\DOMAIN_USER`</span></span>

<span data-ttu-id="19de9-112">Para usar la unidad de usuario y copiar archivos a o desde un punto de conexión JEA configurado para exponer la unidad de usuario, use los parámetros `-ToSession` y `-FromSession` en Copy-Item.</span><span class="sxs-lookup"><span data-stu-id="19de9-112">To utilize the user drive and copy files to/from a JEA endpoint configured to expose the User drive, use the `-ToSession` and `-FromSession` parameters on Copy-Item.</span></span>

```powershell
# Connect to the JEA endpoint
$jeasession = New-PSSession -ComputerName 'srv01' -ConfigurationName 'UserDemo'

# Copy a file in the local folder to the remote machine.
# Note: you cannot specify the file name or subfolder on the remote machine. You must exactly type "User:"
Copy-Item -Path .\SampleFile.txt -Destination User: -ToSession $jeasession

# Copy the file back from the remote machine to your local machine
Copy-Item -Path User:\SampleFile.txt -Destination . -FromSession $jeasession
```

<span data-ttu-id="19de9-113">Después, puede escribir funciones personalizadas para procesar los datos almacenados en la unidad de usuario y ponerlas a disposición de los usuarios en el archivo de funcionalidad de roles.</span><span class="sxs-lookup"><span data-stu-id="19de9-113">You can then write custom functions to process the data stored in the user drive and make those available to users in your Role Capability file.</span></span>

## <a name="support-for-group-managed-service-accounts"></a><span data-ttu-id="19de9-114">Compatibilidad con las cuentas de servicio administradas de grupo</span><span class="sxs-lookup"><span data-stu-id="19de9-114">Support for Group Managed Service Accounts</span></span>

<span data-ttu-id="19de9-115">En algunos casos, puede que una tarea que tenga que realizar un usuario en una sesión JEA necesite acceso a recursos más allá de la máquina local.</span><span class="sxs-lookup"><span data-stu-id="19de9-115">In some cases, a task a user needs to perform in a JEA session may need to access resources beyond the local machine.</span></span>
<span data-ttu-id="19de9-116">Cuando una sesión JEA está configurada para usar una cuenta virtual, cualquier intento de tener acceso a esos recursos parecerá que proviene de la identidad de la máquina local, y no de la cuenta virtual ni del usuario conectado.</span><span class="sxs-lookup"><span data-stu-id="19de9-116">When a JEA session is configured to use a virtual account, any attempt to reach such resources will appear to come from the local machine's identity, not the virtual account or connected user.</span></span>
<span data-ttu-id="19de9-117">En TP5, hemos habilitado la compatibilidad para ejecutar JEA en el contexto de una [cuenta de servicio administrada de grupo](https://technet.microsoft.com/es-es/library/jj128431(v=ws.11\).aspx), lo que facilita el acceso a recursos de red mediante una identidad de dominio.</span><span class="sxs-lookup"><span data-stu-id="19de9-117">In TP5, we have enabled support for running JEA under the context of a [Group Managed Service Account](https://technet.microsoft.com/en-us/library/jj128431(v=ws.11\).aspx), making it much easier to access network resources by using a domain identity.</span></span>

<span data-ttu-id="19de9-118">Para configurar una sesión JEA para que se ejecute en una cuenta de gMSA, use la siguiente clave nueva en el archivo PSSC:</span><span class="sxs-lookup"><span data-stu-id="19de9-118">To configure a JEA session to run under a gMSA account, use the following new key in your PSSC file:</span></span>

```powershell
# Provide the name of your gMSA account here (don't include a trailing $)
# The local machine must be privileged to use this gMSA in Active Directory
GroupManagedServiceAccount = 'myGMSAforJEA'

# You cannot configure a JEA endpoint to use both a gMSA and virtual account
# You can leave the RunAsVirtualAccount field commented out or explicitly set it to false
RunAsVirtualAccount = $false
```

> <span data-ttu-id="19de9-119">**Nota:** Las cuentas de servicio administradas de grupo no permiten el ámbito limitado o de aislamiento de las cuentas virtuales.</span><span class="sxs-lookup"><span data-stu-id="19de9-119">**Note:** Group Managed Service Accounts do not afford the isolation or limited scope of virtual accounts.</span></span>
> <span data-ttu-id="19de9-120">Cada usuario que se conecta compartirá la misma identidad de gMSA, que puede tener permisos en toda la empresa.</span><span class="sxs-lookup"><span data-stu-id="19de9-120">Every connecting user will share the same gMSA identity, which may have permissions across your entire enterprise.</span></span>
> <span data-ttu-id="19de9-121">Tenga mucho cuidado al seleccionar la opción de usar una gMSA; siempre son preferibles las cuentas virtuales que están limitadas a la máquina local cuando sea posible.</span><span class="sxs-lookup"><span data-stu-id="19de9-121">Be very careful when selecting to use a gMSA, and always prefer virtual accounts which are limited to the local machine when possible.</span></span>

## <a name="conditional-access-policies"></a><span data-ttu-id="19de9-122">Directivas de acceso condicional</span><span class="sxs-lookup"><span data-stu-id="19de9-122">Conditional access policies</span></span>

<span data-ttu-id="19de9-123">JEA es ideal para limitar lo que alguien puede hacer cuando está conectado a un sistema para administrarlo, pero ¿qué sucede si también quiere limitar *el momento* en que alguien puede usar JEA?</span><span class="sxs-lookup"><span data-stu-id="19de9-123">JEA is great at limiting what someone can do when they've connected to a system to manage it, but what if you also want to limit *when* someone can use JEA?</span></span>
<span data-ttu-id="19de9-124">Hemos agregado opciones de configuración en los archivos de configuración de sesión (.pssc) para permitirle especificar grupos de seguridad a los que debe pertenecer un usuario para establecer una sesión JEA.</span><span class="sxs-lookup"><span data-stu-id="19de9-124">We have added configuration options into the session configuration files (.pssc) to let you specify security groups to which a user must belong in order to establish a JEA session.</span></span>
<span data-ttu-id="19de9-125">Esto puede resultar especialmente útil si tiene un sistema Just In Time (JIT) en su entorno y quiere que sus usuarios eleven los privilegios antes de acceder a un punto de conexión JEA con privilegios elevados.</span><span class="sxs-lookup"><span data-stu-id="19de9-125">This can be particularly helpful if you have a Just In Time (JIT) system in your environment, and want to make your users elevate their privileges before accessing a highly-privileged JEA endpoint.</span></span>

<span data-ttu-id="19de9-126">El nuevo campo *RequiredGroups* en el archivo PSSC le permite especificar la lógica para determinar si un usuario puede conectarse a JEA.</span><span class="sxs-lookup"><span data-stu-id="19de9-126">The new *RequiredGroups* field in the PSSC file allows you to specify the logic to determine if a user can connect to JEA.</span></span>
<span data-ttu-id="19de9-127">Consiste en especificar una tabla hash (opcionalmente anidada) que use las claves "And" y "Or" para construir las reglas.</span><span class="sxs-lookup"><span data-stu-id="19de9-127">It consists of specifying a hashtable (optionally nested) that uses the 'And' and 'Or' keys to construct your rules.</span></span>
<span data-ttu-id="19de9-128">Estos son algunos ejemplos sobre cómo sacar provecho de este campo:</span><span class="sxs-lookup"><span data-stu-id="19de9-128">Here are some examples of how to leverage this field:</span></span>

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

## <a name="fixed-virtual-accounts-are-now-supported-on-windows-server-2008-r2"></a><span data-ttu-id="19de9-129">Solucionado: las cuentas virtuales ahora son compatibles con Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="19de9-129">Fixed: Virtual accounts are now supported on Windows Server 2008 R2</span></span>
<span data-ttu-id="19de9-130">En WMF 5.1, ahora puede usar cuentas virtuales en Windows Server 2008 R2, lo que permite configuraciones coherentes y paridad de funcionalidades en Windows Server 2008 R2 - 2016.</span><span class="sxs-lookup"><span data-stu-id="19de9-130">In WMF 5.1, you are now able to use virtual accounts on Windows Server 2008 R2, enabling consistent configurations and feature parity across Windows Server 2008 R2 - 2016.</span></span>
<span data-ttu-id="19de9-131">Las cuentas virtuales siguen sin admitirse al usar JEA en Windows 7.</span><span class="sxs-lookup"><span data-stu-id="19de9-131">Virtual accounts remain unsupported when using JEA on Windows 7.</span></span>

