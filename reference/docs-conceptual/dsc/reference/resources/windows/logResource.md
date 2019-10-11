---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Log
ms.openlocfilehash: a1b7bf44fbaf36a3adaf0666e9f0a754fa3f6ee1
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954672"
---
# <a name="dsc-log-resource"></a>Recurso de DSC Log

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.x

El recurso **Log** de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para escribir mensajes en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.

## <a name="syntax"></a>Sintaxis

```Syntax
Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

> [!NOTE]
> De forma predeterminada, solo están habilitados los registros operativos para DSC. Para que el registro analítico esté disponible o visible, es necesario habilitarlo. Para más información, consulte [¿Dónde se encuentran los registros de eventos de DSC?](../../../troubleshooting/troubleshooting.md#where-are-dsc-event-logs)

## <a name="properties"></a>Propiedades

|Propiedad |Descripción |
|---|---|
|Mensaje |Indica el mensaje que quiere escribir en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows. |

## <a name="common-properties"></a>Propiedades comunes

|Propiedad |Descripción |
|---|---|
|DependsOn |Indica que la configuración de otro recurso debe ejecutarse antes de que se configure este recurso. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es ResourceName y su tipo es ResourceType, la sintaxis para usar esta propiedad es `DependsOn = "[ResourceType]ResourceName"`. |
|PsDscRunAsCredential |Establece la credencial con la que se ejecutará todo el recurso. |

> [!NOTE]
> Se ha agregado la propiedad común **PsDscRunAsCredential** en WMF 5.0 para permitir la ejecución de cualquier recurso de DSC en el contexto de otras credenciales. Para obtener más información, vea [Uso de las credenciales con recursos de DSC](../../../configurations/runasuser.md).

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