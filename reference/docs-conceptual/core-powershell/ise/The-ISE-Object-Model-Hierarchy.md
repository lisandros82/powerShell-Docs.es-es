---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "La jerarquía del modelo de objetos de ISE"
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a>La jerarquía del modelo de objetos de ISE
En este tema se muestra la jerarquía de objetos que forman parte del Entorno de scripting integrado (ISE) de Windows PowerShell. Windows PowerShell ISE se incluye en Windows PowerShell 3.0 y Windows PowerShell 4.0. Haga clic en un objeto para ir a la documentación de referencia de la clase que define el objeto.

## <a name="psise-object"></a>Objeto $psISE

El objeto **$psISE** es el [objeto raíz](The-ObjectModelRoot-Object.md) de la jerarquía de objetos de Windows PowerShell ISE.
Ubicado en el nivel superior, este objeto hace que estén disponibles para scripting los objetos siguientes:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

El objeto **$psISE.CurrentFile** es una instancia de la clase [ISEFile](The-ISEFile-Object.md).

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

El objeto **$psISE.CurrentPowerShellTab** es una instancia de la clase [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

El objeto **$psISE.CurrentVisibleHorizontalTool** es una instancia de la clase [ISEAddOnTool](The-ISEAddOnTool-Object.md).
Representa la herramienta de complemento instalada que actualmente está acoplada al borde superior de la ventana de Windows PowerShell ISE.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

El objeto **$psISE.CurrentVisibleHorizontalTool** es una instancia de la clase [ISEAddOnTool](The-ISEAddOnTool-Object.md).
Representa la herramienta de complemento instalada que actualmente está acoplada al borde derecho de la ventana de Windows PowerShell ISE.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

El objeto **$psISE.Options** es una instancia de la clase [ISEOptions](The-ISEOptions-Object.md).
El objeto ISEOptions representa distintas configuraciones de Windows PowerShell ISE.
Es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

El objeto **$psISE.PowerShellTabs** es una instancia de la clase [PowerShellTabCollection](The-PowerShellTabCollection-Object.md).
Es una colección de todas las pestañas de PowerShell abiertas actualmente que representan los entornos de ejecución de Windows PowerShell disponibles en el equipo local o en equipos remotos conectados. Cada miembro de la colección es una instancia de la clase [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="see-also"></a>Véase también
- [El modelo de objetos de scripting de ISE de Windows PowerShell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Referencia del modelo de objetos de ISE de Windows PowerShell](Windows-PowerShell-ISE-Object-Model-Reference.md)
