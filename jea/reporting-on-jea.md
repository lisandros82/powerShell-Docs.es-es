---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Generación de informes en JEA"
ms.technology: powershell
ms.openlocfilehash: 3e7bd2755281f491bba8a905df018fb2e1cac6ff
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: es-ES
---
# <a name="reporting-on-jea"></a><span data-ttu-id="bd9a8-103">Generación de informes en JEA</span><span class="sxs-lookup"><span data-stu-id="bd9a8-103">Reporting on JEA</span></span>
<span data-ttu-id="bd9a8-104">El registro y la auditoría son muy importantes, ya que JEA permite que usuarios sin privilegios se ejecuten en un contexto con privilegios.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-104">Because JEA allows non-privileged users to run in a privileged context, logging and auditing are extremely important.</span></span>
<span data-ttu-id="bd9a8-105">En esta sección veremos las herramientas que puede usar como ayuda para el registro y la creación de informes.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-105">In this section, we'll run through the tools you can use to help you with logging and reporting.</span></span>

## <a name="reporting-on-jea-actions"></a><span data-ttu-id="bd9a8-106">Acciones de generación de informes en JEA</span><span class="sxs-lookup"><span data-stu-id="bd9a8-106">Reporting on JEA Actions</span></span>
### <a name="over-the-shoulder-transcription"></a><span data-ttu-id="bd9a8-107">Transcripción con consentimiento temporal</span><span class="sxs-lookup"><span data-stu-id="bd9a8-107">Over-the-Shoulder Transcription</span></span>
<span data-ttu-id="bd9a8-108">Una de las formas más rápidas de obtener un resumen de lo que ocurre en una sesión de PowerShell es mirar por encima del hombro de la persona que está escribiendo.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-108">One of the quickest ways to get a summary of what's happening in a PowerShell session is to look over the shoulder of the person typing.</span></span>
<span data-ttu-id="bd9a8-109">De este modo ve los comandos y la salida de los comandos y comprueba que todo está bien.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-109">You see their commands, the output of those commands, and all is well.</span></span>
<span data-ttu-id="bd9a8-110">O no, pero al menos lo sabe.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-110">Or it's not, but at least you'll know.</span></span>
<span data-ttu-id="bd9a8-111">La transcripción de PowerShell está diseñada para proporcionarle una vista similar a posteriori.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-111">PowerShell transcription is designed to give you a similar view after the fact.</span></span>

<span data-ttu-id="bd9a8-112">Cuando se usa el campo "TranscriptDirectory" en la configuración de sesión, PowerShell graba automáticamente una transcripción de todas las acciones realizadas en una sesión determinada.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-112">When using the "TranscriptDirectory" field in your Session Configuration, PowerShell will automatically record a transcript of all actions taken in a given session.</span></span>
<span data-ttu-id="bd9a8-113">Verá transcripciones de sus sesiones en el documento que se encuentra aquí: "$env:ProgramData\JEAConfiguration\Transcripts".</span><span class="sxs-lookup"><span data-stu-id="bd9a8-113">You can find transcripts from your sessions in this document here: "$env:ProgramData\JEAConfiguration\Transcripts"</span></span>

