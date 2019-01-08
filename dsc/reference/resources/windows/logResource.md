---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Log
ms.openlocfilehash: 1f94a2d847a4ef63f81e2fb83d1a0f76f5677b09
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048028"
---
# <a name="dsc-log-resource"></a>Recurso de DSC Log

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0_

El recurso __Log__ de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para escribir mensajes en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> De forma predeterminada, solo están habilitados los registros operativos para DSC. Para que el registro analítico esté disponible o visible, es necesario habilitarlo. Para más información, consulte [¿Dónde se encuentran los registros de eventos de DSC?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs)

## <a name="properties"></a>Propiedades

| Propiedad | Descripción |
| --- | --- |
| Mensaje| Indica el mensaje que quiere escribir en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se escriba este mensaje de registro. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es **ResourceName** y su tipo es **ResourceType**, la sintaxis para usar esta propiedad es `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo incluir un mensaje en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.

> [!NOTE]
> Si ejecuta [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) con este recurso configurado, siempre devolverá **$false**.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```
