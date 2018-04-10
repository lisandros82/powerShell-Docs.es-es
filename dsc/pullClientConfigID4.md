---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Configuración de un cliente de extracción mediante un id. de configuración en PowerShell 4.0
ms.openlocfilehash: 7074d842b7b99ef3fb6498b6dbc1e561b14caf16
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
---
# <a name="setting-up-a-pull-client-using-configuration-id-in-powershell-40"></a><span data-ttu-id="79df3-103">Configuración de un cliente de extracción mediante un id. de configuración en PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="79df3-103">Setting up a pull client using configuration ID in PowerShell 4.0</span></span>

><span data-ttu-id="79df3-104">Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="79df3-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="79df3-105">Es necesario indicar a cada nodo de destino que debe usar el modo de extracción y se le debe facilitar la dirección URL donde puede establecer contacto con el servidor de extracción para obtener las configuraciones.</span><span class="sxs-lookup"><span data-stu-id="79df3-105">Each target node has to be told to use pull mode and given the URL where it can contact the pull server to get configurations.</span></span> <span data-ttu-id="79df3-106">Para ello, tendrá que configurar el administrador de configuración local (LCM) con la información necesaria.</span><span class="sxs-lookup"><span data-stu-id="79df3-106">To do this, you have to configure the Local Configuration Manager (LCM) with the necessary information.</span></span> <span data-ttu-id="79df3-107">Para configurar el LCM, debe crear un tipo especial de configuración conocida como "metaconfiguración".</span><span class="sxs-lookup"><span data-stu-id="79df3-107">To configure the LCM, you create a special type of configuration known as a "metaconfiguration".</span></span> <span data-ttu-id="79df3-108">Para más información sobre cómo configurar el LCM, consulte [Administrador de configuración local de configuración de estado deseado de Windows PowerShell 4.0](metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="79df3-108">For more information about configuring the LCM, see [Windows PowerShell 4.0 Desired State Configuration Local Configuration Manager](metaConfig4.md)</span></span>