<span data-ttu-id="bd9a8-114">Como puede imaginar, la transcripción registra información sobre el usuario conectado, el usuario de ejecución, los comandos que se ejecutaron en la sesión, etc.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-114">As you can tell, the transcript records information about the "Connected" user, the "Run As" user, the commands run in the session, and more.</span></span>
<span data-ttu-id="bd9a8-115">Para obtener más información sobre la transcripción de PowerShell, consulte [esta entrada de blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span><span class="sxs-lookup"><span data-stu-id="bd9a8-115">For more information about PowerShell transcription, check out [this blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>

### <a name="powershell-event-logs"></a><span data-ttu-id="bd9a8-116">Registros de eventos de PowerShell</span><span class="sxs-lookup"><span data-stu-id="bd9a8-116">PowerShell Event Logs</span></span>
<span data-ttu-id="bd9a8-117">Una vez que ha activado el registro de módulos, también se registran todas las acciones de PowerShell en los registros de eventos de Windows normales.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-117">When you have module logging turned on, all PowerShell actions are also recorded in regular Windows Event logs.</span></span>
<span data-ttu-id="bd9a8-118">Esto es ligeramente más complicado que las transcripciones, pero el nivel de detalle que ofrece puede resultarle útil.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-118">This is slightly messier to deal with when compared to transcripts, but the level of detail it gives you can be useful.</span></span>

<span data-ttu-id="bd9a8-119">En el registro operativo "PowerShell", el identificador de evento 4104 registrará cada comando que se invoque si ha habilitado el registro del módulos.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-119">In the "PowerShell" operational log, Event ID 4104 will record each command invoked if you have enabled module logging.</span></span>

### <a name="other-event-logs"></a><span data-ttu-id="bd9a8-120">Otros registros de eventos</span><span class="sxs-lookup"><span data-stu-id="bd9a8-120">Other Event Logs</span></span>
<span data-ttu-id="bd9a8-121">A diferencia de los registros y las transcripciones de PowerShell, otros mecanismos de registro no capturan al "usuario conectado".</span><span class="sxs-lookup"><span data-stu-id="bd9a8-121">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the "Connected User".</span></span>
<span data-ttu-id="bd9a8-122">Deberá establecer alguna correlación entre los demás registros y los registros de PowerShell para que las acciones realizadas coincidan.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-122">You will need to do some correlation between other logs and PowerShell logs to match up actions taken.</span></span>

<span data-ttu-id="bd9a8-123">En el registro operativo "Administración remota de Windows", el identificador de evento 193 registrará el SID y el nombre del usuario que se conecta, así como el SID de la cuenta virtual de ejecución para ayudar a esta correlación.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-123">In the "Windows Remote Management" operational log, Event ID 193 will record the Connecting User's SID and Name, as well as the RunAs Virtual Account's SID to assist with this correlation.</span></span>
<span data-ttu-id="bd9a8-124">Probablemente habrá observado que el nombre de la cuenta virtual de ejecución incluye al final el dominio y el nombre del usuario que se conecta.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-124">You may have also noticed that the name of the RunAs Virtual Account includes the connecting user's domain and username at the end.</span></span>

## <a name="reporting-on-jea-configuration"></a><span data-ttu-id="bd9a8-125">Configuración de la generación de informes en JEA</span><span class="sxs-lookup"><span data-stu-id="bd9a8-125">Reporting on JEA Configuration</span></span>
### <a name="get-pssessionconfiguration"></a><span data-ttu-id="bd9a8-126">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bd9a8-126">Get-PSSessionConfiguration</span></span>
<span data-ttu-id="bd9a8-127">Para realizar informes sobre el estado de su entorno, es importante saber cuántos puntos de conexión de JEA ha configurado en la máquina.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-127">In order to accurately report on the state of your environment, it's important to know how many JEA endpoints you have set up on your machine.</span></span>
<span data-ttu-id="bd9a8-128">`Get-PSSessionConfiguration` hace precisamente eso.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-128">`Get-PSSessionConfiguration` does just that.</span></span>

### <a name="get-pssessioncapability"></a><span data-ttu-id="bd9a8-129">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="bd9a8-129">Get-PSSessionCapability</span></span>
<span data-ttu-id="bd9a8-130">La realización manual de informes sobre las funcionalidades de un usuario dado a través de un punto de conexión de JEA puede ser bastante compleja.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-130">Manually reporting on the capabilities of any given user through a JEA endpoint can be quite complex.</span></span>
<span data-ttu-id="bd9a8-131">Probablemente tendría que inspeccionar varias funcionalidades de rol.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-131">You would potentially need to inspect several role capabilities.</span></span>
<span data-ttu-id="bd9a8-132">Por suerte, el cmdlet "Get-PSSessionCapability" lo hace automáticamente.</span><span class="sxs-lookup"><span data-stu-id="bd9a8-132">Fortunately, the "Get-PSSessionCapability" cmdlet does this.</span></span>

<span data-ttu-id="bd9a8-133">Para probarlo, ejecute el comando siguiente desde un símbolo del sistema de administrador de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="bd9a8-133">To test this out, run the following command from an administrator PowerShell prompt:</span></span>
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```

