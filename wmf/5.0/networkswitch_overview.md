---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 4868cf657f678ee43a6c92d5ee286e9ddb490964
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="933b4-102">Administración de conmutadores de red con PowerShell</span><span class="sxs-lookup"><span data-stu-id="933b4-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="933b4-103">El cmdlet **Get-NetworkSwitchEthernetPort** devuelve ahora la siguiente información adicional con las instancias:</span><span class="sxs-lookup"><span data-stu-id="933b4-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="933b4-104">IPAddress: dirección IP asociada con el puerto.</span><span class="sxs-lookup"><span data-stu-id="933b4-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="933b4-105">PortMode: modo de puerto (acceso, ruta o tronco).</span><span class="sxs-lookup"><span data-stu-id="933b4-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="933b4-106">AccessVLAN: identificador de la VLAN asociada con este puerto en el modo de acceso.</span><span class="sxs-lookup"><span data-stu-id="933b4-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="933b4-107">TrunkedVLANList: lista de identificadores de las VLAN asociadas con este puerto en el modo de tronco.</span><span class="sxs-lookup"><span data-stu-id="933b4-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="933b4-108">Administración de modificadores de red fundamentales con Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="933b4-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="933b4-109">Los cmdlet NetworkSwitch, introducidos en WMF 5.0, permiten aplicar la configuración de modificador, LAN virtual (VLAN) y básica del puerto del modificador de red de capa 2 a los modificadores de red certificados con el logotipo de Windows Server 2012 R2.</span><span class="sxs-lookup"><span data-stu-id="933b4-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="933b4-110">Microsoft mantiene su compromiso por admitir la visión de la [capa de abstracción del centro de datos](http://technet.microsoft.com/cloud/dal.aspx) (DAL) y para mostrar el valor para nuestros clientes y socios en este espacio.</span><span class="sxs-lookup"><span data-stu-id="933b4-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="933b4-111">Con estos cmdlets puede hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="933b4-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="933b4-112">Configuración global del modificador, como:</span><span class="sxs-lookup"><span data-stu-id="933b4-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="933b4-113">Establecer el nombre de host.</span><span class="sxs-lookup"><span data-stu-id="933b4-113">Set host name</span></span>
    - <span data-ttu-id="933b4-114">Establecer el banner del modificador.</span><span class="sxs-lookup"><span data-stu-id="933b4-114">Set switch banner</span></span>
    - <span data-ttu-id="933b4-115">Mantener la configuración.</span><span class="sxs-lookup"><span data-stu-id="933b4-115">Persist configuration</span></span>
    - <span data-ttu-id="933b4-116">Habilitar o deshabilitar una característica.</span><span class="sxs-lookup"><span data-stu-id="933b4-116">Enable or disable feature</span></span>

- <span data-ttu-id="933b4-117">Configuración de VLAN:</span><span class="sxs-lookup"><span data-stu-id="933b4-117">VLAN configuration:</span></span>
    - <span data-ttu-id="933b4-118">Crear o quitar la VLAN.</span><span class="sxs-lookup"><span data-stu-id="933b4-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="933b4-119">Habilitar o deshabilitar la VLAN.</span><span class="sxs-lookup"><span data-stu-id="933b4-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="933b4-120">Enumerar la VLAN.</span><span class="sxs-lookup"><span data-stu-id="933b4-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="933b4-121">Establecer el nombre descriptivo de una VLAN.</span><span class="sxs-lookup"><span data-stu-id="933b4-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="933b4-122">Configuración de puerto de la capa 2:</span><span class="sxs-lookup"><span data-stu-id="933b4-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="933b4-123">Enumerar los puertos.</span><span class="sxs-lookup"><span data-stu-id="933b4-123">Enumerate ports</span></span>
    - <span data-ttu-id="933b4-124">Habilitar o deshabilitar los puertos.</span><span class="sxs-lookup"><span data-stu-id="933b4-124">Enable or disable ports</span></span>
    - <span data-ttu-id="933b4-125">Establecer los modos de puerto y sus propiedades.</span><span class="sxs-lookup"><span data-stu-id="933b4-125">Set port modes and properties</span></span>
    - <span data-ttu-id="933b4-126">Agregar o asociar la VLAN al modo de tronco o acceso en el puerto.</span><span class="sxs-lookup"><span data-stu-id="933b4-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="933b4-127">Empiece a explorar buscando todos los cmdlets NetworkSwitch.</span><span class="sxs-lookup"><span data-stu-id="933b4-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

<span data-ttu-id="933b4-128">Existe más información disponible en la entrada de blog del anuncio de WMF 5.0 Preview de Jeffrey Snover: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="933b4-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>