<span data-ttu-id="79df3-109">El script siguiente configura el LCM para que extraiga configuraciones de un servidor denominado "PullServer":</span><span class="sxs-lookup"><span data-stu-id="79df3-109">The following script configures the LCM to pull configurations from a server named "PullServer":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "WebDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "http://PullServer:8080/PSDSCPullServer/PSDSCPullServer.svc"; AllowUnsecureConnection = “TRUE”}
    }
}
SimpleMetaConfigurationForPull -Output "."
```

<span data-ttu-id="79df3-110">En el script, **DownloadManagerCustomData** pasa la dirección URL del servidor de incorporación de cambios y (en este ejemplo) permite una conexión no segura.</span><span class="sxs-lookup"><span data-stu-id="79df3-110">In the script, **DownloadManagerCustomData** passes the URL of the pull server and (for this example) allows an unsecured connection.</span></span>

<span data-ttu-id="79df3-111">Después de que se ejecute este script, se crea una nueva carpeta de salida denominada **SimpleMetaConfigurationForPull** y se coloca un archivo MOF de metaconfiguración en ella.</span><span class="sxs-lookup"><span data-stu-id="79df3-111">After this script runs, it creates a new output folder called **SimpleMetaConfigurationForPull** and puts a metaconfiguration MOF file there.</span></span>

<span data-ttu-id="79df3-112">Para aplicar la configuración, utilice **Set-DscLocalConfigurationManager** con parámetros para **ComputerName** (utilice "localhost") y **Path** (la ruta de acceso a la ubicación del archivo de localhost.meta.mof del nodo de destino).</span><span class="sxs-lookup"><span data-stu-id="79df3-112">To apply the configuration, use **Set-DscLocalConfigurationManager** with parameters for **ComputerName** (use “localhost”) and **Path** (the path to the location of the target node’s localhost.meta.mof file).</span></span> <span data-ttu-id="79df3-113">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="79df3-113">For example:</span></span>
```powershell
Set-DSCLocalConfigurationManager –ComputerName localhost –Path . –Verbose.
```

## <a name="configuration-id"></a><span data-ttu-id="79df3-114">Id. de configuración</span><span class="sxs-lookup"><span data-stu-id="79df3-114">Configuration ID</span></span>
<span data-ttu-id="79df3-115">El script establece la propiedad **ConfigurationID** del LCM en un GUID que se había creado anteriormente para este fin (puede crear un GUID mediante el cmdlet **New-Guid**).</span><span class="sxs-lookup"><span data-stu-id="79df3-115">The script sets the **ConfigurationID** property of the LCM to a GUID that had been previously created for this purpose (you can create a GUID by using the **New-Guid** cmdlet).</span></span> <span data-ttu-id="79df3-116">La propiedad **ConfigurationID** es lo que usa el LCM para buscar la configuración adecuada en el servidor de incorporación de cambios.</span><span class="sxs-lookup"><span data-stu-id="79df3-116">The **ConfigurationID** is what the LCM uses to find the appropriate configuration on the pull server.</span></span> <span data-ttu-id="79df3-117">El archivo MOF de configuración del servidor de incorporación de cambios debe denominarse `ConfigurationID.mof`, donde *ConfigurationID* es el valor de la propiedad **ConfigurationID** del LCM del nodo de destino.</span><span class="sxs-lookup"><span data-stu-id="79df3-117">The configuration MOF file on the pull server must be named `ConfigurationID.mof`, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span>

## <a name="pulling-from-an-smb-server"></a><span data-ttu-id="79df3-118">Incorporación de cambios de un servidor SMB</span><span class="sxs-lookup"><span data-stu-id="79df3-118">Pulling from an SMB server</span></span>

<span data-ttu-id="79df3-119">Si el servidor de incorporación de cambios está configurado como un recurso compartido de archivos SMB, en lugar de un servicio web, especifique **DscFileDownloadManager** en lugar de **WebDownLoadManager**.</span><span class="sxs-lookup"><span data-stu-id="79df3-119">If the pull server is set up as an SMB file share, rather than a web service, you specify the **DscFileDownloadManager** rather than the **WebDownLoadManager**.</span></span>
<span data-ttu-id="79df3-120">**DscFileDownloadManager** toma una propiedad **SourcePath** en lugar de **ServerUrl**.</span><span class="sxs-lookup"><span data-stu-id="79df3-120">The **DscFileDownloadManager** takes a **SourcePath** property instead of **ServerUrl**.</span></span> <span data-ttu-id="79df3-121">El script siguiente configura el LCM para que extraiga configuraciones de un recurso compartido SMB denominado "SmbDscShare" en un servidor denominado "CONTOSO-SERVER":</span><span class="sxs-lookup"><span data-stu-id="79df3-121">The following script configures the LCM to pull configurations from an SMB share named "SmbDscShare" on a server named "CONTOSO-SERVER":</span></span>

```powershell
Configuration SimpleMetaConfigurationForPull
{
    LocalConfigurationManager
    {
        ConfigurationID = "1C707B86-EF8E-4C29-B7C1-34DA2190AE24";
        RefreshMode = "PULL";
        DownloadManagerName = "DscFileDownloadManager";
        RebootNodeIfNeeded = $true;
        RefreshFrequencyMins = 30;
        ConfigurationModeFrequencyMins = 30;
        ConfigurationMode = "ApplyAndAutoCorrect";
        DownloadManagerCustomData = @{ServerUrl = "\\CONTOSO-SERVER\SmbDscShare"}
    }
}
SimpleMetaConfigurationForPull -Output "."
```

## <a name="see-also"></a><span data-ttu-id="79df3-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="79df3-122">See Also</span></span>

- [<span data-ttu-id="79df3-123">Configuración de un servidor de extracción web de DSC</span><span class="sxs-lookup"><span data-stu-id="79df3-123">Setting up a DSC web pull server</span></span>](pullServer.md)
- [<span data-ttu-id="79df3-124">Configuración de un servidor de extracción SMB de DSC</span><span class="sxs-lookup"><span data-stu-id="79df3-124">Setting up a DSC SMB pull server</span></span>](pullServerSMB.md)