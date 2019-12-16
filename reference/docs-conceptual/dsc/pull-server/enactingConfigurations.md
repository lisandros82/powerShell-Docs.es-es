---
ms.date: 10/16/2017
keywords: dsc,powershell,configuration,setup
title: Establecer configuraciones
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953652"
---
# <a name="enacting-configurations"></a>Establecer configuraciones

>Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Hay dos maneras de establecer las configuraciones de la configuración de estado deseado (DSC) de PowerShell: el modo de inserción y el modo de extracción.

## <a name="push-mode"></a>Modo de inserción

![Modo de inserción](../images/pushModel.png "Cómo funciona el modo de inserción")

El modo de inserción se refiere a un usuario que aplica activamente una configuración a un nodo de destino mediante una llamada al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

Después de crear y compilar una configuración, puede establecerla en el modo de inserción con una llamada al cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration), estableciendo el parámetro -Path del cmdlet en la ruta de acceso donde se encuentra el MOF de configuración.
Por ejemplo, si el MOF de configuración está ubicado en `C:\DSC\Configurations\localhost.mof`, se aplicaría a la máquina local con el comando siguiente: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Nota__: De forma predeterminada, DSC ejecuta una configuración como un trabajo en segundo plano. Para ejecutar la configuración de forma interactiva, llame a [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) con el parámetro __-Wait__.

## <a name="pull-mode"></a>Modo de extracción

![Modo de extracción](../images/pullModel.png "Cómo funciona el modo de extracción")

En el modo de extracción, los clientes de extracción se configuran para obtener sus configuraciones de estado deseado desde un servicio de extracción remoto.
Del mismo modo, el servicio de extracción se ha configurado para hospedar el servicio de DSC y se ha aprovisionado con las configuraciones y los recursos que necesitan los clientes de extracción.
Cada uno de los clientes de extracción tiene un evento programado que realiza una comprobación periódica del cumplimiento de la configuración del nodo.
Cuando el evento se desencadena por primera vez, el administrador de configuración local (LCM) del cliente de extracción realiza una solicitud al servicio de extracción para obtener la configuración especificada en el LCM.
Si dicha configuración existe en el servicio de extracción y pasa las comprobaciones de validación iniciales, la configuración se descarga en el cliente de extracción, donde a continuación el LCM la ejecuta.

El LCM comprueba que el cliente es conforme con la configuración a intervalos regulares especificados por la propiedad **ConfigurationModeFrequencyMins** del LCM.
El LCM busca configuraciones actualizadas en el servicio de extracción a intervalos regulares especificados por la propiedad **RefreshModeFrequency** del LCM.
Para obtener información sobre la configuración del LCM, consulte [Configuración del administrador de configuración local](../managing-nodes/metaConfig.md).

La solución recomendada para hospedar un servicio de extracción es [Azure Automation](https://azure.microsoft.com/services/automation/), el servicio en la nube de DSC.
Esta solución hospedada ofrece administración de gráficos, informes y administración centralizada.

Para más información sobre la configuración de un servicio de extracción de Windows Server, consulte [Configuración de un servidor de extracción web de DSC](pullServer.md).
Sin embargo, debe tener en cuenta que esta implementación tiene características limitadas y requiere que haga cierta integración de manera manual.

En los temas siguientes se explican los clientes y el servicio de extracción:

- [Información general de DSC de Azure Automation](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Configuración de un servidor de extracción SMB](pullServerSMB.md)
- [Configuración de un cliente de extracción](pullClientConfigID.md)
