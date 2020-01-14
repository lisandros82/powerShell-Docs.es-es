---
ms.date: 12/31/2019
keywords: powershell, cmdlet
title: La jerarquía del modelo de objetos de ISE
ms.openlocfilehash: 1ec5810fc5e7b765c2a08af83bce0415dd61a54b
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737039"
---
# <a name="the-ise-object-model-hierarchy"></a>La jerarquía del modelo de objetos de ISE

En este tema se muestra la jerarquía de objetos que forman parte del Entorno de scripting integrado (ISE) de Windows PowerShell. Windows PowerShell ISE se incluye en Windows PowerShell 3.0, 4.0 y 5.1. Haga clic en un objeto para ir a la documentación de referencia de la clase que define el objeto.

## <a name="psise-object"></a>Objeto $psISE

El objeto `$psISE` es el [objeto raíz](The-ObjectModelRoot-Object.md) de la jerarquía de objetos de Windows PowerShell ISE. Ubicado en el nivel superior, este objeto hace que estén disponibles para scripting los objetos siguientes:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

El objeto `$psISE.CurrentFile` es una instancia de la clase [ISEFile](The-ISEFile-Object.md).

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

El objeto `$psISE.CurrentPowerShellTab` es una instancia de la clase [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

El objeto `$psISE.CurrentVisibleHorizontalTool` es una instancia de la clase [ISEAddOnTool](The-ISEAddOnTool-Object.md). Representa la herramienta de complemento instalada que actualmente está acoplada al borde superior de la ventana de Windows PowerShell ISE.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

El objeto `$psISE.CurrentVisibleHorizontalTool` es una instancia de la clase [ISEAddOnTool](The-ISEAddOnTool-Object.md). Representa la herramienta de complemento instalada que actualmente está acoplada al borde derecho de la ventana de Windows PowerShell ISE.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

El objeto `$psISE.Options` es una instancia de la clase [ISEOptions](The-ISEOptions-Object.md). El objeto ISEOptions representa distintas configuraciones de Windows PowerShell ISE. Es una instancia de la clase Microsoft.PowerShell.Host.ISE.ISEOptions.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

El objeto `$psISE.PowerShellTabs` es una instancia de la clase [PowerShellTabCollection](The-PowerShellTabCollection-Object.md). Es una colección de todas las pestañas de PowerShell abiertas actualmente que representan los entornos de ejecución de Windows PowerShell disponibles en el equipo local o en equipos remotos conectados. Cada miembro de la colección es una instancia de la clase [PowerShellTab](The-PowerShellTab-Object.md).

## <a name="see-also"></a>Consulte también

- [Finalidad del modelo de objetos de scripting de Windows PowerShell ISE](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [La jerarquía del modelo de objetos de ISE](The-ISE-Object-Model-Hierarchy.md)
